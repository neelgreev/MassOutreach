Agentic AI Outreach Pipeline
Overview
Personalized B2B communication is a major scaling bottleneck. Manual outreach is highly effective but time-consuming, while generic automated campaigns suffer from low engagement and aggressive spam filtering.

This project solves this by bridging the gap with an AI-driven orchestration system. It ingests structured lead data, leverages Large Language Models (LLMs) to dynamically generate context-aware, hyper-personalized messaging for each recipient, and dispatches them as individual network requests. Custom rate-limiting ensures the system mimics human sending patterns, maintaining high deliverability with zero manual intervention.

Key Features
🧠 Agentic Content Generation: Uses LLM APIs to read target company context and dynamically craft unique email bodies, moving beyond static {{First_Name}} templates.

🚦 Algorithmic Rate Limiting: Implements randomized chron-delays (e.g., 2–6 minutes between dispatches) to optimize network requests and bypass standard provider spam filters.

📨 Direct SMTP Dispatch: Connects directly to email servers via Python's smtplib, sending true 1-on-1 emails rather than relying on bulk BCC or marketing headers.

📊 Automated Ingestion: Parses structured datasets (CSV) for seamless pipeline execution.

Pipeline Architecture
Data Ingestion Node: Reads and parses leads.csv (Name, Company, Target Role, Context).

LLM Orchestration Node: Injects row data into a strict system prompt. The LLM generates a tailored 3-paragraph message.

Dispatcher Script: Python loop initiates an SMTP connection, constructs a unique MIME multipart message, and sends it to the sole recipient.

Sleep State: The system pauses for a randomized interval before processing the next row.

Tech Stack
Orchestration: n8n, Python 3.x

AI/LLM: Groq / Gemini / OpenAI API (Configurable)

Networking/Protocols: SMTP, email.message

Data Processing: Python csv module

Getting Started
Prerequisites
Python 3.10 or higher

n8n installed locally or via cloud

An LLM API Key (e.g., Groq, Google Gemini)

An email account with an App Password generated (Standard passwords will fail SMTP authentication).

Installation
Clone this repository:

Bash
git clone https://github.com/yourusername/agentic-outreach-pipeline.git
cd agentic-outreach-pipeline
Install required dependencies:

Bash
pip install -r requirements.txt
Create a .env file in the root directory and add your credentials:

Code snippet
SMTP_EMAIL=your_email@gmail.com
SMTP_APP_PASSWORD=your_16_digit_app_password
LLM_API_KEY=your_api_key_here
Usage
Populate the leads.csv file with your target contacts.

Run the main orchestration script:

Bash
python main.py
Monitor the terminal output for dispatch logs and randomized delay countdowns.

Ethical Usage Disclaimer
This tool is built to automate legitimate, highly targeted communication. It should not be used to send unsolicited bulk spam. Always comply with local anti-spam regulations (like CAN-SPAM or GDPR) when executing automated outreach.

Built by Neelgreev Ganguly(tiptaptoe)
