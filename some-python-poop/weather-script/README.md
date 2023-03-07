# ☁ Weather script

```
from config import weather_token
import requests
import datetime
from colourtest import *


def weather_no_country(city, API_token):
    try:
        r = requests.get(
            f'https://api.openweathermap.org/data/2.5/weather?q={city}&appid={API_token}')
        data = r.json()

        cur_datetime = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

        cur_temp = int((data['main']['temp']) - 273.15)

        feel_like = int(data['main']['feels_like'] - 273.15)

        wind_speed = data['wind']['speed']

        weather_type = data['weather'][0]['description']

        dolgota = data['coord']['lon']

        shirota = data['coord']['lat']

        country = data['sys']['country']
        # print(data)
        print(
            f'\033[38;5;141m*****{cur_datetime}*****\033[0;0m\n'
            f'Weather in \033[38;5;40m{city}\033[0;0m, \033[38;5;40m{country}\033[0;0m:\n'
            f'Current temperature is {colored_tmp(cur_temp)}°C\n'
            f'Feels like {colored_tmp(feel_like)}°C\n'
            f'Wind speed is {colored_wind(wind_speed)} m/s\n'
            f'There is \033[38;5;156m{weather_type}\033[0;0m outside\n'
            f'City coordinats is \033[4m{shirota}\033[0m \033[4m{dolgota}\033[0m')

    except Exception as ex:
        print(ex)
        print(f'\033[93mSomething gone wrong, u might check city name\033[0m')


def weather(city, country_token, API_token):
    try:
        r = requests.get(f'https://api.openweathermap.org/data/2.5/weather?q={city},{country_token}&appid={API_token}')
        data = r.json()

        cur_datetime = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")

        cur_temp = int((data['main']['temp']) - 273.15)

        feel_like = int(data['main']['feels_like'] - 273.15)

        wind_speed = data['wind']['speed']

        weather_type = data['weather'][0]['description']

        longitude = data['coord']['lon']

        latitude = data['coord']['lat']

        country = data['sys']['country']

        # print(data)

        print(
            f'\033[38;5;141m*****{cur_datetime}*****\033[0;0m\n'
            f'Weather in {city}, {country}:\n'
            f'Current temperature is {colored_tmp(cur_temp)}°C\n'
            f'Feels like {colored_tmp(feel_like)}°C\n'
            f'Wind speed is {colored_wind(wind_speed)} m/s\n'
            f'There is \033[38;5;156m{weather_type}\033[0;0m outside\n'
            f'City coordinats is \033[4m{latitude}\033[0m \033[4m{longitude}\033[0m')

    except Exception as ex:
        print(ex)
        print(f'\033[93mSomething gone wrong, u might check city name\033[0m')


def main():

    city = input('Enter city: ')
    country_token = input('Enter tountry code: ')
    if country_token == '':
        weather_no_country(city, weather_token)
    else:
        weather(city, country_token, weather_token)


if __name__ == '__main__':    #everlasting script
    while True:
        main()

# if __name__ == '__main__':
#     main()
```
