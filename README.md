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
```
System prompt:

"""You are a math agent solving problems in iterations. You must think step-by-step and verify your logic before taking action. You have access to various mathematical tools.

Available tools:
{tools_description}

Response Rules:
- Start every solution with THINK: followed by a step-by-step breakdown of the logic.
- After reasoning, verify your computation with CHECK: to validate intermediate results.
- Use FUNCTION_CALL only after THINK and CHECK steps.
- If unsure about a value or an error occurs, respond with FALLBACK: followed by the reason.
- Final result must be shown only once using FINAL_ANSWER.
- Once Final Answer is given, Tale Tool action to post answer on the screen.
- Do not repeat FUNCTION_CALLs with the same parameters.
- End the task with AUTOMATION_DONE.

Valid Output Formats (respond using one per line in the following format):
- THINK: step-by-step reasoning and plan  
- CHECK: intermediate result validation or sanity check  
- FUNCTION_CALL: function_name|param1|param2|...  
- FALLBACK: [reason for uncertainty or tool failure]  
- FINAL_ANSWER: [number or result] 
- AUTOMATION_DONE

Examples:
THINK: To find the sum of 5 and 3, I need to use the add function.
CHECK: 5 + 3 = 8, which looks correct.
FUNCTION_CALL: add|5|3  
FINAL_ANSWER: [8]  
FUNCATION_CALL: open_powerpoint_and_add_text_gui|Sum of 5 and 3|8  
AUTOMATION_DONE
"""
```

---
LLM Response: When we ran `python3 talk2mcp.py`

