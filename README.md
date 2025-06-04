
# 🧠 Ollama LLM Setup Guide (Local Development)

This guide walks you through installing, running, and integrating LLMs locally using **Ollama**, an easy-to-use LLM deployment framework for local use.

---

## 🚀 What is Ollama?

**Ollama** is a simple tool to run and interact with large language models like Mistral, Llama 2, and more — directly on your machine, no cloud required.

- Local inference for privacy and speed
- CLI and API access
- Custom model support and model file caching

---

## 🛠️ Installation

### macOS / Linux

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

### Windows (WSL2 Required)

1. Enable WSL2
2. Install Ubuntu from Microsoft Store
3. Inside Ubuntu, run:

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

---

## 📥 Pull a Model

You can run models like `mistral`, `llama2`, `gemma`, `codellama`, etc.

```bash
ollama pull mistral
```

This downloads the model and prepares it for local use.

---

## ▶️ Run a Model

```bash
ollama run mistral
```

You can then interact with the model directly from the terminal.

---

## 🌐 API Access

Ollama runs a local API server at `http://localhost:11434`.

Example Python call:

```python
import requests

response = requests.post(
    "http://localhost:11434/api/generate",
    json={"model": "mistral", "prompt": "What is quantum computing?"}
)
print(response.json()["response"])
```

---

## 🧪 Use in RAG or FastAPI Projects

You can use Ollama models as local LLMs in any Retrieval-Augmented Generation (RAG) pipeline or with LangChain:

```python
from langchain_community.llms import Ollama

llm = Ollama(model="mistral")
llm.invoke("Explain transformers in NLP.")
```

---

## 📦 Custom Model Creation

You can build your own models using:

```bash
ollama create my-model -f Modelfile
```

Where `Modelfile` contains instructions like:

```
FROM mistral
SYSTEM You are an assistant that explains concepts clearly.
```

---

## 🧹 Stop Ollama

To stop the Ollama background service:

```bash
ollama stop
```

---

## 📚 Resources

- Website: [https://ollama.com](https://ollama.com)
- Docs: [https://ollama.com/library](https://ollama.com/library)
- GitHub: [https://github.com/ollama/ollama](https://github.com/ollama/ollama)

---

## 📬 Contact

**Sujoy Banerjee**  
📧 bsujoy577@gmail.com  
