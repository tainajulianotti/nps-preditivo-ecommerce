# 📦 NPS Preditivo — Tech Challenge Fase 1
**FIAP PosTech | Pós-Graduação em Data Science**

Tainá Julianotti

---

## 🎯 Objetivo do projeto

Este projeto tem como objetivo identificar os principais fatores operacionais que influenciam a satisfação de clientes em um e-commerce — medida pelo **Net Promoter Score (NPS)** — e explorar como dados de pedidos, logística e atendimento podem ser usados para antecipar a experiência do cliente antes mesmo da aplicação da pesquisa.

A pergunta orientadora do trabalho é:

> **Quais fatores operacionais realmente determinam se um cliente se tornará promotor ou detrator da marca — e como a empresa pode agir de forma proativa?**

---

## 📁 Estrutura do repositório

```
├── data/
│   └── desafio_nps_fase_1.csv       # Base de dados original (não versionada no Git)
│
├── notebooks/
│   └── eda_nps.ipynb                # Análise exploratória completa (EDA)
│
├── reports/
│   ├── 01_distribuicao_nps.png
│   ├── 02_correlacoes_nps.png
│   ├── 03_boxplots_segmentos.png
│   ├── 04_recompra_segmento.png
│   ├── 05_ruptura_atraso.png
│   ├── 06_ruptura_atendimento.png
│   ├── 07_nps_regiao.png
│   ├── 08_nps_faixa_etaria.png
│   └── 09_nps_tenure.png
│
└── README.md
```

---

## 📊 Descrição da base de dados

A base contém **2.500 registros** de pedidos de um e-commerce, com informações sobre o pedido, logística, atendimento e a avaliação NPS do cliente.

| Coluna | Descrição |
|---|---|
| `customer_id` | Identificador único do cliente |
| `order_id` | Identificador único do pedido |
| `customer_age` | Idade do cliente |
| `customer_region` | Região geográfica (Sul, Sudeste, Norte, Nordeste, Centro-Oeste) |
| `customer_tenure_months` | Tempo de relacionamento com a empresa (meses) |
| `order_value` | Valor total do pedido (R$) |
| `items_quantity` | Quantidade de itens no pedido |
| `discount_value` | Valor de desconto aplicado (R$) |
| `payment_installments` | Número de parcelas do pagamento |
| `delivery_time_days` | Tempo total de entrega (dias) |
| `delivery_delay_days` | Dias de atraso na entrega |
| `freight_value` | Valor do frete (R$) |
| `delivery_attempts` | Número de tentativas de entrega |
| `customer_service_contacts` | Número de contatos com o atendimento |
| `resolution_time_days` | Tempo para resolução de problemas (dias) |
| `complaints_count` | Número de reclamações registradas |
| `repeat_purchase_30d` | Recompra em 30 dias (0 = não, 1 = sim) |
| `csat_internal_score` | Score interno de satisfação (0 a 10) |
| `nps_score` | **Nota NPS do cliente (0 a 10)** — variável target |

---

## 🔬 Metodologia

### 1. Entendimento do negócio
Análise do problema de negócio, importância do NPS para e-commerce e identificação das áreas que se beneficiam dos insights (logística, atendimento, produto, pricing, CRM).

### 2. Definição da variável target
O `nps_score` foi definido como variável alvo e segmentado conforme a metodologia padrão NPS:
- **Promotores:** nota 9–10
- **Neutros:** nota 7–8
- **Detratores:** nota 0–6

### 3. Análise Exploratória (EDA)
A EDA foi conduzida com foco em negócio, respondendo:
- Qual a distribuição atual de promotores, neutros e detratores?
- Quais variáveis operacionais têm maior correlação com o NPS?
- Em que ponto (atraso, número de contatos) a satisfação entra em colapso?
- Qual o impacto do NPS na recompra em 30 dias?
- Existem diferenças por região, faixa etária ou tempo de relacionamento?

---

## 📈 Principais achados

- **80% dos clientes são Detratores** — NPS da empresa muito abaixo do benchmark de mercado (30–50 pontos para e-commerce)
- **Atraso na entrega** é o fator com maior correlação negativa com o NPS (r = -0.60). A partir de **3 dias de atraso**, o NPS médio cai abaixo de 3
- **Reclamações** têm segunda maior correlação negativa (r = -0.50)
- **Contatos com atendimento**: cada contato adicional reduz o NPS em ~0.8 pontos. A partir do 3º contato, o cliente já está na zona de Detrator
- **Recompra em 30 dias**: Promotores recompram 100% das vezes; Detratores, 0% — impacto financeiro direto e imediato
- **Centro-Oeste** apresenta o menor NPS médio entre as regiões

---

## ⚙️ Como reproduzir os resultados

### Pré-requisitos

- Python 3.9+
- Bibliotecas: `pandas`, `numpy`, `matplotlib`, `seaborn`

Instale as dependências:
```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Passos

1. Clone o repositório:
```bash
git clone https://github.com/tainajulianotti/nps-preditivo-ecommerce.git
cd nps-preditivo-fase1
```

2. Adicione o arquivo de dados na pasta `data/`:
```
data/desafio_nps_fase_1.csv
```

3. Abra o notebook:
```bash
jupyter notebook notebooks/notebook_analise_exploratoria.ipynb
```

4. Execute todas as células em ordem (`Kernel > Restart & Run All`)

Os gráficos serão salvos automaticamente na pasta `reports/`.

---

## Referencias

https://www.salesforce.com/br/blog/net-promoter-score/
https://www.sults.com.br/blog/nps-para-franquias/
https://www.tabcut.com/blog/post/supply-chain-for-e-commerce-companies

---
