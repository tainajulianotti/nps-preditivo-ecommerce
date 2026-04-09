# NPS Preditivo — E-commerce

> Tech Challenge | Fase 1 | Pós-Tech FIAP — IA Scientist
> Autor: Taina Julianotti

---

## Sobre o projeto

Com o crescimento acelerado do e-commerce, empresas passam a lidar com volumes cada vez maiores de pedidos, entregas e interações com clientes. Mesmo com indicadores operacionais semelhantes, alguns clientes se tornam promotores da marca enquanto outros se tornam detratores — e essa diferença raramente é compreendida a tempo de agir.

Este projeto propõe transformar dados operacionais em **inteligência preditiva de satisfação do cliente**, antecipando o Net Promoter Score (NPS) antes mesmo da pesquisa ser aplicada. O objetivo é identificar quais fatores mais influenciam a experiência do cliente e apoiar áreas como logística, atendimento e estratégia na tomada de decisão proativa.

---

## Estrutura do repositório

```
nps-preditivo-ecommerce/
│
├── data/
│   └── base_nps.csv               # Base de dados histórica (pedidos, logística, atendimento)
│
├── notebooks/
│   ├── 01_entendimento_negocio.ipynb   # Análise conceitual e perguntas de negócio
│   ├── 02_definicao_target.ipynb       # Definição e justificativa da variável alvo
│   ├── 03_eda.ipynb                    # Análise Exploratória dos Dados
│   └── 04_modelo_preditivo.ipynb       # Pipeline completa do modelo de classificação
│
├── models/
│   └── modelo_nps.pkl             # Modelo treinado serializado
│
├── reports/
│   └── apresentacao_storytelling.pdf  # Slides para stakeholders não técnicos
│
└── README.md
```

---

## Base de dados

A base contém dados históricos de pedidos, entregas e interações com o atendimento ao cliente.

| Variável | Descrição |
|---|---|
| `customer_id` | Identificador único do cliente |
| `order_id` | Identificador único do pedido |
| `customer_age` | Idade do cliente |
| `customer_region` | Região geográfica do cliente |
| `customer_tenure_months` | Tempo de relacionamento com a empresa (meses) |
| `order_value` | Valor total do pedido |
| `items_quantity` | Quantidade de itens no pedido |
| `discount_value` | Valor de desconto aplicado |
| `payment_installments` | Número de parcelas |
| `delivery_time_days` | Tempo total de entrega (dias) |
| `delivery_delay_days` | Dias de atraso na entrega |
| `freight_value` | Valor do frete |
| `delivery_attempts` | Número de tentativas de entrega |
| `customer_service_contacts` | Contatos com o atendimento |
| `resolution_time_days` | Tempo para resolução de problemas (dias) |
| `complaints_count` | Número de reclamações registradas |
| `repeat_purchase_30d` | Recompra em até 30 dias (0 = não, 1 = sim) |
| `csat_internal_score` | Score interno de satisfação |
| `nps_score` | Nota NPS do cliente (0 a 10) — variável alvo |

---

## Metodologia

O projeto foi estruturado em quatro etapas principais:

### 1. Entendimento do negócio
Análise conceitual do problema: por que o NPS é crítico para e-commerce, quais áreas se beneficiam de uma visão preditiva e como a satisfação do cliente impacta recompra, boca a boca e market share.

### 2. Definição da variável alvo
A variável `nps_score` (nota de 0 a 10) foi escolhida como alvo por representar diretamente a percepção do cliente ao final da jornada de compra. Para o modelo preditivo, ela foi binarizada em duas classes:
- **Satisfeito:** notas 9 ou 10 (promotores)
- **Insatisfeito:** notas de 0 a 8 (neutros e detratores)

### 3. Análise Exploratória dos Dados (EDA)
Investigação dos padrões da base com foco em negócio:
- Distribuição do NPS por região, faixa de valor e tipo de cliente
- Correlação entre atrasos na entrega e notas baixas
- Perfil dos detratores vs. promotores
- Identificação de variáveis com maior poder explicativo

### 4. Modelo preditivo
Pipeline de classificação binária para prever se um cliente será promotor ou detrator antes da pesquisa de NPS:
- Pré-processamento e engenharia de features
- Separação treino/teste (80/20)
- Treinamento com Random Forest
- Avaliação com Acurácia, F1-Score e Matriz de Confusão
- Interpretação das variáveis mais importantes (feature importance)

---

## Como reproduzir os resultados

### Pré-requisitos

- Python 3.9+
- Jupyter Notebook ou JupyterLab

### Instalação das dependências

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### Executando os notebooks

1. Clone o repositório:
```bash
git clone https://github.com/tainajulianotti/nps-preditivo-ecommerce.git
cd nps-preditivo-ecommerce
```

2. Inicie o Jupyter:
```bash
jupyter notebook
```

3. Execute os notebooks na ordem numérica dentro da pasta `notebooks/`.

---

## Principais insights

- Atrasos na entrega acima de 3 dias estão fortemente associados a notas NPS baixas
- Clientes que contataram o atendimento mais de 2 vezes têm probabilidade significativamente maior de se tornarem detratores
- Regiões com maior tempo médio de entrega apresentam NPS sistematicamente inferior
- Clientes com histórico de recompra tendem a ser mais tolerantes a falhas pontuais

---

## Tecnologias utilizadas

- **Python** — linguagem principal
- **Pandas / NumPy** — manipulação e análise de dados
- **Matplotlib / Seaborn** — visualização
- **Scikit-learn** — modelo preditivo
- **Jupyter Notebook** — ambiente de desenvolvimento

---

## Referências

- ABCOMM — Associação Brasileira de Comércio Eletrônico
- Reichheld, F. (2003). *The One Number You Need to Grow*. Harvard Business Review.
- ABRALOG — Associação Brasileira de Logística

---

*Projeto desenvolvido para o Tech Challenge da Fase 1 da Pós-Tech FIAP.*
