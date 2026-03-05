# NUST Bank RAG Assistant

A customer support chatbot for NUST Bank powered by Retrieval-Augmented Generation (RAG) using LLaMA 3.2 via Ollama.

## Prerequisites

- Python 3.8 or higher
- Ollama with LLaMA 3.2 model

## Installation

1. Install Ollama and pull the model:
```bash
ollama pull llama3.2
```

2. Clone the repository and navigate to the project folder:
```bash
git clone <repository-url>
cd bank-llm-project
```

3. Create and activate a virtual environment:
```powershell
# Windows PowerShell
python -m venv venv
.\venv\Scripts\activate
```

4. Install dependencies:
```bash
pip install -r requirements.txt
```

5. Ensure knowledge base files are in the project root:
   - `NUST Bank-Product-Knowledge.xlsx`
   - `full_transfer_app_feature_faq.json`

## Running the Project

Run the assistant:
```bash
python main.py
```

Rebuild the index (if knowledge base is updated):
```bash
python main.py --rebuild
```

## Usage

Once running, interact with the chatbot:
- Ask questions about bank products and services
- Type `help` for commands
- Type `sources` to toggle source document display
- Type `exit` to quit

## How It Works

1. **Indexing Phase** (first run):
   - Loads documents from Excel and JSON files
   - Cleans and chunks the text
   - Generates embeddings using Sentence Transformers
   - Stores vectors in FAISS index

2. **Query Phase** (each question):
   - Converts user question to an embedding
   - Searches FAISS for similar document chunks
   - Passes retrieved context to LLaMA 3.2
   - Generates and returns the answer

## Troubleshooting

- **Ollama connection error**: Start Ollama with `ollama serve`
- **Model not found**: Run `ollama pull llama3.2`
- **No documents found**: Verify knowledge base files are in project root
- **Index errors**: Rebuild with `python main.py --rebuild`