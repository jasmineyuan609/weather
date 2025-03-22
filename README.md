#London Weather API

Overview

The London Weather API provides real-time and forecasted weather data for London, UK. This API allows developers to retrieve current temperature, humidity, wind speed, and other meteorological data.

Features

Real-time weather data for London

7-day weather forecast

Hourly weather updates

Air quality index (AQI)

UV index information

Base URL

https://api.londonweather.com/v1/

Authentication

To use the API, you need an API key. Register at London Weather API to obtain a key.

Include your API key in the request header:

Authorization: Bearer YOUR_API_KEY

Endpoints

1. Get Current Weather

GET /weather/current

Response:

{
  "temperature": "15°C",
  "humidity": "72%",
  "wind_speed": "10 km/h",
  "condition": "Cloudy",
  "aqi": 42,
  "uv_index": 3
}

2. Get 7-Day Forecast

GET /weather/forecast

Response:

{
  "forecast": [
    {"day": "Monday", "temperature": "14°C", "condition": "Rainy"},
    {"day": "Tuesday", "temperature": "16°C", "condition": "Cloudy"},
    {"day": "Wednesday", "temperature": "17°C", "condition": "Sunny"}
  ]
}

3. Get Hourly Weather

GET /weather/hourly

Response:

{
  "hourly": [
    {"time": "09:00", "temperature": "14°C", "condition": "Cloudy"},
    {"time": "12:00", "temperature": "16°C", "condition": "Sunny"}
  ]
}

4. Get Air Quality Index

GET /weather/air-quality

Response:

{
  "aqi": 42,
  "status": "Good"
}

Rate Limits

Free Tier: 1000 requests/month

Pro Tier: 10,000 requests/month

Enterprise: Unlimited

Error Handling

401 Unauthorized: Invalid or missing API key

404 Not Found: Requested resource not available

429 Too Many Requests: Rate limit exceeded

500 Internal Server Error: API server issue

Support

For questions and support, contact us at support@londonweather.com.
