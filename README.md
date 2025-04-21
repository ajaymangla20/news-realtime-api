
# 📈 Stock News API Script

This Python script fetches stock-related news articles using the **NewsAPI** and stores them in a **pandas DataFrame**. It includes robust error handling for HTTP errors, timeouts, and other common issues when working with APIs.

---

## 📋 Requirements

- Python 3.x
- Libraries:
  - `requests`
  - `pandas`
  - `python-dotenv` (optional but recommended for managing API keys securely)

---

## 🛠 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/stock-news-api.git
cd stock-news-api
```

### 2. Install Dependencies

```bash
pip install -r requirements.txt
```

### 3. Set Up Environment Variables

Create a `.env` file in your project directory:

```dotenv
NEWS_API_KEY=your_api_key_here
```


---

## 🚀 Usage

Run the script:

```bash
python fetch_stock_news.py
```

It will fetch the latest articles containing the keyword `stocks`, process them, and display the results as a DataFrame.

---

## 🔄 Script Logic

1. Load `NEWS_API_KEY` from environment.
2. Make a GET request to NewsAPI with a `q=stocks` query.
3. Parse the JSON response.
4. Store articles in a pandas DataFrame.
5. Print the first few rows.

---

## ❗ Error Handling

- `HTTPError`: Handles 4xx and 5xx status codes.
- `Timeout`: In case the request takes too long.
- `JSONDecodeError`: If response is not valid JSON.
- `RequestException`: Catches all other request-related issues.

---

## 🧪 Example Output

```
Success! Data received:
         source       author              title             published_at
0     Reuters     John Smith     Stocks Rally Today     2025-04-21T12:00:00Z
1     CNBC        Jane Doe       Market Update         2025-04-21T11:30:00Z
...
```

---

## 📦 requirements.txt

```text
requests==2.28.1
pandas==1.5.3
python-dotenv==0.21.0
```

---

## 🔐 API Key Safety

Never hardcode API keys into your script. Use environment variables or `.env` files, and **do not upload `.env` to GitHub**. Add it to `.gitignore`.

---


