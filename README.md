# 🚀 SaiGPT – Agentic AI Chatbot

SaiGPT is an open-source **Agentic AI Chatbot** built using Python, FastAPI, LangGraph, LangChain, multiple LLM providers, ChromaDB, and SQLite.

It combines modern AI agent architecture with Retrieval-Augmented Generation (RAG), real-time streaming, web search, conversational memory, and external tools to provide an intelligent conversational experience.

The project also demonstrates backend development, containerization, cloud deployment, and CI/CD automation using AWS and GitHub Actions.

---

## ✨ Features

- 🤖 AI-powered conversational assistant
- 🧠 Agent orchestration using LangGraph
- 🔗 LLM integration using LangChain
- ⚡ Real-time streaming responses
- 📄 Document upload and processing
- 📚 Retrieval-Augmented Generation (RAG)
- 🔎 Real-time web search using Tavily
- 💬 Persistent conversation history
- 🗄️ Vector storage using ChromaDB
- 💾 SQLite-based persistence
- 🌐 FastAPI backend
- 🌤️ Weather information through external APIs
- 🔌 Multiple LLM provider integrations
- 🐳 Docker containerization
- ☁️ AWS deployment using ECR and EC2
- 🔄 Automated CI/CD using GitHub Actions
- 📊 LangSmith tracing and monitoring

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python 3.11 | Programming language |
| FastAPI | Backend framework |
| LangChain | LLM integration and RAG |
| LangGraph | Agent orchestration |
| OpenRouter | Multiple LLM access |
| Google Gemini | LLM inference |
| Groq | Fast LLM inference |
| OpenAI | LLM integration |
| Hugging Face | Embeddings and NLP |
| Tavily | Web search |
| ChromaDB | Vector database |
| SQLite | Persistent storage |
| Jinja2 | Frontend templating |
| Weatherstack | Weather information |
| OpenWeather | Weather information |
| LangSmith | Tracing and monitoring |
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

*Note: The structure may evolve as the project develops.*

---

## ⚙️ Getting Started

### Prerequisites

Make sure you have installed:

- Python 3.11
- pip
- Git
- Docker (optional)
- API keys for the services you intend to use

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

SaiGPT integrates multiple LLM providers, monitoring services, web search tools, and weather APIs.

Create a `.env` file in the root directory of the project.

```env
# =========================
# LLM Providers
# =========================

OPENROUTER_API_KEY=your_openrouter_api_key
GOOGLE_API_KEY=your_google_api_key
GROQ_API_KEY=your_groq_api_key
OPENAI_API_KEY=your_openai_api_key

# =========================
# LangSmith Monitoring
# =========================

LANGSMITH_TRACING=true
LANGSMITH_ENDPOINT=https://api.smith.langchain.com
LANGSMITH_API_KEY=your_langsmith_api_key
LANGSMITH_AGENT_ID=agentic-chatbot-project
LANGSMITH_AGENT_ENVIRONMENT=local

# =========================
# Web Search
# =========================

TAVILY_API_KEY=your_tavily_api_key

# =========================
# Weather APIs
# =========================

WEATHERSTACK_API_KEY=your_weatherstack_api_key
OPENWHEATHER_API_KEY=your_openweather_api_key
```

### Supported Integrations

| Provider | Purpose |
|---|---|
| OpenRouter | Access to multiple LLMs |
| Google Gemini | LLM inference |
| Groq | Fast LLM inference |
| OpenAI | LLM integration |
| LangSmith | Agent tracing and monitoring |
| Tavily | Web search |
| Weatherstack | Weather information |
| OpenWeather | Weather information |

**Important:**

- You only need API keys for the integrations you actually use.
- Never commit your `.env` file to GitHub.
- Never hardcode API keys in Python files.
- Use GitHub Secrets for cloud deployment.
- Rotate any credentials accidentally exposed publicly.

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

### Useful Docker Commands

Check running containers:

```bash
docker ps
```

View application logs:

```bash
docker logs -f saigpt
```

Stop the container:

```bash
docker stop saigpt
```

Remove the container:

```bash
docker rm saigpt
```

---

## ☁️ AWS CI/CD Deployment

SaiGPT supports automated deployment using:

- GitHub Actions
- Amazon ECR
- Amazon EC2
- Docker
- GitHub Self-Hosted Runner

### Deployment Architecture

```text
Developer
    |
    v
GitHub Repository
    |
    v
GitHub Actions
    |
    v
Build Docker Image
    |
    v
Amazon ECR
    |
    v
Amazon EC2
    |
    v
Pull Latest Image
    |
    v
Run SaiGPT Container
    |
    v
Live Application
```

