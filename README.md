# Kaggle-Google-AI-agent-Healthcare-Agent-

🌐 HealthGuard AI — Multi-Agent Medication Safety Assistant
By Ravikrishna M & Harini K V

A Gemini-powered healthcare agent that checks drug interactions, analyzes evidence from Google Search, and generates safe medication schedules in real-time.

🚀 Overview

HealthGuard AI is an intelligent multi-agent system built using Google Gemini 2.5 Flash and Google Custom Search Engine (CSE).
It helps users avoid dangerous medication combinations by:

✔ Parsing medications & foods from natural language
✔ Searching the web for real medical evidence
✔ Detecting drug–drug & drug–food interactions
✔ Generating a personalized safe medication schedule
✔ Evaluating the agent’s correctness using an automated evaluator agent

This project was developed as part of the Google AI Agents Intensive – Capstone Project (Nov 2025) under the Agents for Good track.

🧠 Problem Statement

Medication misuse is a major global health issue:

People mix common drugs unsafely (e.g., ibuprofen + alcohol, statins + grapefruit)

There is no single tool that parses real user inputs like:

“I took 2 dolo 650 and ibuprofen after drinking”

Existing tools do not combine LLM reasoning + internet evidence + rule-based clinical overrides

Goal:
Build an agent that provides safe, accurate, evidence-backed medication interaction checks, usable by everyday people.

🤖 Why Agents?

Agents are the ideal solution because:

📌 Multi-step reasoning required:

Parsing natural language medication descriptions

Searching the internet dynamically

Interpreting clinical evidence

Combining rule-based and evidence-based decision making

Generating personalized schedules

📌 Multi-agent architecture fits perfectly:

Parser Agent → Understands user input

Search Agent → Retrieves Google CSE medical evidence

Interaction Agent → Clinical reasoning + rule-engine

Schedule Agent → Personalized medication planning

Evaluator Agent → Scores correctness for safety

Agents allow reliability, modularity, and traceability — essential for healthcare systems.

🏗️ System Architecture
User Input
    │
    ▼
🧩 1. Medication Parser Agent (Gemini 2.5 Flash)
    - Extracts drugs, doses, foods
    - Normalizes branded names → generic
    - Produces structured JSON

    │
    ▼
🌐 2. Google CSE Evidence Agent
    - Searches drug side effects & interactions
    - Extracts top snippets as medical evidence

    │
    ▼
⚠️ 3. Interaction Checker Agent
    - Uses snippets + clinical rules
    - Identifies severity
    - Provides explanation

    │
    ▼
⏱️ 4. Schedule Builder Agent
    - Builds safe medication schedule
    - Adds spacing, max dose limits, food warnings

    │
    ▼
📊 5. Evaluator Agent
    - Compares system output vs expected behavior
    - Generates safety scores (0–10)

    ▼
 Final Output

🧪 Demo (Example Run)
Input
I take paracetamol 500mg and ibuprofen 400mg

Output
{
  "interaction_found": true,
  "severity": "Moderate",
  "explanation": "Paracetamol + ibuprofen may cause GI irritation (rule-override)."
}

Generated Safe Schedule
{
  "schedule": [
    {"drug": "paracetamol 500mg", "time": "08:00", "note": "Do not exceed 4000mg/day."},
    {"drug": "ibuprofen 400mg", "time": "11:00", "note": "Take with food."}
  ]
}

🛠️ Technologies Used
🚀 Core Technologies

Gemini 2.5 Flash API (LLM reasoning)

Google Custom Search Engine (CSE) (real-time evidence retrieval)

Python

Colab environment

🧩 Key Agent Concepts Implemented

✔ Multi-agent pipeline
✔ Sequential agents
✔ External tool usage (Google CSE)
✔ Context engineering + JSON extraction
✔ Retry logic + error handling
✔ Evaluation agent for safety scoring

🔧 Components
1. Medication Parser Agent

Extracts drug name, dose, route, frequency, duration

Normalizes brand names

Detects foods (coffee, alcohol, grapefruit…)

2. Google CSE Search Agent

Searches "drug + side effects"

Fetches real-world medical snippets

Handles HTTP errors, rate limits, and empty results

3. Interaction Checker Agent

Uses clinical hard rules:

Paracetamol + Ibuprofen → Moderate

Ibuprofen + Alcohol → High

Iron + Coffee → Moderate

Atorvastatin + Grapefruit → High

Uses snippet-based semantic reasoning

Generates severity and explanation

4. Schedule Builder Agent

Creates safe schedule with:

Time slots

Dose spacing

Max daily limits

Food warnings

5. Evaluator Agent

Scores:

Severity

Reasoning

Clarity

Hallucination

Consistency

Produces an Overall Safety Score.

📈 Test Case Results (Phase-3 Evaluation)
Input	Expected	Model Severity	Score
Paracetamol + Ibuprofen	Moderate	Moderate	10/10
Ibuprofen + Alcohol	High	High	10/10
Iron + Coffee	Moderate	Moderate	10/10
Atorvastatin + Grapefruit	High	High	10/10

Perfect safety alignment.

🏁 How to Run the Project

Open Google Colab

Load API keys:

os.environ["GEMINI_API_KEY"] = "your_key"
os.environ["CSE_API_KEY"] = "your_key"
os.environ["CSE_ID"]      = "your_cse_id"


Run the full notebook in order

Call:

orchestrator("I took iron tablets with coffee")

📌 If We Had More Time

We would add:

Deployment using Vertex AI Agent Engine

A mobile UI for patients

Memory for tracking daily adherence

Voice input using Gemini Audio

A full drug database with 1000+ molecules

Integration with Google Fit health signals

❤️ Authors

Ravikrishna M
Harini K V

⭐ If this repo helped you, please star it!

Let’s make healthcare safer using AI 💊✨
