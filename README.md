# Invoice Chaser AI

An automated invoice follow-up system that sends escalating, personalised reminder emails to clients with unpaid invoices — no manual work required. It reads invoice data from Google Sheets, uses Groq AI to write a context-aware email for each overdue invoice, and sends it automatically via Gmail on a daily schedule.

Built for freelancers, small agencies, consultants, and solo service businesses who don't have time to chase unpaid invoices by hand.

## What It Does

1. Every day at 9am, the workflow reads your Google Sheet of invoices.
2. It skips anything already marked Paid, and skips any invoice already contacted in the last 48 hours.
3. Based on how many days overdue an invoice is, it picks one of 4 tones: Friendly (1–7 days), Firm (8–14 days), Urgent (15–30 days), or Final Notice (30+ days).
4. Groq AI writes a unique, human-sounding email for that specific invoice and tone.
5. The email is sent from your Gmail account automatically.
6. The Sheet is updated with the new reminder count and contact date.
7. A daily summary is sent to you on Telegram.

## Prerequisites

- A Groq API key (free tier available at console.groq.com)
- An n8n account or self-hosted n8n instance
- A Gmail account (OAuth connection, not SMTP)
- A Telegram Bot token (created via @BotFather on Telegram)

## Setup Steps

1. Import the workflow: open n8n, click "Import from File," and select `workflow/invoice-chaser.json` from this repo.
2. Make a copy of the Google Sheets template (link below) into your own Google Drive.
3. In n8n, connect your Google Sheets account to the "Get row(s) in sheet" and "Update row" nodes, pointing them to your copied Sheet.
4. Connect your Gmail account via OAuth2 to the "Send a message" nodes.
5. Add your Groq API key to the HTTP Request nodes (as a header credential or in the node's authentication settings).
6. Create a Telegram bot via @BotFather, get your bot token, and connect it to the "Send a text message" node.
7. Open the "Schedule Trigger" node and confirm it's set to run daily at 9am in your timezone.
8. Click "Execute workflow" once to test manually with sample data.
9. Once you're happy with a test run, toggle the workflow to "Active"/"Published" so it runs automatically every day.

## Google Sheets Template

[Add your Sheet's shareable view-access link here]

## Demo Video

[Add your Loom link here]
