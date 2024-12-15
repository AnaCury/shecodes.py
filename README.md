# shecodes.py
Python foundations
def get_weather(city):
  '''Display currrent weather for a city'''
  api_key = "59bb440b331f3618c8f63oceca0t0e45"
  api_url = f"https://api.shecodes.io/weather/v1/current?query={city_name}&key={api_key}"
  response = requests.get(api_url)
  weather_data = response.json()
  weather_city = weather_data['city']
  weather_temp = weather_data['temperature']['current']

  print(f"The temperatue in {weather_city} is {weather_temp} degrees")


def display_forecast_weather(city_name):
  api_key = "59bb440b331f3618c8f63oceca0t0e45"
  api_url = f"https://api.shecodes.io/weather/v1/forecast?query={city_name}&key={api_key}"

  response_forecast = requests.get(api_url)
  forecast_data = response_forecast.json()

  for day in forecast_data['daily']:
    timestamp = day['time']
    date = datetime.fromtimestamp(timestamp).strftime('%A')

    temperature_forecast = day['temperature']['day']

    print(f"{date}: {temperature_forecast}")


city_name = input("Enter city name: ")
city_name = city_name.strip()

if city_name:
  get_weather(city_name)
  print("\n[blue bold]Forecast:[/blue bold]")
  display_forecast_weather(city_name)
  print("\n[yellow bold]This app was made with love by Ana Cury[/yellow bold]")

else:
  print("Please enter a city name.")
