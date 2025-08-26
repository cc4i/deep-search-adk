# Deep Researcher

A Deep Researcher Agent is built with Google's Agent Development Kit (ADK).

## Project Structure

This project is organized as follows:

```
fun-agents-adk/
├── app/                 # Core application code
│   ├── agent.py         # Main agent logic
│   ├── server.py        # FastAPI Backend server
│   └── utils/           # Utility functions and helpers
├── deployment/          # Infrastructure and deployment scripts
├── notebooks/           # Jupyter notebooks for prototyping and evaluation
├── tests/               # Unit, integration, and load tests
├── Makefile             # Makefile for common commands
└── pyproject.toml       # Project dependencies and configuration
```

## Requirements

- Python  3.12+
- Install packages: google-adk, agent-starter-pack
- Get GEMINI API KEY
- VSCODE
- Install gcloud (Ignore if no GCP account)


## Code 1 - Warm UP 

```bash

agent-starter-pack create base-agent-adk

cd base-agent-adk

# Add your Gemini API Key
vi app/.env 
>>>
GOOGLE_API_KEY="???"
GOOGLE_GENAI_USE_VERTEXAI=FALSE
<<<

# Run agent locally
make playground

# Deploy agent into GCP
make backend (ignore if no GCP account)

```

## Code 2 - Deep Search

```bash
git clone https://github.com/cc4i/deep-search-adk

cd deep-search-adk

# Add your Gemini API Key
vi app/.env 
>>>
GOOGLE_API_KEY="???"
GOOGLE_GENAI_USE_VERTEXAI=FALSE
<<<

# Copy all code form app/guidance.md by order

# Run agent locally
make playground

# Deploy agent into GCP
make backend (ignore if no GCP account)
```