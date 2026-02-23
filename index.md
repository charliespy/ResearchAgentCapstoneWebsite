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

1. Introduction

In the rapidly evolving domain of deep learning research, the efficiency of the scientific cycle
is increasingly limited not by the availability of raw compute, but by the researcher’s capac-
ity to maintain continuous oversight of experimental states. As machine learning models
grow in complexity and training pipelines extend over days or weeks, the cognitive burden
of monitoring multiple concurrent processes has become a primary bottleneck. The pre-
vailing workflow relies heavily on synchronous desktop-bound interaction–using tools such
as SSH terminals and large-screen dashboards such as TensorBoard–which fails to account
for the asynchronous reality of modern model training. This rigidity forces researchers to
structure their lives around their experiments, tethering them to workstations to ensure
runs do not fail unobserved.

This reliance on desktop-centric tooling creates a significant ”blind spot” in the research
workflow . Standard observability tools are poorly optimized for mobile devices, touch inter-
faces, or intermittent network connectivity . Consequently , when researchers are traveling,
in meetings, or simply away from their desks, they lose the ability to effectively supervise
their work. This physical constraint leads to tangible resource waste: critical failures–such
as hyperparameter divergence, metric collapse, or infrastructure crashes–often go unno-
ticed for hours until the researcher returns to their desk. The result is a cycle of delayed
insights and wasted computational credits, driven purely by the lack of a flexible supervision
interface.

To address these limitations, this project introduces Research Agent Mobile, a specialized
system that decouples experiment management from the desktop environment. The project
has a concrete objective: minimize the latency between an experimental deviation and
an actionable human response. Unlike passive monitoring dashboards that merely display
static charts, this system functions as an active, intelligent partner in the research process.
It establishes a ”mobile control plane” specifically optimized for small viewports, allowing
researchers to maintain high-level supervision and situational awareness regardless of their
physical location.

The core philosophy of Research Agent Mobile is to empower the researcher with actionable
intervention capabilities rather than passive visibility . The system allows users to monitor
the health of runs via prioritized, context-sensitive alerts and perform safe, immediate in-
terventions such as stopping a failing run, restarting a stalled job, or launching a new
hyperparameter sweep without ever returning to a workstation. By facilitating these inter-
actions through a mobile-first interface, the system bridges the gap between the demanding
requirements of deep learning training and the mobility of the modern researcher .

---

2. System Overview

To realize the vision of a mobile-first research workflow , we engineered Research Agent
Mobile as a dual-component distributed system. The architecture is designed to bridge
the gap between ephemeral mobile interactions and persistent, long-running server pro-
cesses. High-level, the system integrates a high-performance Next.js frontend–specifically
optimized for the constraints of mobile viewports and touch latency–with a robust Python-
based orchestration backend.

This separation of concerns is critical. The backend manages job execution via persistent
tmux sessions, ensuring that computationally intensive training processes remain stable and
recoverable even if the client device loses connectivity or runs out of battery . Simultane-
ously , the frontend acts as a unified ”command center ,” decoupling the user from the raw
execution environment while providing a control plane for visualizing real-time metrics,
managing hyperparameter configurations, and inspecting generated artifacts.

Central to our methodology is the embedding of a context-aware Large Language Model
(LLM) agent directly into the experiment control loop. Unlike standard wrappers, this agent
is granted read-and-write access to the experiment’s execution context. This capability
enables it to interpret complex log streams, answer natural language queries regarding
training dynamics (e.g., ”Why is the loss diverging?”), and autonomously flag anomalies. By
synthesizing raw telemetry into semantic insights, the system transforms the mobile device
from a passive monitor into an active tool for high-level reasoning, allowing researchers to
collaborate with the system as they would with a peer .

---

## 3. Key Features

### 3.1 Mobile-First Interface

Standard web interfaces for experiment tracking often fail on mobile devices due to poor re-
sponsiveness and clutter . To address this, we implemented a responsive, dual-layout system
using Next.js 16. A primary engineering focus was the ”mobile-first” design philosophy , en-
suring the application adapts fluidly between minimum mobile viewports (down to 300px
width) and full desktop environments without loss of functionality . We developed a cus-
tom UI engine to resolve critical overflow issues common in standard CSS viewport queries.
This engine allows users to granularly adjust font scaling, button sizing, and layout density ,
ensuring usability is maintained regardless of the specific device hardware.

