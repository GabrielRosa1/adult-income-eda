# Adult Income: EDA e Classificação

Projeto acadêmico da disciplina de Machine Learning do curso de Ciência da Computação do Insper, desenvolvido em duas etapas sobre a base **Adult Income Census**:

| Etapa | Conteúdo | Notebook | Relatório |
|---|---|---|---|
| **APS1: EDA** | Qualidade dos dados, análise exploratória, PCA e pipeline de pré-processamento | [`APS_EDA.ipynb`](APS_EDA.ipynb) · [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GabrielRosa1/adult-income-eda/blob/main/APS_EDA.ipynb) | [`docs/index.html`](docs/index.html) |
| **APS2: Classificação** | Modelos, seleção de hiperparâmetros, avaliação no teste, explicabilidade (SHAP) e discussão crítica | [`APS2_Classificacao.ipynb`](APS2_Classificacao.ipynb) · [![Abrir no Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GabrielRosa1/adult-income-eda/blob/main/APS2_Classificacao.ipynb) | [`docs/aps2.html`](docs/aps2.html) |

A documentação navegável das duas etapas é publicada com GitHub Pages a partir da pasta `docs/`.

## Sobre o projeto

O projeto investiga características demográficas, educacionais e profissionais associadas à faixa de renda anual de uma pessoa. A variável-alvo, `income`, divide os registros em duas classes:

- `<=50K`: renda anual de até US$ 50 mil;
- `>50K`: renda anual superior a US$ 50 mil.

## Base de dados

- **Nome:** Adult Income Census
- **Fonte:** [Kaggle — Adult Income Census](https://www.kaggle.com/datasets/anaghakp/adult-income-census) (fonte primária: [UCI Machine Learning Repository](https://doi.org/10.24432/C5XW20))
- **Registros na base original:** 31.947 (31.882 após remover 65 duplicatas)
- **Variáveis:** 12, incluindo a variável-alvo

## APS1: Análise Exploratória de Dados

1. Carregamento, inspeção e descrição das variáveis;
2. identificação de valores ausentes codificados como `?`, inconsistências e duplicatas;
3. análise do desbalanceamento do target e separação estratificada 80/20;
4. análises univariada, bivariada e multivariada;
5. tratamento justificado de outliers e transformação `log1p` em `fnlwgt`;
6. PCA nas variáveis numéricas;
7. pipeline de pré-processamento com `Pipeline` e `ColumnTransformer`.

**Principais achados:** 24,1% da base tem renda `>50K`; a escolaridade tem a associação mais clara com renda; a relação da idade com a renda é não linear; `fnlwgt` (peso amostral) tem distribuições semelhantes nas duas classes.

## APS2: Classificação

Com o mesmo split e o mesmo pipeline da APS1:

| Etapa | Resultado |
|---|---|
| Métrica de seleção | ROC-AUC, validação cruzada estratificada de 5 folds (mesmos folds para todos os modelos) |
| Dummy | AUC 0,500 (acurácia de 75,9% sem identificar ninguém de renda alta) |
| Regressão logística regularizada (`GridSearchCV`) | AUC 0,884 (L2, C = 1) |
| Random Forest (`RandomizedSearchCV`) | AUC 0,890; vence a logística nos 5 folds |
| Mudança no pipeline | Remoção de `fnlwgt`: AUC 0,8904 (empate), menos sobreajuste → **modelo final** |
| Teste (usado uma única vez) | AUC 0,884; com limiar 0,35: recall 75,6%, precisão 58,9%, F1 0,662 |
| Interpretação | Estado civil, escolaridade e idade lideram (coeficientes, permutação e SHAP) |
| Limitação principal | Recall de 60% para mulheres contra 78% para homens |

## Estrutura do repositório

```text
adult-income-eda/
├── APS_EDA.ipynb             # APS1: notebook da análise exploratória
├── APS2_Classificacao.ipynb  # APS2: notebook de modelagem (executado, com saídas)
├── README.md
└── docs/                     # Site publicado com GitHub Pages
    ├── index.html            # Relatório da APS1
    ├── aps2.html             # Relatório da APS2
    ├── aps2-notebook.html    # Notebook da APS2 renderizado (código e saídas)
    └── assets/               # Figuras das duas etapas
```

## Como executar

### Google Colab

Use os botões **Abrir no Colab** da tabela acima e execute as células em ordem. O notebook baixa a base automaticamente com `kagglehub` quando `adult_income.csv` não está presente.

> A APS2 leva cerca de 40 minutos num ambiente com 2 núcleos, por causa das duas buscas de hiperparâmetros da Random Forest.

### Ambiente local

```bash
git clone https://github.com/GabrielRosa1/adult-income-eda.git
cd adult-income-eda
pip install pandas numpy matplotlib seaborn scikit-learn shap kagglehub jupyter
jupyter notebook APS2_Classificacao.ipynb
```

## Tecnologias utilizadas

Python · Pandas · NumPy · Matplotlib · Seaborn · Scikit-learn · SHAP · Google Colab · GitHub Pages

## Autores

- Gabriel Martins Rosa
- João Pedro Baungartner

**Instituição:** Insper · **Curso:** Ciência da Computação · **Disciplina:** Machine Learning · **Professor:** Humberto Sandmann
