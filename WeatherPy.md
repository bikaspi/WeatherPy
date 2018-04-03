

```python
import pandas as pd
import json
import requests
import numpy as np
import matplotlib.pyplot as plt
import random
from config import api_key
import openweathermapy.core as owm
from citipy import citipy
```


```python
# get the OpenWeatherMap url
url = 'http://api.openweathermap.org/data/2.5/weather?'
units = "imperial"

# Build partial query URL
query_url = f"{url}units={units}&appid={api_key}&q="
query_url

```




    'http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q='




```python
# list to hold the coordinates and cities
coordinates = []

# generate random coordinate pairs of latitude and longitudes
lat = np.random.uniform(low = -90, high = 90, size = 1500)
lon = np.random.uniform(low = -180, high = 180, size = 1500)
coordinates = zip(lat,lon)

```


```python
# creating a DataFrame to hold required values
cities = []


for coordinate_pair in coordinates:
    lat, lon = coordinate_pair
    cities.append(citipy.nearest_city(lat,lon))
   
    
cities_list = []
for city in cities:
    name = city.city_name
    country = city.country_code
    cities_list.append(name)
    


city_name = []
lat = []
temp = []
cloudiness = []
windspeed = []
humidity = []
 
row_count = 1
for city in cities_list:
    print(f"Processing weather information for city {row_count}|{city}")
    print(query_url + str(city))
    row_count+=1

```

    Processing weather information for city 1|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 2|nemuro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nemuro
    Processing weather information for city 3|srikakulam
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=srikakulam
    Processing weather information for city 4|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 5|dikson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dikson
    Processing weather information for city 6|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 7|cherskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cherskiy
    Processing weather information for city 8|ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ribeira grande
    Processing weather information for city 9|nouadhibou
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nouadhibou
    Processing weather information for city 10|itoman
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=itoman
    Processing weather information for city 11|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 12|ostrovnoy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ostrovnoy
    Processing weather information for city 13|chandigarh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chandigarh
    Processing weather information for city 14|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 15|taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=taolanaro
    Processing weather information for city 16|codrington
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=codrington
    Processing weather information for city 17|ellisras
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ellisras
    Processing weather information for city 18|pisco
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pisco
    Processing weather information for city 19|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 20|taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=taolanaro
    Processing weather information for city 21|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 22|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 23|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 24|nouadhibou
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nouadhibou
    Processing weather information for city 25|yerofey pavlovich
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yerofey pavlovich
    Processing weather information for city 26|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 27|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 28|baruun-urt
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=baruun-urt
    Processing weather information for city 29|vanimo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vanimo
    Processing weather information for city 30|lluta
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lluta
    Processing weather information for city 31|nuh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nuh
    Processing weather information for city 32|torbay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=torbay
    Processing weather information for city 33|cabo san lucas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cabo san lucas
    Processing weather information for city 34|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 35|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 36|izvoarele
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=izvoarele
    Processing weather information for city 37|chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chokurdakh
    Processing weather information for city 38|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 39|puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=puerto ayora
    Processing weather information for city 40|longyearbyen
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=longyearbyen
    Processing weather information for city 41|pechora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pechora
    Processing weather information for city 42|vershino-darasunskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vershino-darasunskiy
    Processing weather information for city 43|tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tasiilaq
    Processing weather information for city 44|nong bua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nong bua
    Processing weather information for city 45|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 46|tiksi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tiksi
    Processing weather information for city 47|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 48|kaitangata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kaitangata
    Processing weather information for city 49|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 50|carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carnarvon
    Processing weather information for city 51|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 52|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 53|hofn
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hofn
    Processing weather information for city 54|codrington
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=codrington
    Processing weather information for city 55|saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saskylakh
    Processing weather information for city 56|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 57|baykit
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=baykit
    Processing weather information for city 58|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 59|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 60|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 61|norman wells
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=norman wells
    Processing weather information for city 62|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 63|kiunga
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kiunga
    Processing weather information for city 64|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 65|ilulissat
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ilulissat
    Processing weather information for city 66|amderma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=amderma
    Processing weather information for city 67|bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bengkulu
    Processing weather information for city 68|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 69|puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=puerto ayora
    Processing weather information for city 70|santa eulalia del rio
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=santa eulalia del rio
    Processing weather information for city 71|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 72|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 73|sept-iles
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sept-iles
    Processing weather information for city 74|mount gambier
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mount gambier
    Processing weather information for city 75|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 76|egvekinot
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=egvekinot
    Processing weather information for city 77|mount gambier
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mount gambier
    Processing weather information for city 78|rio grande
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rio grande
    Processing weather information for city 79|panikian
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=panikian
    Processing weather information for city 80|hamilton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hamilton
    Processing weather information for city 81|bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bengkulu
    Processing weather information for city 82|ayan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ayan
    Processing weather information for city 83|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 84|mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mar del plata
    Processing weather information for city 85|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 86|freetown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=freetown
    Processing weather information for city 87|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 88|broken hill
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=broken hill
    Processing weather information for city 89|karla
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=karla
    Processing weather information for city 90|castro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=castro
    Processing weather information for city 91|maarianhamina
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=maarianhamina
    Processing weather information for city 92|oussouye
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=oussouye
    Processing weather information for city 93|buala
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=buala
    Processing weather information for city 94|port-gentil
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port-gentil
    Processing weather information for city 95|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 96|porto novo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=porto novo
    Processing weather information for city 97|ondorhaan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ondorhaan
    Processing weather information for city 98|puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=puerto ayora
    Processing weather information for city 99|vardo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vardo
    Processing weather information for city 100|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 101|qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=qaanaaq
    Processing weather information for city 102|nanortalik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nanortalik
    Processing weather information for city 103|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 104|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 105|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 106|saint-philippe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saint-philippe
    Processing weather information for city 107|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 108|progreso
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=progreso
    Processing weather information for city 109|tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tsihombe
    Processing weather information for city 110|bossangoa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bossangoa
    Processing weather information for city 111|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 112|margate
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=margate
    Processing weather information for city 113|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 114|georgetown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=georgetown
    Processing weather information for city 115|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 116|lorengau
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lorengau
    Processing weather information for city 117|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 118|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 119|wulanhaote
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=wulanhaote
    Processing weather information for city 120|ossora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ossora
    Processing weather information for city 121|taunggyi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=taunggyi
    Processing weather information for city 122|lagoa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lagoa
    Processing weather information for city 123|port blair
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port blair
    Processing weather information for city 124|saleaula
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saleaula
    Processing weather information for city 125|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 126|kaoma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kaoma
    Processing weather information for city 127|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 128|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 129|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 130|vaitupu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaitupu
    Processing weather information for city 131|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 132|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 133|sitka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sitka
    Processing weather information for city 134|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 135|flin flon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=flin flon
    Processing weather information for city 136|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 137|murray bridge
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=murray bridge
    Processing weather information for city 138|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 139|glomfjord
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=glomfjord
    Processing weather information for city 140|santa maria
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=santa maria
    Processing weather information for city 141|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 142|klaksvik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=klaksvik
    Processing weather information for city 143|cayenne
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cayenne
    Processing weather information for city 144|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 145|monrovia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=monrovia
    Processing weather information for city 146|kouroussa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kouroussa
    Processing weather information for city 147|ninh binh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ninh binh
    Processing weather information for city 148|airai
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=airai
    Processing weather information for city 149|clyde river
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=clyde river
    Processing weather information for city 150|shelburne
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=shelburne
    Processing weather information for city 151|tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuktoyaktuk
    Processing weather information for city 152|sentyabrskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sentyabrskiy
    Processing weather information for city 153|mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mar del plata
    Processing weather information for city 154|saldanha
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saldanha
    Processing weather information for city 155|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 156|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 157|koulikoro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=koulikoro
    Processing weather information for city 158|vanavara
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vanavara
    Processing weather information for city 159|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 160|hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hithadhoo
    Processing weather information for city 161|quchan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=quchan
    Processing weather information for city 162|orange park
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=orange park
    Processing weather information for city 163|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 164|aklavik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=aklavik
    Processing weather information for city 165|guelavia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=guelavia
    Processing weather information for city 166|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 167|acapulco
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=acapulco
    Processing weather information for city 168|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 169|san cristobal
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=san cristobal
    Processing weather information for city 170|veraval
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=veraval
    Processing weather information for city 171|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 172|dingle
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dingle
    Processing weather information for city 173|cidreira
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cidreira
    Processing weather information for city 174|sitka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sitka
    Processing weather information for city 175|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 176|nanortalik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nanortalik
    Processing weather information for city 177|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 178|ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ribeira grande
    Processing weather information for city 179|vondrozo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vondrozo
    Processing weather information for city 180|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 181|fortuna
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=fortuna
    Processing weather information for city 182|necochea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=necochea
    Processing weather information for city 183|ilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ilo
    Processing weather information for city 184|bilma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bilma
    Processing weather information for city 185|alice springs
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=alice springs
    Processing weather information for city 186|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 187|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 188|bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bengkulu
    Processing weather information for city 189|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 190|dikson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dikson
    Processing weather information for city 191|cuamba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cuamba
    Processing weather information for city 192|dikson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dikson
    Processing weather information for city 193|kindu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kindu
    Processing weather information for city 194|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 195|luanda
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=luanda
    Processing weather information for city 196|dikson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dikson
    Processing weather information for city 197|saint-pierre
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saint-pierre
    Processing weather information for city 198|ugoofaaru
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ugoofaaru
    Processing weather information for city 199|sangar
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sangar
    Processing weather information for city 200|turayf
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=turayf
    Processing weather information for city 201|leningradskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=leningradskiy
    Processing weather information for city 202|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 203|toliary
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=toliary
    Processing weather information for city 204|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 205|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 206|te anau
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=te anau
    Processing weather information for city 207|lebu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lebu
    Processing weather information for city 208|liuzhou
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=liuzhou
    Processing weather information for city 209|fortuna
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=fortuna
    Processing weather information for city 210|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 211|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 212|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 213|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 214|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 215|saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saskylakh
    Processing weather information for city 216|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 217|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 218|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 219|alofi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=alofi
    Processing weather information for city 220|nizhneyansk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nizhneyansk
    Processing weather information for city 221|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 222|marcona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=marcona
    Processing weather information for city 223|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 224|tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuktoyaktuk
    Processing weather information for city 225|mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mar del plata
    Processing weather information for city 226|gubkinskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=gubkinskiy
    Processing weather information for city 227|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 228|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 229|uri
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=uri
    Processing weather information for city 230|itoman
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=itoman
    Processing weather information for city 231|palmer
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=palmer
    Processing weather information for city 232|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 233|zhanaozen
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zhanaozen
    Processing weather information for city 234|bhilwara
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bhilwara
    Processing weather information for city 235|sovetskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sovetskiy
    Processing weather information for city 236|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 237|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 238|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 239|los llanos de aridane
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=los llanos de aridane
    Processing weather information for city 240|ponta do sol
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ponta do sol
    Processing weather information for city 241|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 242|sao filipe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sao filipe
    Processing weather information for city 243|barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barentsburg
    Processing weather information for city 244|letlhakane
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=letlhakane
    Processing weather information for city 245|mahebourg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mahebourg
    Processing weather information for city 246|tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tsihombe
    Processing weather information for city 247|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 248|andenes
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=andenes
    Processing weather information for city 249|san pedro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=san pedro
    Processing weather information for city 250|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 251|belyy yar
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belyy yar
    Processing weather information for city 252|nikolskoye
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nikolskoye
    Processing weather information for city 253|bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bengkulu
    Processing weather information for city 254|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 255|jalu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jalu
    Processing weather information for city 256|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 257|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 258|chuy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chuy
    Processing weather information for city 259|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 260|longhua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=longhua
    Processing weather information for city 261|faanui
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=faanui
    Processing weather information for city 262|burica
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=burica
    Processing weather information for city 263|acapulco
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=acapulco
    Processing weather information for city 264|makakilo city
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=makakilo city
    Processing weather information for city 265|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 266|bagdarin
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bagdarin
    Processing weather information for city 267|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 268|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 269|bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bengkulu
    Processing weather information for city 270|provideniya
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=provideniya
    Processing weather information for city 271|prata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=prata
    Processing weather information for city 272|port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port elizabeth
    Processing weather information for city 273|tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuktoyaktuk
    Processing weather information for city 274|narsaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=narsaq
    Processing weather information for city 275|severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=severo-kurilsk
    Processing weather information for city 276|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 277|te anau
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=te anau
    Processing weather information for city 278|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 279|hasaki
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hasaki
    Processing weather information for city 280|campbell river
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=campbell river
    Processing weather information for city 281|mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mar del plata
    Processing weather information for city 282|puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=puerto ayora
    Processing weather information for city 283|airai
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=airai
    Processing weather information for city 284|vangaindrano
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vangaindrano
    Processing weather information for city 285|churapcha
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=churapcha
    Processing weather information for city 286|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 287|taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=taolanaro
    Processing weather information for city 288|khovu-aksy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=khovu-aksy
    Processing weather information for city 289|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 290|qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=qaanaaq
    Processing weather information for city 291|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 292|cayenne
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cayenne
    Processing weather information for city 293|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 294|kodiak
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kodiak
    Processing weather information for city 295|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 296|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 297|zhuhai
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zhuhai
    Processing weather information for city 298|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 299|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 300|barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barentsburg
    Processing weather information for city 301|lensk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lensk
    Processing weather information for city 302|touros
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=touros
    Processing weather information for city 303|aldama
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=aldama
    Processing weather information for city 304|milkovo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=milkovo
    Processing weather information for city 305|tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tsihombe
    Processing weather information for city 306|faya
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=faya
    Processing weather information for city 307|labuan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=labuan
    Processing weather information for city 308|barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barentsburg
    Processing weather information for city 309|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 310|torbay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=torbay
    Processing weather information for city 311|tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuktoyaktuk
    Processing weather information for city 312|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 313|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 314|mount gambier
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mount gambier
    Processing weather information for city 315|soc trang
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=soc trang
    Processing weather information for city 316|nizhneyansk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nizhneyansk
    Processing weather information for city 317|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 318|ancud
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ancud
    Processing weather information for city 319|severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=severo-kurilsk
    Processing weather information for city 320|nikolskoye
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nikolskoye
    Processing weather information for city 321|esperance
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=esperance
    Processing weather information for city 322|carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carnarvon
    Processing weather information for city 323|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 324|attawapiskat
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=attawapiskat
    Processing weather information for city 325|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 326|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 327|porto walter
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=porto walter
    Processing weather information for city 328|lorengau
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lorengau
    Processing weather information for city 329|ossora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ossora
    Processing weather information for city 330|sorland
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sorland
    Processing weather information for city 331|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 332|belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belushya guba
    Processing weather information for city 333|nouadhibou
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nouadhibou
    Processing weather information for city 334|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 335|itarema
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=itarema
    Processing weather information for city 336|alofi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=alofi
    Processing weather information for city 337|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 338|nuuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nuuk
    Processing weather information for city 339|plettenberg bay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=plettenberg bay
    Processing weather information for city 340|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 341|mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mys shmidta
    Processing weather information for city 342|bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bredasdorp
    Processing weather information for city 343|kattivakkam
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kattivakkam
    Processing weather information for city 344|qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=qaanaaq
    Processing weather information for city 345|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 346|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 347|gat
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=gat
    Processing weather information for city 348|faanui
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=faanui
    Processing weather information for city 349|luderitz
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=luderitz
    Processing weather information for city 350|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 351|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 352|aras
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=aras
    Processing weather information for city 353|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 354|cherskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cherskiy
    Processing weather information for city 355|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 356|lufilufi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lufilufi
    Processing weather information for city 357|fortuna
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=fortuna
    Processing weather information for city 358|east london
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=east london
    Processing weather information for city 359|coahuayana
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=coahuayana
    Processing weather information for city 360|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 361|puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=puerto ayora
    Processing weather information for city 362|cheuskiny
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cheuskiny
    Processing weather information for city 363|lincoln
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lincoln
    Processing weather information for city 364|guerrero negro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=guerrero negro
    Processing weather information for city 365|liniere
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=liniere
    Processing weather information for city 366|san pablo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=san pablo
    Processing weather information for city 367|brownsville
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=brownsville
    Processing weather information for city 368|brazii
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=brazii
    Processing weather information for city 369|mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mar del plata
    Processing weather information for city 370|bereda
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bereda
    Processing weather information for city 371|tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tasiilaq
    Processing weather information for city 372|port lincoln
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port lincoln
    Processing weather information for city 373|thinadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=thinadhoo
    Processing weather information for city 374|severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=severo-kurilsk
    Processing weather information for city 375|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 376|belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belushya guba
    Processing weather information for city 377|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 378|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 379|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 380|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 381|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 382|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 383|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 384|belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belushya guba
    Processing weather information for city 385|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 386|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 387|anzio
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=anzio
    Processing weather information for city 388|belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belushya guba
    Processing weather information for city 389|lorengau
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lorengau
    Processing weather information for city 390|ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ribeira grande
    Processing weather information for city 391|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 392|mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mar del plata
    Processing weather information for city 393|palmer
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=palmer
    Processing weather information for city 394|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 395|matara
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=matara
    Processing weather information for city 396|lata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lata
    Processing weather information for city 397|ust-nera
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ust-nera
    Processing weather information for city 398|khatanga
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=khatanga
    Processing weather information for city 399|pascagoula
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pascagoula
    Processing weather information for city 400|esperance
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=esperance
    Processing weather information for city 401|hambantota
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hambantota
    Processing weather information for city 402|tres arroyos
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tres arroyos
    Processing weather information for city 403|gat
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=gat
    Processing weather information for city 404|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 405|karwar
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=karwar
    Processing weather information for city 406|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 407|luderitz
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=luderitz
    Processing weather information for city 408|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 409|los llanos de aridane
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=los llanos de aridane
    Processing weather information for city 410|caravelas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=caravelas
    Processing weather information for city 411|marawi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=marawi
    Processing weather information for city 412|pevek
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pevek
    Processing weather information for city 413|awbari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=awbari
    Processing weather information for city 414|yanan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yanan
    Processing weather information for city 415|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 416|abbeville
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=abbeville
    Processing weather information for city 417|mandera
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mandera
    Processing weather information for city 418|sisimiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sisimiut
    Processing weather information for city 419|necochea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=necochea
    Processing weather information for city 420|seymchan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=seymchan
    Processing weather information for city 421|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 422|port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port elizabeth
    Processing weather information for city 423|cayenne
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cayenne
    Processing weather information for city 424|kikwit
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kikwit
    Processing weather information for city 425|graaff-reinet
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=graaff-reinet
    Processing weather information for city 426|tura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tura
    Processing weather information for city 427|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 428|qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=qaanaaq
    Processing weather information for city 429|la palma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=la palma
    Processing weather information for city 430|kulunda
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kulunda
    Processing weather information for city 431|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 432|carquefou
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carquefou
    Processing weather information for city 433|yining
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yining
    Processing weather information for city 434|sitka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sitka
    Processing weather information for city 435|qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=qaanaaq
    Processing weather information for city 436|huarmey
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=huarmey
    Processing weather information for city 437|fortuna
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=fortuna
    Processing weather information for city 438|springbok
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=springbok
    Processing weather information for city 439|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 440|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 441|tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tasiilaq
    Processing weather information for city 442|san cristobal
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=san cristobal
    Processing weather information for city 443|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 444|nanortalik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nanortalik
    Processing weather information for city 445|galiwinku
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=galiwinku
    Processing weather information for city 446|ust-nera
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ust-nera
    Processing weather information for city 447|port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port elizabeth
    Processing weather information for city 448|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 449|dekar
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dekar
    Processing weather information for city 450|paamiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=paamiut
    Processing weather information for city 451|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 452|yilan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yilan
    Processing weather information for city 453|berlevag
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=berlevag
    Processing weather information for city 454|nizhneyansk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nizhneyansk
    Processing weather information for city 455|iqaluit
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=iqaluit
    Processing weather information for city 456|dingle
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dingle
    Processing weather information for city 457|maniitsoq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=maniitsoq
    Processing weather information for city 458|sibu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sibu
    Processing weather information for city 459|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 460|yulara
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yulara
    Processing weather information for city 461|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 462|ancud
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ancud
    Processing weather information for city 463|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 464|tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tasiilaq
    Processing weather information for city 465|saleaula
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saleaula
    Processing weather information for city 466|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 467|lazarev
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lazarev
    Processing weather information for city 468|hami
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hami
    Processing weather information for city 469|castro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=castro
    Processing weather information for city 470|kuusankoski
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kuusankoski
    Processing weather information for city 471|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 472|olafsvik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=olafsvik
    Processing weather information for city 473|albert
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albert
    Processing weather information for city 474|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 475|attawapiskat
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=attawapiskat
    Processing weather information for city 476|riyadh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=riyadh
    Processing weather information for city 477|makakilo city
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=makakilo city
    Processing weather information for city 478|sydney
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sydney
    Processing weather information for city 479|ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ribeira grande
    Processing weather information for city 480|kaptanganj
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kaptanganj
    Processing weather information for city 481|avera
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avera
    Processing weather information for city 482|umm lajj
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=umm lajj
    Processing weather information for city 483|saint george
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saint george
    Processing weather information for city 484|vredendal
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vredendal
    Processing weather information for city 485|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 486|tubuala
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tubuala
    Processing weather information for city 487|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 488|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 489|taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=taolanaro
    Processing weather information for city 490|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 491|grindavik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=grindavik
    Processing weather information for city 492|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 493|salisbury
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=salisbury
    Processing weather information for city 494|vestmannaeyjar
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vestmannaeyjar
    Processing weather information for city 495|gornopravdinsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=gornopravdinsk
    Processing weather information for city 496|richards bay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=richards bay
    Processing weather information for city 497|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 498|samusu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=samusu
    Processing weather information for city 499|hofn
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hofn
    Processing weather information for city 500|jiuquan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jiuquan
    Processing weather information for city 501|clyde river
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=clyde river
    Processing weather information for city 502|bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bredasdorp
    Processing weather information for city 503|bousso
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bousso
    Processing weather information for city 504|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 505|belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belushya guba
    Processing weather information for city 506|vardo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vardo
    Processing weather information for city 507|carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carnarvon
    Processing weather information for city 508|talnakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=talnakh
    Processing weather information for city 509|vao
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vao
    Processing weather information for city 510|ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ribeira grande
    Processing weather information for city 511|tiksi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tiksi
    Processing weather information for city 512|dudinka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dudinka
    Processing weather information for city 513|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 514|kahului
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kahului
    Processing weather information for city 515|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 516|cayenne
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cayenne
    Processing weather information for city 517|palmer
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=palmer
    Processing weather information for city 518|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 519|kaeo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kaeo
    Processing weather information for city 520|madisonville
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=madisonville
    Processing weather information for city 521|doha
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=doha
    Processing weather information for city 522|narsaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=narsaq
    Processing weather information for city 523|quang ngai
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=quang ngai
    Processing weather information for city 524|rodrigues alves
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rodrigues alves
    Processing weather information for city 525|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 526|tabiauea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tabiauea
    Processing weather information for city 527|veraval
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=veraval
    Processing weather information for city 528|belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belushya guba
    Processing weather information for city 529|zhigansk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zhigansk
    Processing weather information for city 530|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 531|paragominas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=paragominas
    Processing weather information for city 532|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 533|vestmannaeyjar
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vestmannaeyjar
    Processing weather information for city 534|pingxiang
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pingxiang
    Processing weather information for city 535|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 536|beringovskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=beringovskiy
    Processing weather information for city 537|batagay-alyta
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=batagay-alyta
    Processing weather information for city 538|alofi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=alofi
    Processing weather information for city 539|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 540|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 541|vao
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vao
    Processing weather information for city 542|surt
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=surt
    Processing weather information for city 543|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 544|luderitz
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=luderitz
    Processing weather information for city 545|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 546|port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port elizabeth
    Processing weather information for city 547|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 548|lorengau
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lorengau
    Processing weather information for city 549|rincon de la victoria
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rincon de la victoria
    Processing weather information for city 550|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 551|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 552|lagos
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lagos
    Processing weather information for city 553|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 554|nanortalik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nanortalik
    Processing weather information for city 555|la asuncion
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=la asuncion
    Processing weather information for city 556|makakilo city
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=makakilo city
    Processing weather information for city 557|englehart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=englehart
    Processing weather information for city 558|broken hill
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=broken hill
    Processing weather information for city 559|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 560|satitoa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=satitoa
    Processing weather information for city 561|baykit
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=baykit
    Processing weather information for city 562|upernavik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=upernavik
    Processing weather information for city 563|vaitupu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaitupu
    Processing weather information for city 564|tilichiki
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tilichiki
    Processing weather information for city 565|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 566|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 567|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 568|sao geraldo do araguaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sao geraldo do araguaia
    Processing weather information for city 569|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 570|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 571|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 572|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 573|kodiak
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kodiak
    Processing weather information for city 574|lukovetskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lukovetskiy
    Processing weather information for city 575|victoria
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=victoria
    Processing weather information for city 576|inuvik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=inuvik
    Processing weather information for city 577|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 578|kinsale
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kinsale
    Processing weather information for city 579|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 580|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 581|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 582|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 583|ancud
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ancud
    Processing weather information for city 584|grimstad
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=grimstad
    Processing weather information for city 585|broken hill
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=broken hill
    Processing weather information for city 586|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 587|grindavik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=grindavik
    Processing weather information for city 588|hasaki
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hasaki
    Processing weather information for city 589|attawapiskat
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=attawapiskat
    Processing weather information for city 590|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 591|saint-philippe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saint-philippe
    Processing weather information for city 592|syamzha
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=syamzha
    Processing weather information for city 593|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 594|pimentel
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pimentel
    Processing weather information for city 595|wapi pathum
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=wapi pathum
    Processing weather information for city 596|port lincoln
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port lincoln
    Processing weather information for city 597|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 598|tingrela
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tingrela
    Processing weather information for city 599|rajshahi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rajshahi
    Processing weather information for city 600|boffa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=boffa
    Processing weather information for city 601|bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bredasdorp
    Processing weather information for city 602|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 603|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 604|bilma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bilma
    Processing weather information for city 605|iberia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=iberia
    Processing weather information for city 606|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 607|pangnirtung
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pangnirtung
    Processing weather information for city 608|plastun
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=plastun
    Processing weather information for city 609|mazatlan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mazatlan
    Processing weather information for city 610|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 611|arys
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=arys
    Processing weather information for city 612|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 613|thompson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=thompson
    Processing weather information for city 614|nikolskoye
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nikolskoye
    Processing weather information for city 615|luderitz
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=luderitz
    Processing weather information for city 616|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 617|shebunino
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=shebunino
    Processing weather information for city 618|mount pleasant
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mount pleasant
    Processing weather information for city 619|boguchany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=boguchany
    Processing weather information for city 620|upernavik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=upernavik
    Processing weather information for city 621|sentyabrskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sentyabrskiy
    Processing weather information for city 622|tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tasiilaq
    Processing weather information for city 623|batagay-alyta
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=batagay-alyta
    Processing weather information for city 624|curvelo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=curvelo
    Processing weather information for city 625|axixa do tocantins
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=axixa do tocantins
    Processing weather information for city 626|nagua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nagua
    Processing weather information for city 627|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 628|airai
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=airai
    Processing weather information for city 629|mongo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mongo
    Processing weather information for city 630|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 631|bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bengkulu
    Processing weather information for city 632|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 633|saldanha
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saldanha
    Processing weather information for city 634|okandja
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=okandja
    Processing weather information for city 635|iberia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=iberia
    Processing weather information for city 636|mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mar del plata
    Processing weather information for city 637|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 638|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 639|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 640|bargal
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bargal
    Processing weather information for city 641|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 642|port macquarie
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port macquarie
    Processing weather information for city 643|lisakovsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lisakovsk
    Processing weather information for city 644|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 645|tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tasiilaq
    Processing weather information for city 646|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 647|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 648|vila
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vila
    Processing weather information for city 649|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 650|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 651|cabo san lucas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cabo san lucas
    Processing weather information for city 652|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 653|necochea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=necochea
    Processing weather information for city 654|belaya gora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belaya gora
    Processing weather information for city 655|khatanga
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=khatanga
    Processing weather information for city 656|nishihara
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nishihara
    Processing weather information for city 657|torbay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=torbay
    Processing weather information for city 658|saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saskylakh
    Processing weather information for city 659|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 660|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 661|hofn
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hofn
    Processing weather information for city 662|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 663|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 664|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 665|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 666|chateaubelair
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chateaubelair
    Processing weather information for city 667|lethem
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lethem
    Processing weather information for city 668|saint-augustin
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saint-augustin
    Processing weather information for city 669|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 670|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 671|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 672|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 673|luderitz
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=luderitz
    Processing weather information for city 674|alexandria
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=alexandria
    Processing weather information for city 675|saratov
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saratov
    Processing weather information for city 676|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 677|hagenow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hagenow
    Processing weather information for city 678|lavrentiya
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lavrentiya
    Processing weather information for city 679|cherskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cherskiy
    Processing weather information for city 680|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 681|moranbah
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=moranbah
    Processing weather information for city 682|cherskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cherskiy
    Processing weather information for city 683|taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=taolanaro
    Processing weather information for city 684|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 685|padang
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=padang
    Processing weather information for city 686|amderma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=amderma
    Processing weather information for city 687|broken hill
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=broken hill
    Processing weather information for city 688|mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mar del plata
    Processing weather information for city 689|boa vista
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=boa vista
    Processing weather information for city 690|talnakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=talnakh
    Processing weather information for city 691|grand river south east
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=grand river south east
    Processing weather information for city 692|esperance
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=esperance
    Processing weather information for city 693|faya
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=faya
    Processing weather information for city 694|kamenka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kamenka
    Processing weather information for city 695|bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bredasdorp
    Processing weather information for city 696|colares
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=colares
    Processing weather information for city 697|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 698|santa maria
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=santa maria
    Processing weather information for city 699|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 700|san ramon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=san ramon
    Processing weather information for city 701|carauari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carauari
    Processing weather information for city 702|mahalapye
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mahalapye
    Processing weather information for city 703|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 704|sao miguel do araguaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sao miguel do araguaia
    Processing weather information for city 705|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 706|pevek
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pevek
    Processing weather information for city 707|qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=qaanaaq
    Processing weather information for city 708|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 709|boshnyakovo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=boshnyakovo
    Processing weather information for city 710|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 711|attawapiskat
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=attawapiskat
    Processing weather information for city 712|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 713|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 714|barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barentsburg
    Processing weather information for city 715|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 716|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 717|maragogi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=maragogi
    Processing weather information for city 718|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 719|east london
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=east london
    Processing weather information for city 720|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 721|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 722|bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bengkulu
    Processing weather information for city 723|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 724|nelson bay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nelson bay
    Processing weather information for city 725|ambovombe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ambovombe
    Processing weather information for city 726|dikson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dikson
    Processing weather information for city 727|rantauprapat
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rantauprapat
    Processing weather information for city 728|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 729|hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hithadhoo
    Processing weather information for city 730|bilma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bilma
    Processing weather information for city 731|ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ribeira grande
    Processing weather information for city 732|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 733|zeya
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zeya
    Processing weather information for city 734|nanortalik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nanortalik
    Processing weather information for city 735|zaraza
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zaraza
    Processing weather information for city 736|deputatskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=deputatskiy
    Processing weather information for city 737|uturoa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=uturoa
    Processing weather information for city 738|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 739|paysandu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=paysandu
    Processing weather information for city 740|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 741|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 742|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 743|hamilton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hamilton
    Processing weather information for city 744|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 745|kahului
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kahului
    Processing weather information for city 746|hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hithadhoo
    Processing weather information for city 747|norman wells
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=norman wells
    Processing weather information for city 748|hualmay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hualmay
    Processing weather information for city 749|george town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=george town
    Processing weather information for city 750|manggar
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=manggar
    Processing weather information for city 751|mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mar del plata
    Processing weather information for city 752|lavrentiya
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lavrentiya
    Processing weather information for city 753|rungata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rungata
    Processing weather information for city 754|dikson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dikson
    Processing weather information for city 755|carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carnarvon
    Processing weather information for city 756|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 757|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 758|kavaratti
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kavaratti
    Processing weather information for city 759|bay city
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bay city
    Processing weather information for city 760|mahebourg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mahebourg
    Processing weather information for city 761|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 762|dikson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dikson
    Processing weather information for city 763|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 764|cidreira
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cidreira
    Processing weather information for city 765|kutulik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kutulik
    Processing weather information for city 766|algiers
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=algiers
    Processing weather information for city 767|itarema
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=itarema
    Processing weather information for city 768|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 769|jizan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jizan
    Processing weather information for city 770|asau
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=asau
    Processing weather information for city 771|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 772|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 773|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 774|qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=qaanaaq
    Processing weather information for city 775|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 776|bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bengkulu
    Processing weather information for city 777|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 778|wyszkow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=wyszkow
    Processing weather information for city 779|khatanga
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=khatanga
    Processing weather information for city 780|leningradskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=leningradskiy
    Processing weather information for city 781|dingle
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dingle
    Processing weather information for city 782|berdigestyakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=berdigestyakh
    Processing weather information for city 783|pontianak
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pontianak
    Processing weather information for city 784|sitka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sitka
    Processing weather information for city 785|barcelos
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barcelos
    Processing weather information for city 786|shimoda
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=shimoda
    Processing weather information for city 787|thio
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=thio
    Processing weather information for city 788|pisco
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pisco
    Processing weather information for city 789|puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=puerto ayora
    Processing weather information for city 790|tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tasiilaq
    Processing weather information for city 791|killybegs
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=killybegs
    Processing weather information for city 792|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 793|hervey bay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hervey bay
    Processing weather information for city 794|dikson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dikson
    Processing weather information for city 795|parry sound
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=parry sound
    Processing weather information for city 796|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 797|richards bay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=richards bay
    Processing weather information for city 798|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 799|pisco
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pisco
    Processing weather information for city 800|kaitangata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kaitangata
    Processing weather information for city 801|faanui
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=faanui
    Processing weather information for city 802|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 803|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 804|tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tasiilaq
    Processing weather information for city 805|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 806|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 807|gurmatkal
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=gurmatkal
    Processing weather information for city 808|dudinka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dudinka
    Processing weather information for city 809|hofn
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hofn
    Processing weather information for city 810|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 811|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 812|tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuktoyaktuk
    Processing weather information for city 813|aykhal
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=aykhal
    Processing weather information for city 814|airai
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=airai
    Processing weather information for city 815|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 816|hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hithadhoo
    Processing weather information for city 817|chumikan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chumikan
    Processing weather information for city 818|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 819|grand river south east
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=grand river south east
    Processing weather information for city 820|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 821|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 822|paramonga
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=paramonga
    Processing weather information for city 823|mayumba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mayumba
    Processing weather information for city 824|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 825|viedma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=viedma
    Processing weather information for city 826|borogontsy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=borogontsy
    Processing weather information for city 827|barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barentsburg
    Processing weather information for city 828|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 829|masvingo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=masvingo
    Processing weather information for city 830|santa ana
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=santa ana
    Processing weather information for city 831|lasa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lasa
    Processing weather information for city 832|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 833|san patricio
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=san patricio
    Processing weather information for city 834|tiksi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tiksi
    Processing weather information for city 835|cherskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cherskiy
    Processing weather information for city 836|provideniya
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=provideniya
    Processing weather information for city 837|ilulissat
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ilulissat
    Processing weather information for city 838|mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mar del plata
    Processing weather information for city 839|yenagoa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yenagoa
    Processing weather information for city 840|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 841|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 842|hasaki
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hasaki
    Processing weather information for city 843|kodiak
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kodiak
    Processing weather information for city 844|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 845|puerto ayacucho
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=puerto ayacucho
    Processing weather information for city 846|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 847|torbay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=torbay
    Processing weather information for city 848|tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuktoyaktuk
    Processing weather information for city 849|qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=qaanaaq
    Processing weather information for city 850|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 851|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 852|mozarlandia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mozarlandia
    Processing weather information for city 853|muswellbrook
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=muswellbrook
    Processing weather information for city 854|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 855|mahebourg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mahebourg
    Processing weather information for city 856|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 857|labuhan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=labuhan
    Processing weather information for city 858|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 859|thompson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=thompson
    Processing weather information for city 860|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 861|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 862|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 863|saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saskylakh
    Processing weather information for city 864|manzil salim
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=manzil salim
    Processing weather information for city 865|bristol
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bristol
    Processing weather information for city 866|puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=puerto ayora
    Processing weather information for city 867|bani
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bani
    Processing weather information for city 868|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 869|mnogovershinnyy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mnogovershinnyy
    Processing weather information for city 870|oranjestad
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=oranjestad
    Processing weather information for city 871|victoria
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=victoria
    Processing weather information for city 872|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 873|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 874|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 875|tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tsihombe
    Processing weather information for city 876|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 877|mehamn
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mehamn
    Processing weather information for city 878|georgetown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=georgetown
    Processing weather information for city 879|port hedland
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port hedland
    Processing weather information for city 880|esna
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=esna
    Processing weather information for city 881|cidreira
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cidreira
    Processing weather information for city 882|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 883|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 884|chokwe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chokwe
    Processing weather information for city 885|ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ribeira grande
    Processing weather information for city 886|caravelas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=caravelas
    Processing weather information for city 887|walvis bay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=walvis bay
    Processing weather information for city 888|sao filipe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sao filipe
    Processing weather information for city 889|bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bengkulu
    Processing weather information for city 890|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 891|halalo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=halalo
    Processing weather information for city 892|nanortalik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nanortalik
    Processing weather information for city 893|oussouye
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=oussouye
    Processing weather information for city 894|leticia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=leticia
    Processing weather information for city 895|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 896|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 897|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 898|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 899|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 900|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 901|ostrovnoy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ostrovnoy
    Processing weather information for city 902|kenai
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kenai
    Processing weather information for city 903|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 904|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 905|aswan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=aswan
    Processing weather information for city 906|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 907|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 908|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 909|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 910|kabare
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kabare
    Processing weather information for city 911|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 912|barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barentsburg
    Processing weather information for city 913|kaitangata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kaitangata
    Processing weather information for city 914|lebu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lebu
    Processing weather information for city 915|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 916|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 917|tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuktoyaktuk
    Processing weather information for city 918|tasiilaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tasiilaq
    Processing weather information for city 919|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 920|port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port elizabeth
    Processing weather information for city 921|ausa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ausa
    Processing weather information for city 922|bilibino
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bilibino
    Processing weather information for city 923|mount isa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mount isa
    Processing weather information for city 924|clyde river
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=clyde river
    Processing weather information for city 925|pacific grove
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pacific grove
    Processing weather information for city 926|carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carnarvon
    Processing weather information for city 927|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 928|olafsvik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=olafsvik
    Processing weather information for city 929|tiksi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tiksi
    Processing weather information for city 930|carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carnarvon
    Processing weather information for city 931|chicama
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chicama
    Processing weather information for city 932|bredasdorp
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bredasdorp
    Processing weather information for city 933|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 934|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 935|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 936|vila do maio
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vila do maio
    Processing weather information for city 937|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 938|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 939|korla
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=korla
    Processing weather information for city 940|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 941|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 942|kamenka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kamenka
    Processing weather information for city 943|ayagoz
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ayagoz
    Processing weather information for city 944|victoria
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=victoria
    Processing weather information for city 945|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 946|pevek
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pevek
    Processing weather information for city 947|port ellen
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port ellen
    Processing weather information for city 948|mayumba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mayumba
    Processing weather information for city 949|attawapiskat
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=attawapiskat
    Processing weather information for city 950|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 951|wagar
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=wagar
    Processing weather information for city 952|portland
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=portland
    Processing weather information for city 953|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 954|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 955|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 956|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 957|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 958|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 959|dingle
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dingle
    Processing weather information for city 960|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 961|belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belushya guba
    Processing weather information for city 962|azanka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=azanka
    Processing weather information for city 963|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 964|mao
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mao
    Processing weather information for city 965|katsuura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=katsuura
    Processing weather information for city 966|severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=severo-kurilsk
    Processing weather information for city 967|vardo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vardo
    Processing weather information for city 968|bolungarvik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bolungarvik
    Processing weather information for city 969|bose
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bose
    Processing weather information for city 970|beloha
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=beloha
    Processing weather information for city 971|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 972|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 973|meyungs
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=meyungs
    Processing weather information for city 974|beipiao
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=beipiao
    Processing weather information for city 975|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 976|rawlins
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rawlins
    Processing weather information for city 977|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 978|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 979|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 980|tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tsihombe
    Processing weather information for city 981|severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=severo-kurilsk
    Processing weather information for city 982|hervey bay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hervey bay
    Processing weather information for city 983|mlonggo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mlonggo
    Processing weather information for city 984|port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port elizabeth
    Processing weather information for city 985|tuatapere
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuatapere
    Processing weather information for city 986|taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=taolanaro
    Processing weather information for city 987|haibowan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=haibowan
    Processing weather information for city 988|torbay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=torbay
    Processing weather information for city 989|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 990|mar del plata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mar del plata
    Processing weather information for city 991|mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mys shmidta
    Processing weather information for city 992|jalu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jalu
    Processing weather information for city 993|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 994|lorengau
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lorengau
    Processing weather information for city 995|cabo san lucas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cabo san lucas
    Processing weather information for city 996|sentyabrskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sentyabrskiy
    Processing weather information for city 997|taburi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=taburi
    Processing weather information for city 998|hamilton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hamilton
    Processing weather information for city 999|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1000|ilulissat
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ilulissat
    Processing weather information for city 1001|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 1002|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1003|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 1004|provideniya
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=provideniya
    Processing weather information for city 1005|los llanos de aridane
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=los llanos de aridane
    Processing weather information for city 1006|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 1007|soe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=soe
    Processing weather information for city 1008|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 1009|newport
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=newport
    Processing weather information for city 1010|cidreira
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cidreira
    Processing weather information for city 1011|kaduqli
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kaduqli
    Processing weather information for city 1012|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 1013|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 1014|cherskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cherskiy
    Processing weather information for city 1015|tabiauea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tabiauea
    Processing weather information for city 1016|aklavik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=aklavik
    Processing weather information for city 1017|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 1018|porosozero
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=porosozero
    Processing weather information for city 1019|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1020|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1021|carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carnarvon
    Processing weather information for city 1022|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 1023|tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tsihombe
    Processing weather information for city 1024|saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saskylakh
    Processing weather information for city 1025|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 1026|biak
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=biak
    Processing weather information for city 1027|rocky mountain house
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rocky mountain house
    Processing weather information for city 1028|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1029|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1030|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 1031|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1032|izhma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=izhma
    Processing weather information for city 1033|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 1034|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 1035|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 1036|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1037|arraial do cabo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=arraial do cabo
    Processing weather information for city 1038|kodiak
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kodiak
    Processing weather information for city 1039|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 1040|leningradskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=leningradskiy
    Processing weather information for city 1041|zinder
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zinder
    Processing weather information for city 1042|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1043|aflu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=aflu
    Processing weather information for city 1044|hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hithadhoo
    Processing weather information for city 1045|mount isa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mount isa
    Processing weather information for city 1046|ugoofaaru
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ugoofaaru
    Processing weather information for city 1047|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 1048|kilindoni
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kilindoni
    Processing weather information for city 1049|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1050|hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hithadhoo
    Processing weather information for city 1051|lorengau
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lorengau
    Processing weather information for city 1052|thinadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=thinadhoo
    Processing weather information for city 1053|arraial do cabo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=arraial do cabo
    Processing weather information for city 1054|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1055|avera
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avera
    Processing weather information for city 1056|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1057|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 1058|zarichne
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zarichne
    Processing weather information for city 1059|manokwari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=manokwari
    Processing weather information for city 1060|kaoma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kaoma
    Processing weather information for city 1061|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 1062|bethel
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bethel
    Processing weather information for city 1063|meulaboh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=meulaboh
    Processing weather information for city 1064|doctor pedro p. pena
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=doctor pedro p. pena
    Processing weather information for city 1065|mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mys shmidta
    Processing weather information for city 1066|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 1067|avera
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avera
    Processing weather information for city 1068|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 1069|richards bay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=richards bay
    Processing weather information for city 1070|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 1071|yirol
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yirol
    Processing weather information for city 1072|severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=severo-kurilsk
    Processing weather information for city 1073|coquimbo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=coquimbo
    Processing weather information for city 1074|belozerskoye
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belozerskoye
    Processing weather information for city 1075|fram
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=fram
    Processing weather information for city 1076|lebu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lebu
    Processing weather information for city 1077|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1078|kabinda
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kabinda
    Processing weather information for city 1079|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 1080|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 1081|dikson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dikson
    Processing weather information for city 1082|hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hithadhoo
    Processing weather information for city 1083|waingapu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=waingapu
    Processing weather information for city 1084|mount darwin
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mount darwin
    Processing weather information for city 1085|puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=puerto ayora
    Processing weather information for city 1086|fairview
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=fairview
    Processing weather information for city 1087|bougouni
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bougouni
    Processing weather information for city 1088|saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saskylakh
    Processing weather information for city 1089|neyshabur
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=neyshabur
    Processing weather information for city 1090|den helder
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=den helder
    Processing weather information for city 1091|mys shmidta
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mys shmidta
    Processing weather information for city 1092|mount gambier
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mount gambier
    Processing weather information for city 1093|lesogorsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lesogorsk
    Processing weather information for city 1094|mahibadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mahibadhoo
    Processing weather information for city 1095|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 1096|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 1097|qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=qaanaaq
    Processing weather information for city 1098|lompoc
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lompoc
    Processing weather information for city 1099|lagoa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lagoa
    Processing weather information for city 1100|namibe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=namibe
    Processing weather information for city 1101|hasaki
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hasaki
    Processing weather information for city 1102|puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=puerto ayora
    Processing weather information for city 1103|vardo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vardo
    Processing weather information for city 1104|ust-omchug
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ust-omchug
    Processing weather information for city 1105|boddam
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=boddam
    Processing weather information for city 1106|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 1107|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1108|tsihombe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tsihombe
    Processing weather information for city 1109|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1110|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 1111|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 1112|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1113|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 1114|chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chokurdakh
    Processing weather information for city 1115|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 1116|bursol
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bursol
    Processing weather information for city 1117|gladstone
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=gladstone
    Processing weather information for city 1118|cayenne
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cayenne
    Processing weather information for city 1119|lebu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lebu
    Processing weather information for city 1120|ketchikan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ketchikan
    Processing weather information for city 1121|saint george
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saint george
    Processing weather information for city 1122|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1123|zemio
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zemio
    Processing weather information for city 1124|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1125|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 1126|srednekolymsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=srednekolymsk
    Processing weather information for city 1127|biloela
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=biloela
    Processing weather information for city 1128|cansahcab
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cansahcab
    Processing weather information for city 1129|svetlyy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=svetlyy
    Processing weather information for city 1130|naze
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=naze
    Processing weather information for city 1131|hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hithadhoo
    Processing weather information for city 1132|pokosnoye
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pokosnoye
    Processing weather information for city 1133|tulum
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tulum
    Processing weather information for city 1134|whittlesea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=whittlesea
    Processing weather information for city 1135|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1136|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 1137|belomorsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belomorsk
    Processing weather information for city 1138|port-gentil
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port-gentil
    Processing weather information for city 1139|port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port elizabeth
    Processing weather information for city 1140|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 1141|elizabeth city
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=elizabeth city
    Processing weather information for city 1142|tete
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tete
    Processing weather information for city 1143|coruripe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=coruripe
    Processing weather information for city 1144|swellendam
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=swellendam
    Processing weather information for city 1145|severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=severo-kurilsk
    Processing weather information for city 1146|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 1147|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 1148|egypt lake-leto
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=egypt lake-leto
    Processing weather information for city 1149|chuy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chuy
    Processing weather information for city 1150|longyearbyen
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=longyearbyen
    Processing weather information for city 1151|puerto ayora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=puerto ayora
    Processing weather information for city 1152|farnham
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=farnham
    Processing weather information for city 1153|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 1154|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1155|tiksi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tiksi
    Processing weather information for city 1156|manaus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=manaus
    Processing weather information for city 1157|tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuktoyaktuk
    Processing weather information for city 1158|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 1159|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 1160|gboko
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=gboko
    Processing weather information for city 1161|isabela
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=isabela
    Processing weather information for city 1162|ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ribeira grande
    Processing weather information for city 1163|clyde river
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=clyde river
    Processing weather information for city 1164|pozoblanco
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pozoblanco
    Processing weather information for city 1165|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1166|ponta do sol
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ponta do sol
    Processing weather information for city 1167|tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuktoyaktuk
    Processing weather information for city 1168|rio gallegos
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rio gallegos
    Processing weather information for city 1169|kiunga
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kiunga
    Processing weather information for city 1170|ponta delgada
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ponta delgada
    Processing weather information for city 1171|qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=qaanaaq
    Processing weather information for city 1172|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 1173|karaton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=karaton
    Processing weather information for city 1174|san policarpo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=san policarpo
    Processing weather information for city 1175|pevek
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pevek
    Processing weather information for city 1176|nikolskoye
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nikolskoye
    Processing weather information for city 1177|tessalit
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tessalit
    Processing weather information for city 1178|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1179|klyuchi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=klyuchi
    Processing weather information for city 1180|praia da vitoria
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=praia da vitoria
    Processing weather information for city 1181|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 1182|leningradskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=leningradskiy
    Processing weather information for city 1183|georgetown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=georgetown
    Processing weather information for city 1184|atambua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atambua
    Processing weather information for city 1185|qaanaaq
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=qaanaaq
    Processing weather information for city 1186|kodiak
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kodiak
    Processing weather information for city 1187|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1188|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 1189|egvekinot
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=egvekinot
    Processing weather information for city 1190|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1191|bethel
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bethel
    Processing weather information for city 1192|bethel
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bethel
    Processing weather information for city 1193|talakan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=talakan
    Processing weather information for city 1194|roald
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=roald
    Processing weather information for city 1195|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 1196|mrirt
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mrirt
    Processing weather information for city 1197|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 1198|isla vista
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=isla vista
    Processing weather information for city 1199|okhotsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=okhotsk
    Processing weather information for city 1200|castro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=castro
    Processing weather information for city 1201|chuy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chuy
    Processing weather information for city 1202|caravelas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=caravelas
    Processing weather information for city 1203|namatanai
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=namatanai
    Processing weather information for city 1204|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 1205|pevek
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pevek
    Processing weather information for city 1206|bluff
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bluff
    Processing weather information for city 1207|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 1208|maun
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=maun
    Processing weather information for city 1209|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1210|zaraza
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zaraza
    Processing weather information for city 1211|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 1212|yellowknife
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yellowknife
    Processing weather information for city 1213|lichinga
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lichinga
    Processing weather information for city 1214|upernavik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=upernavik
    Processing weather information for city 1215|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 1216|barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barentsburg
    Processing weather information for city 1217|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1218|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1219|castro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=castro
    Processing weather information for city 1220|upernavik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=upernavik
    Processing weather information for city 1221|yumen
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yumen
    Processing weather information for city 1222|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 1223|dikson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dikson
    Processing weather information for city 1224|hereford
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hereford
    Processing weather information for city 1225|tiksi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tiksi
    Processing weather information for city 1226|whitehorse
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=whitehorse
    Processing weather information for city 1227|kaitangata
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kaitangata
    Processing weather information for city 1228|manaus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=manaus
    Processing weather information for city 1229|saint-francois
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saint-francois
    Processing weather information for city 1230|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 1231|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 1232|saleaula
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saleaula
    Processing weather information for city 1233|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 1234|luderitz
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=luderitz
    Processing weather information for city 1235|maldonado
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=maldonado
    Processing weather information for city 1236|kailua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kailua
    Processing weather information for city 1237|portland
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=portland
    Processing weather information for city 1238|gwadar
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=gwadar
    Processing weather information for city 1239|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1240|inirida
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=inirida
    Processing weather information for city 1241|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 1242|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1243|port-gentil
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port-gentil
    Processing weather information for city 1244|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 1245|malanje
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=malanje
    Processing weather information for city 1246|thompson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=thompson
    Processing weather information for city 1247|tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuktoyaktuk
    Processing weather information for city 1248|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1249|lambari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lambari
    Processing weather information for city 1250|dakar
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dakar
    Processing weather information for city 1251|el dorado
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=el dorado
    Processing weather information for city 1252|provideniya
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=provideniya
    Processing weather information for city 1253|tevriz
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tevriz
    Processing weather information for city 1254|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1255|miracema do tocantins
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=miracema do tocantins
    Processing weather information for city 1256|mahon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mahon
    Processing weather information for city 1257|niles
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=niles
    Processing weather information for city 1258|grand river south east
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=grand river south east
    Processing weather information for city 1259|belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belushya guba
    Processing weather information for city 1260|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 1261|bima
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bima
    Processing weather information for city 1262|sarangani
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sarangani
    Processing weather information for city 1263|yumen
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yumen
    Processing weather information for city 1264|saint-francois
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saint-francois
    Processing weather information for city 1265|port lincoln
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port lincoln
    Processing weather information for city 1266|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1267|umm kaddadah
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=umm kaddadah
    Processing weather information for city 1268|tuatapere
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuatapere
    Processing weather information for city 1269|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 1270|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 1271|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1272|marsh harbour
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=marsh harbour
    Processing weather information for city 1273|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 1274|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1275|tunceli
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tunceli
    Processing weather information for city 1276|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 1277|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 1278|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1279|correntina
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=correntina
    Processing weather information for city 1280|winneba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=winneba
    Processing weather information for city 1281|tiksi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tiksi
    Processing weather information for city 1282|santa cruz
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=santa cruz
    Processing weather information for city 1283|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 1284|sentyabrskiy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sentyabrskiy
    Processing weather information for city 1285|akita
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=akita
    Processing weather information for city 1286|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 1287|syracuse
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=syracuse
    Processing weather information for city 1288|zyryanka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zyryanka
    Processing weather information for city 1289|port augusta
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port augusta
    Processing weather information for city 1290|chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chokurdakh
    Processing weather information for city 1291|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 1292|kruisfontein
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kruisfontein
    Processing weather information for city 1293|castro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=castro
    Processing weather information for city 1294|severo-kurilsk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=severo-kurilsk
    Processing weather information for city 1295|saskylakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saskylakh
    Processing weather information for city 1296|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1297|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1298|ponta do sol
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ponta do sol
    Processing weather information for city 1299|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 1300|karratha
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=karratha
    Processing weather information for city 1301|amderma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=amderma
    Processing weather information for city 1302|dromolaxia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dromolaxia
    Processing weather information for city 1303|geraldton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=geraldton
    Processing weather information for city 1304|kwinana
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kwinana
    Processing weather information for city 1305|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 1306|belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belushya guba
    Processing weather information for city 1307|quezon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=quezon
    Processing weather information for city 1308|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 1309|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 1310|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 1311|hobyo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobyo
    Processing weather information for city 1312|finschhafen
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=finschhafen
    Processing weather information for city 1313|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 1314|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 1315|kingaroy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kingaroy
    Processing weather information for city 1316|tuatapere
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuatapere
    Processing weather information for city 1317|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 1318|san patricio
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=san patricio
    Processing weather information for city 1319|flin flon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=flin flon
    Processing weather information for city 1320|iquique
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=iquique
    Processing weather information for city 1321|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 1322|amderma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=amderma
    Processing weather information for city 1323|namatanai
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=namatanai
    Processing weather information for city 1324|aklavik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=aklavik
    Processing weather information for city 1325|dzhubga
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dzhubga
    Processing weather information for city 1326|thompson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=thompson
    Processing weather information for city 1327|neulengbach
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=neulengbach
    Processing weather information for city 1328|yerbogachen
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yerbogachen
    Processing weather information for city 1329|dikson
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dikson
    Processing weather information for city 1330|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 1331|bandarbeyla
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bandarbeyla
    Processing weather information for city 1332|tiksi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tiksi
    Processing weather information for city 1333|tura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tura
    Processing weather information for city 1334|lompoc
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lompoc
    Processing weather information for city 1335|poum
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=poum
    Processing weather information for city 1336|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1337|broome
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=broome
    Processing weather information for city 1338|amderma
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=amderma
    Processing weather information for city 1339|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1340|carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carnarvon
    Processing weather information for city 1341|taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=taolanaro
    Processing weather information for city 1342|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 1343|hobart
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hobart
    Processing weather information for city 1344|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 1345|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 1346|tautira
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tautira
    Processing weather information for city 1347|carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carnarvon
    Processing weather information for city 1348|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1349|tiksi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tiksi
    Processing weather information for city 1350|hilo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hilo
    Processing weather information for city 1351|petatlan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=petatlan
    Processing weather information for city 1352|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1353|mahebourg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mahebourg
    Processing weather information for city 1354|artyk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=artyk
    Processing weather information for city 1355|mbanza-ngungu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mbanza-ngungu
    Processing weather information for city 1356|nemuro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nemuro
    Processing weather information for city 1357|port alfred
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port alfred
    Processing weather information for city 1358|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1359|sandy bay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sandy bay
    Processing weather information for city 1360|los andes
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=los andes
    Processing weather information for city 1361|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1362|ponta do sol
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ponta do sol
    Processing weather information for city 1363|alihe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=alihe
    Processing weather information for city 1364|taitung
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=taitung
    Processing weather information for city 1365|revelstoke
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=revelstoke
    Processing weather information for city 1366|tiksi
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tiksi
    Processing weather information for city 1367|banda aceh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=banda aceh
    Processing weather information for city 1368|batemans bay
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=batemans bay
    Processing weather information for city 1369|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 1370|manokwari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=manokwari
    Processing weather information for city 1371|novopokrovka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=novopokrovka
    Processing weather information for city 1372|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 1373|kontagora
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kontagora
    Processing weather information for city 1374|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 1375|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 1376|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 1377|zhuozhou
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zhuozhou
    Processing weather information for city 1378|clyde river
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=clyde river
    Processing weather information for city 1379|khasan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=khasan
    Processing weather information for city 1380|simao
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=simao
    Processing weather information for city 1381|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 1382|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 1383|butaritari
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=butaritari
    Processing weather information for city 1384|saleaula
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saleaula
    Processing weather information for city 1385|bakel
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bakel
    Processing weather information for city 1386|cape town
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cape town
    Processing weather information for city 1387|luderitz
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=luderitz
    Processing weather information for city 1388|kapaa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kapaa
    Processing weather information for city 1389|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 1390|whitianga
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=whitianga
    Processing weather information for city 1391|upernavik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=upernavik
    Processing weather information for city 1392|carnarvon
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=carnarvon
    Processing weather information for city 1393|skalistyy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=skalistyy
    Processing weather information for city 1394|taolanaro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=taolanaro
    Processing weather information for city 1395|quatre cocos
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=quatre cocos
    Processing weather information for city 1396|egvekinot
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=egvekinot
    Processing weather information for city 1397|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1398|sinnamary
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sinnamary
    Processing weather information for city 1399|bondo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bondo
    Processing weather information for city 1400|norman wells
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=norman wells
    Processing weather information for city 1401|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1402|nossa senhora das dores
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nossa senhora das dores
    Processing weather information for city 1403|chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chokurdakh
    Processing weather information for city 1404|saint-philippe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saint-philippe
    Processing weather information for city 1405|ponta do sol
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ponta do sol
    Processing weather information for city 1406|vaini
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=vaini
    Processing weather information for city 1407|tagusao
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tagusao
    Processing weather information for city 1408|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1409|acarau
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=acarau
    Processing weather information for city 1410|port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port elizabeth
    Processing weather information for city 1411|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 1412|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 1413|tuktoyaktuk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tuktoyaktuk
    Processing weather information for city 1414|nhulunbuy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nhulunbuy
    Processing weather information for city 1415|eyl
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=eyl
    Processing weather information for city 1416|bengkulu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bengkulu
    Processing weather information for city 1417|ushuaia
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ushuaia
    Processing weather information for city 1418|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 1419|koryukivka
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=koryukivka
    Processing weather information for city 1420|pevek
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pevek
    Processing weather information for city 1421|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1422|shelburne
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=shelburne
    Processing weather information for city 1423|chuy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chuy
    Processing weather information for city 1424|ahipara
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ahipara
    Processing weather information for city 1425|camacupa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=camacupa
    Processing weather information for city 1426|yatou
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yatou
    Processing weather information for city 1427|port elizabeth
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=port elizabeth
    Processing weather information for city 1428|bambous virieux
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bambous virieux
    Processing weather information for city 1429|zhigansk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=zhigansk
    Processing weather information for city 1430|castro
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=castro
    Processing weather information for city 1431|ballina
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ballina
    Processing weather information for city 1432|east london
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=east london
    Processing weather information for city 1433|yaring
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=yaring
    Processing weather information for city 1434|lebu
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lebu
    Processing weather information for city 1435|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1436|belgaum
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belgaum
    Processing weather information for city 1437|barrow
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barrow
    Processing weather information for city 1438|nanortalik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nanortalik
    Processing weather information for city 1439|kodiak
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kodiak
    Processing weather information for city 1440|cortez
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cortez
    Processing weather information for city 1441|ahipara
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ahipara
    Processing weather information for city 1442|dunedin
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dunedin
    Processing weather information for city 1443|albany
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=albany
    Processing weather information for city 1444|kidal
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kidal
    Processing weather information for city 1445|dzilam gonzalez
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=dzilam gonzalez
    Processing weather information for city 1446|luena
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=luena
    Processing weather information for city 1447|upernavik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=upernavik
    Processing weather information for city 1448|chuy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chuy
    Processing weather information for city 1449|bethel
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bethel
    Processing weather information for city 1450|bonthe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bonthe
    Processing weather information for city 1451|mataura
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mataura
    Processing weather information for city 1452|isangel
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=isangel
    Processing weather information for city 1453|provideniya
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=provideniya
    Processing weather information for city 1454|nanortalik
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nanortalik
    Processing weather information for city 1455|saint-philippe
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=saint-philippe
    Processing weather information for city 1456|lasa
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lasa
    Processing weather information for city 1457|thinadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=thinadhoo
    Processing weather information for city 1458|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1459|hithadhoo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hithadhoo
    Processing weather information for city 1460|pontianak
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pontianak
    Processing weather information for city 1461|iracoubo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=iracoubo
    Processing weather information for city 1462|atuona
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=atuona
    Processing weather information for city 1463|hegang
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hegang
    Processing weather information for city 1464|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 1465|illoqqortoormiut
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=illoqqortoormiut
    Processing weather information for city 1466|talnakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=talnakh
    Processing weather information for city 1467|chokurdakh
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=chokurdakh
    Processing weather information for city 1468|sao joao da barra
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=sao joao da barra
    Processing weather information for city 1469|cidreira
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cidreira
    Processing weather information for city 1470|broome
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=broome
    Processing weather information for city 1471|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1472|nikolskoye
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nikolskoye
    Processing weather information for city 1473|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1474|raudeberg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=raudeberg
    Processing weather information for city 1475|new norfolk
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=new norfolk
    Processing weather information for city 1476|busselton
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=busselton
    Processing weather information for city 1477|mongo
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=mongo
    Processing weather information for city 1478|tumannyy
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=tumannyy
    Processing weather information for city 1479|manhattan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=manhattan
    Processing weather information for city 1480|suzhou
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=suzhou
    Processing weather information for city 1481|avarua
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=avarua
    Processing weather information for city 1482|ribeira grande
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=ribeira grande
    Processing weather information for city 1483|koslan
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=koslan
    Processing weather information for city 1484|georgetown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=georgetown
    Processing weather information for city 1485|rikitea
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=rikitea
    Processing weather information for city 1486|nikolskoye
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=nikolskoye
    Processing weather information for city 1487|cidreira
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=cidreira
    Processing weather information for city 1488|lincoln
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=lincoln
    Processing weather information for city 1489|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1490|kodiak
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=kodiak
    Processing weather information for city 1491|pacific grove
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=pacific grove
    Processing weather information for city 1492|jamestown
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=jamestown
    Processing weather information for city 1493|faanui
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=faanui
    Processing weather information for city 1494|barentsburg
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=barentsburg
    Processing weather information for city 1495|esperance
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=esperance
    Processing weather information for city 1496|bandarbeyla
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=bandarbeyla
    Processing weather information for city 1497|punta arenas
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=punta arenas
    Processing weather information for city 1498|hermanus
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=hermanus
    Processing weather information for city 1499|belushya guba
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=belushya guba
    Processing weather information for city 1500|khatanga
    http://api.openweathermap.org/data/2.5/weather?units=imperial&appid=e2a6ea9786b38b55cafa2a4fcad7ed7b&q=khatanga



