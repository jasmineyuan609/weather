UK Weather API 
This project provides a simple Python-based API for retrieving weather data across various cities in the UK. It fetches weather information from an external service (e.g., OpenWeatherMap) and uses Pygame to display it in a graphical interface.

Features
Fetches weather data for various UK cities.

Displays weather information (e.g., temperature, conditions) using Pygame.

Shows real-time weather updates with a user-friendly interface.

Requirements
Python 3.x

Pygame

Requests (for fetching weather data from an external API)

OpenWeatherMap API Key (or similar weather data provider)

Install Dependencies
Install the required libraries using pip:

bash
Copy
Edit
pip install pygame requests
Get an API key from OpenWeatherMap (or another weather provider). You can sign up for a free API key on their website.

Setup
Download the project and navigate to the folder containing the code.

Open the file weather_api.py and replace the API_KEY variable with your own key from OpenWeatherMap or another provider.

Run the program:

bash
Copy
Edit
python weather_api.py
Usage
The program will display a graphical interface using Pygame, showing the weather information for a default UK city (e.g., London).

You can update the city by typing the name of another city in the input box.

Weather details like temperature, humidity, and conditions will be updated and displayed on the screen.

Example Output
City: London

Temperature: 15°C

Condition: Clear Sky

Humidity: 75%

Code Example
python
Copy
Edit
import pygame
import requests
import json

# Pygame setup
pygame.init()
screen = pygame.display.set_mode((400, 300))
pygame.display.set_caption("UK Weather")

font = pygame.font.SysFont('Arial', 24)

# API Configuration
API_KEY = "your_openweathermap_api_key"
BASE_URL = "http://api.openweathermap.org/data/2.5/weather?"

# Function to fetch weather data
def get_weather(city):
    complete_url = BASE_URL + "q=" + city + "&appid=" + API_KEY + "&units=metric"
    response = requests.get(complete_url)
    data = response.json()

    if data["cod"] == "404":
        return None
    else:
        main_data = data["main"]
        weather_data = data["weather"][0]
        temperature = main_data["temp"]
        description = weather_data["description"]
        humidity = main_data["humidity"]

        return {"temp": temperature, "desc": description, "humidity": humidity}

# Main loop
running = True
city = "London"
weather_info = get_weather(city)

while running:
    screen.fill((255, 255, 255))  # Fill the screen with a white background

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    if weather_info:
        temp_text = font.render(f"Temperature: {weather_info['temp']}°C", True, (0, 0, 0))
        desc_text = font.render(f"Condition: {weather_info['desc']}", True, (0, 0, 0))
        humidity_text = font.render(f"Humidity: {weather_info['humidity']}%", True, (0, 0, 0))

        screen.blit(temp_text, (20, 50))
        screen.blit(desc_text, (20, 100))
        screen.blit(humidity_text, (20, 150))

    pygame.display.flip()

pygame.quit()
Customization
Cities: You can change the city by modifying the city variable in the code or adding an input box to let the user enter a city dynamically.

Weather Information: Modify the get_weather function to display additional weather data like wind speed or pressure.

Troubleshooting
API Key Error: Ensure you've replaced the API_KEY variable with a valid API key from OpenWeatherMap.

Pygame Issues: Make sure Pygame is correctly installed and that your Python environment is set up properly.

License
This project is open-source and available under the MIT License.
