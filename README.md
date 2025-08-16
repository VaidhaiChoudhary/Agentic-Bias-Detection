# Agentic-Bias-Detection: Can AI Catch Its Flaws?
## Exploring how AI agents might critique bias in other agents or themselves

**Agentic AI** refers to AI systems designed as autonomous “agents” capable of making decisions, taking actions, and even interacting with other agents or tools.
**Bias Detection** is the process of identifying unfair or prejudiced outcomes in AI decisions, like a loan model giving lower approval rates to certain demographics.

##**How It Works**
_Agent 1: Decision Generator_
This agent uses an LLM (LLaMA 3 via Groq API) prompted as an admissions advisor. It receives a sensitive prompt (e.g., “Who should get preference in college admissions?”) and responds based on the model’s pretraining.
Prompt formatting follows a standard messages structure with a "system" role to define the agent's persona and a "user" role for the actual question.

_Agent 2: Bias Critic_
A second LLM instance is used with a different system prompt — this time as a fairness and bias detection expert. It is given the response from Agent 1 and asked to:

- Identify any bias (e.g., demographic, regional, social),
- Explain why it’s problematic (if any),
- Suggest revisions to improve fairness.

_Iterative Loop (Agentic Refinement)_
In the extended version, the critic’s feedback is passed back to Agent 1 in the next round, where it’s included as additional system context. The agent then generates a revised answer, incorporating the fairness critique.

This loop continues for up to 2 iterations or until the critic explicitly states “no bias found.” This mimics a self-auditing AI workflow, where generation and evaluation are decoupled but cooperative.

##**Core Design Takeaways**
Uses multi-agent prompting to simulate oversight roles.
Leverages Groq’s ultra-low latency for rapid back-and-forth without GPU setup.
Uses open models (LLaMA 3 70B), showing that powerful, bias-aware interactions are possible even without proprietary LLMs.
Encourages a design pattern where AI reflects on its own outputs, not just via static fairness metrics, but through dynamic peer critique.
This small-scale implementation mirrors real-world interest in LLM-as-auditor, a growing research and application area in trustworthy AI.
