# MVP — Previsão de Cancelamento de Clientes (Churn) em Telecom

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MateusMMatos/mvp-churn-telco/blob/main/notebook.ipynb)

Projeto final (MVP) da Pós-Graduação em Análise de Dados com IA. Um projeto completo de Machine Learning que prevê quais clientes de uma operadora de telecom têm risco de cancelar o serviço (churn), permitindo à empresa agir antes e reduzir perdas.

O foco do MVP é demonstrar o fluxo completo de um projeto de ML — do problema à conclusão — com cada decisão justificada, solução reprodutível e bem documentada.

---

## O problema

Reter um cliente custa muito menos do que conquistar um novo. O objetivo é identificar clientes propensos a cancelar a partir de seu perfil (tempo de casa, tipo de contrato, serviços, forma de pagamento etc.).

- Tipo de tarefa: classificação binária supervisionada
- Variável-alvo: `Churn` (cancelou = 1 / permaneceu = 0)

## Os dados

- Dataset: [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) (base pública e fictícia da IBM)
- Volume: 7.043 clientes e 21 atributos
- Classes desbalanceadas: 73,5% permaneceram e 26,5% cancelaram
- Carregado diretamente por URL pública — o notebook roda sem upload, login ou token.

## Metodologia

1. Apresentação do problema e dos dados
2. Análise exploratória (EDA) — perfil de risco de cancelamento
3. Preparação dos dados (correção de tipos, nulos, codificação, padronização)
4. Divisão treino/teste estratificada, com pré-processamento em pipeline (sem vazamento de dados)
5. Modelagem: baseline, Regressão Logística e Random Forest
6. Otimização de hiperparâmetros (Grid Search com validação cruzada)
7. Avaliação crítica (overfitting, análise de erros, limitações)

## Resultados

| Modelo | Acurácia | Precisão | Recall | F1 |
|---|---|---|---|---|
| Baseline (sempre "não cancela") | 0,735 | 0,000 | 0,000 | 0,000 |
| Regressão Logística | 0,809 | 0,667 | 0,560 | 0,609 |
| Random Forest | 0,779 | 0,606 | 0,474 | 0,532 |
| Regressão Logística (otimizada) | 0,743 | 0,511 | 0,790 | 0,620 |

Modelo escolhido: Regressão Logística otimizada. Ela prioriza o recall (detecta cerca de 4 em cada 5 clientes que vão cancelar), o que é mais valioso para retenção do que a acurácia. É simples, interpretável e não apresenta overfitting.

## Como executar

Clique no botão "Open in Colab" acima e use Ambiente de execução > Executar tudo. Não é preciso instalar nada nem baixar dados.

## Tecnologias

Python, pandas, numpy, scikit-learn, matplotlib, seaborn.

## Estrutura

```
mvp-churn-telco/
├── notebook.ipynb              # O projeto completo (código e análise)
├── Telco-Customer-Churn.csv    # Dataset
└── README.md
```

---

Autor: Mateus M. Matos — Pós-Graduação em Análise de Dados com IA
