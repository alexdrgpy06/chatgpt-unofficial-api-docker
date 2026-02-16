# ChatGPT Unofficial API Docker

A robust, containerized solution for automating ChatGPT interactions using Selenium and Chrome. This project provides a headless (or headful via VNC) environment to interact with the ChatGPT web interface programmatically.

## 🚀 Features

- **Dockerized Environment:** Fully isolated setup with all dependencies pre-installed.
- **Selenium Automation:** Uses Selenium with Chrome to interact with the ChatGPT web UI.
- **Visual Debugging (NoVNC):** Access the browser inside the container via a web-based VNC client (NoVNC) on port 8080.
- **Python 3.10:** Modern Python environment managed by PyEnv.
- **Persistent Sessions:** Configured to handle cookies and session data for continuous interactions.
- **Proxy Support:** Ready for integration with proxies to avoid rate limits or regional restrictions.

## 📦 Project Structure

- `Dockerfile`: Multi-stage build for a slim yet powerful image.
- `docker-compose.yml`: Easy orchestration for the API and browser environment.
- `app/`: Contains the core logic for the Selenium-based API.
- `demo.py`: A sample script demonstrating how to use the API for conversations.
- `vncmain.sh`: Entrypoint script to manage the VNC server and application.

## 🛠️ Installation & Setup

### Prerequisites

- Docker
- Docker Compose

### Quick Start

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd chatgpt-unofficial-api-docker
   ```

2. **Build and Start:**
   ```bash
   docker-compose up --build
   ```

3. **Access NoVNC:**
   Open your browser and navigate to `http://localhost:8080` to see the automated browser in action.

## 💻 API Usage

The system exposes an internal endpoint (or can be used as a library) to send messages and receive responses.

```python
import httpx

# Example payload
payload = {
    "action": "next",
    "messages": [{
        "content": {"content_type": "text", "parts": ["Hello!"]},
        "role": "user"
    }],
    "model": "text-davinci-002-render"
}

response = httpx.post("http://localhost:8080/backend-api/conversation", json=payload)
print(response.json())
```

## 🛡️ Safety & Disclaimer

This is an **unofficial** API. It is not affiliated with, endorsed, or sponsored by OpenAI. Use this project responsibly and in compliance with OpenAI's Terms of Service. Frequent or high-volume requests may result in account suspension or IP blocking.

---
*Automate with caution.*
