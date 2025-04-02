# Modelo para diagnóstico de câncer de mama

👩‍💻 Autor: Kelly Ferreira

🛠️ Linguagem: Python

📈 Desenvolvido durante a [Trilha Data Science - ADA Tech Santander Coders](https://ada.tech/certificado?code=91beda22-296b-ad92-1553-3580486bc487)

Fonte do Dataset: [Kaggle](https://github.com/fsantoskelly/reg_lin_casas/blob/main/Housing.ipynb)

## Objetivo do Modelo

O objetivo do modelo é prever o preço das casas com base em algumas características do imóvel e da região. 

## 📚Bibliotecas utilizadas/ aplicabilidade

🔹 Pandas

O `pandas` foi usado para manipulação e análise dos dados, facilitando a leitura do arquivo e o pré-processamento das variáveis. 

🔹 MatplotLib

O `matplotlib.pyplot` foi usado para a apresentação gráfica e visualização das informações.

🔹 Scikit-learn

O `scikit-learn` foi usado para a regressão linear, treinamento do modelo, para parametrizar avaliar a performance do modelo, medindo o erro médio absoluto.

## 🧮Desenvolvimento das análises

Será aplicado um modelo de **Regressão Linear**, buscando encontrar uma relação matemática entre as variáveis.

🔹 Carregamento do dataset e remoção da primeira coluna:

`df = pd.read_csv('USA_Housing.csv.csv')`

🔹Visualização das colunas/linhas da tabela:

`df.head()`

![image](https://github.com/user-attachments/assets/54781b54-b272-413a-bb55-f0db622dca89)


🔹Preparação dos dados

▸ Seleção das variáveis preditoras (features):

▸  `['Avg. Area Income', 'Avg. Area House Age', 'Avg. Area Number of Rooms', 'Area Population']` na variável X;

▸ Seleção da variável alvo (label):

`df['Price']` na variável Y.
       
🔹Treinamento do modelo de regressão linear
    
▸Separação dos dados entre **treino (75%) e teste (25%)** usando `train_test_split()`

▸ Criação de  um modelo de **Regressão Linear**:

 `LinearRegression()`.
    
▸ Inserção de dados de treino:

`x_treino` e `y_treino`.

X treino:

![image](https://github.com/user-attachments/assets/7d23b541-10d1-48e7-a08d-9c6cb1d8f10b)

Y treino:

![image](https://github.com/user-attachments/assets/a7cc4592-d466-4d0d-acb6-e062ca3d06d2)

        
🔹Cálculo do preço médio das casas:
    
`df['Price'].mean()`

![image](https://github.com/user-attachments/assets/1b9c1036-72fd-4e68-a4e0-951880527184)
    
🔹Cálculo do erro absoluto

O **erro absoluto médio (MAE - Mean Absolute Error)** foi calculado utilizando o comando abaixo, resultando em **USD 80.634 **, ou seja, em média, a previsão do modelo tem essa margem de erro.

 `mean_absolute_error(y_previsto, y_teste)`

🔹Criação de gráfico de dispersão para comparar dados reais x dados previstos
 
`import seaborn as sns
import matplotlib.pyplot as plt
plt.figure(figsize=(8, 6))
sns.scatterplot(x=y_teste, y=y_previsto)
plt.plot(y_teste, y_teste, color='red', linestyle='--')
plt.title("Valores reais x Valores previstos")
plt.xlabel("Valores Reais")
plt.ylabel("Valores Previstos")
plt.show()`

![image](https://github.com/user-attachments/assets/84981325-e009-4cf3-b59c-dd249e049937)


🔹Criação de mapa de calor para avaliar as variáveis que mais influenciam nos valores

Utilizada matrix de correlação para estabelecer a correlação entre as variáveis:

`import seaborn as sns
import matplotlib.pyplot as plt
correlacao = df.corr()
print(correlacao["Price"])
plt.figure(figsize=(8, 6))
sns.heatmap(correlacao, annot=True, cmap="coolwarm", fmt=".2f", linewidths=0.5)
plt.title("Influenciadores de Preço")
plt.show()`

![image](https://github.com/user-attachments/assets/0a0b9f7d-07bb-40ec-99a5-ac06c4825bea)


##  📝Considerações Finais

🔹 O modelo de **regressão linear** conseguiu prever os preços das casas com uma média de erro de **81.127 dólares**;

🔹O fator que demonstrou-se mais relevante para interferir no preço das casas é a renda média da região (Avg. Area Income), exercendo uma correlação positiva onde, quanto maior a renda média da região, maior tende a ser o preço das casas;

🔹Em uma correlação mais fraca, as casas mais antigas e regiões mais populosas tendem a ter preços mais altos.

💡 Com os dados apresentados, podemos observar uma bom comportamento do modelo de regressão linear para previsão dos preços, visto no gráfico de dispersão e que o principal fator que influencia o aumento do preço das casas seria a renda média da região.










