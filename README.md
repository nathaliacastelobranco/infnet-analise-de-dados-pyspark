#  Análise de dados com PySpark

**Nathalia Castelo Branco**

Este repositório contém o desenvolvimento das **duas etapas do trabalho final** da disciplina de **Análise de dados com PySpark**, aplicando o ecossistema **Apache Spark** para análise e modelagem de dados.

---

## Estrutura do Trabalho

O projeto foi dividido em **duas partes**, que integram os conceitos de processamento distribuído e aprendizado de máquina.

### Parte I - Análise Exploratória e Consultas com SparkSQL

Nesta etapa, o objetivo foi **refazer as consultas e análises desenvolvidas previamente em Hadoop/Hive**, agora utilizando o **PySpark** e o módulo **SparkSQL** para leitura, transformação e consulta de grandes volumes de dados.

#### Objetivos
- Carregar dados do CAGED (Cadastro Geral de Empregados e Desempregados) em formato Parquet que já estava salvos no Google Cloud Storage (Carga feita no trabalho [Infraestrutura Hadoop](https://github.com/nathaliacastelobranco/infnet-infraestrutura-hadoop)).  
- Reproduzir consultas SQL realizadas anteriormente no Hive.  
- Aplicar funções de agregação e ordenação (COUNT, SUM, AVG, GROUP BY).  
- Criar **gráficos exploratórios** em Python (Matplotlib e Seaborn) para facilitar a visualização dos resultados.
  
#### Jupyter Notebook

A análise de dados está no arquivo `01_EDA_Análise_de_dados_com_PySpark` deste repositório.

---

### Parte II - Predição de Custos de Seguro de Saúde com PySpark MLlib

Nesta segunda etapa, foi desenvolvido um **modelo de regressão linear** utilizando o módulo **MLlib** do PySpark, com base no *Medical Cost Personal Dataset**.

####  Objetivos
- Prever o valor (`charges`) do seguro de saúde de uma pessoa com base em variáveis demográficas e comportamentais.  
- Aplicar técnicas de **análise exploratória**, **correlação de Pearson** e **modelagem supervisionada**.  
- Avaliar o desempenho do modelo por meio das métricas **RMSE** e **R²**.

#### Dicionário de Dados

| Variável | Tipo | Descrição | Unidade / Categoria |
|-----------|------|------------|----------------------|
| `age` | Numérica | Idade do beneficiário. | Anos |
| `sex` | Categórica | Sexo biológico (`male`, `female`). | - |
| `bmi` | Numérica | Índice de Massa Corporal. | kg/m² |
| `children` | Numérica | Quantidade de filhos/dependentes. | Número |
| `smoker` | Categórica | Indica se o beneficiário é fumante (`yes`, `no`). | - |
| `region` | Categórica | Região geográfica de residência (`northeast`, `southeast`, `southwest`, `northwest`). | - |
| `charges` | Numérica | Valor total cobrado pelo plano de saúde (variável alvo). | USD |

#### Metodologia

1. **Leitura e pré-processamento dos dados:** conversão de colunas categóricas em numéricas com `StringIndexer`.  
2. **Análise exploratória:** cálculo da correlação de Pearson e geração de heatmap de correlação.  
3. **Treinamento do modelo:** `LinearRegression` com divisão `train/test` (80/20).  
4. **Avaliação:** cálculo das métricas `RMSE` e `R²`.  

#### Resultados Obtidos
- **RMSE:** 6392.75  
- **R²:** 0.719  

O modelo explica cerca de **72% da variabilidade dos custos de seguro de saúde**, com erro médio de aproximadamente **US$ 6.392**, indicando bom ajuste linear aos dados.

#### Jupyter Notebook

O modelo de regressão linear está no arquivo `02_MLib_Análise_de_dados_PySpark` deste repositório.


#### Sugestões de Melhoria
- Aplicar codificação *One-Hot Encoding* nas variáveis categóricas.  
- Testar modelos não lineares como Random Forest.  

