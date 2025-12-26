App Review Trend Analysis using Agentic AI
Overview

This project implements an agentic AI system to analyze Google Play Store reviews for a popular food delivery application (e.g., Swiggy/Zomato).
The system processes reviews received daily as batches and generates a trend analysis report that helps product teams identify recurring issues, feature requests, and new evolving topics over time.

The solution is designed with high recall as a primary objective to ensure that no relevant user feedback is missed.

Problem Statement

Given app store reviews received daily starting from a target date, the goal is to:

Extract issues, requests, and feedback from reviews

Consolidate semantically similar feedback into unified topics

Track topic frequency trends from T-30 to T

Enable identification of emerging issues early

Agentic Architecture

The system follows a multi-agent design, avoiding traditional topic modeling approaches (LDA, TopicBERT), as required.

Agent 1: High-Recall Topic Extraction

Extracts candidate issue phrases directly from review text

Does not rely on predefined categories

Ensures that any new or rare issue is captured

Agent 2: Topic Deduplication & Evolution

Uses semantic similarity (sentence embeddings) to merge similar topics

Example:

“delivery guy was rude”

“delivery partner behaved badly”
→ consolidated into a single canonical topic

If similarity is below a defined threshold, a new topic is automatically created, allowing evolving issues to surface

Agent 3: Trend Analysis Agent

Aggregates canonical topics by date

Produces a topic × date frequency table

Enables trend analysis from T-30 to T

High Recall & Evolving Topics

To satisfy the evaluation focus:

No fixed taxonomy is enforced

New topics are created dynamically

Similar topics are merged using semantic similarity

This design prioritizes recall over premature categorization

This allows product teams to:

Detect emerging issues early

Track growth or decline of known problems

Make data-driven prioritization decisions

Input Assumptions

Reviews are received daily as batches

Each review contains:

date

review text

For demonstration, reviews are simulated; the logic remains identical for real Google Play data

Output

The primary output is a trend analysis report:

Format

Rows: Topics (issues / requests / feedback)

Columns: Dates (T-30 → T)

Cells: Frequency of topic occurrence on that date

Example:

Topic	2024-06-01	2024-06-02	2024-06-03
delivery partner rude	1	1	0
food quality issue	1	1	0
maps not working	0	0	1

The generated report is available as:

trend_analysis_report.csv

Project Structure
app-review-trend-ai-agent/
├── notebook/
│   └── app_review_trend_ai_agent.ipynb
├── output/
│   └── trend_analysis_report.csv


Note: Outputs are generated alongside the notebook execution context for simplicity and reproducibility.

Technologies Used

Python

Pandas, NumPy

Sentence Transformers (all-MiniLM-L6-v2)

Scikit-learn (cosine similarity)

Google Colab (execution environment)

Key Design Decisions

Agentic architecture chosen over classical topic models

High recall prioritized over rigid categorization

Semantic deduplication used to avoid fragmented trends

Model-agnostic design (can be extended to GPT-based agents if required)

Limitations & Future Work

Real-time scraping can be integrated for live deployment

Topic labeling can be refined using LLM-based summarization

Dashboard visualization can be added for product stakeholders

Conclusion

This system demonstrates how agentic AI can be used to transform raw app reviews into actionable trend insights. By prioritizing high recall and supporting evolving topics, it provides product teams with a reliable view of user feedback over time.
