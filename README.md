# Data-Science-com-Python
Analise de dados de 2 case, o primeiro uma base de 70.000 linhas de uma rede de lojas de vendas de açai, e o outro ciclo de venda de um infoproduto na plataforma eduzzuma empresa 

# Análise de Dados

[Para acessar o PDF com os gráficos clique aqui:](https://drive.google.com/file/d/1xlgbZ6Wk499_UpXTZl6ejby0Fv0J4BFp)



## Biblioteca


```python
# Quando usamos "as"podemos dar um apelido para a biblioteca

import pandas as pd
```


```python
# Biblioteca geradora de grafico

!pip install plotly_express
```

    Requirement already satisfied: plotly_express in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (0.4.1)
    Requirement already satisfied: patsy>=0.5 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (0.5.2)
    Requirement already satisfied: scipy>=0.18 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (1.9.1)
    Requirement already satisfied: pandas>=0.20.0 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (1.4.4)
    Requirement already satisfied: plotly>=4.1.0 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (5.9.0)
    Requirement already satisfied: numpy>=1.11 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (1.21.5)
    Requirement already satisfied: statsmodels>=0.9.0 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (0.13.2)
    Requirement already satisfied: python-dateutil>=2.8.1 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from pandas>=0.20.0->plotly_express) (2.8.2)
    Requirement already satisfied: pytz>=2020.1 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from pandas>=0.20.0->plotly_express) (2023.3.post1)
    Requirement already satisfied: six in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from patsy>=0.5->plotly_express) (1.16.0)
    Requirement already satisfied: tenacity>=6.2.0 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly>=4.1.0->plotly_express) (8.0.1)
    Requirement already satisfied: packaging>=21.3 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from statsmodels>=0.9.0->plotly_express) (21.3)
    Requirement already satisfied: pyparsing!=3.0.5,>=2.0.2 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from packaging>=21.3->statsmodels>=0.9.0->plotly_express) (3.0.9)



```python
import plotly_express as px
```

## Carregando os dados


```python
dados = pd.read_excel("vendas.xlsx")
```


```python
dados2 = pd.read_excel("vendas-eduzz-2022.xlsx")
```

## Verificando se os dados foram carregados


```python
dados.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id_pedido</th>
      <th>data</th>
      <th>loja</th>
      <th>cidade</th>
      <th>estado</th>
      <th>regiao</th>
      <th>tamanho</th>
      <th>local_consumo</th>
      <th>preco</th>
      <th>forma_pagamento</th>
      <th>ano_mes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>PED1994</td>
      <td>2020-01-01</td>
      <td>Loja 4</td>
      <td>Santos</td>
      <td>São Paulo</td>
      <td>Sudeste</td>
      <td>300ml</td>
      <td>Consumo no local</td>
      <td>5</td>
      <td>Dinheiro</td>
      <td>2020-01</td>
    </tr>
    <tr>
      <th>1</th>
      <td>PED2246</td>
      <td>2020-01-01</td>
      <td>Loja 6</td>
      <td>Florianópolis</td>
      <td>Santa Catarina</td>
      <td>Sul</td>
      <td>500ml</td>
      <td>Consumo no local</td>
      <td>11</td>
      <td>Débito</td>
      <td>2020-01</td>
    </tr>
    <tr>
      <th>2</th>
      <td>PED3876</td>
      <td>2020-01-01</td>
      <td>Loja 3</td>
      <td>Rio de Janeiro</td>
      <td>Rio de Janeiro</td>
      <td>Sudeste</td>
      <td>300ml</td>
      <td>Delivery</td>
      <td>7</td>
      <td>Crédito</td>
      <td>2020-01</td>
    </tr>
    <tr>
      <th>3</th>
      <td>PED4352</td>
      <td>2020-01-01</td>
      <td>Loja 1</td>
      <td>Fortaleza</td>
      <td>Ceará</td>
      <td>Nordeste</td>
      <td>1000ml</td>
      <td>Consumo no local</td>
      <td>7</td>
      <td>Débito</td>
      <td>2020-01</td>
    </tr>
    <tr>
      <th>4</th>
      <td>PED8633</td>
      <td>2020-01-01</td>
      <td>Loja 5</td>
      <td>São Paulo</td>
      <td>São Paulo</td>
      <td>Sudeste</td>
      <td>200ml</td>
      <td>Delivery</td>
      <td>9</td>
      <td>Crédito</td>
      <td>2020-01</td>
    </tr>
  </tbody>
</table>
</div>




```python
dados2.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Forma de Pagamento</th>
      <th>Data de Pagamento</th>
      <th>Produto</th>
      <th>Valor da Venda</th>
      <th>Cidade</th>
      <th>UF</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Pix</td>
      <td>2022-12-16 19:23:49</td>
      <td>Faça Acontecer - Programa de Implementação e A...</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Mastercard</td>
      <td>2022-12-16 19:15:31</td>
      <td>Faça Acontecer - Programa de Implementação e A...</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Mastercard</td>
      <td>2022-12-16 19:05:41</td>
      <td>Ebook - Como Controlar os Pensamentos Negativos</td>
      <td>10.0</td>
      <td>São José dos Campos</td>
      <td>SP</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Mastercard</td>
      <td>2022-12-16 19:05:41</td>
      <td>Ebook - Como Parar de Sofrer com a Preocupação...</td>
      <td>0.0</td>
      <td>São José dos Campos</td>
      <td>SP</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Pix</td>
      <td>2022-12-16 18:51:31</td>
      <td>Faça Acontecer - Programa de Implementação e A...</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
