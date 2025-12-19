# 🤖 Autonomous Research Agent | LangGraph

An advanced, multi-agent autonomous research system built with **LangGraph**. This project implements a sophisticated "Reasoning-and-Act" (ReAct) loop that allows AI agents to plan, browse the web, critique their own findings, and compile high-quality research papers without human intervention.

## 🚀 Overview

Traditional LLM chains often struggle with "hallucinations" or shallow results when asked to perform deep research. This project solves that by using **stateful, cyclic graphs**. 

The agent doesn't just provide a one-shot answer; it behaves like a human researcher:
1. **Analyzes** the prompt to identify core objectives.
2. **Performs** initial web searches.
3. **Evaluates** the results for depth and accuracy.
4. **Re-searches** if gaps in information are detected.
5. **Synthesizes** a final report with citations.

---

## 🏗 System Architecture

The project is built on a **Directed Acyclic Graph (DAG)** (with cycles allowed) using LangGraph. Each node represents a specific function or agent logic.



### 🔄 The Workflow:
* **Planner Node**: Breaks down complex queries into specific research tasks.
* **Researcher Node**: Utilizes Search APIs (Tavily/Serper) to gather raw data.
* **Critique Node**: Acts as a "Quality Gate," checking if the data collected satisfies the initial plan.
* **Writer Node**: Formats the final state into a structured Markdown report.

---

## ✨ Core Features

* **Cyclic Self-Correction**: If the Critique node finds the information insufficient, it triggers a loop back to the Search node with refined queries.
* **State Management**: Uses LangGraph's `StateGraph` to maintain research memory across multiple iterations.
* **Source Attribution**: Automatically generates a bibliography of all URLs visited.
* **Custom Tools**: Integration for ArXiv (academic papers), Tavily (web search), and local PDF processing.

---

## 🛠 Tech Stack

* **Orchestration**: [LangGraph](https://python.langchain.com/docs/langgraph)
* **LLM**: GPT-4o, Claude 3.5 Sonnet, or Llama 3 (via Groq/Ollama)
* **Search Infrastructure**: Tavily AI / DuckDuckGo Search
* **Environment**: Python 3.10+
* **Tracing**: LangSmith (for debugging agent reasoning)
