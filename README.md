# Previsão de Vendas - Açaí do Jezão 🍦📊

Bem-vindo ao repositório do projeto **Previsão de Vendas - Açaí do Jezão**, uma solução de Machine Learning desenvolvida para otimizar a produção de açaí e sorvete localizada na 
cidade de Serrolândia-Bahia. Este projeto adapta o desafio "Prevendo Vendas de Sorvete" da DIO, utilizando dados reais de vendas por dia da semana para prever a demanda e reduzir 
desperdícios enquanto maximiza lucros. 🚀

## Descrição do Projeto

Imagine que você é o proprietário do **Açaí do Jezão** e percebeu que as vendas variam bastante dependendo do dia da semana. Sem um planejamento adequado, posso produzir mais açaí 
e sorvete do que o necessário (gerando prejuízo) ou menos do que a demanda (perdendo vendas). Para resolver isso, desenvolvi um modelo preditivo com Machine Learning usando Python, 
scikit-learn e MLflow, rodando localmente no Jupyter Notebook.

### Objetivo
- **Treinar um modelo** de regressão para prever vendas de açaí com base no dia da semana.
- **Registrar o modelo** com MLflow para reprodutibilidade.
- **Otimizar produção** antecipando a demanda diária.

## Estrutura do Repositório

- **`inputs/`**: Contém o arquivo original de dados (`Vendas projeto no Azure.xlsx`) e um texto com a descrição inicial dos dados ("Dados de vendas reais da loja Açaí do Jezão.").
- **`vendas_acai.csv`**: Dados processados e salvos como CSV para reprodutibilidade.
- **`scripts/`**: Notebook Jupyter ou scripts Python (ex: `Vendas_Jezão.ipynb`) com o código completo.
- **`outputs/`**: Gráficos gerados (ex: `Distribuição_de_vendas_gráficas.png`, `Predições_vs_vendas_reais.png`).
- **`README.md`**: Este arquivo com a documentação.

## Processo de Desenvolvimento

### 1. Coleta e Preparação dos Dados
- Carreguei dados reais de vendas da loja, com colunas `data`, `vendas` e `dia_semana`.
- Converti datas seriais do Excel para formato datetime e removi valores inválidos (zeros).
- Salvei como `vendas_acai.csv` para facilitar o uso futuro.

### 2. Análise Exploratória de Dados (EDA)
- Gerei um boxplot de vendas por dia da semana (veja [Média de vendas por dia.png](#)).
  - **Insight**: Vendas são significativamente maiores nos fins de semana (Sábado e Domingo, média ~500-600) e menores em dias úteis (ex: Segunda ~80).
- Identifiquei padrões sazonais que podem guiar a produção.

### 3. Modelagem
- Usei um pipeline com `OneHotEncoder` para transformar `dia_semana` em features numéricas e `LinearRegression` como modelo base.
- Dividi os dados em treino (80%) e teste (20%).

### 4. Treinamento e Avaliação
- Treinei o modelo e avaliei com RMSE (~150) e R² (~0.5), indicando uma previsão razoável, mas com espaço para melhorias.
- Criei um gráfico de predições vs vendas reais ([Predições vs vendas reais.png](#)) para visualizar a performance.

### 5. Registro com MLflow
- Registrei o modelo como "modelo_acai" usando MLflow, logando métricas, parâmetros e artefatos.
- O dashboard local (http://localhost:5000 com `python -m mlflow ui`) permite rastrear os runs.

### 6. Previsões
- Salvei o modelo como `modelo_acai.pkl` e testei uma previsão para Sábado (~400 vendas), útil para planejar estoque.

## Resultados e Insights
- **Padrão de Vendas**: Fins de semana (Sábado/Domingo) têm picos de vendas, sugerindo maior produção nesses dias.
- **Desafios**: O R² de 0.5 indica que outras variáveis (ex: temperatura, feriados) poderiam melhorar o modelo.

## Possibilidades Aprendidas
- **Reprodutibilidade**: Uso de MLflow para rastrear experimentos é essencial para projetos colaborativos.
- **Escalabilidade**: Planejo migrar para Azure para pipelines mais robustos.
- **Customização**: Adaptei o desafio de sorvetes para açaí, aplicando conceitos reais à minha loja.