dados.tail()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id_pedido</th>
      <th>data</th>
      <th>loja</th>
      <th>cidade</th>
      <th>estado</th>
      <th>regiao</th>
      <th>tamanho</th>
      <th>local_consumo</th>
      <th>preco</th>
      <th>forma_pagamento</th>
      <th>ano_mes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>69995</th>
      <td>PED67084</td>
      <td>2022-12-31</td>
      <td>Loja 6</td>
      <td>Florianópolis</td>
      <td>Santa Catarina</td>
      <td>Sul</td>
      <td>500ml</td>
      <td>Consumo no local</td>
      <td>11</td>
      <td>Crédito</td>
      <td>2022-12</td>
    </tr>
    <tr>
      <th>69996</th>
      <td>PED67857</td>
      <td>2022-12-31</td>
      <td>Loja 3</td>
      <td>Rio de Janeiro</td>
      <td>Rio de Janeiro</td>
      <td>Sudeste</td>
      <td>200ml</td>
      <td>Consumo no local</td>
      <td>7</td>
      <td>Pix</td>
      <td>2022-12</td>
    </tr>
    <tr>
      <th>69997</th>
      <td>PED69171</td>
      <td>2022-12-31</td>
      <td>Loja 4</td>
      <td>Santos</td>
      <td>São Paulo</td>
      <td>Sudeste</td>
      <td>500ml</td>
      <td>Consumo no local</td>
      <td>5</td>
      <td>Dinheiro</td>
      <td>2022-12</td>
    </tr>
    <tr>
      <th>69998</th>
      <td>PED69229</td>
      <td>2022-12-31</td>
      <td>Loja 4</td>
      <td>Santos</td>
      <td>São Paulo</td>
      <td>Sudeste</td>
      <td>300ml</td>
      <td>Consumo no local</td>
      <td>9</td>
      <td>Pix</td>
      <td>2022-12</td>
    </tr>
    <tr>
      <th>69999</th>
      <td>PED69356</td>
      <td>2022-12-31</td>
      <td>Loja 1</td>
      <td>Fortaleza</td>
      <td>Ceará</td>
      <td>Nordeste</td>
      <td>300ml</td>
      <td>Delivery</td>
      <td>9</td>
      <td>Pix</td>
      <td>2022-12</td>
    </tr>
  </tbody>
</table>
</div>




