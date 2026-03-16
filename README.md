# 📊 Projeto de Data Science: Previsão de Intenção de Compra Online

## 📌 Objetivo do Projeto

Este projeto tem como objetivo analisar o comportamento dos clientes de uma campanha de marketing e desenvolver um modelo de **Machine Learning** capaz de prever a **intenção de compra online** dos clientes.

A base original utilizada foi:

`marketing_campaign.csv`

Após o processo de limpeza e preparação, foi gerada uma nova base analítica:

`campaign_analytics_base.csv`

Essa base contém as variáveis tratadas e prontas para análise e modelagem.

---

# 📂 1. Preparação e Limpeza dos Dados

## Carregamento dos dados

O dataset `marketing_campaign.csv` foi carregado e as colunas foram **renomeadas para português** com o objetivo de melhorar a legibilidade e interpretação das variáveis durante a análise.

---

## Tratamento de valores nulos

Foram identificados valores ausentes na coluna:

`renda_anual_da_familia`

Para preservar a distribuição dos dados e evitar distorções, os valores faltantes foram preenchidos utilizando **a mediana da variável**.


---

## **Análise de Outliers**


<img width="1990" height="1122" alt="image" src="https://github.com/user-attachments/assets/8a6759ef-e7fd-4ceb-bf29-3a64b9f7d3b0" />


### **Decisão**

A maioria dos outliers foi mantida, pois representam clientes de alto valor, comportamento comum em bases de marketing e consumo.

Entretanto, foram identificados valores inconsistentes na variável ano_nascimento, indicando possíveis erros de cadastro.

Esses registros foram removidos.


### Matriz de Correlação das Variáveis Numéricas

<img width="1337" height="1141" alt="image" src="https://github.com/user-attachments/assets/9c1c1a88-ebc9-4cad-a714-1955d2c4e0f7" />


### Remoção de variáveis irrelevantes

Algumas variáveis apresentaram baixa correlação com a variável alvo, como:

* reclamacoes

* ultima_compra

Essas variáveis foram removidas para simplificar o modelo e reduzir ruído.

---

# 📊 2. Análise Exploratória de Dados (EDA)

Durante a análise exploratória foram identificados padrões importantes no comportamento dos clientes.

**Relação entre Renda Anual, Compras na Loja e Compras no Site da Empresa**

<img width="1068" height="590" alt="image" src="https://github.com/user-attachments/assets/2449e56b-0799-4c7d-b003-7a0cc69f7747" />

* Este lmplot (gráfico de dispersão com linha de regressão) é muito útil. Ele revela uma correlação positiva entre renda_anual_da_familia e compras_loja. Clientes com renda mais alta tendem a fazer mais compras na loja física. A coloração pelos pontos de compras_site_empresa (0: Não Comprou, 1: Comprou) é crucial: você provavelmente notará que os pontos azuis (clientes que compraram online) estão mais concentrados na parte superior direita do gráfico, indicando que clientes com alta renda e que já compram bastante na loja física também são mais propensos a comprar no site da empresa. Isso sugere um perfil de cliente de alto valor e multicanal.


**Clientes com maior renda anual da família apresentam:**

* maior número de compras em loja

* maior probabilidade de compras no site

Isso sugere um perfil de cliente multicanal e de alto valor.

### Gastos com Vinhos

**Foi observada forte correlação positiva entre:**

  
  <img width="859" height="547" alt="image" src="https://github.com/user-attachments/assets/4f9059fb-d7a5-45a8-b760-ce52d18d7e2b" />


**Clientes que gastam mais em vinhos são significativamente mais propensos a comprar online.**

### Número de Crianças

Observou-se uma correlação negativa.

Clientes com menos crianças (0 ou 1) apresentam maior propensão a realizar compras online.

<img width="850" height="548" alt="image" src="https://github.com/user-attachments/assets/8c433169-9a91-4f66-b0b7-b61452588e49" />


### Frequência de Visitas ao Site

Clientes que realizam compras online apresentam maior número de visitas ao site por mês, indicando alto nível de engajamento com a plataforma.

<img width="855" height="547" alt="image" src="https://github.com/user-attachments/assets/5805d3c3-2816-4dfa-8689-f89fb9399bc3" />


### Escolaridade

**Clientes com maior nível educacional demonstraram maior probabilidade de comprar online.**

* Graduação

