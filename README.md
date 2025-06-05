
# Ollama Persistent Setup for Google Colab

A complete solution for running Ollama with persistent storage in Google Colab, eliminating the need to reinstall models every session.

## 🚀 Quick Start

### First Time Setup
1. Open the notebook in Google Colab  
2. Run all cells to install Ollama in your Google Drive  
3. Download your first model:

```python
download_model('llama3.2:1b')  # Small, fast model for testing
```

4. Test the setup:

```python
response = chat_with_model('llama3.2:1b', 'Hello, how are you?')
print(response)
```

### Subsequent Sessions
- Mount Google Drive  
- Run the "Start Ollama Server" section  
- Your models are ready to use immediately!

## 📁 Storage Structure

Your Google Drive will contain:

```
MyDrive/
└── ollama_setup/
    ├── bin/
    │   └── ollama          # Ollama binary (persistent)
    └── models/             # All downloaded models (persistent)
        ├── llama3.2:1b/
        ├── llama3.2:3b/
        └── ...
```

## 🤖 Recommended Models

### For Development & Testing
- `llama3.2:1b` - Fastest, good for prototyping  
- `phi3:mini` - Microsoft's efficient model  
- `gemma2:2b` - Google's compact model  

### For Production Use
- `llama3.2:3b` - Better reasoning capabilities  
- `mistral:7b` - Excellent instruction following  
- `codellama:7b` - Best for code-related tasks  

### For Medical Applications
- `llama3.2:3b` - Recommended for medical Q&A  
- `mistral:7b` - Good for complex medical reasoning  

## 🛠️ Available Functions

### Model Management

```python
# List popular models you can download
list_available_models()

# Download a model (saves to Google Drive)
download_model('llama3.2:1b')

# See what models you have installed
list_installed_models()
```

### Chat Interface

```python
# Simple chat with any installed model
response = chat_with_model('llama3.2:1b', 'Your question here')
print(response)
```

### Server Management

```python
# Start Ollama server (automatic in setup)
server_process = start_ollama_server()

# Check if server is running
# Server runs on http://localhost:11434
```

## 💡 Usage Examples

### Basic Chat

```python
download_model('llama3.2:1b')
response = chat_with_model('llama3.2:1b', 'Explain machine learning in simple terms')
print(response)
```

### Medical Q&A Setup

```python
download_model('llama3.2:3b')
response = chat_with_model('llama3.2:3b', 'What are the common symptoms of diabetes?')
print(response)
```

### Code Generation

```python
download_model('codellama:7b')
code = chat_with_model('codellama:7b', 'Write a Python function to read a CSV file')
print(code)
```

## 🔧 RAG Integration

For building RAG systems, the setup includes optional packages:

```python
# Uncomment in the notebook to install RAG dependencies
setup_rag_environment()
```

This installs:
- `langchain` (RAG framework)
- `chromadb` (vector database)
- `sentence-transformers` (embeddings)
- `transformers` (Hugging Face models)
- `Pillow`, `easyocr` (image processing)
- `pypdf` (document processing)

## ⚡ Performance Tips

### Model Size vs Performance

| Model | RAM Usage | Notes |
|-------|-----------|-------|
| 1B    | ~1-2GB    | Fast inference |
| 3B    | ~3-4GB    | Balanced |
| 7B    | ~7-8GB    | Best quality, slower |

### Colab Notes
- Colab RAM: ~12GB
- Free tier: ~12 hours per session
- Your models persist in Drive between sessions

## 🐛 Troubleshooting

### Server Won't Start

```python
import subprocess
subprocess.run(["pkill", "-f", "ollama"], capture_output=True)
server_process = start_ollama_server()
```

### Model Download Fails
- Check internet connection  
- Try a smaller model first  
- Ensure enough space in Google Drive  

### Out of Memory
- Use smaller models (1B or 3B)  
- Restart Colab runtime  
- Clear variables: `del large_variable`  

### Drive Not Mounting

```python
from google.colab import drive
drive.mount('/content/drive', force_remount=True)
```

## 📋 System Requirements
- Google Colab (Free or Pro)  
- Google Drive with at least 5GB free space  
- Internet connection for initial model downloads  

## 🔒 Security & Privacy
- Models run locally in your Colab session  
- No data sent to external servers (except initial download)  
- Your conversations are not stored or monitored  
- Models are saved privately in your Google Drive  

## 📈 Next Steps

### For Medical RAG Projects
- Set up image processing pipeline  
- Implement document chunking and embedding  
- Create vector database with ChromaDB  
- Build question-answering interface  

### For General Development
- Experiment with different models  
- Fine-tune prompts for your use case  
- Integrate with external APIs or databases  
- Deploy to production environment  

## 📞 Support
If you encounter issues:
- Check the troubleshooting section above  
- Ensure you're using the latest version of the notebook  
- Verify Google Drive has sufficient space  
- Try restarting the Colab runtime  

## 📄 License
This setup script is provided as-is for educational and development purposes. Ollama and individual models have their own licenses - please check before commercial use.

---

**Happy coding! 🚀**

_Last updated: June 2025_
