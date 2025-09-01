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


## Coding 
### Code 1 - Warm UP 

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

# Deploy agent into Cloud Run
make cloud-run-backend (ignore if no GCP account)

```

### Code 2 - Deep Search

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

# Deploy agent into Cloud Run
make cloud-run-backend (ignore if no GCP account)
```

## Deploy onto AgentEngine 

```bash
# Deploy the agent into AgentEngine
make agent-engine-backend
```

## Register into Agentspace

```bash
# Register agent into Agentspace
curl -X POST \
    -H "Authorization: Bearer $(gcloud auth print-access-token)" \
    -H "Content-Type: application/json" \
    -H "X-Goog-User-Project: <project_id>" \
    "https://discoveryengine.googleapis.com/v1alpha/projects/<project_id>/locations/global/collections/default_collection/engines/<agentspace_id>/assistants/default_assistant/agents" \
    -d '{
        "displayName": "Deep Research ADK v1",
        "description": "A specialized assistant for customized Deep Research.",
        "adk_agent_definition": {
            "tool_settings": {
                "tool_description": "A specialized assistant for customized Deep Research and report."
              },
            "provisioned_reasoning_engine": { "reasoning_engine": "projects/<project_id>/locations/<region>/reasoningEngines/<agent_id>"}
        }
    }'

# Patch the agent
...

# Deregister agent
...

# List all agent in the Agentspace
curl -X GET \
    -H "Authorization: Bearer $(gcloud auth print-access-token)" \
    -H "Content-Type: application/json" \
    -H "X-Goog-User-Project: <project_id>" \
    "https://discoveryengine.googleapis.com/v1alpha/projects/<project_id>/locations/global/collections/default_collection/engines/<agentspace_id>/assistants/default_assistant/agents"

```