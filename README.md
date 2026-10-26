# LangChain Course

## Connect to an Ollama server

This project uses LangChain's `ChatOllama` integration. The application reads the server URL from `OLLAMA_BASE_URL`; if it is not set, it connects to `http://localhost:11434`.

### 1. Set the server URL

In the project directory, add the Ollama server's reachable address to `.env`:

```dotenv
OLLAMA_BASE_URL=http://192.168.1.100:11434
```

Replace the example address with your server's private IP or hostname. Do not add `/api` to the URL; the Ollama client handles API paths. Keep `.env` private and do not commit credentials or secrets.

### 2. Check connectivity and run

From the project directory, check that the Ollama API is reachable and that the model appears in the response:

```sh
curl http://192.168.1.100:11434/api/tags
```

Then run the app using the project's uv environment:

```sh
uv sync
uv run python main.py
```

The `ChatOllama` client in `main.py` uses `OLLAMA_BASE_URL` and requests `qwen3.8:27b`. If you change the model, make sure that model is available on the Ollama server and update the `model` value in `main.py` to match.
