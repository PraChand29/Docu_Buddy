# DocuBuddy
DocuBuddy — Your friendly local AI assistant for multi-modal document analysis, hybrid search, SQL spreadsheet querying, interactive mind maps, and strategic roadmaps. 100% private, powered by Ollama & LangGraph.
## 🤖 DocuBuddy — Your AI-Powered Knowledge Companion Transform multi-format documents, spreadsheets, and presentations into actionable intelligence, interactive mind maps, and strategic roadmaps — completely on-premise. 
License: MIT Python 3.10+ React + Vite Ollama Powered 
## ✨ Key Features 
📑 **Multi-Format Ingestion**: Support for PDF, Excel, CSV, PowerPoint, Images, and Markdown.
🔍 **Hybrid RAG Search**: Combines Dense Vector Similarity (ChromaDB) with BM25 Keyword Search & Cross-Encoder re-ranking.
📊 **Natural Language to SQL**: Query Excel and CSV files using plain conversational English.
🧠 **Interactive Mind Maps & Roadmaps**: Automatically generate ReactFlow mind maps, SWOT analyses, and technical roadmaps.
🔒 **100% On-Premise Privacy**: Runs locally using Ollama — no data ever leaves your machine.

Here are the setup instructions formatted specifically for a **GitHub user** who clones your `Docu_Buddy` repository:

---

# 🤖 DocuBuddy — Setup Guide for GitHub Users

Welcome to **DocuBuddy**! Follow these instructions to set up and run DocuBuddy locally on your machine.

---

## 📋 Prerequisites

Make sure you have the following installed before starting:

- **Python**: `3.10` or `3.11` ([Download Python](https://www.python.org/downloads/))
- **Node.js**: `v18+` or `v22` ([Download Node.js](https://nodejs.org/))
- **MongoDB**: Community Server ([Download MongoDB](https://www.mongodb.com/try/download/community))
- **Tesseract OCR**: ([Download Tesseract for Windows](https://github.com/UB-Mannheim/tesseract/wiki))
- **Ollama**: ([Download Ollama](https://ollama.com/download))

---

## 🚀 Step-by-Step Local Setup

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/PraChand29/Docu_Buddy.git
cd Docu_Buddy
```

---

### 2️⃣ Backend Setup

#### A. Create and Activate Virtual Environment
- **Windows (PowerShell):**
  ```powershell
  python -m venv virtualEnv
  .\virtualEnv\Scripts\Activate.ps1
  ```
- **Linux / macOS:**
  ```bash
  python3 -m venv virtualEnv
  source virtualEnv/bin/activate
  ```

#### B. Install Python Dependencies
```bash
pip install -r requirements.txt
```

#### C. Environment Configuration
Copy the template `.env` file:
```bash
# On Windows PowerShell
copy .env.example .env

# On Linux / macOS
cp .env.example .env
```

#### D. Start Ollama Local LLM Servers
In separate terminal windows, start the Ollama instances:

* **Terminal 1 (Primary Ollama):**
  ```bash
  OLLAMA_HOST=0.0.0.0:11434 OLLAMA_KEEP_ALIVE=-1 ollama serve
  ```

* **Terminal 2 (Parallel Worker Ollama):**
  ```bash
  OLLAMA_HOST=0.0.0.0:11435 OLLAMA_KEEP_ALIVE=-1 ollama serve
  ```

*(Run `./setmodel.sh` to initialize required local model aliases if running for the first time).*

#### E. Run the Backend API
In your activated virtual environment terminal:
```bash
python backend.py
```
*(Backend runs on `http://localhost:8000`)*

---

### 3️⃣ Frontend Setup

Open a new terminal window:

```bash
cd frontend
npm install
npm run dev
```
*(Frontend dev server will start at `http://localhost:8080` or `http://localhost:5173`)*

---

## 🐳 Alternative: Running with Docker (Linux)

If you prefer using Docker:

```bash
# 1. Copy environment template
cp .env.docker .env

# 2. Build Docker container
make build

# 3. Start Ollama and run app
make ollama
make run
```

---

## 🌐 Access the Platform

Open your browser and navigate to:
👉 **[http://localhost:8080](http://localhost:8080)**

### 📌 Default Ports
- **Frontend App**: `8080`
- **Backend API**: `8000`
- **Ollama Primary**: `11434`
- **Ollama Parallel**: `11435`
