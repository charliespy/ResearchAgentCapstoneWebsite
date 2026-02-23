---
layout: default
title: Research Agent Mobile
description: A Mobile-First Agentic Interface for Monitoring and Steering Machine Learning Experiments
---

# Research Agent Mobile

**A mobile-first, AI-powered control center for machine learning experiments — monitor, debug, and steer your training runs from anywhere.**

*Hargen Zheng, Charlie Sun, Avi Mehta, Mihir Joshi*
*Mentored by Hao Zhang*
*UC San Diego, DSC 180B Capstone — 2025–2026*

### Project Links

- [Live Demo](#)
- [Technical Report](#)
- [Poster](#)
- [GitHub Repository](https://github.com/hao-ai-lab/research-agent)

---

## 1. Introduction

<!-- 
Hook the reader with a relatable scenario:

Training a large ML model can take days — or even weeks. During that time,
things go wrong: losses spike, GPUs crash, hyperparameters diverge. But today's
monitoring tools (TensorBoard, SSH terminals, WandB dashboards) all assume
you're sitting at a desktop. Step away for a meeting, a commute, or dinner,
and you're flying blind.

The cost is real: unnoticed failures waste hundreds of GPU-hours and stall
research for days. What if you could check on your experiments, get intelligent
alerts, and even fix problems — all from your phone?

That's what Research Agent Mobile does.

Include: a figure or illustration showing the "before vs. after" workflow
(e.g., desktop-only monitoring vs. mobile + agent monitoring)
-->

<!-- ![Before vs. After workflow](assets/img/workflow-comparison.png) -->

---

## 2. System Overview

<!-- 
Plain-language description of the system for a general audience:

Research Agent Mobile is a web application with two halves:

- A **responsive frontend** built with Next.js, designed from the ground up
  for phones and tablets (down to 300px wide).
- A **Python backend** (FastAPI) that manages your training jobs, streams logs,
  and hosts an AI agent that can reason about your experiments in real time.

Together they give you a "mobile control plane" — a single place to see what's
running, ask the AI what's going wrong, and take action without opening a laptop.

Include: a simplified architecture diagram
(Frontend ↔ Backend ↔ GPU Cluster, with the AI agent in the middle)
-->

<!-- ![Architecture diagram](assets/img/architecture.png) -->

---

## 3. Key Features

### 3.1 Mobile-First Interface

<!-- 
- Designed for phones and tablets from day one — not a shrunken desktop app.
- Custom UI engine handles font scaling, button sizing, and layout density
  across every screen size.
- Touch-optimized controls for common actions (stop run, restart, launch sweep).

Include: side-by-side screenshot of mobile vs. desktop view
-->

<!-- ![Mobile vs. Desktop](assets/img/mobile-desktop.png) -->

### 3.2 AI-Powered Chat Assistant

<!-- 
- Talk to your experiments in plain English.
  Ask "Why is the loss diverging?" and get an answer grounded in your actual logs.
- The agent can read logs, interpret metrics, and suggest fixes.
- Interruptible workflows: the agent pauses and asks for confirmation before
  doing anything destructive (like stopping a run).

Include: screenshot of the chat interface with an example conversation
-->

<!-- ![Chat interface](assets/img/chat.png) -->

<details>
<summary>Technical details: how the chat agent works</summary>

<!--
- The backend captures the full "cognitive chain" — internal thought, tool
  execution, and final response — and renders each step in the UI.
- Session isolation prevents context bleeding between concurrent experiments.
- A "quote-and-reply" feature lets you reference specific log lines in the chat.
-->

</details>

### 3.3 Real-Time Visualization

<!-- 
- Interactive, client-side charts for training metrics (loss, accuracy, learning rate, etc.)
- Weights & Biases (WandB) integration — pull in your existing dashboards.
- Toggle metric visibility, adjust axes, manage chart density — all from mobile.
- "Insight Charts": the AI agent can autonomously generate visualizations
  to surface patterns you might miss.

Include: screenshot of a chart view on mobile
-->

<!-- ![Charts](assets/img/charts.png) -->

### 3.4 Research Journey

<!-- 
- A "semantic git" for your research process — not just code commits,
  but the decisions and reasoning behind them.
- Visualize your project as a branching graph of hypotheses, experiments,
  and outcomes.
- The AI agent can review your journey and suggest what to try next,
  based on what has (and hasn't) worked before.

Include: screenshot or mockup of the Research Journey view
-->

<!-- ![Research Journey](assets/img/research-journey.png) -->

### 3.5 Autonomous Monitoring (Wild Loop)

<!-- 
- The agent runs continuously on the server — even when your phone is off.
- It watches your training logs and detects anomalies in real time
  (e.g., loss spikes > 50%, stalled progress, GPU errors).
- When something goes wrong, you get an instant alert on your phone
  with a summary and suggested action.
- Configurable autonomy: set the agent to just notify you, or let it
  take corrective action automatically.

Include: diagram of the Wild Loop (server agent → anomaly detection → mobile alert)
-->

<!-- ![Wild Loop](assets/img/wild-loop.png) -->

<details>
<summary>Technical details: Wild Loop & MCP</summary>

<!--
- The Wild Loop is a backend execution environment that monitors tmux sessions,
  parses real-time logs, and triggers interventions based on heuristics or
  emergent anomalies.
- We use the Model Context Protocol (MCP) to standardize how the agent
  interacts with external tools — adding a new capability is as simple as
  registering a new MCP tool.
- A prioritized event queue ensures mobile alerts contain synthesized
  intelligence, not raw noise.
-->

</details>

---

## 4. Results

<!-- 
Placeholder — fill in as results become available:

- Usability study results or user feedback
- Case study: catching a real failure from mobile
- Comparison of response time vs. traditional desktop-only workflow
- Demo GIFs or video walkthrough

Include: key figures, tables, or before/after comparisons
-->

*Coming soon.*

---

## 5. Conclusion

<!-- 
Wrap up with impact and future direction:

- Research Agent Mobile shifts ML experiment management from "check when
  you're at your desk" to "stay in control from anywhere."
- By combining a mobile-first interface with an AI agent that understands
  your experiments, researchers can catch failures faster, waste less compute,
  and iterate more quickly.
- Future work: expanded MCP tool integrations, multi-user collaboration,
  deeper anomaly detection models.
-->

---

## Team

| Name | Contributions |
|------|--------------|
| **Hargen Zheng** | Front-end/back-end integration, real-time streaming, message editing |
| **Charlie Sun** | Chat UX features, smart follow-up questions, research journey |
| **Avi Mehta** | Chat streaming, saved chats, WandB integration, MCP server |
| **Mihir Joshi** | Chat selectors, token estimation, run selection, WandB & MCP |
| **Hao Zhang** | Mentor and advisor |

---

## Acknowledgements

<!-- 
Thank your mentor, course staff, and anyone who helped.
-->

---

## References

<!-- 
Link to relevant papers, tools, and resources:
- OpenCode / LLM tooling
- Model Context Protocol (MCP)
- Weights & Biases
- Next.js, FastAPI
- Any papers that informed your approach
-->

---

*UC San Diego — Data Science Capstone (DSC 180AB) — 2025–2026*
