# 💬 ReadyAnswers API

A simple **FastAPI-based REST API** that provides quick pre-defined answers for common questions — ideal for bots, prototypes, or internal tools.  
This version replaces the original Portuguese database and endpoints with English ones.

---

## 🚀 Features

- 🔑 Simple API key authentication  
- 💡 Fuzzy search for best matching answers (using RapidFuzz)  
- 📦 Import and store Q&A data in SQLite  
- 📊 Daily usage limit per IP  
- 📁 CSV import support  
- ⚙️ FastAPI + Uvicorn stack for easy deployment  

---

## 🧠 Endpoints Overview

| Method | Endpoint | Description |
|--------|-----------|-------------|
| `POST` | `/answer` | Returns the best-matching answer for a question |
| `GET`  | `/categories` | Lists all categories available |
| `GET`  | `/questions/{category}` | Lists all questions from a category |
| `POST` | `/add` | Add a new question/answer pair manually |
| `POST` | `/import_csv` | Import multiple Q&A entries via CSV |
| `GET`  | `/status` | API status and uptime |

---

## 🔒 Authentication

Every request must include an API key:
?api_key=123abc


(Default key can be changed in the environment variable `API_KEY`.)

Example:


POST /answer?api_key=123abc


---

## 🧩 Database

SQLite database file: `answers.db`  
Schema:

| Column | Type | Description |
|--------|------|-------------|
| id | INTEGER | Auto increment |
| question | TEXT | User question |
| answer | TEXT | Stored response |
| category | TEXT | Optional category |

---

## 📥 CSV Import Format

To bulk import data, upload a `.csv` file with the following format:

```csv
question,answer,category
"What is FastAPI?","FastAPI is a modern, fast web framework for Python.","Python"
"How to install it?","Use pip install fastapi uvicorn.","Python"


Then use the /import_csv endpoint.

⚡ Deployment

Example render.yaml for Render.com:

services:
  - type: web
    name: readyanswers-api
    env: python
    buildCommand: ""
    startCommand: uvicorn main:app --host 0.0.0.0 --port 10000
    plan: free
    autoDeploy: true

requirements.txt
fastapi
uvicorn
pydantic
python-multipart
rapidfuzz
unidecode

🧪 Test Locally
uvicorn main:app --reload


Then open:
👉 http://127.0.0.1:8000/docs

🧰 Example Request
curl -X POST "https://readyanswers-api.onrender.com/answer?api_key=123abc" \
     -H "Content-Type: application/json" \
     -d '{"question": "What is FastAPI?"}'


Response:

{
  "answer": "FastAPI is a modern, fast web framework for Python.",
  "confidence": "97.2%"
}

🧙‍♂️ About

Originally created for Portuguese users as “Respostas Prontas BR”,
now rebuilt for global usage with English dataset and structure.
