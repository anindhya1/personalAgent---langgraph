# Sidekick.ai

A lightweight AI-powered sidekick that integrates multiple tools and reasoning abilities to assist with research, planning, and automation.

---

## Overview

Sidekick.ai is a modular AI agent that can answer questions, run tools, and help automate everyday tasks. It is designed around a simple core agent (`sidekick.py`) with extendable tools (`sidekick_tools.py`) and a user-facing app (`app.py`).

---

## Features

- Modular tool system – extend with custom tools in `sidekick_tools.py`
- Conversational agent – powered by an LLM backend
- Easy deployment – runs locally or can be hosted on Spaces/Streamlit
- Task automation – supports planning, search, writing, and more

---

## Project Structure

- `app.py` – main entry point for running the app
- `sidekick.py` – core agent logic, manages reasoning and tool calls
- `sidekick_tools.py` – library of available tools the agent can use

---

## Tech Stack

- Python 3.10+
- OpenAI API (or compatible LLM provider)
- Pydantic for structured outputs
- Requests for external API calls
- Gradio or Streamlit (depending on your UI choice)

---

## Installation

Clone the repository:

    git clone https://github.com/<your-username>/Sidekick.ai.git
    cd Sidekick.ai

Install dependencies:

    pip install -U python-dotenv openai requests pydantic gradio

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

## Extending with Tools

You can add new tools by editing `sidekick_tools.py`. Each tool should define:
- A schema (inputs/outputs)
- A function implementation
- Registration into the toolset

This allows Sidekick to call external services or APIs seamlessly.

---

## Use Cases

- Answering research questions
- Automating small workflows
- Acting as a personal knowledge assistant
- Experimenting with agent-based AI design

---

## License

MIT License.

---

## Acknowledgments

- OpenAI for language model APIs
- Pydantic for structured validation
- Gradio/Streamlit for the frontend