### 3.2 AI-Powered Chat Assistant

The chat interface – the central hub for human-agent collaboration – was re-architected to
support complex, non-linear workflows. We moved beyond simple request-response loops
to a state-managed message queue. This allows users to queue multiple commands, reorder
tasks, and utilize ”interruptible” states, giving the agent the ability to pause execution to
request human feedback before proceeding with destructive actions (such as terminating a
run).

On the backend, we refactored the data serialization format to accurately preserve the ”cog-
nitive chain” of the AI model. Rather than flattening the interaction history into simple text,
the system captures and renders the precise sequence of internal thought, tool execution, and
final text response. This granular fidelity is visualized in the frontend through distinct UI ele-
ments, distinguishing internal reasoning from external output. This transparency is vital for
building user trust in the agent’s decisions. Additional enhancements include session isola-
tion to prevent context bleeding between concurrent experiments, and a ”quote-and-reply”
feature that mirrors desktop-grade IDE interactions, enabling researchers to reference spe-
cific log lines or code blocks directly in the chat for targeted debugging.

### 3.3 Real-Time Visualization

Effective research requires immediate, interpretable visual feedback on training dynam-
ics. We integrated a flexible charting engine capable of interfacing with standard logging
frameworks like Weights & Biases (WandB). However , simply rendering external iframes
is insufficient for mobile contexts. Our system implements interactive, client-side charts
that allow users to toggle metric visibility , dynamically adjust axis scaling without page
re-renders, and manage chart density via a dedicated management popup.

We are currently extending this module to support ”Insight Charts”–custom visualizations
generated autonomously by the agent. By granting the agent direct access to raw metric
streams, it can identify patterns that a human might overlook. The agent can proactively
propose and generate comparative visualizations–such as radar charts for data mixture
analysis or video comparisons at specific training steps–without explicit user configura-
tion. This shifts visualization from a reactive task (plotting what you know to look for) to
a proactive one (surfacing anomalies through automated plotting and color-coded stability
indicators).

### 3.4 Research Journey

Scientific discovery is rarely a linear path; it is a branching tree of hypotheses, failures,
and refinements. Traditional version control systems track code changes but fail to cap-
ture the logic and decision-making process behind those changes. We introduce the ”Re-
search Journey”–a hierarchical, temporal visualization of the research lifecycle that effec-
tively functions as a ”semantic git” for experimental logic.

This feature allows researchers to visualize their project trajectory not as a flat list of com-
mits, but as a branching graph of decisions and outcomes. This structure enables deep ret-
rospective analysis: researchers can inspect the ”journey” to identify high-cost paths that
yielded low information gain, optimizing resource allocation for future iterations. Further-
more, by structuring history hierarchically , we empower the AI agent to perform ”meta-
analysis.” The agent can review the project’s entire branching history , reflecting on past
failures to recommend optimized directions for future experiments. This transforms the
history log from a passive record into an active knowledge base, significantly reducing the
cognitive load required to context-switch between long-running experiments.

### 3.5 Autonomous Monitoring (Wild Loop)

The core intelligence of the platform is driven by the ”Wild Loop,” an autonomous execution
environment that operates on the server independently of direct user interaction. This
backend architecture allows the agent to continuously monitor tmux sessions, parse real-
time logs, and execute interventions based on pre-defined heuristics or emergent anomalies
(e.g., ”stop training if loss spikes > 50%”).

To standardize the agent’s interaction with external tools and the file system, we adopted
the Model Context Protocol (MCP). MCP provides a universal interface for the agent to
connect with new libraries, custom scripts, or data sources without requiring core backend
refactoring. This modularity ensures the system is extensible; adding a new capability (e.g.,
querying a new dataset) is as simple as registering a new MCP tool.

The ”Wild Loop” is highly configurable, allowing users to define the boundaries of the
agent’s autonomy–ranging from passive monitoring to active hyperparameter tuning. By
integrating these loops with a prioritized event queue system, alerts generated during au-
tonomous operation are pushed instantly to the mobile client. This architecture ensures the
mobile device acts as a high-level command center , receiving synthesized intelligence and
strategic decision points rather than raw noise, thereby enabling effective ”human-in-the-
loop” supervision for otherwise autonomous research workflows.

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
