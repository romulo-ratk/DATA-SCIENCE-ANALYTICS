# MVP — Machine Learning & Analytics: Scoring Fundamentalista de Ações da B3

Projeto desenvolvido para a disciplina de Machine Learning & Analytics da Pós-Graduação em Data Science & Analytics (PUC-Rio).

## Sobre o projeto

A ideia deste MVP é usar Machine Learning para tentar prever quais ações brasileiras têm mais chance de superar o Ibovespa nos 12 meses seguintes. Para isso, o modelo olha para indicadores fundamentalistas das empresas (como rentabilidade, endividamento e crescimento) e também para o contexto econômico do país (Selic, inflação, PIB e câmbio).

## O que tem neste repositório

| Arquivo | Descrição |
|---|---|
| `MVP_ML_Acoes_Final.ipynb` | O notebook principal, com todo o código, análises e resultados |
| `dataset_modelo.csv` | Dados usados para treinar e testar o modelo (1163 linhas, apenas anos com resultado conhecido) |
| `dataset_completo.csv` | Dados completos, incluindo 2024 (usado para prever 2025) |

## Como o dataset foi montado

Os dados vêm de três fontes públicas:

- **CVM** — demonstrações financeiras das empresas (balanços e resultados)
- **Banco Central (BCB)** — dados de Selic, inflação, câmbio e PIB
- **Yahoo Finance** — preços das ações para calcular quem superou o Ibovespa

O universo final tem **93 empresas** acompanhadas de **2010 a 2024**, distribuídas em vários setores da economia (bancos, energia, varejo, mineração, saúde, entre outros).

## Como executar

O jeito mais fácil é abrir o notebook direto no Google Colab. Os datasets são carregados automaticamente a partir deste repositório, então não precisa baixar nada — é só rodar as células na ordem.

O notebook está organizado em 15 seções, do problema até a conclusão, seguindo o template da disciplina.

## Principais resultados

- O modelo consegue ordenar as ações um pouco melhor do que um chute aleatório, de forma parecida com o que a literatura acadêmica encontra para esse tipo de problema (que é reconhecidamente difícil).
- Simulei uma carteira que, a cada ano, compra as 10 ações mais bem ranqueadas pelo modelo. Nos anos testados (2018 a 2025), essa carteira superou o Ibovespa em todos eles — embora parte desse resultado seja influenciada por uma limitação do estudo (ver abaixo).
- Também testei o modelo "de verdade": treinei com dados até 2023, gerei uma previsão para 2025, e depois comparei com o que realmente aconteceu. O modelo acertou um pouco mais da metade das previsões.

## Limitações

A principal limitação é o chamado **survivorship bias** (viés de sobrevivência): o dataset só inclui empresas que continuavam na bolsa em 2024. Empresas que faliram ou saíram da bolsa entre 2010 e 2024 ficaram de fora. Como essas empresas normalmente teriam retornos ruins, o modelo pode parecer um pouco melhor do que seria na realidade.

Fiz um estudo à parte que mostra o tamanho desse problema: das 372 empresas que existiam em 2010, só 212 (57%) continuavam na bolsa em 2024.

Outras limitações: os dados são anuais (dados trimestrais teriam mais informação) e alguns indicadores de mercado ficaram faltando para algumas empresas por causa de problemas na coleta de preços.

## Conclusão

O modelo funciona melhor como uma **ferramenta de apoio** — ele ajuda a direcionar a atenção para um grupo menor de ações com fundamentos mais interessantes, mas não substitui a análise de quem investe. Não é um sistema de "compre e ganhe dinheiro garantido", e sim uma camada a mais de informação para tomar decisões.

---

*Autor: Rômulo A. T. Kohler | Pós-Graduação em Data Science & Analytics — PUC-Rio*
