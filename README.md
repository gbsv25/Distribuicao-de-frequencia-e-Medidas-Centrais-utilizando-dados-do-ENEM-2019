# Distribuicao-de-frequencia-e-Medidas-Centrais-utilizando-dados-do-ENEM-2019

🖥 Linguagem: Python

Este repositório contém notebooks que realizam análises estatísticas dos dados do ENEM 2019, incluindo medidas de tendência central, dispersão e distribuição de frequência. Também apresenta visualizações para melhor compreensão dos resultados.

As Medidas Centrais apresentam o cálculo de média, mediana, moda, dispersão das notas e idades dos candidatos e visualizações com boxplots. A Análise da distribuição de frequência , fez o uso de apenas uma cidade de São Paulo, Sorocaba. A distribuição de frequência analisa as idades dos candidatos do ENEM 2019 em Sorocaba, incluindo frequências absoluta e relativa e visualizações com histogramas.

## 1. Medidas de Tendência Central e Dispersão 📊 

🔹 Objetivo: Analisar estatísticas descritivas das notas e idades dos candidatos do ENEM 2019;

🔹 Bibliotecas utilizadas: pandas, numpy, plotly.express, matplotlib.pyplot;

🔹 Principais Operações:

✔ Cálculo da média, mediana e moda das notas e idades.✔ Cálculo do desvio padrão para avaliar a dispersão das notas.✔ Geração de boxplots para visualizar a distribuição das notas.

📌 Destaques do Código

### Cálculo da média e arredondamento para 2 casas decimais
print("Média das variáveis principais:")

print("Idade:", round(enem_sp['IDADE'].mean(), 2))

print("Nota Matemática:", round(enem_sp['NOTA_MT'].mean(), 2))

Fornece uma visão geral das médias das principais variáveis.

### Moda - '[0]' retorna o primeiro valor caso haja mais de uma moda
print("Moda das variáveis principais:")

print("Idade:", enem_sp['IDADE'].mode()[0])  

Se houver múltiplos valores modais, [0] seleciona o primeiro.

### Boxplot para visualizar a dispersão das notas
import plotly.express as px

fig = px.box(enem_sp, y=['NOTA_REDACAO', 'NOTA_MT', 'NOTA_CN', 'NOTA_CH', 'NOTA_LC'],
             title='Distribuição das Notas do ENEM 2019')
fig.show()

Gera um boxplot interativo para identificar a variabilidade das notas.

## 2. Distribuição de Frequência das Idades 📊 

🔹 Objetivo: Analisar a distribuição etária dos candidatos do ENEM 2019 em Sorocaba.

🔹 Bibliotecas utilizadas: pandas, numpy, collections.Counter, matplotlib.pyplot, seaborn

🔹 Principais Operações:

✔ Filtragem dos dados para considerar apenas os candidatos de Sorocaba;

✔ Cálculo da frequência absoluta e relativa das idades;

✔ Visualização com histogramas para identificar padrões de idade.

📌 Destaques do Código

### Frequência absoluta das idades
from collections import Counter

freq_absoluta = Counter(enem_sorocaba['IDADE'])

freq_absoluta = pd.DataFrame.from_dict(freq_absoluta, orient='index', columns=['Frequência'])

Conta a ocorrência de cada idade na base de dados.

### Frequência relativa percentual
freq_relativa = freq_absoluta / freq_absoluta.sum() * 100

Transforma a contagem em percentual sobre o total de candidatos.

### Histograma da distribuição de idades
import matplotlib.pyplot as plt

plt.hist(enem_sorocaba['IDADE'], bins=10, color='red', alpha=0.7, rwidth=0.85)

plt.title('Distribuição das Idades - ENEM Sorocaba 2019')

plt.xlabel('Idade')

plt.ylabel('Frequência')

plt.show()

Exibe a distribuição etária dos candidatos com um histograma.

## Interpretação dos Dados 📌 

Os resultados da análise indicam que a média de idade dos candidatos do ENEM 2019 é aproximadamente 20,6 anos, com a moda sendo 17 anos, sugerindo que a maioria dos participantes são jovens. As notas do ENEM apresentam uma grande variação, conforme mostrado pelos boxplots, com uma média de aproximadamente 593 pontos em Redação e 497 pontos em Matemática. 

A distribuição etária em Sorocaba revelou que 37% dos candidatos tinham 17 anos, e cerca de 60% estavam entre 17 e 19 anos, indicando um predomínio de candidatos em idade escolar. Os histogramas confirmam essa tendência, com uma distribuição assimétrica para idades mais altas.

Esses insights podem ser usados para compreender melhor o perfil dos participantes, direcionando estratégias de educação e políticas públicas para essa faixa etária.

📎 Autor: Gabriela – Analista de Dados Júnior

📝 Requisitos: Python 3, Google Colab, Pandas, Matplotlib, Seaborn, Plotly
