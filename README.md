# Desafio de Projeto 1 - Trabalhando com *Machine Learning* na Prática no *Azure ML*
Este desafio de projeto foi proposto no *Bootcamp AI Fundamentals* da DIO, utilizando-se de materiais disponibilizados pelo Microsoft Learn neste [link](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html).

## Criação de um Workspace do *Azure Machine Learning*
O início deste projeto considera que o usuário já possua uma assinatura ativa no Azure. Para o uso do *Azure Machine Learning* é necessário inicialmente provisionar um *Workspace*, onde em seguida, será possível utilizar dos recursos aqui mencionados. Seguem os passos para criação do *Workspace*:

1. Acessar o [https://portal.azure.com](portal do *Azure*) utilizando as credenciais de uma conta Microsoft.

2. Pesquisar pelo serviço **Azure Machine Learning**. No diretório padrão, selecionar **+ Create** e **New Workspace**. O novo *Workspace* deve possuir as seguintes configurações:

- ***Subscription***: Escolher a assinatura a ser utilizada na criação do recurso;
- ***Resource group***: Grupo de recursos onde o Workspace será alocado. Caso não exista um grupo de recursos definido, um novo poderá ser criado neste passo através do link *Create new*;
- ***Name***: Escolher um nome único para o *Workspace* que obedeça aos seguintes requisitos: possuir entre 3 e 33 caracteres, sendo mandatório que o primeiro seja alfanumérico (os restantes podem possuir hífens e subtraço/underscore), não sendo permitida a inclusão de espaços;
- ***Region***: Selecionar a região em que serão provisionados os recursos, atentando-se para a diferença de precificação dos recursos em cada região;
- ***Storage account***: Será criada nova *Azure Storage Account* para o *Workspace*. Não é necessário modificar os valores padrão apresentados;
- ***Key vault***: Será criada nova *Azure Key Vault* para o *Workspace*. Não é necessário modificar os valores padrão apresentados;
- ***Application insights***: Será criada nova *Azure Application Insights* para o *Workspace*. Não é necessário modificar os valores padrão apresentados;
-  ***Container registry***: Selecionar *None*. Um recurso será criado automaticamente na primeira vez que for realizado *deploy* de um modelo para um conteiner, não sendo necessário especificá-lo no momento;

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/b4e0a49f-612b-43ae-8873-bfe0b7750e13)

3. Selecionar ***Review + Create*** e então, selecionar ***Create***. Aguardar alguns minutos até que todos os recursos sejam criados e então, selecionar  ***Go to resource***.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/e9661c6a-6dac-4e7d-ad0a-19f3dd77a2eb)

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/c6957096-1e18-4a40-878f-88a7e1fdcee8)

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/6c2246c7-68f4-498a-b5aa-cdfc26e1ae68)

## Acessando o Machine Learning Studio

1. No *Workspace* criado, selecionar ***Launch studio***.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/25bd8352-c4bf-4ab1-ba3d-80cf8b326994)

2. No *Machine Learning Studio* será apresentada a seguinte tela, a partir da qual será possível prosseguir na construção de fluxos de trabalho de *Machine Learning* em um ambiente de desenvolvimento visual.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/8e499083-c51e-41c0-aabd-c2b42e122540)

## Criando um Job Automatizado de ML

A opção "Automated ML" permite experimentar múltiplos algoritmos e parâmetros para treinar múltiplos modelos e identificar o melhor para o conjunto de dados. Neste caso, será utilizado um conjunto de dados do histórico de aluguéis de bicicletas que deveriam ser esperados em um determinado dia, baseado em características sazonais e meteorológicas.

1. No Azure Machine Learning Studio, selecionar ***Automated ML*** da seção *Authoring* e, em seguida, selecionar ***+ New Automated ML job***

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/d8cc153e-4ccf-4769-9dd5-03faab87506d)

2. Na seção ***1 - Training Method*, selecionar ***Train automatically*** e então, ***Start configuring job***.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/f4339613-1e2d-40b7-a285-20d889644dbe)

3. Na seção ***2 - Basic Settings***, definir as configurações ou escolher conforme o sugerido abaixo e selecionar ***Next*** ao final.

- ***Job Name***: mslearn-bike-automl
- ***New experiment name***: mslearn-bike-rental
- ***Description***: Automated machine learning for bike rental prediction
- ***Tags***: A escolha de uma tag não faz-se necessária neste momento

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/b07e22e6-9693-4e6e-b75c-e2601b97287b)

4. Na seção ***3 - Task type & data***, escolher o tipo de tarefa a ser executada pelo modelo, conforme sugerido. Selecionar ***+ Create*** para iniciar a criação de um novo *Data Asset*.

- ***Select task type***: Regression

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/7a4c9931-8e37-49e1-9f4d-d27d555d4290)

## Criando um *Data Asset* (ativo de dados)

