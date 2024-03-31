# Desafio de Projeto 1 - Trabalhando com *Machine Learning* na Prática no *Azure ML*
Este desafio de projeto foi proposto no *Bootcamp AI Fundamentals* da DIO, utilizando-se de materiais disponibilizados pelo Microsoft Learn.

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

2. Na seção ***4 - Task settings***, selecionar *rentals (Integer)* no campo ***Target column*** e selecionar ***View additional configuration settings***.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/38838d57-d0c2-4373-b6e1-39bd9b6a06f2)
