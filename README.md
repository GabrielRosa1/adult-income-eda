# Adult Income EDA

Análise Exploratória de Dados da base **Adult Income Census**, desenvolvida como projeto acadêmico do curso de Ciência da Computação do Insper.

[![Abrir no Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/GabrielRosa1/adult-income-eda/blob/main/APS_EDA.ipynb)

## Sobre o projeto

O projeto investiga características demográficas, educacionais e profissionais associadas à faixa de renda anual de uma pessoa. A variável-alvo, `income`, divide os registros em duas classes:

- `<=50K`: renda anual de até US$ 50 mil;
- `>50K`: renda anual superior a US$ 50 mil.

O objetivo desta etapa é compreender a estrutura e a qualidade dos dados, explorar as distribuições e relações entre as variáveis e preparar um pipeline reproduzível para as futuras etapas de modelagem.

## Base de dados

- **Nome:** Adult Income Census
- **Fonte:** [Kaggle — Adult Income Census](https://www.kaggle.com/datasets/anaghakp/adult-income-census)
- **Registros na base original:** 31.947
- **Variáveis:** 12, incluindo a variável-alvo

Cada registro descreve o perfil de uma pessoa por meio de atributos como idade, escolaridade, ocupação, situação conjugal, sexo, raça, país de origem e peso amostral (`fnlwgt`).

## Etapas realizadas

1. Carregamento e inspeção inicial da base;
2. descrição e classificação das variáveis;
3. identificação de valores ausentes, inconsistências e duplicatas;
4. análise do desbalanceamento da variável-alvo;
5. separação estratificada entre treino e teste;
6. análise univariada das variáveis numéricas e categóricas;
7. análise das relações entre as variáveis e a renda;
8. investigação e tratamento justificado de outliers;
9. transformação logarítmica de `fnlwgt`;
10. padronização das variáveis numéricas;
11. redução de dimensionalidade com PCA;
12. construção do pipeline final de pré-processamento.

## Principais resultados

- A classe de renda `>50K` corresponde a aproximadamente 24,1% dos registros, indicando desbalanceamento da variável-alvo.
- Escolaridades mais elevadas apresentam maior proporção de pessoas com renda superior a US$ 50 mil.
- As maiores taxas de renda alta foram observadas nas faixas de 40 a 59 anos.
- Na amostra analisada, a taxa de renda alta dos homens foi superior à das mulheres.
- As diferenças observadas entre grupos demográficos representam associações da amostra e não devem ser interpretadas como relações causais.
- As variáveis numéricas apresentam correlações lineares fracas entre si.
- As duas primeiras componentes do PCA preservaram aproximadamente 68,7% da variabilidade das três variáveis numéricas.
- Idade, escolaridade e peso amostral, isoladamente, não separaram claramente as duas classes de renda.

## Estrutura do repositório

```text
adult-income-eda/
├── APS_EDA.ipynb        # Notebook principal da análise
├── README.md            # Apresentação e instruções do projeto
└── docs/                # Documentação publicada com GitHub Pages
```

## Como executar

### Google Colab

Use o botão **Abrir no Google Colab** no início desta página e execute as células na ordem apresentada.

### Ambiente local

1. Clone o repositório:

   ```bash
   git clone https://github.com/GabrielRosa1/adult-income-eda.git
   cd adult-income-eda
   ```

2. Abra `APS_EDA.ipynb` em um ambiente compatível com Jupyter Notebook.
3. Execute todas as células desde o início.

O notebook tenta localizar `adult_income.csv` no ambiente. Quando necessário, também apresenta uma alternativa para obtenção da base pública utilizada no projeto.

## Tecnologias utilizadas

- Python
- Pandas e NumPy
- Matplotlib e Seaborn
- Scikit-learn
- Google Colab
- GitHub Pages

## Autores

- Gabriel Martins Rosa
- João Pedro Baungartner

**Instituição:** Insper  
**Curso:** Ciência da Computação  
**Semestre:** 2025.1  
**Professor:** Humberto Sandmann

## Documentação

A versão navegável do relatório será disponibilizada por meio do GitHub Pages deste repositório.