Nesta etapa serão definidas origem, tipo, formato, codificação, entre outros aspectos do conjunto de dados a ser analisado, de modo que o modelo possa utilizá-los e intepretá-los de maneira adequada.

1. Na seção ***1 - Data type***, definir as configurações conforme sugerido e selecionar ***Next*** ao final.

- ***Name***: bike-rentals
- ***Description***: Historic bike rental data
- ***Type***: Tabular

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/9a65a9df-2622-475e-b7a1-99f00b03433b)

2. Na seção ***2 - Data Source***, definir a fonte dos dados selecionando ***From web files***.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/bbf2af6a-7968-4b5f-a714-17965854fd34)

3. Na seção ***3 - Web URL***, especificar a URL pública por onde os dados serão recuperados, conforme sugerido.

- ***Web URL***: https://aka.ms/bike-rentals
- ***Skip data validation***: deixar desativado

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/1b4a7d31-a99f-40a0-b080-7c9fe7b9996f)

4. Na seção ***4 - Settings***, escolher configurações como formatação, delimitação, codificação, entre outras, conforme sugerido, que permitirão a correta extração e análise dos dados obtidos da fonte especificada. Ao final, selecionar ***Next*** para prosseguir para a próxima seção.

- ***File format***: Delimited
- ***Delimiter***: Comma
- ***Encoding***: UTF-8
- ***Column headers***: Only first file has headers
- ***Skip rows***: None
- ***Dataset contains multi-line data***: Não selecionar

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/e4ebb0ee-3b2d-4b75-b627-2bd8d6a536e7)

5. Na seção ***5 - Schema***, deverão ser definidas as configurações de como os valores de cada coluna do conjunto de dados deverão ser convertidos. Para tal, todas as colunas deverão estar ativadas, com exceção da ***Path**, conforme observado na imagem abaixo. Após realizadas as configurações, selecionar ***Next***.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/3fd35774-acbf-4315-990b-cbd2bccc6ce8)

6. Na seção ***6- Review***, revisar as configurações e selecionar ***Create*** para criar o *Data Asset*.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/64f53b0d-a587-4e56-bf50-680b4c9fd314)

## Retornando à criação do Job Automatizado de ML

1. Na seção ***3 - Task type & data***, selecionar o conjunto de dados recém criado ***bike-rentals*** e selecionar ***Next*** para continuar o processo de criação.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/828902ef-cca7-4e53-a3b9-d2d178f46714)

2. Na seção ***4 - Task settings***, selecionar *rentals (Integer)* no campo ***Target column*** e clicar em ***View additional configuration settings***.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/38838d57-d0c2-4373-b6e1-39bd9b6a06f2)

3. Na tela ***Aditional Configuration***, escolher as configirações conforme sugerido e, ao final, selecionar ***Next***.

- ***Primary metric***: NormalizedRootMeanSquaredError
- ***Explain best model***: Não selecionar
- ***Enable ensemble stacking***: Não selecionar
- ***Use all supported models***: Não selecionar
- ***Allowed models***: Selecionar: RandomForest e LightGBM

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/bb32057d-6c33-4742-8888-7ecca6469253)
 
4. Ainda em ***4 - Task settings***, expandir a seção ***Limits***, escolher as configurações conforme sugerido e, ao final, selecionar ***Next***.

- ***Max trials***: 3
- ***Max concurrent trials***: 3
- ***Max nodes***: 3
- ***Metric score threshold***: 0.085
- ***Experiment timeout (minutes)***: 15
- ***Iteration timeout (minutes)***: 15
- ***Enable early termination***: Selecionar

**Validate and test**

- ***Validation type***: Train-validation split
- ***Percentage validation of data***: 10
- ***Test data***: None

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/8093ba17-ec80-473b-8d17-d19e300f04ef)

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/b44f741c-c68a-4c6e-82cf-7c60a0988c7f)

5. Na seção ***5 - Compute***, serão escolhidas configurações relacionadas aos recursos de computação, responsáveis pela execução do *job*. Caso exista alguma restrição de níveis de recursos para o tipo de conta, outras, de capacidades similares poderão ser escolhidas. As configurações abaixo sugeridas poderão ser replicadas. Ao final, selecione ***Next*** para prosseguir para próxima seção.

Obs: Recursos de computação mais robustos promovem maior rapidez na execução, entretanto, demandam maiores custos associados.

- ***Select compute type***: Serverless
- ***Virtual machine type***: CPU
- ***Virtual machine tier***: Dedicated
- ***Virtual machine size***: Standard_DS3_v2
- ***Number of instances***: 1

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/024c94a2-514a-43a7-bd7b-ae49cb74685d)

6. Na seção ***6 - Review*** é possível revisar e alterar, se necessário, as configurações do *job* antes de enviá-las. Ao final, ao selecionar ***Submit training job*, a execução iniciará automaticamente.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/21bd54eb-79ae-488f-a038-f02526829192)

