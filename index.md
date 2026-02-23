---
layout: default
title: Research Agent Mobile
description: A Mobile-First Agentic Interface for Monitoring and Steering Machine Learning Experiments
---

# Research Agent Mobile

**A Mobile-First Agentic Interface for Monitoring and Steering Machine Learning Experiments**

*Hargen Zheng, Charlie Sun, Avi Mehta, Mihir Joshi — Advised by Hao Zhang*

*UC San Diego, DSC 180B Capstone — Winter 2026*

[View Report](#){: .btn } [View Code on GitHub](https://github.com/hao-ai-lab/research-agent){: .btn }

---

## The Problem: ML Researchers Are Chained to Their Desks

<!-- 
Motivate the problem for a general audience:
- ML training runs take days/weeks
- Existing tools (TensorBoard, SSH terminals) are desktop-bound
- Researchers miss critical failures (divergence, crashes) when away
- Wasted compute, delayed insights
- Include a relatable analogy or scenario
-->

---

## What Is Research Agent Mobile?

<!-- 
High-level overview of the system in plain language:
- A mobile-friendly web app that lets researchers monitor and control ML experiments from their phone
- Not just a dashboard — an intelligent assistant that understands your experiments
- Key value props: real-time alerts, natural language interaction, remote intervention
- Include a hero screenshot or diagram of the app
-->

---

## Key Features

### Mobile-First Interface

<!-- 
- Designed for phones and tablets from the ground up
- Custom UI engine for responsive layouts (300px to full desktop)
- Touch-optimized controls
- Include a screenshot showing mobile vs desktop view
-->

### AI-Powered Chat Assistant

<!-- 
- Natural language interaction with your experiments
- Ask questions like "Why is the loss diverging?"
- The agent can read logs, interpret metrics, and provide actionable insights
- Interruptible workflows — the agent asks for confirmation before destructive actions
- Include a screenshot of the chat interface
-->

### Real-Time Visualization

<!-- 
- Interactive charts for training metrics (loss, accuracy, etc.)
- Weights & Biases integration
- Toggle metrics, adjust axes, manage chart density — all from mobile
- "Insight Charts": agent-generated visualizations that surface anomalies automatically
- Include an example chart screenshot
-->

### Research Journey

<!-- 
- A "semantic git" for your research process
- Visualize your project as a branching graph of decisions and outcomes
- Track hypotheses, failures, and refinements over time
- The AI agent can review your journey and suggest next steps
- Include a diagram or screenshot of the journey view
-->

### Autonomous Monitoring (Wild Loop)

<!-- 
- The agent runs continuously on the server, watching your experiments
- Detects anomalies (e.g., loss spikes > 50%) and alerts you instantly on mobile
- Configurable autonomy: from passive monitoring to active intervention
- Model Context Protocol (MCP) for extensible tool integration
- Include a diagram of the Wild Loop architecture
-->

---

## How It Works

<!-- 
Brief, accessible description of the system architecture:
- Next.js frontend + FastAPI backend
- Persistent tmux sessions keep experiments running even if your phone disconnects
- LLM agent embedded in the control loop for semantic reasoning
- Include a simplified architecture diagram
-->

---

## Results

<!-- 
Placeholder for results:
- Usability metrics, user feedback, or case studies
- Demonstration of anomaly detection and remote intervention
- Comparison with existing tools
- Screenshots or short demo GIFs
-->

*Coming soon.*

---

## Team

| Member | Contributions |
|--------|--------------|
| **Hargen Zheng** | Front-end/back-end integration, real-time streaming, message editing |
| **Charlie Sun** | Chat UX features, smart follow-up questions, research journey |
| **Avi Mehta** | Chat streaming, saved chats, WandB integration, MCP server |
| **Mihir Joshi** | Chat selectors, token estimation, run selection, WandB & MCP |
| **Hao Zhang** | Mentor and advisor |

---

## Learn More

- [Full Technical Report](#) — Detailed methodology and analysis
- [GitHub Repository](https://github.com/hao-ai-lab/research-agent) — Source code and documentation

---

*UC San Diego — Data Science Capstone (DSC 180AB) — 2025–2026*
