# Análisis sobre viajes en taxi en Chicago
Esta análisis tiene como objetivo encontrar patrones en la información disponible y comprender las preferencias de los pasajeros y el impacto de los factores externos en los viajes de taxi de la ciudad de Chicago.

## Extraer datos
Primero, se hizo un código para extraer los datos sobre el clima en Chicago en noviembre de 2017. Esto desde un [sitio web](https://practicum-content.s3.us-west-1.amazonaws.com/data-analyst-eng/moved_chicago_weather_2017.html). Tras lo cual se analizaron lo datos. El código usado fue el siguiente:

```python 
import pandas as pd 
import requests  # Importa la librería para enviar solicitudes al servidor 
from bs4 import BeautifulSoup  # Importa la librería para analizar la página web

req = requests.get('https://practicum-content.s3.us-west-1.amazonaws.com/data-analyst-eng/moved_chicago_weather_2017.html') 
soup = BeautifulSoup(req.text, 'lxml') 
table = soup.find('table',attrs={"id": "weather_records"})

heading_table = []  #encabezados de columna
for row in table.find_all('th'): # Los nombres de las columnas están dentro de los elementos <th>
    heading_table.append(row.text)

content = []  #lista donde se almacenarán los datos de la tabla
for row in table.find_all('tr'):
    if not row.find_all('th'):
        # Condición para ignorar la primera fila de la tabla, con encabezados
        content.append([element.text for element in row.find_all('td')])

weather_records = pd.DataFrame(content, columns=heading_table)

print(weather_records)
```
El resultado del código anterior fue el siguiente:
```python
     Date and time          Temperature    Description
0    2017-11-01 00:00:00     276.150     broken clouds
1    2017-11-01 01:00:00     275.700  scattered clouds
2    2017-11-01 02:00:00     275.610   overcast clouds
3    2017-11-01 03:00:00     275.350     broken clouds
4    2017-11-01 04:00:00     275.240     broken clouds
5    2017-11-01 05:00:00     275.050   overcast clouds
6    2017-11-01 06:00:00     275.140   overcast clouds
7    2017-11-01 07:00:00     275.230   overcast clouds
8    2017-11-01 08:00:00     275.230   overcast clouds
9    2017-11-01 09:00:00     275.320   overcast clouds
..                   ...         ...               ...
687  2017-11-29 15:00:00     275.210      sky is clear
688  2017-11-29 16:00:00     278.030      sky is clear
689  2017-11-29 17:00:00     279.580      sky is clear
690  2017-11-29 18:00:00     280.310        few clouds
691  2017-11-29 19:00:00     281.050        few clouds
692  2017-11-29 20:00:00     281.340        few clouds
693  2017-11-29 21:00:00     281.690      sky is clear
694  2017-11-29 22:00:00     281.070        few clouds
695  2017-11-29 23:00:00     280.060      sky is clear
696  2017-11-30 00:00:00     278.460      sky is clear

[697 rows x 3 columns]
```

abc
