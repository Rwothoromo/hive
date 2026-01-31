# Agent Explainability & Log Viewing

This document describes how to use the agent explainability features in Aden Hive, including the CLI and web UI for viewing agent reasoning, decisions, and actions.

## Overview

Agent explainability lets you see why and how agents made decisions during each run. This improves trust, transparency, and debugging for both developers and end users.

## Features
- **Explainability CLI**: View agent reasoning, decisions, and actions for any run log file.
- **Web UI Dashboard**: Browse, search, and view run logs in your browser.
- **Sample Logs**: Example logs are provided for testing and demonstration.

## CLI Usage

After running an agent, a run log file is generated (e.g., `agent_logs/runs/run_20260131_abcdef12.json`).

To view the explainability log in the CLI:

```bash
python -m framework.cli show-run-log agent_logs/runs/run_20260131_abcdef12.json
```

Example output:

```
Run ID: run_20260131_abcdef12
Goal: Get weather information
Status: completed

Decisions and Reasoning:

- Node: weather-llm
    Intent: Execute Weather LLM Node
    Reasoning: Node type is llm_generate with input: {'question': 'What is the weather?'}
    Chosen Option: llm_execute
    Options:
        - llm_execute: Use LLM to get weather
    Outcome: True
        Result: {'answer': 'It is sunny.'}

--- End of Run Log ---
```

## Web UI Usage

A minimal Flask web dashboard is provided in `webui/`.

1. Install Flask if needed:
   ```bash
   pip install flask
   ```
2. Start the server:
   ```bash
   cd webui
   python app.py
   ```
3. Open your browser at [http://localhost:5000](http://localhost:5000)

You can browse available run logs, search/filter by filename, and view detailed reasoning for each run.

## Customization
- The web UI looks for logs in `../agent_logs/runs/` by default. You can change this in `webui/app.py`.
- You can extend the UI with more filters, richer visualizations, or authentication as needed.

## Example Agent & Logs

A minimal agent example is provided in `examples/minimal_agent/` with sample run logs in `agent_logs/runs/`.

## For More Information
- See the main [README.md](README.md) for project setup and core features.
- For advanced observability and monitoring, see [issue #2331](https://github.com/adenhq/hive/issues/2331).

---

This document will be updated as explainability features evolve.