### 1. Create an IAM User

Create an AWS IAM identity with the required permissions for:

- Amazon ECR image push and pull
- EC2 deployment operations

Prefer a restricted custom IAM policy over broad administrator or full-access policies.

### 2. Create an ECR Repository

Create an Amazon ECR repository.

Example:

```text
Repository Name: saigpt
AWS Region: us-east-1
```

Example ECR image URI:

```text
315865595366.dkr.ecr.us-east-1.amazonaws.com/saigpt
```

### 3. Create an EC2 Instance

Launch an Ubuntu EC2 instance.

Configure the security group to allow the required traffic.

Example:

```text
Type: Custom TCP
Port: 8080
Source: Your IP address
```

For public production access, use a reverse proxy with HTTPS rather than exposing the application directly.

### 4. Install Docker on EC2

Connect to your EC2 instance:

```bash
sudo apt-get update -y
sudo apt-get upgrade -y
```

Install Docker:

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

Add the Ubuntu user to the Docker group:

```bash
sudo usermod -aG docker ubuntu
newgrp docker
```

Verify installation:

```bash
docker --version
```

### 5. Configure GitHub Self-Hosted Runner

Navigate to:

```text
GitHub Repository
    → Settings
    → Actions
    → Runners
    → New self-hosted runner
```

Select Linux and follow the commands provided by GitHub.

Start the runner:

```bash
./run.sh
```

For persistent execution, configure the runner as a service:

```bash
sudo ./svc.sh install
sudo ./svc.sh start
```

### 6. Configure GitHub Secrets

Navigate to:

```text
Repository
    → Settings
    → Secrets and variables
    → Actions
    → New repository secret
```

Add the following secrets:

```text
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_DEFAULT_REGION
ECR_REPO

OPENROUTER_API_KEY
GOOGLE_API_KEY
GROQ_API_KEY
OPENAI_API_KEY

TAVILY_API_KEY

LANGSMITH_TRACING
LANGSMITH_ENDPOINT
LANGSMITH_API_KEY
LANGSMITH_AGENT_ID
LANGSMITH_AGENT_ENVIRONMENT

WEATHERSTACK_API_KEY
OPENWHEATHER_API_KEY
```

Only configure secrets for integrations used by your deployed application.

Example configuration:

```text
AWS_DEFAULT_REGION=us-east-1
ECR_REPO=saigpt
LANGSMITH_TRACING=true
LANGSMITH_AGENT_ID=agentic-chatbot-project
LANGSMITH_AGENT_ENVIRONMENT=production
```

### 7. GitHub Actions Workflow

Create the workflow file:

```text
.github/workflows/cicd.yaml
```

The CI/CD workflow automates:

1. Docker image building.
2. AWS authentication.
3. Pushing the image to Amazon ECR.
4. Connecting to the EC2 deployment environment.
5. Pulling the latest image.
6. Stopping the previous container.
7. Starting the updated SaiGPT container.

---

## 💡 Example Use Cases

### 1. General AI Assistance

```text
Explain how LangGraph works with an example.
```

### 2. Document Intelligence

```text
Summarize the uploaded PDF.
```

### 3. RAG-Based Question Answering

```text
Based on my uploaded document, explain the important concepts.
```

### 4. Web Research

```text
Search the web for the latest developments in AI agents.
```

### 5. Weather Information

```text
What is the current weather in New Delhi?
```

---

## 🔒 Security

- Never expose API keys publicly.
- Keep `.env` out of version control.
- Use GitHub Secrets for deployment credentials.
- Apply least-privilege IAM permissions.
- Restrict EC2 security group access.
- Avoid exposing database files and uploaded documents publicly.
- Use HTTPS for production deployments.
- Rotate accidentally exposed credentials immediately.

---

## 🚧 Future Improvements

- [ ] Advanced multi-agent architecture
- [ ] Improved conversational memory
- [ ] Advanced RAG retrieval and reranking
- [ ] Hybrid search
- [ ] User authentication
- [ ] Chat history management
- [ ] Improved frontend interface
- [ ] Production monitoring
- [ ] Scalable cloud deployment
- [ ] Automated testing and CI pipeline

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repository.
2. Create a new feature branch.
3. Make your changes.
4. Commit your changes.
5. Submit a pull request.

---

## 📜 License

This project is open source. Check the repository's license for usage and distribution terms.

---

## 👨‍💻 Author

**Sai Deependra Kumar Nanda**

GitHub: [@saideependra](https://github.com/saideependra)

---

<div align="center">

### ⭐ SaiGPT

**Your Intelligent Agentic AI Assistant**

Built with ❤️ using Python, LangChain, and LangGraph.

</div>