```python
dados2.tail()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Forma de Pagamento</th>
      <th>Data de Pagamento</th>
      <th>Produto</th>
      <th>Valor da Venda</th>
      <th>Cidade</th>
      <th>UF</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1957</th>
      <td>Visa</td>
      <td>2021-07-07 13:32:06</td>
      <td>Acesso Gratuito - Aliviar</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1958</th>
      <td>Visa</td>
      <td>2021-02-01 04:08:14</td>
      <td>Combo: Metas que Geram Resultados</td>
      <td>6.63</td>
      <td>Cuiabá</td>
      <td>MT</td>
    </tr>
    <tr>
      <th>1959</th>
      <td>Visa</td>
      <td>2021-03-02 05:25:22</td>
      <td>Combo: Metas que Geram Resultados</td>
      <td>6.63</td>
      <td>Cuiabá</td>
      <td>MT</td>
    </tr>
    <tr>
      <th>1960</th>
      <td>Visa</td>
      <td>2020-12-30 22:44:58</td>
      <td>Combo: Metas que Geram Resultados</td>
      <td>6.63</td>
      <td>Cuiabá</td>
      <td>MT</td>
    </tr>
    <tr>
      <th>1961</th>
      <td>Boleto Bancário</td>
      <td>2020-08-19 14:52:29</td>
      <td>Força da Aceleração: Aulão da Produtividade</td>
      <td>29.00</td>
      <td>Brasília</td>
      <td>DF</td>
    </tr>
  </tbody>
</table>
</div>



## Quantidade de linhas e colunas

Podemos usar a propriedade **shape** para verificar a quantidade de linhas e colunas. O primeiro valor é a quantidade de **linhas** e o segundo  a de **colunas**.


```python
dados.shape
```




    (70000, 11)




```python
dados2.shape
```




    (1962, 6)



## Informações sobre as colunas

O Pandas tem um método muito poderoso para gerar informações importantes sobre o conjuto de **dados.info()**


```python
dados.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 70000 entries, 0 to 69999
    Data columns (total 11 columns):
     #   Column           Non-Null Count  Dtype         
    ---  ------           --------------  -----         
     0   id_pedido        70000 non-null  object        
     1   data             70000 non-null  datetime64[ns]
     2   loja             70000 non-null  object        
     3   cidade           70000 non-null  object        
     4   estado           70000 non-null  object        
     5   regiao           70000 non-null  object        
     6   tamanho          70000 non-null  object        
     7   local_consumo    70000 non-null  object        
     8   preco            70000 non-null  int64         
     9   forma_pagamento  70000 non-null  object        
     10  ano_mes          70000 non-null  object        
    dtypes: datetime64[ns](1), int64(1), object(9)
    memory usage: 5.9+ MB



```python
dados2.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1962 entries, 0 to 1961
    Data columns (total 6 columns):
     #   Column              Non-Null Count  Dtype         
    ---  ------              --------------  -----         
     0   Forma de Pagamento  1962 non-null   object        
     1   Data de Pagamento   1962 non-null   datetime64[ns]
     2   Produto             1962 non-null   object        
     3   Valor da Venda      1962 non-null   float64       
     4   Cidade              919 non-null    object        
     5   UF                  919 non-null    object        
    dtypes: datetime64[ns](1), float64(1), object(4)
    memory usage: 92.1+ KB


## Gerando estatísticas

O método **describe()** gera estatísticas sobre as colunas quantitativas.


```python
dados.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>preco</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>70000.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>8.355200</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2.653061</td>
    </tr>
    <tr>
      <th>min</th>
      <td>5.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>7.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>7.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>11.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>13.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
dados2.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Valor da Venda</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1962.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5.827569</td>
    </tr>
    <tr>
      <th>std</th>
      <td>10.394321</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>5.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>299.000000</td>
    </tr>
  </tbody>
</table>
</div>



## Acessando uma coluna

Para acessar uma coluna, podemos utilizar a notação de colchetes, passando o nome da coluna desejada. 

Caso o nome da coluna não possua espaços em branco de nem caracteres especiais, podemos acessar também com a notação de ponto.


```python
dados['loja']
```




    0        Loja 4
    1        Loja 6
    2        Loja 3
    3        Loja 1
    4        Loja 5
              ...  
    69995    Loja 6
    69996    Loja 3
    69997    Loja 4
    69998    Loja 4
    69999    Loja 1
    Name: loja, Length: 70000, dtype: object




```python
dados.loja
```




    0        Loja 4
    1        Loja 6
    2        Loja 3
    3        Loja 1
    4        Loja 5
              ...  
    69995    Loja 6
    69996    Loja 3
    69997    Loja 4
    69998    Loja 4
    69999    Loja 1
    Name: loja, Length: 70000, dtype: object




```python
dados2['Produto']
```




    0       Faça Acontecer - Programa de Implementação e A...
    1       Faça Acontecer - Programa de Implementação e A...
    2         Ebook - Como Controlar os Pensamentos Negativos
    3       Ebook - Como Parar de Sofrer com a Preocupação...
    4       Faça Acontecer - Programa de Implementação e A...
                                  ...                        
    1957                            Acesso Gratuito - Aliviar
    1958                    Combo: Metas que Geram Resultados
    1959                    Combo: Metas que Geram Resultados
    1960                    Combo: Metas que Geram Resultados
    1961          Força da Aceleração: Aulão da Produtividade
    Name: Produto, Length: 1962, dtype: object