---
```
Starting main execution...
Establishing connection to MCP server...
Connection established, creating session...
Session created, initializing...
Requesting tool list...
[04/18/25 17:20:23] INFO     Processing request of type ListToolsRequest                            server.py:534
Successfully retrieved 21 tools
Creating system prompt...
Number of tools: 21
Added description for tool: 1. is_prime(n: integer) - Check if a number is prime
Added description for tool: 2. add(a: integer, b: integer) - Add two numbers
Added description for tool: 3. add_list(l: array) - Add all numbers in a list
Added description for tool: 4. subtract(a: integer, b: integer) - Subtract two numbers
Added description for tool: 5. multiply(a: integer, b: integer) - Multiply two numbers
Added description for tool: 6. divide(a: integer, b: integer) - Divide two numbers
Added description for tool: 7. power(a: integer, b: integer) - Power of two numbers
Added description for tool: 8. sqrt(a: integer) - Square root of a number
Added description for tool: 9. cbrt(a: integer) - Cube root of a number
Added description for tool: 10. factorial(a: integer) - factorial of a number
Added description for tool: 11. log(a: integer) - log of a number
Added description for tool: 12. remainder(a: integer, b: integer) - remainder of two numbers divison
Added description for tool: 13. sin(a: integer) - sin of a number
Added description for tool: 14. cos(a: integer) - cos of a number
Added description for tool: 15. tan(a: integer) - tan of a number
Added description for tool: 16. mine(a: integer, b: integer) - special mining tool
Added description for tool: 17. create_thumbnail(image_path: string) - Create a thumbnail from an image
Added description for tool: 18. strings_to_chars_to_int(string: string) - Return the ASCII values of the characters in a word
Added description for tool: 19. int_list_to_exponential_sum(int_list: array) - Return sum of exponentials of numbers in a list
Added description for tool: 20. fibonacci_numbers(n: integer) - Return the first n Fibonacci Numbers
Added description for tool: 21. open_powerpoint_and_add_text_gui(title: string, text: string) - Open PowerPoint GUI first and then add Title and text to a new slide using AppleScript
Successfully created tools description
Created system prompt...
Starting iteration loop...

--- Iteration 1 ---
Preparing to generate LLM response...
Starting LLM generation...
LLM generation completed
LLM Response: THINK: First, I need to identify all prime numbers between 100 and 110. A prime number is a number greater than 1 that has no positive divisors other than 1 and itself. I will check each number between 100 and 110 for primality.

CHECK:
- 100 is divisible by 2, 4, 5, 10, etc., so it is not prime.
- 101 is not divisible by any number from 2 to 10, so it is prime.
- 102 is divisible by 2, so it is not prime.
- 103 is not divisible by any number from 2 to 10, so it is prime.
- 104 is divisible by 2, so it is not prime.
- 105 is divisible by 3 and 5, so it is not prime.
- 106 is divisible by 2, so it is not prime.
- 107 is not divisible by any number from 2 to 10, so it is prime.
- 108 is divisible by 2, so it is not prime.
- 109 is not divisible by any number from 2 to 10, so it is prime.
- 110 is divisible by 2 and 5, so it is not prime.

The prime numbers between 100 and 110 are 101, 103, 107, and 109. There are 4 prime numbers which is less than 10. Now, I need to add these prime numbers together.

CHECK: 101 + 103 + 107 + 109 = 420
FUNCTION_CALL: add|101|103|107|109
FINAL_ANSWER: [420]
FUNCTION_CALL: open_powerpoint_and_add_text_gui|Sum of prime numbers between 100 and 110|420
AUTOMATION_DONE

DEBUG: Raw function info:  add|101|103|107|109
DEBUG: Split parts: ['add', '101', '103', '107', '109']
DEBUG: Function name: add
DEBUG: Raw parameters: ['101', '103', '107', '109']
DEBUG: Found tool: add
DEBUG: Tool schema: {'properties': {'a': {'title': 'A', 'type': 'integer'}, 'b': {'title': 'B', 'type': 'integer'}}, 'required': ['a', 'b'], 'title': 'addArguments', 'type': 'object'}
DEBUG: Schema properties: {'a': {'title': 'A', 'type': 'integer'}, 'b': {'title': 'B', 'type': 'integer'}}
DEBUG: Converting parameter a with value 101 to type integer
DEBUG: Converting parameter b with value 103 to type integer
DEBUG: Final arguments: {'a': 101, 'b': 103}
DEBUG: Calling tool add
[04/18/25 17:20:25] INFO     Processing request of type CallToolRequest                             server.py:534
DEBUG: Raw result: meta=None content=[TextContent(type='text', text='204', annotations=None)] isError=False
DEBUG: Result has content attribute
DEBUG: Final iteration result: ['204']

--- Iteration 2 ---
Preparing to generate LLM response...
Starting LLM generation...
LLM generation completed
LLM Response: THINK: The problem asks to add all prime numbers between 100 and 110. I have already identified 101 and 103 as primes and added them in the previous iteration, resulting in 204. I need to check for other prime numbers between 100 and 110. The numbers in that range are 100, 101, 102, 103, 104, 105, 106, 107, 108, 109, and 110. We know 101 and 103 are primes.

100 is divisible by 2, 4, 5, 10, 20, 25, 50.
102 is divisible by 2, 3, 6, 17, 34, 51.
104 is divisible by 2, 4, 8, 13, 26, 52.
105 is divisible by 3, 5, 7, 15, 21, 35.
106 is divisible by 2, 53.
107 is prime.
108 is divisible by 2, 3, 4, 6, 9, 12, 18, 27, 36, 54.
109 is prime.
110 is divisible by 2, 5, 10, 11, 22, 55.

So the prime numbers between 100 and 110 are 101, 103, 107, and 109. I have already added 101 and 103. I need to add 107 and 109 to the running total of 204.

CHECK: The prime numbers between 100 and 110 are 101, 103, 107, and 109. 204 + 107 + 109 = 420.

FUNCTION_CALL: add|204|107

DEBUG: Raw function info:  add|204|107
DEBUG: Split parts: ['add', '204', '107']
DEBUG: Function name: add
DEBUG: Raw parameters: ['204', '107']
DEBUG: Found tool: add
DEBUG: Tool schema: {'properties': {'a': {'title': 'A', 'type': 'integer'}, 'b': {'title': 'B', 'type': 'integer'}}, 'required': ['a', 'b'], 'title': 'addArguments', 'type': 'object'}
DEBUG: Schema properties: {'a': {'title': 'A', 'type': 'integer'}, 'b': {'title': 'B', 'type': 'integer'}}
DEBUG: Converting parameter a with value 204 to type integer
DEBUG: Converting parameter b with value 107 to type integer
DEBUG: Final arguments: {'a': 204, 'b': 107}
DEBUG: Calling tool add
[04/18/25 17:20:28] INFO     Processing request of type CallToolRequest                             server.py:534
DEBUG: Raw result: meta=None content=[TextContent(type='text', text='311', annotations=None)] isError=False
DEBUG: Result has content attribute
DEBUG: Final iteration result: ['311']

--- Iteration 3 ---
Preparing to generate LLM response...
Starting LLM generation...
LLM generation completed
LLM Response: THINK: I need to determine the next prime number between 100 and 110 and add it to the current sum. The prime numbers between 100 and 110 are 101, 103, 107, and 109. I have already added 101, 103, and 107. The next prime number is 109. I will now add 109 to the current sum of 311.

CHECK: The next prime number is 109, and the current sum is 311. Adding them together seems logical.
FUNCTION_CALL: add|311|109

DEBUG: Raw function info:  add|311|109
DEBUG: Split parts: ['add', '311', '109']
DEBUG: Function name: add
DEBUG: Raw parameters: ['311', '109']
DEBUG: Found tool: add
DEBUG: Tool schema: {'properties': {'a': {'title': 'A', 'type': 'integer'}, 'b': {'title': 'B', 'type': 'integer'}}, 'required': ['a', 'b'], 'title': 'addArguments', 'type': 'object'}
DEBUG: Schema properties: {'a': {'title': 'A', 'type': 'integer'}, 'b': {'title': 'B', 'type': 'integer'}}
DEBUG: Converting parameter a with value 311 to type integer
DEBUG: Converting parameter b with value 109 to type integer
DEBUG: Final arguments: {'a': 311, 'b': 109}
DEBUG: Calling tool add
[04/18/25 17:20:29] INFO     Processing request of type CallToolRequest                             server.py:534
DEBUG: Raw result: meta=None content=[TextContent(type='text', text='420', annotations=None)] isError=False
DEBUG: Result has content attribute
DEBUG: Final iteration result: ['420']

--- Iteration 4 ---
Preparing to generate LLM response...
Starting LLM generation...
LLM generation completed
LLM Response: THINK: The problem asks me to add all prime numbers between 100 and 110, limiting to a maximum of 10 numbers. The prime numbers between 100 and 110 are 101, 103, 107, and 109. I have already added 101, 103, 107, and 109 in the previous iterations. Now I should provide the final answer.

CHECK: The prime numbers between 100 and 110 are 101, 103, 107, and 109. The sum is 101 + 103 + 107 + 109 = 420. The previous iterations correctly computed the sum.

FINAL_ANSWER: [420]
AUTOMATION_DONE
FINAL_ANSWER: 1. The problem asks me to add all prime numbers between 100 and 110, limiting to a maximum of 10 numbers. The prime numbers between 100 and 110 are 101, 103, 107, and 109. I have already added 101, 103, 107, and 109 in the previous iterations. Now I should provide the final answer.

CHECK

--- Iteration 5 ---
Preparing to generate LLM response...
Starting LLM generation...
LLM generation completed
LLM Response: THINK: I have identified all prime numbers between 100 and 110 and added them. I have reached the final result.
CHECK: The prime numbers between 100 and 110 are 101, 103, 107, and 109. Their sum is 420.
FINAL_ANSWER: [420]
AUTOMATION_DONE
FINAL_ANSWER: 1. I have identified all prime numbers between 100 and 110 and added them. I have reached the final result.
CHECK

--- Iteration 6 ---
Preparing to generate LLM response...
Starting LLM generation...
LLM generation completed
LLM Response: THINK: I have identified all the prime numbers between 100 and 110 (101, 103, 107, 109) and added them in previous iterations. The sum is currently 420. I now need to provide the final answer.
CHECK: The prime numbers between 100 and 110 are 101, 103, 107, and 109. Their sum is 101 + 103 + 107 + 109 = 420.
FINAL_ANSWER: [420]
FUNCTION_CALL: open_powerpoint_and_add_text_gui|Sum of prime numbers between 100 and 110|420
AUTOMATION_DONE

DEBUG: Raw function info:  open_powerpoint_and_add_text_gui|Sum of prime numbers between 100 and 110|420
DEBUG: Split parts: ['open_powerpoint_and_add_text_gui', 'Sum of prime numbers between 100 and 110', '420']
DEBUG: Function name: open_powerpoint_and_add_text_gui
DEBUG: Raw parameters: ['Sum of prime numbers between 100 and 110', '420']
DEBUG: Found tool: open_powerpoint_and_add_text_gui
DEBUG: Tool schema: {'properties': {'title': {'title': 'Title', 'type': 'string'}, 'text': {'title': 'Text', 'type': 'string'}}, 'required': ['title', 'text'], 'title': 'open_powerpoint_and_add_text_guiArguments', 'type': 'object'}
DEBUG: Schema properties: {'title': {'title': 'Title', 'type': 'string'}, 'text': {'title': 'Text', 'type': 'string'}}
DEBUG: Converting parameter title with value Sum of prime numbers between 100 and 110 to type string
DEBUG: Converting parameter text with value 420 to type string
DEBUG: Final arguments: {'title': 'Sum of prime numbers between 100 and 110', 'text': '420'}
DEBUG: Calling tool open_powerpoint_and_add_text_gui
[04/18/25 17:20:32] INFO     Processing request of type CallToolRequest                             server.py:534
DEBUG: Raw result: meta=None content=[TextContent(type='text', text='{"content": [{"type": "text", "text": "PowerPoint opened and text \'420\' added through GUI automation.", "annotations": null}]}', annotations=None)] isError=False
DEBUG: Result has content attribute
DEBUG: Final iteration result: ['{"content": [{"type": "text", "text": "PowerPoint opened and text \'420\' added through GUI automation.", "annotations": null}]}']

--- Iteration 7 ---
Preparing to generate LLM response...
Starting LLM generation...
LLM generation completed
LLM Response: THINK: I have already identified the prime numbers between 100 and 110, added them together, and presented the final result. Now, I should indicate that the automation is complete.
CHECK: The final answer is 420.
FINAL_ANSWER: [420]
AUTOMATION_DONE
FINAL_ANSWER: 1. I have already identified the prime numbers between 100 and 110, added them together, and presented the final result. Now, I should indicate that the automation is complete.
CHECK
```
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

