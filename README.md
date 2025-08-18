# Sidekick.ai

A lightweight AI-powered sidekick that integrates multiple tools (including **Playwright**), structured reasoning, and graph-based workflows using **LangGraph** to assist with research, planning, and automation.

**Live demo:** https://huggingface.co/spaces/Anindhya/AIAssistant_LangGraph

---

## Overview

Sidekick.ai is a modular AI agent that can answer questions, run tools, and help automate everyday tasks. It is designed around a simple core agent (`sidekick.py`), extendable tools (`sidekick_tools.py`), a user-facing app (`app.py`), and orchestration powered by **LangGraph**.

Unlike linear agents, Sidekick uses LangGraph to represent its reasoning as a **graph of nodes** (LLM, tools, planner, decision points). This graph-based structure makes workflows transparent, stateful, and easy to extend.

---

## Features

- **LangGraph orchestration** – reasoning and workflows are represented as a directed graph of nodes  
- **Pydantic schemas** – each tool defines structured inputs/outputs with validation and parsing  
- **Asynchronous execution** – uses `async/await` for Playwright and external API calls without blocking  
- **Playwright integration** – enables browser automation, scraping, and interaction with dynamic sites  
- **Function calling with LLMs** – the model decides when to call a tool and provides structured arguments  
- **Modular design** – separate layers for app (`app.py`), core agent (`sidekick.py`), and tools (`sidekick_tools.py`)  
- **Stateful workflows** – LangGraph allows branching, retries, and memory of intermediate results  
- **Config-driven setup** – secrets and keys are managed via `.env` for secure deployment  

---

## Project Structure

- `app.py` – main entry point, launches Gradio/Streamlit interface  
- `sidekick.py` – core agent logic, integrates LangGraph, manages reasoning and tool calls  
- `sidekick_tools.py` – library of tools, each defined with a Pydantic schema and implementation  

---

## Tech Stack

- Python 3.10+  
- [LangGraph](https://langchain-ai.github.io/langgraph/) – graph-based orchestration  
- OpenAI API (or compatible LLM provider) – reasoning and function calling  
- [Pydantic](https://docs.pydantic.dev/) – structured validation and parsing for tool schemas  
- [Playwright](https://playwright.dev/python/) – browser automation and scraping  
- Asyncio (`async`/`await`) – concurrent, non-blocking execution  
- Requests – lightweight API calls  
- Gradio or Streamlit – interactive frontend  

---

## Installation

Clone the repository:

    git clone https://github.com/<your-username>/Sidekick.ai.git
    cd Sidekick.ai

Install dependencies:

    pip install -U python-dotenv openai requests pydantic gradio langgraph playwright

---

## Configuration

Create a `.env` file in the root directory:

    OPENAI_API_KEY=sk-your-key

Add any other API keys required by tools you enable in `sidekick_tools.py`.

---

## Usage

Run the app locally:

    python app.py

This will launch the interface in your browser (default at `http://127.0.0.1:7860/`).

---

## Key Concepts Implemented

### 1. LangGraph Orchestration
- Reasoning represented as nodes in a graph (LLM → Tool → Planner → Decision).
- Graph ensures workflows are **transparent, composable, and stateful**.

### 2. Pydantic Schemas
- Each tool uses `BaseModel` to define structured inputs and outputs.
- Ensures **automatic validation and parsing** of LLM-generated arguments.
- Prevents errors from malformed tool calls.

### 3. Asynchronous Programming
- Tools like Playwright are `async` functions.
- `await` allows non-blocking execution of browser automation and web requests.
- Enables Sidekick to remain responsive while performing heavy tasks.

### 4. Function Calling with LLMs
- LLMs decide when to invoke a tool, generating arguments in the schema’s format.
- Bridges natural language queries into **structured function execution**.

### 5. Playwright Integration
- Sidekick can open browsers, navigate dynamic sites, extract content, and interact with pages.
- Much more powerful than static `requests`-based scraping.

### 6. Modular Design
- Separation of concerns: 
  - `app.py` (UI)
  - `sidekick.py` (reasoning/orchestration)
  - `sidekick_tools.py` (tools)
- Makes it easy to extend or swap components.

### 7. Stateful Workflows
- Intermediate results are stored in the LangGraph state.
- Allows retries, branching logic, and multi-step planning without restarting.

### 8. Config-Driven Setup
- `.env` holds API keys and secrets, keeping code clean and deployable.
- Best practice for open-source sharing and Hugging Face Spaces deployment.

---

## Extending with Tools

To add a new tool:
1. Define a Pydantic `BaseModel` for inputs/outputs.  
2. Implement the tool function (sync or async).  
3. Register the tool in `sidekick_tools.py`.  

LangGraph will automatically be able to incorporate it into workflows.

---

## Use Cases

- Research question answering  
- Automated web workflows with Playwright  
- Personal knowledge assistant  
- Experimental agent-based design with LangGraph  
- Graph-structured task orchestration  
- Browser-based scraping and automation  

---

## License

MIT License.

---

## Acknowledgments

- OpenAI for language model APIs  
- Pydantic for structured validation  
- Playwright for browser automation  
- Gradio/Streamlit for frontend  
- [LangGraph](https://langchain-ai.github.io/langgraph/) for orchestration  