* Mestrado

* Doutorado


<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/c868594b-295e-47c3-9289-f14dcf8fafbd" />

**Isso indica que escolaridade é um fator mais relevante que estado civil na intenção de compra.**

### Estado Civil

<img width="1189" height="590" alt="image" src="https://github.com/user-attachments/assets/c54c1a3a-0ae8-40db-8fa2-d2feadd1a5e5" />

**Apesar de Married e Together representarem a maioria da base, o estado civil não demonstrou grande poder preditivo isoladamente.**

---

# 🤖 3. Modelagem de Machine Learning
**Separação de dados**

Os dados foram divididos em:

* 80% treino

* 20% teste

## Padronização dos dados

As variáveis numéricas foram padronizadas utilizando:

**StandardScaler**

para garantir melhor desempenho do modelo.


---

# 🌳 Modelo 1: Random Forest

## Resultados

**Acurácia:** 0.93

**Recall (classe compra):** 0.96

Isso indica que o modelo possui excelente capacidade de identificar clientes que realmente irão comprar.

**Matriz de Confusão**

O modelo apresentou apenas:

10 falsos negativos

Ou seja, poucos clientes compradores deixaram de ser identificados.

# 📈 Modelo 2: Regressão Logística

## Resultados

**Acurácia:** 0.84

**Recall:** 0.84

**Matriz de Confusão**

Foram identificados:

* 36 falsos negativos

Ou seja, o modelo deixou de identificar uma quantidade maior de compradores.

---

# 🏆 Comparação dos Modelos

| Modelo              | Acurácia | Recall |
| ------------------- | -------- | ------ |
| Random Forest       | 0.93     | 0.96   |
| Regressão Logística | 0.84     | 0.84   |

--- 


# 📊 Conclusão da Modelagem

O modelo **Random Forest** apresentou desempenho superior em todas as métricas avaliadas.

Principais vantagens observadas:

* maior acurácia

* maior capacidade de identificar compradores

* menor número de falsos negativos

* melhor generalização no conjunto de teste

Portanto, o Random Forest foi selecionado como o modelo final para previsão de intenção de compra online.

---

# **Insights (Foco no Valor de Negócio):**
1. **Poder Preditivo e Otimização de Marketing:**

* **Ponto-chave:** "Desenvolvemos um modelo de Machine Learning (Random Forest) com 93% de acurácia e impressionantes 96% de recall na identificação de clientes com intenção de compra online.
* **Impacto:** Isso significa que a empresa pode identificar com alta precisão seus potenciais compradores, otimizando campanhas de marketing, reduzindo custos com anúncios para quem não tem interesse e aumentando a taxa de conversão ao direcionar ofertas personalizadas para os clientes certos.

2. **Segmentação de Clientes Acionável:**

* Ponto-chave: A análise revelou perfis de clientes claros: aqueles com maior renda, menos filhos, maior gasto em vinhos e níveis de escolaridade mais altos são os mais propensos a comprar online.
* **Impacto:** Esses insights permitem a criação de segmentos de clientes altamente qualificados, possibilitando estratégias de marketing mais eficazes e personalizadas. Por exemplo, campanhas para clientes de alta renda com baixo número de filhos teriam um ROI (Retorno sobre Investimento) potencialmente muito maior.

3. **Engajamento e Experiência do Cliente:**

* **Ponto-chave:** Identificamos que clientes que visitam o site com maior frequência são mais propensos a comprar.
* **Impacto:** Este insight pode guiar iniciativas para melhorar o engajamento no site e a experiência do usuário, convertendo visitantes em compradores. Sugere também que podemos reter clientes já engajados com ações específicas para estimular a compra online."

# 🚀 Possíveis Melhorias Futuras

**Algumas melhorias que podem ser implementadas no projeto:**

* otimização de hiperparâmetros (GridSearch ou RandomSearch)

* teste com modelos adicionais (XGBoost, LightGBM)

* deploy do modelo em API para uso em aplicações de marketing


---


# 🧠 Tecnologias Utilizadas

* Python

* Pandas

* Numpy

* Scikit-learn

* Matplotlib

* Seaborn

---

📎 **Projeto desenvolvido por:** Diego Kaique

🔗 **LinkedIn:** [https://www.linkedin.com/in/diego-kaique-9ba3697b]

📧 **Contato:** [kaique_0208@hotmail.com]
