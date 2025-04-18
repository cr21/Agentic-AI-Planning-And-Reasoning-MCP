# Agentic-AI-Planning-And-Reasoning-MCP

## 🧠 Planning & Reasoning with Language Models

---

## 📌 Table of Contents
- [🧠 How LLMs Reason](#-how-llms-reason)
- [🔗 Chain-of-Thought Prompting](#-chain-of-thought-prompting)
- [🤖 ReAct: Reason + Act](#-react-reason--act)
- [🧱 Structured Prompting Techniques](#-structured-prompting-techniques)
- [🌳 LLM-based Planning & Goal Decomposition](#-llm-based-planning--goal-decomposition)
- [🛡️ Prompt Engineering Best Practices](#️-prompt-engineering-best-practices)
- [📚 References](#-references)
- [📌 Project Overview](#-project-overview)

---

## 🧠 How LLMs Reason

LLMs don't just complete text—they simulate reasoning using internal circuits, discovered through *[Transformer Circuits](https://transformer-circuits.pub/2025/attribution-graphs/static_js/attribution_graphs/index.html?clickedId=11_17926448_-0)* research.

### 🧩 Internal Logic Features:
- **Entity Reasoning**: "Bangalore → Karnataka", "Dallas is in Texas"
- **Math Computation**: Rounding, addition across contexts
- **Behavioral Control**: “Refusal mode”, “instruction detected”
- **Chain-of-Thought Activation**: Features like “Plan before generation”
- **Hallucination Control**: Suppresses unknown or uncertain answers
- **Multilingual Logic**: Language-independent semantic mappings

### 🧠 Memory in LLMs:
- **Frozen Memory**: Cached values from previous layers
- **Working Memory**: Actively updated logic per token

[🔗 Visual Exploration Tool (Anthropic)](https://transformer-circuits.pub/2025/attribution-graphs/static_js/attribution_graphs/index.html)

---

## 🔗 Chain-of-Thought Prompting

CoT encourages **step-by-step reasoning**, helping models arrive at logically consistent answers.

### 💡 Example:
```
Q: A bag has 3 apples, 5 oranges, 2 bananas. What's the chance it’s not an orange?

A: Total fruits = 10
Oranges = 5
Not oranges = 5
Answer = 5/10 = 0.5
```

### 🆚 Zero-shot vs. Few-shot CoT

| Type | Description |
|------|-------------|
| Zero-shot | Uses prompt like "Let's solve this step by step" |
| Few-shot | Gives multi-step reasoning examples |

These prompt structures **activate internal planning modules**.

---

## 🤖 ReAct: Reason + Act

ReAct combines **thinking + tool use** in a loop:
```
Thought → Action → Observation → Thought → ...
```

### 🧠 Used for:
- Web search
- Code execution
- Database querying
- Agent-based reasoning

### 🔍 Example Prompt:
```
Thought: Need to get stock price
Action: Query Yahoo Finance
Observation: $130
Thought: Proceed with calculation...
```

---

## 🧱 Structured Prompting Techniques

Structured prompting makes model output **more predictable and verifiable**.

### 📐 Types:
1. **Input-Output Templates**  
   Provide clear formatting to help the model generalize patterns.

2. **Step-Labeled Reasoning (SLR)**  
   ```text
   Step 1: Identify problem  
   Step 2: Break down steps  
   Step 3: Solve
   ```

3. **Function-like Prompts**
   - Wrap tasks in function-like structures
   - Easy for validation and tool-chaining

---

## 🌳 LLM-Based Planning & Goal Decomposition

LLMs can simulate **tree-based search** and **hierarchical planning**.

### 🪄 Planning Patterns:
- Simulated **Breadth-First Search**: Ask for multiple paths first
- Simulated **Depth-First Search**: Fully explore one idea

### 🎯 Goal Decomposition:
Prompt: *“What steps are needed to build a weather app?”*  
Model Output:
1. Fetch data from API  
2. Build UI  
3. Render output

This reflects *Hierarchical Task Networks* (HTN) behavior in classical planning.

---

## 🛡️ Prompt Engineering Best Practices

### ✅ Tips:
- Use `JSON` output format for clarity
- Ask model to **self-check** its answer
- Label reasoning types explicitly
- Use **fallback logic** for uncertain outputs
- Keep **conversation history** for continuity in agents

### 🧪 Example:
```json
{
  "thought": "I need the sum of two numbers",
  "function_call": "add(4, 5)",
  "result": 9,
  "verified": true
}
```
---
## How to Evaluate Prompt
---
If we're build Mathamatical Reasoning Agent or Agent which requires step by step thinking or reasonning, we could have write below prompt
```

Evaluate the prompt on the following criteria:

1. ✅ Explicit Reasoning Instructions  
   - Does the prompt tell the model to reason step-by-step?  
   - Does it include instructions like “explain your thinking” or “think before you answer”?

2. ✅ Structured Output Format  
   - Does the prompt enforce a predictable output format (e.g., FUNCTION_CALL, JSON, numbered steps)?  
   - Is the output easy to parse or validate?

3. ✅ Separation of Reasoning and Tools  
   - Are reasoning steps clearly separated from computation or tool-use steps?  
   - Is it clear when to calculate, when to verify, when to reason?

4. ✅ Conversation Loop Support  
   - Could this prompt work in a back-and-forth (multi-turn) setting?  
   - Is there a way to update the context with results from previous steps?

5. ✅ Instructional Framing  
   - Are there examples of desired behavior or “formats” to follow?  
   - Does the prompt define exactly how responses should look?

6. ✅ Internal Self-Checks  
   - Does the prompt instruct the model to self-verify or sanity-check intermediate steps?

7. ✅ Reasoning Type Awareness  
   - Does the prompt encourage the model to tag or identify the type of reasoning used (e.g., arithmetic, logic, lookup)?

8. ✅ Error Handling or Fallbacks  
   - Does the prompt specify what to do if an answer is uncertain, a tool fails, or the model is unsure?

9. ✅ Overall Clarity and Robustness  
   - Is the prompt easy to follow?  
   - Is it likely to reduce hallucination and drift?

```

---



## 📌 Project Overview

This project demonstrates a Multi-Component Protocol (MCP) server-client system for logical reasoning and planning by AI agents. The AI agent is designed to solve mathematical reasoning questions step-by-step, execute calculations using available tools, and call GUI actions (such as opening PowerPoint and displaying results). The system leverages LLMs (like Google's Gemini) to perform these tasks in iterations.

---

## 📦 Requirements

- Python 3.12 or higher
- Google Gemini API key
- MCP protocol library (custom implementation)
- Required Python packages:
  - `google-genai`
  - `asyncio`
  - `python-dotenv`
  - `aiohttp`
  - `functools`
  - `fastmcp`
  
Install required packages with:

```bash

# Install uv (only need pip once)
pip install uv

# Initialize project
uv init my_project

uv pip install -r requirements.txt
```

---

## ⚙️ Setup Instructions

1. Clone the repository:

```bash
git clone https://github.com/cr21/Agentic-AI-Planning-And-Reasoning-MCP.git
```

2. Set up your `.env` file with your Gemini API key:

```plaintext
GEMINI_API_KEY=your_api_key_here
```

3. Install the required dependencies:

```bash
uv pip install -r requirements.txt
```

4. Run the `talk2mcp.py` script:

```bash
python talk2mcp.py
```

The system will initiate the client-server connection and start processing mathematical queries.

---

## 🛠️ How It Works

### 1. The Agent Receives Queries
- The agent receives a mathematical question in the form of a query.
- The agent processes the query step-by-step by reasoning through it using the available tools.

### 2. Function Calls and Tool Interactions
- The agent identifies the required function call (e.g., adding numbers, checking prime numbers) based on the reasoning.
- The system invokes tool which are corresponding function from a set of available tools, passing the required parameters.

### 3. Result Verification
- After obtaining the function call result, the agent verifies intermediate calculations and checks for correctness.

### 4. GUI Interactions
- Once the final answer is computed, the agent can interact with the GUI to display results, such as opening PowerPoint and adding text.

### 5. Iteration Handling
- The system processes each query in multiple iterations, updating the query based on previous responses. The agent continues iterating until the task is complete.

---

## 🔧 How to Extend the System

- **Adding new tools**: To add new tools, modify the `tools_description` and ensure the correct parameters are provided for the new tools.
- **Adding new queries**: You can extend the system by adding new queries to the `current_query` section of the code.
- **Customizing reasoning steps**: Modify the `system_prompt` to adjust the reasoning or steps the agent should follow for each query.

---
## 📚 References

- 📖 [Chain-of-Thought Prompting (Google, 2022)](https://arxiv.org/abs/2201.11903)  
- ⚙️ [ReAct: Reasoning + Acting (Yao et al., 2022)](https://openreview.net/pdf?id=WE_vluYUL-X)  
- 🎯 [Prompting 101 – Notion Guide](https://datareporting.notion.site/Prompting-101-1c30e122af9180f690ebe50f93fb4d0f)  
- 🔍 [Transformer Circuits Explorer](https://transformer-circuits.pub)

