🤖 AI Email Scheduler — Automated Gmail & Google Calendar Integration
📘 Overview

This project showcases an AI-powered workflow built in n8n that connects Gmail, Google Gemini (PaLM), and Google Calendar to create an intelligent email assistant.
Whenever a new email arrives, the system automatically analyzes its content to detect meeting or event requests. It then checks your calendar availability:

                  ✅ If you’re free — it books the event automatically.
                  ❌ If you’re busy — it sends a polite email reply suggesting an alternate time.

This automation removes the manual hassle of scheduling and replying to meeting requests.

⚙️ Key Components
Node	Description
📩 Gmail Trigger	Detects new incoming emails in real time and starts the workflow.
🧩 Edit Fields (Set Node)	Extracts important email fields — sender, subject, and snippet — for the AI to process.
🧠 AI Agent (LangChain Agent)	Acts as the intelligent assistant. It interprets the email content, extracts event details, checks availability, and decides the next action.
💬 Google Gemini Chat Model	Provides the natural-language understanding and reasoning power for the AI Agent.
📅 Google Calendar Tools	Used for two operations — checking calendar availability and creating new events automatically.
✉️ Gmail Tool	Sends email replies when the user’s calendar slot is already booked, ensuring professional communication.
🧩 Workflow Architecture:-

                                                              [Gmail Trigger]
                                                                    ↓
                                                               [Edit Fields]
                                                                    ↓
                                                                   [AI Agent]
                                                                   ↙    ↓     ↘
                                                              [Check Calendar] [Create Event] [Send Gmail Reply]
                                                                      ↓             ↓              ↓
                                                                 (Decision)    (Add to Calendar)  (Inform Sender)
                                                                 

💡 How It Works

1. Gmail Trigger detects a new message in your inbox.
2. The Edit Fields node extracts From, Subject, and Snippet data.
3. The AI Agent uses the Google Gemini Chat Model to analyze the email text.
4. It determines whether the email is about an event or meeting.
5. Extracts event details (title, date, time, and duration).
6. The agent uses Google Calendar Tools to check if you are available.
7. If you are free → it creates an event automatically.
8. If you are busy → it uses Gmail Tool to send a reply explaining your unavailability and suggests another time.

🧰 Tech Stack

n8n — Visual workflow automation tool
Google Gemini (PaLM API) — AI reasoning and language understanding
LangChain Agent — AI workflow logic and tool orchestration
Google Calendar API — Event creation and availability check
Gmail API — Email retrieval and automated responses
Timezone: Asia/Kolkata

🚀 Features

✅ Intelligent email parsing and intent recognition
✅ Auto-scheduling directly in Google Calendar
✅ Smart busy-time detection
✅ Automated email responses using AI
✅ Fully modular n8n design — easy to expand or modify

🔐 Setup Instructions

Clone the repository

git clone https://github.com/<your-username>/AI-Email-Scheduler.git
cd AI-Email-Scheduler

Import the workflow into n8n

Open n8n → Workflows → Import from File → select My workflow.json.

Add your credentials

Gmail OAuth2

Google Calendar OAuth2

Google Gemini (PaLM) API key

Activate the workflow

Enable the Gmail Trigger and let n8n run continuously.

📧 Example Scenario

Incoming email:

“Hi, can we meet tomorrow at 3 PM to discuss the project update?”

AI response:

Checks your Google Calendar → finds that 3 PM is free

Creates a calendar event titled Project Update Meeting

Sends a confirmation reply (if configured)

If 3 PM is busy, the agent automatically replies:

“I’m unavailable at 3 PM tomorrow, but how about 4:30 PM instead?”

🧭 Future Enhancements

> Add support for recurring meetings and reminders

> Integrate with Microsoft Outlook and Apple Calendar

> Add natural-language confirmations (“Yes, schedule it”)

> Include voice assistant triggers
