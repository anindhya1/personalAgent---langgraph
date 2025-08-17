# Sidekick.ai

A lightweight AI-powered sidekick that integrates multiple tools, reasoning abilities, and graph-based workflows using LangGraph to assist with research, planning, and automation.

---

## Overview

Sidekick.ai is a modular AI agent that can answer questions, run tools, and help automate everyday tasks. It is designed around a simple core agent (`sidekick.py`) with extendable tools (`sidekick_tools.py`), a user-facing app (`app.py`), and graph-based orchestration powered by LangGraph.

LangGraph is used to structure the agent’s reasoning process as a directed graph of nodes, where each node represents a step (LLM call, tool execution, planner, etc.). This makes the system more robust, transparent, and extensible compared to a purely sequential agent.

---

## Features

- Modular tool system – extend with custom tools in `sidekick_tools.py`
- LangGraph orchestration – agent reasoning is represented as a stateful graph
- Conversational agent – powered by an LLM backend
- Easy deployment – runs locally or can be hosted on Spaces/Streamlit
- Task automation – supports planning, search, writing, and more

---

## Project Structure

- `app.py` – main entry point for running the app
- `sidekick.py` – core agent logic, integrates with LangGraph for orchestration
- `sidekick_tools.py` – library of available tools the agent can use

---

## Tech Stack

- Python 3.10+
- [LangGraph](https://langchain-ai.github.io/langgraph/) for agent orchestration
- OpenAI API (or compatible LLM provider)
- Pydantic for structured outputs
- Requests for external API calls
- Gradio or Streamlit for the frontend

---

## Installation

Clone the repository:

    git clone https://github.com/<your-username>/Sidekick.ai.git
    cd Sidekick.ai

Install dependencies:

    pip install -U python-dotenv openai requests pydantic gradio langgraph

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

## LangGraph Integration

LangGraph structures the agent’s reasoning process as a graph of nodes. Each node can be:

- **LLM node** – for reasoning and conversation
- **Tool node** – for executing specific functions from `sidekick_tools.py`
- **Planner node** – for breaking down complex tasks
- **Decision node** – for branching logic depending on context

This design ensures that Sidekick is:
- **Composable** – new workflows can be created by rearranging nodes
- **Transparent** – reasoning steps are explicit in the graph
- **Stateful** – memory and intermediate results are stored as the graph executes

---

## Extending with Tools

You can add new tools by editing `sidekick_tools.py`. Each tool should define:
- A schema (inputs/outputs)
- A function implementation
- Registration into the toolset

LangGraph will then be able to incorporate these tools into its workflow.

---

## Use Cases

- Answering research questions
- Automating small workflows
- Acting as a personal knowledge assistant
- Experimenting with agent-based AI design
- Building graph-structured reasoning pipelines with LangGraph

---

## License

MIT License.

---

## Acknowledgments

- OpenAI for language model APIs
- Pydantic for structured validation
- Gradio/Streamlit for the frontend
- [LangGraph](https://langchain-ai.github.io/langgraph/) for agent orchestration
