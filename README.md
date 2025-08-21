# 🌱 AgriBot – AI-powered Agriculture Assistant

AgriBot is an intelligent chatbot designed to answer **agriculture-related questions** by extracting knowledge from PDFs, embedding the content into a **vector database (FAISS)**, and retrieving answers using **LLMs from Together AI**. It supports **multi-language queries** by detecting the input language, translating into English for processing, and returning the answer back in the user’s language.  

<img width="1867" height="916" alt="Screenshot 2025-08-21 145629" src="https://github.com/user-attachments/assets/d2202389-86a4-4510-8d74-2c07bc0ea2d8" />

---

## 🚀 Features
- Extracts knowledge from **PDFs**  
- **RAG pipeline** (Retrieval-Augmented Generation) using FAISS + HuggingFace embeddings  
- **Multi-language support** (via Google Translate & LangDetect)  
- LLM-powered answers using **Together AI** (`Qwen/QwQ-32B-Preview`)  
- Deployed on **Vercel** with Python runtime  
- Simple web UI with **Flask + Jinja2 templates**  

---

## 🛠 Tech Stack
- **Backend**: Python, Flask, RAG
- **AI & NLP**: LangChain, HuggingFace, NLP, FAISS, Together AI  
- **Embeddings**: `all-MiniLM-L6-v2` (SentenceTransformers)  
- **Vector Store**: FAISS  
- **Translation**: Googletrans + LangDetect  
- **Frontend**: HTML, CSS, JavaScript (Jinja2 templates)  
- **Deployment**: Vercel  

---

## 📂 Project Structure

```bash
Agribot/
│── Data/
│ └── farmerbook.pdf # Knowledge source (PDF)
│
│── templates/
│ └── index.html # Chatbot UI
│
│── app.py # Main Flask application
│── index.py # Entry point (for local & Vercel)
│── wsgi.py # WSGI configuration
│── vercel.json # Vercel deployment config
│── requirements.txt # Python dependencies
│── .env # Environment variables (ignored in Git)
│── README.md # Project documentation
```
---

## ⚙️ Installation & Setup

1. **Clone the repository**
```bash
git clone https://github.com/shruti-shreya01/AgriBot.git
cd Agribot
   ```

2. **Create a virtual environment and activate it**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install the required packages**

   ```bash
   pip install -r requirements.txt
   ```

4. **Create a `.env` file**

   Create a `.env` file in the root directory of the project and add your Together API key and Google Translate API key:

   ```
   TOGETHER_API_KEY=your_together_api_key
   ```

## Usage

1. **Run the Flask application**

   ```bash
   python index.py
   ```

2. **Access the chatbot**

   Open your browser and go to `http://127.0.0.1:5000` to use the AgriBot.

## 📡 How It Works

1. **PDF Extraction** → Reads text from Data/farmerbook.pdf using PyPDF2

2. **Text Splitting** → Chunks text via RecursiveCharacterTextSplitter

3. **Embeddings** → Encodes chunks using HuggingFace MiniLM (all-MiniLM-L6-v2)

4. **Vector Storage** → Stores embeddings in FAISS for retrieval

5. **Retriever** → Fetches relevant context for user queries

6. **LLM (Together AI)** → Generates answer using Qwen/QwQ-32B-Preview

7. **Translation** → Auto-detects language → Translates to English → Answer → Translates back







