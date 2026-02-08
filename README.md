# Agentic AI System with Guardrails and Dynamic Tooling

## 📌 Project Overview

This project demonstrates an **advanced Agentic AI system** designed to orchestrate multiple specialized AI agents and dynamic tools, while enforcing **strong guardrails for safety, reliability, and privacy**.

At the core of the system is a **Brain Agent** that intelligently interprets user goals and routes them to the most suitable sub-agent. Each sub-agent leverages domain-specific tools to generate structured, task-oriented outputs. The system also includes robust mechanisms for **JSON safety, PII detection, and high-risk topic filtering**.

This architecture reflects **real-world agentic AI design patterns** used in modern LLM-based systems.

---

## ✨ Key Features

### 🧠 Intelligent Routing (Brain Agent)
- Uses an LLM to analyze user intent
- Dynamically routes requests to the appropriate specialized agent:
  - Vacation Agent
  - Hackathon Agent
  - Social Event Agent

### 🔧 Dynamic Tool Invocation
- Sub-agents extract parameters from user input
- Automatically invoke the correct LangChain tools
- Generate **structured JSON outputs** (e.g., travel plans, event configurations)

### 🛡️ Robust Guardrails
- **High-Risk Topic Detection**
  - Blocks unsafe or unreliable requests (e.g., stock price prediction)
- **PII Filtering**
  - Detects and blocks Personally Identifiable Information (names, emails, etc.)

### 🧾 Safe LLM Output Parsing
- Includes a `safe_json_parse` utility
- Handles malformed or partially invalid JSON from LLM responses gracefully

### 🧩 Modular Agent Architecture
- Clear separation of responsibilities
- Easy to extend with new agents or tools
- Improves maintainability and scalability

---

## 🏗️ High-Level Architecture

```
User Goal
↓
Guardrails (Risk & PII Checks)
↓
Brain Agent (Intent Routing)
↓
Specialized Agent
↓
Dynamic Tool Invocation
↓
Structured JSON Output
```


---

## ⚙️ Setup and Installation

### 1️⃣ Clone the Repository (or open in Google Colab)

```bash
git clone <your-repo-url>
```

### 2️⃣ Install Dependencies
```
pip install -U langchain-groq langchain-core
```

### 3️⃣ Configure API Key

Groq API Key

Obtain your API key from:
```
👉 https://console.groq.com/keys
```

Google Colab (Recommended)

- Open 🔑 Secrets in the left sidebar
- Add:
   Name: GROQ_API_KEY
   Value: your Groq API key
- Enable Notebook access
- Restart runtime

Local Environment
```
export GROQ_API_KEY=your_api_key_here
```
⚠️ API keys are never hardcoded and are safe for GitHub.

---

## ▶️ How to Run

The main entry point is the agentic_ai_system function.

Simply pass a natural language goal, and the system will:
- Apply guardrails
- Route to the correct agent
- Invoke tools
- Return structured results

Example Usage
```
agentic_ai_system("Plan a 10 day trip to forest anywhere with 40k budget suggest")
agentic_ai_system("Organize an all india hackathon finals in Delhi")
agentic_ai_system("Plan a political party for 1000 guests")

# Blocked by guardrails
agentic_ai_system("Stock market price next minute predict")

# Blocked by PII filter
agentic_ai_system("My name is John Doe and my email is john.doe@example.com")
```
---

## 🤖 Agents

```
brain_decide_agent(goal)
Determines which agent should handle the request

vacation_agent(goal)
Handles travel-related planning

hackathon_agent(goal)
Handles hackathon organization

social_event_agent(goal)
Handles social and political event planning
```
---
## 🧠 Orchestrator
```
agentic_ai_system(goal)
```
Master function that:

- Applies guardrails
- Routes requests
- Invokes agents and tools
- Returns final output
  
---
## ⭐ Final Note

This project showcases real-world Agentic AI design:
- Intelligent orchestration
- Safety-first mindset
- Modular, scalable architecture
- Production-oriented thinking

If you find this useful, feel free to ⭐ the repository.

---