```python
dados2.Produto
```




    0       Faça Acontecer - Programa de Implementação e A...
    1       Faça Acontecer - Programa de Implementação e A...
    2         Ebook - Como Controlar os Pensamentos Negativos
    3       Ebook - Como Parar de Sofrer com a Preocupação...
    4       Faça Acontecer - Programa de Implementação e A...
                                  ...                        
    1957                            Acesso Gratuito - Aliviar
    1958                    Combo: Metas que Geram Resultados
    1959                    Combo: Metas que Geram Resultados
    1960                    Combo: Metas que Geram Resultados
    1961          Força da Aceleração: Aulão da Produtividade
    Name: Produto, Length: 1962, dtype: object



## Obtendo valores únicos de uma coluna

Para obter os valores únicos de uma coluna, utilizamos o método **unique()**


```python
dados['loja'].unique()
```




    array(['Loja 4', 'Loja 6', 'Loja 3', 'Loja 1', 'Loja 5', 'Loja 2'],
          dtype=object)




```python
dados2['Produto'].unique()
```




    array(['Faça Acontecer - Programa de Implementação e Aceleração',
           'Ebook - Como Controlar os Pensamentos Negativos',
           'Ebook - Como Parar de Sofrer com a Preocupação e o Pensamento Acelereado',
           'Livro Digital - Como Fazer Acontecer',
           'Clube Aliviar - Alívio dos Sintomas da Ansiedade',
           'ACESSO VITALÍCIO À GRAVAÇÃO | Treinamento Cérebro Lucrativo',
           'Como se Reinventar em Época de Crise',
           'Livro digital - Como controlar a Ansiedade',
           'ACESSO ZOOM | Sessão de Terapia Estratégica',
           'Ebook - Como Ter Alívio dos Sintomas da Ansiedade',
           '[VERSÃO AUDIO/ VÍDEO] GUIA DE ALÍVIO IMEDIATO DA ANSIEDADE - Cópia',
           'Livro digital | O Segredo para Emagrecer e Manter o Peso Ideal da Forma Certa',
           'Análise de Perfil Comportamental - HMI',
           '[Aluno] Programa/Protocolo Ansiedade Controlada - Aliviar',
           'Livro digital - O Segredo para Emagrecer e Manter o Peso Ideal da Forma Certa',
           'ACESSO VIP | Treinamento Cérebro Lucrativo',
           'AO VIVO | Treinamento Cérebro Lucrativo',
           'GUIA DE ALÍVIO IMEDIATO DA ANSIEDADE',
           'Acesso Gratuito - Aliviar', 'Combo: Metas que Geram Resultados',
           'Força da Aceleração: Aulão da Produtividade'], dtype=object)



## Contagem de valores

Para fazer a contagem de valores de uma coluna, podemos utilizar o **método value_counts()**.

Podemos obter também o valor relativo, utilizando o parâmetro **normalize=True**


```python
dados['loja'].value_counts()
```




    Loja 4    13483
    Loja 6    13075
    Loja 1    12344
    Loja 5    12177
    Loja 3    10603
    Loja 2     8318
    Name: loja, dtype: int64




```python
dados['loja'].value_counts(normalize=True)
```




    Loja 4    0.192614
    Loja 6    0.186786
    Loja 1    0.176343
    Loja 5    0.173957
    Loja 3    0.151471
    Loja 2    0.118829
    Name: loja, dtype: float64




```python
dados2['Valor da Venda'].value_counts()
```




    0.00      854
    5.00      533
    10.00     300
    15.00     126
    34.90      66
    2.00       22
    24.90      13
    29.90      12
    9.00        8
    7.00        7
    20.00       6
    12.00       4
    6.63        3
    49.00       1
    299.00      1
    97.00       1
    23.00       1
    19.90       1
    1.00        1
    22.00       1
    29.00       1
    Name: Valor da Venda, dtype: int64




```python
dados2['Valor da Venda'].value_counts(normalize=True)
```




    0.00      0.435270
    5.00      0.271662
    10.00     0.152905
    15.00     0.064220
    34.90     0.033639
    2.00      0.011213
    24.90     0.006626
    29.90     0.006116
    9.00      0.004077
    7.00      0.003568
    20.00     0.003058
    12.00     0.002039
    6.63      0.001529
    49.00     0.000510
    299.00    0.000510
    97.00     0.000510
    23.00     0.000510
    19.90     0.000510
    1.00      0.000510
    22.00     0.000510
    29.00     0.000510
    Name: Valor da Venda, dtype: float64



