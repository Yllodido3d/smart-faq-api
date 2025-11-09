# 🧠 ReadyAnswers API

Automatic answer API with text matching in English using Fuzzy Matching.

## 🚀 Main Endpoints

| Method | Route | Description |
|--------|--------|--------------|
| POST | `/answer` | Returns the most similar answer to the given question |
| GET | `/categories` | Lists all existing categories |
| GET | `/questions/{cat}` | Lists all questions from a category |
| POST | `/add` | Adds a new question/answer |
| POST | `/import_csv` | Imports questions from a CSV file |
| GET | `/status` | Shows uptime, total answers, and version |

## 🔑 Authentication

All routes (except `/status`) require an **API Key**:
```bash
?api_key=123abc
````

##💡 Example Usage
curl -X POST "https://your-render-url.onrender.com/answer?api_key=123abc" \
     -H "Content-Type: application/json" \
     -d '{"question": "what is your name?"}'

##📦 Deploy

The project is ready for deployment on Render.com

and integration with RapidAPI
.
