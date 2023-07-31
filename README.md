# Análisis sobre viajes en taxi en Chicago
Esta análisis tiene como objetivo encontrar patrones en la información disponible y comprender las preferencias de los pasajeros y el impacto de los factores externos en los viajes de taxi de la ciudad de Chicago.

## Extraer datos
Primero, se hizo un código para extraer los datos sobre el clima en Chicago en noviembre de 2017. Esto desde un [sitio web](https://practicum-content.s3.us-west-1.amazonaws.com/data-analyst-eng/moved_chicago_weather_2017.html). Tras lo cual se analizaron lo datos. El código usado fue el siguiente:

```python 
import pandas as pd 
import requests  # Importa la librería para enviar solicitudes al servidor 
from bs4 import BeautifulSoup  # Importa la librería para analizar la página web 
```