## Agrupando dados

O método **groupby()** realiza o agrupamento de dados por determinada coluna.

Sempre que utilizamos o **groupby()**, precisamos definir o **método de agregação** que será usado.


```python
# faturamento por loja
dados.groupby('loja').preco.sum()
```




    loja
    Loja 1    103162
    Loja 2     69592
    Loja 3     88357
    Loja 4    112379
    Loja 5    102189
    Loja 6    109185
    Name: preco, dtype: int64




```python
# faturamento por Produto
dados2.groupby('Produto').sum()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Valor da Venda</th>
    </tr>
    <tr>
      <th>Produto</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>ACESSO VIP | Treinamento Cérebro Lucrativo</th>
      <td>97.00</td>
    </tr>
    <tr>
      <th>ACESSO VITALÍCIO À GRAVAÇÃO | Treinamento Cérebro Lucrativo</th>
      <td>0.00</td>
    </tr>
    <tr>
      <th>ACESSO ZOOM | Sessão de Terapia Estratégica</th>
      <td>0.00</td>
    </tr>
    <tr>
      <th>AO VIVO | Treinamento Cérebro Lucrativo</th>
      <td>50.00</td>
    </tr>
    <tr>
      <th>Acesso Gratuito - Aliviar</th>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Análise de Perfil Comportamental - HMI</th>
      <td>49.00</td>
    </tr>
    <tr>
      <th>Clube Aliviar - Alívio dos Sintomas da Ansiedade</th>
      <td>90.00</td>
    </tr>
    <tr>
      <th>Combo: Metas que Geram Resultados</th>
      <td>19.89</td>
    </tr>
    <tr>
      <th>Como se Reinventar em Época de Crise</th>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Ebook - Como Controlar os Pensamentos Negativos</th>
      <td>9651.70</td>
    </tr>
    <tr>
      <th>Ebook - Como Parar de Sofrer com a Preocupação e o Pensamento Acelereado</th>
      <td>484.20</td>
    </tr>
    <tr>
      <th>Ebook - Como Ter Alívio dos Sintomas da Ansiedade</th>
      <td>0.00</td>
    </tr>
    <tr>
      <th>Faça Acontecer - Programa de Implementação e Aceleração</th>
      <td>92.00</td>
    </tr>
    <tr>
      <th>Força da Aceleração: Aulão da Produtividade</th>
      <td>29.00</td>
    </tr>
    <tr>
      <th>GUIA DE ALÍVIO IMEDIATO DA ANSIEDADE</th>
      <td>109.00</td>
    </tr>
    <tr>
      <th>Livro Digital - Como Fazer Acontecer</th>
      <td>25.00</td>
    </tr>
    <tr>
      <th>Livro digital - Como controlar a Ansiedade</th>
      <td>407.90</td>
    </tr>
    <tr>
      <th>Livro digital - O Segredo para Emagrecer e Manter o Peso Ideal da Forma Certa</th>
      <td>10.00</td>
    </tr>
    <tr>
      <th>Livro digital | O Segredo para Emagrecer e Manter o Peso Ideal da Forma Certa</th>
      <td>20.00</td>
    </tr>
    <tr>
      <th>[Aluno] Programa/Protocolo Ansiedade Controlada - Aliviar</th>
      <td>299.00</td>
    </tr>
    <tr>
      <th>[VERSÃO AUDIO/ VÍDEO] GUIA DE ALÍVIO IMEDIATO DA ANSIEDADE - Cópia</th>
      <td>0.00</td>
    </tr>
  </tbody>
</table>
</div>




```python
# média de faturamento por loja (ticket médio)
dados.groupby('loja').preco.mean()
```




    loja
    Loja 1    8.357259
    Loja 2    8.366434
    Loja 3    8.333208
    Loja 4    8.334866
    Loja 5    8.391968
    Loja 6    8.350669
    Name: preco, dtype: float64




```python
# média de faturamento por Produto (ticket médio)
dados2.groupby('Produto').mean()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Valor da Venda</th>
    </tr>
    <tr>
      <th>Produto</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>ACESSO VIP | Treinamento Cérebro Lucrativo</th>
      <td>97.000000</td>
    </tr>
    <tr>
      <th>ACESSO VITALÍCIO À GRAVAÇÃO | Treinamento Cérebro Lucrativo</th>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>ACESSO ZOOM | Sessão de Terapia Estratégica</th>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>AO VIVO | Treinamento Cérebro Lucrativo</th>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>Acesso Gratuito - Aliviar</th>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Análise de Perfil Comportamental - HMI</th>
      <td>49.000000</td>
    </tr>
    <tr>
      <th>Clube Aliviar - Alívio dos Sintomas da Ansiedade</th>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>Combo: Metas que Geram Resultados</th>
      <td>6.630000</td>
    </tr>
    <tr>
      <th>Como se Reinventar em Época de Crise</th>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Ebook - Como Controlar os Pensamentos Negativos</th>
      <td>9.778825</td>
    </tr>
    <tr>
      <th>Ebook - Como Parar de Sofrer com a Preocupação e o Pensamento Acelereado</th>
      <td>1.264230</td>
    </tr>
    <tr>
      <th>Ebook - Como Ter Alívio dos Sintomas da Ansiedade</th>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>Faça Acontecer - Programa de Implementação e Aceleração</th>
      <td>3.538462</td>
    </tr>
    <tr>
      <th>Força da Aceleração: Aulão da Produtividade</th>
      <td>29.000000</td>
    </tr>
    <tr>
      <th>GUIA DE ALÍVIO IMEDIATO DA ANSIEDADE</th>
      <td>9.909091</td>
    </tr>
    <tr>
      <th>Livro Digital - Como Fazer Acontecer</th>
      <td>0.083333</td>
    </tr>
    <tr>
      <th>Livro digital - Como controlar a Ansiedade</th>
      <td>2.977372</td>
    </tr>
    <tr>
      <th>Livro digital - O Segredo para Emagrecer e Manter o Peso Ideal da Forma Certa</th>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>Livro digital | O Segredo para Emagrecer e Manter o Peso Ideal da Forma Certa</th>
      <td>5.000000</td>
    </tr>
    <tr>
      <th>[Aluno] Programa/Protocolo Ansiedade Controlada - Aliviar</th>
      <td>149.500000</td>
    </tr>
    <tr>
      <th>[VERSÃO AUDIO/ VÍDEO] GUIA DE ALÍVIO IMEDIATO DA ANSIEDADE - Cópia</th>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
