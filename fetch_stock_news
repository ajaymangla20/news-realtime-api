import requests
import pandas as pd
from datetime import datetime
import os

API_KEY = os.getenv("NEWS_API_KEY")

url = f"https://newsapi.org/v2/everything?q=stocks&sources=bloomberg,financial-times,cnbc&apiKey={API_KEY}"

try:
    # Send GET request with a timeout of 10 seconds
    response = requests.get(url, timeout=10)
    
    # Raise an HTTPError for bad responses (4xx, 5xx)
    response.raise_for_status()
    
    # Try to parse JSON response
    articles = response.json()
    print("Success! Data received:")
    news_data = []
    for article in articles['articles']:
        news_data.append({
            "source": article['source']['name'],
            "author": article['author'],
            "title": article['title'],
            "description": article['description'],
            "url": article['url'],
            "published_at": article['publishedAt'],
            "content": article['content']
        })
    df = pd.DataFrame(news_data)
    print(df.head())

except HTTPError as http_err:
    # Handle HTTP error (4xx or 5xx responses)
    if 400 <= response.status_code < 500:
        print(f"Client Error: {http_err}")
        print(f"Status Code: {response.status_code}, Message: {response.text}")
    elif 500 <= response.status_code < 600:
        print(f"Server Error: {http_err}")
        print(f"Status Code: {response.status_code}, Message: {response.text}")

except Timeout:
    # Handle timeout error (request took too long)
    print("The request timed out. Try again later.")

except JSONDecodeError:
    # Handle errors when JSON decoding fails
    print("Failed to decode JSON. The response might not be in JSON format.")

except RequestException as req_err:
    # Handle other types of errors (e.g., network issues, invalid URL)
    print(f"Request failed: {req_err}")

except Exception as err:
    # Catch any other unexpected errors
    print(f"An unexpected error occurred: {err}")

