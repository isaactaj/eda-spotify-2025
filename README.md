# Análise Exploratória: O Impacto do Conteúdo Explícito no Spotify

**Uma investigação baseada em dados sobre como a classificação "Explicit" afeta a popularidade e o engajamento de artistas e faixas na plataforma (Global 2025).**

---

## Sobre o Projeto

Este projeto de Análise Exploratória de Dados (EDA) busca validar uma hipótese de negócio recorrente na indústria musical: **O conteúdo explícito atua como um fator de impulsionamento de popularidade?**

Para garantir que os resultados não fossem apenas reflexo de variáveis isoladas, a análise foi estruturada em três camadas metodológicas:
1. **Visão Macro:** Comparação geral de todo o catálogo.
2. **Segmentação de Mercado:** Análise dividida pelo porte do artista (Emerging, Mid, Top).
3. **Análise Intra-Artista:** Estudo de caso isolando o catálogo de artistas gigantes (Drake, Taylor Swift e Bad Bunny).

**Dataset:** 8.582 músicas e 2.548 artistas.

---

## Arquitetura e Pipeline de Dados

Diferente de análises convencionais baseadas em arquivos locais (CSV na memória), este projeto simulou um ambiente real de produção corporativa, separando o armazenamento, o processamento e a visualização:

1. **Sourcing:** Extração do dataset bruto do **Kaggle** (Spotify Global 2025).
2. **Ingestão e Storage:** Os dados foram carregados no **Google BigQuery**, utilizando a infraestrutura de Data Warehouse da GCP.
3. **ETL & Limpeza (SQL):** Todo o tratamento de dados, limpeza de valores nulos, padronização de tipos e agregações iniciais foram realizados via **SQL** nativo, processado diretamente pelo motor do BigQuery.
4. **Orquestração e Visualização:** O ambiente em **Python (Google Colab)** atuou apenas como cliente. A biblioteca `google-cloud-bigquery` enviou as requisições, e o Pandas/Matplotlib consumiram os dados já agregados e limpos para a geração de insights visuais.

---

## Stack Tecnológico

* **Google BigQuery (SQL):** Data Warehouse, ETL, agregações complexas e criação de métricas compostas.
* **Python (Pandas):** Manipulação de DataFrames e orquestração da API do BigQuery.
* **Python (Matplotlib):** Visualização de dados e storytelling visual.
* **Google Colab:** Ambiente de desenvolvimento e documentação do projeto.

---

## Principais Descobertas (TL;DR)

* **O Padrão é Real:** Faixas explícitas apresentam popularidade média **14,4% superior** no panorama global. Além de maior média, possuem menor desvio padrão, indicando um retorno de engajamento mais consistente.
* **A Alavanca dos Emergentes:** Artistas do tier "Emerging" possuem catálogos com proporção muito menor de músicas explícitas (18%). No entanto, quando utilizam, registram o **maior ganho relativo de popularidade (+13%)**, sugerindo que o selo funciona como tração de audiência em estágios iniciais de carreira.
* **Múltiplas Estratégias (Intra-Artista):** * Artistas como Drake (87% explícito) usam a tag como domínio de nicho (uso massivo).
  * Artistas como Taylor Swift (14% explícito) usam a tag como quebra de expectativa (uso cirúrgico), gerando saltos de até +14 pontos de popularidade quando a utilizam.
* **Maturidade Analítica (Score Composto):** A análise demonstrou que rankings puramente baseados em *volume* criam distorções de mercado. Foi desenvolvida uma métrica de **Score Composto (Volume × Popularidade)**, que filtrou falsos positivos (como artistas inativos com grandes catálogos) e revelou os verdadeiros líderes de mercado atuais.

---

## Como navegar neste projeto

1. **`eda_spotify.ipynb`**: Notebook principal contendo a conexão com o BigQuery, as queries SQL executadas e os gráficos gerados.
2. *(Opcional)* As queries de limpeza e preparação de dados executadas diretamente no BigQuery podem ser encontradas documentadas no corpo do notebook.

---

## Autor

**Isaac Trindade** *Analista de Dados* [LinkedIn](https://www.linkedin.com/in/isaac-araujo-junior/)