</div>



## Gráficos

Para gerar gráficos vamos utilizar a biblioteca **Plotly Express**.


```python
!pip install plotly_express
```

    Requirement already satisfied: plotly_express in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (0.4.1)
    Requirement already satisfied: plotly>=4.1.0 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (5.9.0)
    Requirement already satisfied: pandas>=0.20.0 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (1.4.4)
    Requirement already satisfied: numpy>=1.11 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (1.21.5)
    Requirement already satisfied: statsmodels>=0.9.0 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (0.13.2)
    Requirement already satisfied: patsy>=0.5 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (0.5.2)
    Requirement already satisfied: scipy>=0.18 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly_express) (1.9.1)
    Requirement already satisfied: python-dateutil>=2.8.1 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from pandas>=0.20.0->plotly_express) (2.8.2)
    Requirement already satisfied: pytz>=2020.1 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from pandas>=0.20.0->plotly_express) (2023.3.post1)
    Requirement already satisfied: six in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from patsy>=0.5->plotly_express) (1.16.0)
    Requirement already satisfied: tenacity>=6.2.0 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from plotly>=4.1.0->plotly_express) (8.0.1)
    Requirement already satisfied: packaging>=21.3 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from statsmodels>=0.9.0->plotly_express) (21.3)
    Requirement already satisfied: pyparsing!=3.0.5,>=2.0.2 in /Users/wallacefirmo/opt/anaconda3/lib/python3.9/site-packages (from packaging>=21.3->statsmodels>=0.9.0->plotly_express) (3.0.9)



```python
import plotly_express as px
```

## Contagem de pedidos por loja


```python
px.histogram(dados, x="loja",  color="regiao", text_auto=True)
``````


## Contagem de Pedido por Produto


```python
px.histogram(dados2, x="Valor da Venda",  color="Produto", text_auto=True)
```




```python
px.histogram(dados2, x="UF",  color="Valor da Venda", text_auto=True)
```


# FRASE DO DIA

## eu quero ser expert em python


```python

```