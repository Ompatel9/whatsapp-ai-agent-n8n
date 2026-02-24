# WhatsApp AI Agent using n8n

## Overview

This project implements a real-time WhatsApp AI assistant using n8n and the WhatsApp Business Cloud API.  
Incoming WhatsApp messages are received via a webhook, processed by an AI model, and responded to automatically.

The system follows an event-driven architecture and demonstrates API integration, webhook handling, authentication, and containerized deployment.

---

## Architecture

User → WhatsApp → Meta Cloud API → Webhook (ngrok) → n8n (Docker) → AI Model → WhatsApp Send API → User

---

## Tech Stack

- n8n (Workflow Automation Engine)
- WhatsApp Business Cloud API
- Docker (Containerization)
- ngrok (Public HTTPS tunneling for webhook)
- AI Model (Gemini / OpenAI)

---

## Key Concepts Demonstrated

- API integration
- Webhook-based event-driven architecture
- Bearer token authentication
- JSON payload parsing
- Session-based conversation memory
- Docker container deployment
- Local-to-public HTTPS tunneling

---

## How It Works

1. A user sends a message to the WhatsApp Business number.
2. Meta sends a POST request to the configured webhook URL.
3. The webhook forwards the request to the n8n workflow.
4. The message text (`messages[0].text.body`) is extracted.
5. The AI model generates a response.
6. The response is sent back using the WhatsApp Cloud API.

---

## Setup Instructions

### 1. Install Docker
Run n8n using a Docker container.

### 2. Expose Local Server
Use ngrok to expose the local n8n instance:

Copy the HTTPS forwarding URL.

### 3. Configure Webhook
In Meta Developer Dashboard:
- Set the webhook callback URL
- Verify using a verify token
- Subscribe to message events

### 4. Add Access Token
Generate a temporary or permanent access token from Meta and configure it in n8n credentials.

---

## Security Notes

- Access tokens and secrets are not included in this repository.
- Use environment variables for sensitive configuration.
- Temporary tokens expire within 24 hours.

---

## Future Improvements

- Deploy to a cloud server (remove dependency on ngrok)
- Use persistent memory (Redis / database-backed)
- Add conversation logging database
- Implement webhook signature verification
- Add rate limiting and retry logic

---

## Learning Outcomes

This project demonstrates real-world API integration, webhook handling, authentication, automation design, and containerized deployment.

---

## Author

Om M Patel
