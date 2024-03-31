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

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/dc9ce009-d26f-4dbd-add0-aa4caa036f62)

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/6c2246c7-68f4-498a-b5aa-cdfc26e1ae68)

## Acessando o Machine Learning Studio

1. No *Workspace* criado, selecionar ***Launch studio***.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/25bd8352-c4bf-4ab1-ba3d-80cf8b326994)

2. No *Machine Learning Studio* será apresentada a seguinte tela, a partir da qual será possível prosseguir na construção de fluxos de trabalho de *Machine Learning* em um ambiente de desenvolvimento visual.

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/8e499083-c51e-41c0-aabd-c2b42e122540)

## Criando um Job Automatizado de ML

A opção "Automated ML" permite experimentar múltiplos algoritmos e p

![image](https://github.com/danielfscosta/dio-aifundamentals-projeto1-azml/assets/69484807/d8cc153e-4ccf-4769-9dd5-03faab87506d)



Para excluir o seu espaço de trabalho:

No portal do Azure, na página Grupos de recursos, abra o grupo de recursos que você especificou ao criar o seu espaço de trabalho de Azure Machine Learning.
Clique em Excluir grupo de recursos, digite o nome do grupo de recursos para confirmar que deseja excluí-lo e selecione Excluir.