```python
for city_count in cities_list:
    response = requests.get(query_url + str(city_count)).json()
    try:
        lat.append(response['coord']['lat'])
    except:
        continue
    city_name.append(response['name'])
    temp.append(response['main']['temp'])
    windspeed.append(response['wind']['speed'])
    cloudiness.append(response['clouds']['all'])
    humidity.append(response['main']['humidity'])
```


```python
city_df=pd.DataFrame({"City":city_name,
                      "Latitude":lat,
                      "Temperature":temp,
                      "Cloudiness":cloudiness,
                      "Windspeed":windspeed,
                      "Humidity":humidity,
                      })
city_df.head()
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
      <th>City</th>
      <th>Cloudiness</th>
      <th>Humidity</th>
      <th>Latitude</th>
      <th>Temperature</th>
      <th>Windspeed</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Hilo</td>
      <td>1</td>
      <td>88</td>
      <td>19.71</td>
      <td>73.40</td>
      <td>6.93</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nemuro</td>
      <td>75</td>
      <td>81</td>
      <td>43.32</td>
      <td>46.40</td>
      <td>8.05</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Srikakulam</td>
      <td>0</td>
      <td>92</td>
      <td>18.29</td>
      <td>85.61</td>
      <td>10.76</td>
    </tr>
    <tr>
      <th>3</th>
      <td>New Norfolk</td>
      <td>20</td>
      <td>40</td>
      <td>-42.78</td>
      <td>69.80</td>
      <td>17.22</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Dikson</td>
      <td>36</td>
      <td>91</td>
      <td>73.51</td>
      <td>1.55</td>
      <td>18.81</td>
    </tr>
  </tbody>
</table>
</div>




```python
# exporting data frame to a csv file
csv_data = city_df.to_csv('Weather Data.csv')
```


```python
# scatter plot of Temperature vs. Latitude
x_axis = city_df['Latitude']
y_axis = city_df['Temperature']
plt.scatter(x_axis,y_axis)
plt.gca().set(xlabel='Latitude',ylabel='Temperature(F)',title='Latitude vs. Temperature')
plt.legend(loc = 'best')
plt.savefig('Scatter plot L-T.png')
plt.show()
```


![png](output_7_0.png)



```python
# scatter plot of Humidity vs. Latitude
x_axis = city_df['Latitude']
y_axis = city_df['Humidity']
plt.scatter(x_axis,y_axis)
plt.gca().set(xlabel='Latitude',ylabel='Humidity(%)',title='Latitude vs. Humidity')
plt.legend(loc = 'best')
plt.savefig('Scatter plot L-H.png')
plt.show()
```


![png](output_8_0.png)



```python
# scatter plot of Cloudiness vs. Latitude
x_axis = city_df['Latitude']
y_axis = city_df['Cloudiness']
plt.scatter(x_axis,y_axis)
plt.gca().set(xlabel='Latitude',ylabel='Cloudiness(%)',title='Latitude vs. Cloudiness')
plt.legend(loc = 'best')
plt.savefig('Scatter plot L-C.png')
plt.show()
```


![png](output_9_0.png)



```python
# scatter plot of Windspeed vs. Latitude
x_axis = city_df['Latitude']
y_axis = city_df['Windspeed']
plt.scatter(x_axis,y_axis)
plt.gca().set(xlabel='Latitude',ylabel='Windspeed(mph)',title='Latitude vs. Windspeed')
plt.legend(loc = 'best')
plt.savefig('Scatter plot L-WS.png')
plt.show()
```


![png](output_10_0.png)

