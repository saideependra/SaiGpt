# 🚀 SaiGPT – Agentic AI Chatbot

SaiGPT is an open-source **Agentic AI Chatbot** built using Python, FastAPI, LangGraph, LangChain, Google Gemini, Tavily, ChromaDB, and SQLite.

It provides an intelligent conversational experience with real-time response streaming, document uploads, Retrieval-Augmented Generation (RAG), web search, and persistent conversation memory.

The project is designed to demonstrate modern agentic AI architecture with scalable backend development and cloud deployment.

---

## ✨ Features

- 🤖 AI-powered chatbot using Google Gemini
- ⚡ Real-time streaming responses
- 📄 Upload PDF, DOCX, TXT, MD, PY, and CSV documents
- 🧠 Retrieval-Augmented Generation (RAG)
- 🔎 Web search using Tavily
- 💬 Persistent conversation history
- 🔗 Agent orchestration using LangGraph
- 🗄️ Vector storage using ChromaDB
- 💾 SQLite-based persistence
- 🌐 FastAPI backend with a simple web interface
- 🐳 Docker containerization
- ☁️ AWS deployment using ECR and EC2
- 🔄 Automated CI/CD using GitHub Actions

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python 3.11 | Programming language |
| FastAPI | Backend framework |
| LangChain | LLM integration and RAG |
| LangGraph | Agent orchestration |
| Google Gemini | Large Language Model |
| Tavily | Web search |
| ChromaDB | Vector database |
| SQLite | Persistent storage |
| Hugging Face | Embeddings and NLP |
| Jinja2 | Frontend templating |
| Docker | Containerization |
| AWS ECR | Container image registry |
| AWS EC2 | Cloud deployment |
| GitHub Actions | CI/CD automation |

---

## 📁 Project Structure

```text
SaiGpt/
│
├── app.py
├── agent.py
├── database.py
├── rag.py
├── tools.py
│
├── requirements.txt
├── .env
├── .gitignore
│
├── Dockerfile
├── .dockerignore
│
├── templates/
│   └── index.html
│
├── uploads/
├── data/
├── chroma_db/
│
└── .github/
    └── workflows/
        └── cicd.yaml
```

*The structure may evolve as new features are added.*

---

## ⚙️ Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/SaiGpt.git
```

### 2. Navigate to the Project

```bash
cd SaiGpt
```

### 3. Create a Virtual Environment

For Ubuntu/Linux:

```bash
python3 -m venv venv
```

### 4. Activate the Virtual Environment

```bash
source venv/bin/activate
```

### 5. Upgrade pip

```bash
python -m pip install --upgrade pip
```

### 6. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 🔑 Environment Variables

Create a `.env` file in the project root directory.

```env
GOOGLE_API_KEY=your_google_api_key
GOOGLE_MODEL=gemini-2.5-flash

TAVILY_API_KEY=your_tavily_api_key

LANGSMITH_TRACING=false
LANGSMITH_ENDPOINT=https://api.smith.langchain.com
LANGSMITH_API_KEY=your_langsmith_api_key
LANGSMITH_PROJECT=saigpt
```

**Note:** LangSmith is optional. Keep `LANGSMITH_TRACING=false` if you do not want tracing.

Never commit your `.env` file to GitHub.

---

## ▶️ Run Locally

Activate your virtual environment:

```bash
source venv/bin/activate
```

Start the FastAPI application:

```bash
python app.py
```

Open your browser:

```text
http://127.0.0.1:8080
```

---

## 🐳 Docker Deployment

### 1. Build Docker Image

```bash
docker build -t saigpt .
```

### 2. Run Docker Container

```bash
docker run -d \
  --name saigpt \
  --restart always \
  -p 8080:8080 \
  --env-file .env \
  saigpt
```

Access the application:

```text
http://localhost:8080
```

---

## ☁️ AWS CI/CD Deployment

SaiGPT supports automated deployment using:

- GitHub Actions
- Amazon ECR
- Amazon EC2
- Docker
- GitHub Self-Hosted Runner

### Deployment Workflow

1. Developer pushes code to GitHub.
2. GitHub Actions triggers the CI/CD pipeline.
3. Docker image is built.
4. Image is pushed to Amazon E