# Pizza-Restaurant-RAG-Chatbot
An AI-powered Retrieval-Augmented Generation (RAG) agent that answers questions about a pizza restaurant based on actual customer reviews. This project uses Ollama for local LLM inference and embeddings, ensuring 100% data privacy.


🛠️ Tech Stack
LLM: Ollama (Running llama3.2)

Framework: LangChain

Vector Database: ChromaDB (Persistent Storage)

Embeddings: mxbai-embed-large via Ollama

Data Processing: Pandas

Language: Python 3.10+

🚀 Features
Local Execution: No API keys required; everything runs on your hardware.

Persistent Memory: Uses ChromaDB to store vector embeddings locally in ./chrome_langchain_db, so the CSV is only processed once.

Context-Aware: Uses a similarity search to find the top 5 most relevant reviews before answering a user's question.

📂 Project Structure
Plaintext
├── main.py                          # Chat loop and LLM chain logic
├── vector.py                        # Data ingestion and vector store setup
├── realistic_restaurant_reviews.csv  # Your source data
├── requirements.txt                 # Python dependencies
└── chrome_langchain_db/             # Local vector database (auto-generated)

⚙️ Installation & Setup

1. Prerequisites
Install Ollama and pull the necessary models:
Bash
ollama pull llama3.2
ollama pull mxbai-embed-large
2. Virtual Environment
Bash
python -m venv .venv

# Activate on Windows:
.venv\Scripts\activate

# Activate on Mac/Linux:
source .venv/bin/activate
3. Dependencies

Bash
pip install langchain-ollama langchain-chroma langchain-core pandas
📝 How to Use
Place your realistic_restaurant_reviews.csv in the root directory.

Run the application:

Bash
python main.py
Ask questions like:

"What do people say about the crust?"

"Are there any complaints about delivery times?"

"Which pizza is the most recommended?"

🔍 How it Works
Ingestion: vector.py reads the CSV, combines the Title and Review text, and generates high-dimensional vectors (embeddings).

Retrieval: When you ask a question, the system searches the ChromaDB for the 5 reviews most mathematically similar to your query.

Augmentation: Those reviews are injected into a prompt template.

Generation: The llama3.2 model reads the reviews and provides a concise, expert answer.