## Executando o Automated ML Job e verificando os resultados

1. Após o envio das configurações na etapa anterior e o *job* iniciar sua execução, aguardar alguns minutos até que o campo ***Status** da aba ***Overview*** mude de *Running* para *Completed*.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/483edff4-25f1-447f-8953-3350014de41f)

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/1d8869c1-2257-4cc6-a502-984ca8ca4839)

Obs: Com a execução completa, informações sobre o melhor modelo treinado serão mostradas na seção ***Best model summary***, da aba ***Overview***. Poderá ser obtido maior detalhamento sobre o algoritmo para o melhor modelo ao clicar no nome sob o campo ***Algorithm name***.

2. Selecionar a aba ***Metrics*** para visualizar todas as métricas obtidas pela execução. Selecionar os gráficos ***residuals*** (que mostra as diferenças entre os valores reais e os previstos) e ***predicted_true*** (que compara os valores previstos e os valores verdadeiros), caso estes não sejam mostrados por padrão.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/16cb18d8-9597-4b6d-a52a-e7995c30f62a)

Obs: A métrica ***Normalized Squared Error*** alcançada e os valores previstos foram satisfatórios na execução.

## Implantando o modelo

1. Na aba ***Model*** (para o melhor modelo treinado pelo *job* de ML), selecionar ***Deploy*** e em seguida a opção ***Web service*** para implantar o modelo com as configurações abaixo relacionadas. Finalizadas as configurações, selecionar ***Deploy***.

- ***Name***: predict-rentals
- ***Description***: Predict cycle rentals
- ***Computer type***: Azure Container Instance
- ***Enable authentication***: Selecionar

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/95a2b0b4-1b48-4443-bf60-26e8208d21c1)

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/6b4c9416-31e1-4875-b5b5-9870292500c1)

2. Esperar alguns segundos até o início da implantação. Aguarde mais um tempo (5 ou 10 minutos) até que os campos ***Operation State*** e ***Deployment state*** da seção ***Endpoint Attributes*** (na aba ***Details***) apresentem os estados *Succeeded* e *Healthy*, respectivamente, o que indicam que a operação foi bem-sucedida.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/23fe7c76-151f-4ad0-b95f-767f2693bcc1)

## Testando o modelo implantado

1. Finalmente é possível testar o modelo implantado com valores de entrada definidos pelo utilizador. Para isso, selecionar ***Endpoints*** do menu ***Assets*** à esquerda, e abrir o *endpoint* ***predict-rentals***. Na aba ***Test***, insirerir no formato *JSON* os parâmetros a serem testados e selecionar ***Test***.

Obs: Durante a execução, foram utilizados os dados originais fornecidos no laboratório da Microsoft, que podem ser conferidos no arquivo [request.json](request.json) deste projeto. Entretanto, estes podem ser alterados de acordo com a necessidade do utilizador.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/2e3f2d61-478d-4f3d-bd77-2578fbef56e1)

2. Os resultados calculados pelo modelo sobre o número de bicicletas alugadas para os dados de entrada informados serão apresentados no campo ***Test results*** à direita, como pode ser observado na imagem anterior.

Obs: Os resultados obtidos neste experimento podem ser conferidos diretamente na imagem anterior ou no arquivo [response.json](response.json) deste projeto.

## Conclusão

É possível verificar o funcionamento do modelo treinado na previsão de respostas para dados de entrada definidos pelo utilizador. Para isso foram utilizados dados históricos de aluguéis e o modelo estima o número de aluguéis em um dia especificado, baseado em características sazonais e meteorológicas.

## IMPORTANTE: Limpeza dos recursos provisionados

1. Ao final do projeto, caso não seja mais necessária a experimentação utilizando o modelo, recomenda-se que os recursos provisionados sejam removidos para evitar o desperdício e cobranças sobre custos não previstos. Para tal, selecionar ***Endpoints*** do menu ***Assets*** à esquerda e em seguida o ***predict-rentals*** criado anteriormente. Selecionar ***Delete*** e confirmar a deleção do *endpoint*.

Obs: Mesmo deletados os recursos de computação, ainda será cobrada uma pequena parcela para a manutenção do *workspace* do *Azure Machine Learning studio* criado. Caso este não seja mais necessário, é recomendado removê-lo, bem como todos os demais recursos associados.

2. Para remover o *workspace* do *Azure Machine Learning studio* criado, bem como todos os recursos associados, retornar até o ***Portal do Azure*** e procurar pela página ***Resource Groups***. Selecionar o grupo de recursos especificado ao criar o *workspace* e em seguida ***Delete resource group***. Será solicitado que o nome do grupo de recursos seja informado para confirmar a remoção e é necessário finalmente selecionar ***Delete***.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/a74ba409-08bf-427e-b0a4-90c603b84772)

Ao final do processo, confirmar que não realmente não sejam listados recursos remanescentes utilizados no projeto.
