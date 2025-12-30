# AI-Powered Smart Gmail Assistant with Telegram Approval

An intelligent automation workflow built with n8n that streamlines email management. It uses Google Gemini AI to summarize incoming emails, logs details to Google Sheets, sends interactive notifications to Telegram, and drafts professional replies upon user approval.

![Workflow Overview Screenshot](https://github.com/Eshtiaque/Gmail-Automation/blob/main/Images/Screenshot%202025-12-23%20034346.png)

---

## 🚀 Overview

This workflow is designed to save time and improve email productivity. Instead of checking every email manually, the system analyzes incoming messages, determines their urgency, and presents a summary via Telegram. With a single tap, you can authorize the AI to draft a context-aware reply directly in your Gmail draft folder.

## ✨ Key Features

 📥 Automated Email Monitoring Instantly triggers on new emails received in Gmail.
 🧠 AI Analysis (Gemini) Uses Google Gemini (e.g., gemini-1.5-flash) to generate concise summaries and detect the urgency level of the email.
 📊 Google Sheets Logging Automatically saves email details (Date, Sender, Subject, Summary, Urgency) into a Google Sheet for record-keeping.
 📱 Interactive Telegram Notifications Sends a summary alert to your Telegram bot with a ✅ Yes button for action.
 ⏸️ Human-in-the-Loop Approval The workflow pauses execution using a `Wait` node until you click the approval button on Telegram.
 ✍️ AI Reply Drafting Once approved, AI generates a polite and professional reply based on the original email's context.
 📝 Draft Creation The generated reply is automatically saved as a draft in Gmail, ready for final review before sending.

## 🛠️ Workflow Steps (How it Works)

1.  Gmail Trigger Watches for new emails.
2.  AI Summary Gemini AI analyzes the email body to create a summary and gauge urgency.
3.  Log to Sheets Essential data is appended to a designated Google Sheet.
4.  Notify Telegram A message with the summary and a Yes approval URL button is sent to the user.
5.  Wait for Approval The workflow pauses at a `Wait` node, listening for the webhook call from the Telegram button click.
6.  Generate Reply Upon clicking Yes, the workflow resumes, and another Gemini AI node generates a draft response.
7.  Create Draft The AI-generated response is saved into the Gmail drafts folder.

## ⚙️ Prerequisites & Tools Used

 n8n (Self-hosted or Cloud)
 Gmail Account (with OAuth2 credentials)
 Google Cloud Platform Account (for Gemini API Key and Sheets API)
 Telegram Bot (Create via BotFather to get the Token and Chat ID)
 Google Sheets
## Run process
```
npx ngrok http 5678
$env:WEBHOOK_URL="https://use here the ngrok link"; npx n8n start
```
---
Note This project uses n8n's `Wait` node with a webhook resume URL to handle asynchronous user approval via Telegram without losing execution context.
