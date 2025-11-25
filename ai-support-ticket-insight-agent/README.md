# AI Support Ticket Insight Agent  
Google 5-Day AI Agents Intensive — Capstone Project

## Overview  
This project is a multi-agent AI system that automatically analyzes customer support tickets using Gemini.  
It classifies issues, detects sentiment, extracts insights, generates weekly reports, and stores the results in long-term memory for trend analysis.

The goal is to help support teams understand recurring problems, track customer frustration, and prioritize areas that need attention — without manual review.

---

## Problem Statement  
Support teams receive hundreds or thousands of customer tickets each week.  
Manually identifying top issues, understanding sentiment shifts, and generating weekly insights is slow, repetitive, and error-prone. As a result, teams often lack visibility into what customers are experiencing and where urgent issues lie.

An automated, AI-driven analysis system can save hours of human effort and provide more consistent, reliable insights.

---

## Why Agents?  
Agents are a natural fit because the workflow breaks into distinct tasks that can be performed independently or sequentially:

- Issue classification  
- Sentiment detection  
- Insight extraction  
- Report generation  
- Memory storage and trend comparison  

Using multiple agents makes the system modular, scalable, and easy to extend.  
Parallel agents speed up processing, while sequential agents ensure structured insight generation.

---

## What I Built  
This project implements a multi-agent pipeline with the following components:

1. **Classifier Agent**  
   Classifies each ticket into login, payment, refund, delivery, or other.

2. **Sentiment Agent**  
   Detects emotional tone (neutral, frustrated, angry).

3. **Insight Agent**  
   Extracts top categories, keywords, and sentiment distribution.

4. **Report Agent**  
   Generates a weekly summary with recommended actions.

5. **Memory System**  
   Saves reports into `memory.json` so the system can track changes across weeks.

6. **Trend Comparison**  
   Compares the newest report with the previous one to highlight increases or decreases in complaints.

The pipeline runs end-to-end in the notebook: ingest → analyze → summarize → store → compare.

---

## Architecture  
The system uses a combination of parallel and sequential agents.

### Parallel Agents
- Classifier Agent  
- Sentiment Agent  

These operate independently on each ticket.

### Sequential Agents
- Insight Agent (depends on classifier + sentiment outputs)  
- Report Agent (depends on insights)

### Memory  
Reports are saved to JSON so the agent can reference past weeks.

### Logging  
All operations write to a `logger.log` file for observability and debugging.

```
Input Tickets
      │
      ├── Classifier Agent
      ├── Sentiment Agent
      │
      ▼
Insight Agent
      │
      ▼
Report Agent → memory.json → Trend Comparison
```

---

## Demo Instructions  
1. Add your Gemini API key under Kaggle Secrets as `GOOGLE_API_KEY`.  
2. Run all cells in order.  
3. The notebook will:
   - Generate a dataset  
   - Run classification and sentiment agents  
   - Produce a weekly insight report  
   - Save the report into memory  
   - Compare with previous reports (if available)

---

## Tools and Technologies  
- Python  
- Gemini (LLM via `google.genai`)  
- Multi-agent design  
- JSON-based memory  
- Logging for observability  
- Pandas for data handling  
- Regular expressions for keyword extraction  

---

## Future Work  
If I had more time, I would:

- Connect to a real ticketing API for live data ingestion  
- Deploy the system using Agent Engine or Cloud Run  
- Add a dashboard to visualize trends over time  
- Build a front-end UI for non-technical users  
- Improve classifier accuracy using fine-tuned models  
- Add embeddings for semantic search over historical tickets  
- Implement agent evaluation metrics

---

## Summary  
This project demonstrates a complete multi-agent AI system using Gemini that can automate customer support ticket analysis, generate insights, and track trends across weeks. It showcases parallel and sequential agents, memory, observability, and practical industry-aligned functionality in a clean, modular design.

