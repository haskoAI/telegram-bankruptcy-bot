# Telegram Bankruptcy Bot

AI-powered Telegram bot for first-touch lead qualification in the bankruptcy niche.

The bot:

- answers common questions with a lightweight RAG flow;
- collects lead data in Telegram chat;
- writes submissions to Google Sheets;
- can notify the manager in Telegram about new leads.

## Features

- Regular Telegram bot, not a Mini App
- Long polling with `telegraf`
- FAQ answers via OpenAI + local knowledge base
- Multi-step lead capture flow
- Google Sheets integration
- Optional admin notifications
- Local launch without hosting

## Stack

- Node.js
- Telegraf
- OpenAI API
- Google Sheets API

## Project Structure

- `src/index.js` - app entry point
- `src/bot.js` - Telegram bot logic and conversation flow
- `src/rag.js` - retrieval and answer generation
- `src/sheets.js` - Google Sheets integration
- `src/config.js` - environment config
- `src/prompts.js` - system and user prompts
- `src/knowledge-base.json` - FAQ knowledge base
- `.env.example` - safe environment template

## Environment Variables

Copy `.env.example` to `.env` and fill in the values:

```env
BOT_TOKEN=
OPENAI_API_KEY=
OPENAI_MODEL=gpt-4.1-mini
OPENAI_EMBEDDING_MODEL=text-embedding-3-small
GOOGLE_SHEETS_ID=
GOOGLE_SERVICE_ACCOUNT_EMAIL=
GOOGLE_PRIVATE_KEY=
GOOGLE_SHEET_NAME=Leads
CONSULTATION_MANAGER_NAME=Legal Team
ADMIN_CHAT_ID=
```

## Local Run

Install dependencies:

```powershell
npm install
```

Run the bot:

```powershell
npm start
```

The bot works while the local process is running. If the PC is выключен or sleeps, the bot stops responding.

## Google Sheets Setup

1. Create or open a Google Sheet.
2. Copy the spreadsheet ID from the URL.
3. Create a Google Cloud service account.
4. Enable Google Sheets API.
5. Generate a JSON key.
6. Put `client_email` and `private_key` into `.env`.
7. Share the spreadsheet with the service account email as `Editor`.

## What Gets Stored

Each new lead writes one row with:

- timestamp
- telegram user id
- username
- full name
- phone
- city
- debt amount
- overdue period
- official income
- property
- preferred contact time
- short case summary
- stage
- source

## Editing the Knowledge Base

Update `src/knowledge-base.json`.

Each item looks like this:

```json
{
  "id": "documents",
  "title": "What documents are needed",
  "tags": ["documents", "bankruptcy", "faq"],
  "content": "Text used by the bot in RAG answers."
}
```

Better knowledge base quality gives better answers.

## Safety

- Do not commit `.env`
- Rotate secrets if they were ever shared in chat or screenshots
- This bot gives general guidance, not final legal advice

## GitHub

Publishing instructions are in [GITHUB_SETUP.md](./GITHUB_SETUP.md).
