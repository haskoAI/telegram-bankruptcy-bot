# GitHub Setup

This file explains how to publish the bot to GitHub safely.

## Before You Push

Make sure these files are **not** committed:

- `.env`
- `node_modules/`
- `*.log`

The project already ignores them in `.gitignore`.

## Important

Secrets were used during local setup:

- Telegram bot token
- OpenAI API key
- Google service account private key

Before making the repository public, rotate these secrets and put the new values only into local `.env`.

## Option A: GitHub Desktop

If Git is not installed in terminal, the easiest way is GitHub Desktop.

1. Install GitHub Desktop.
2. Click `Add` -> `Add Existing Repository`.
3. If the folder is not a repository yet, choose `Create a Repository`.
4. Select the folder:

```text
C:\Users\hasan\OneDrive\Рабочий стол\telegram-bankruptcy-bot
```

5. Repository name:

```text
telegram-bankruptcy-bot
```

6. Add description, for example:

```text
Telegram AI bot for bankruptcy FAQ, lead qualification, and Google Sheets capture
```

7. Publish repository to GitHub.
8. Choose `Private` unless you are sure secrets were rotated.

## Option B: Command Line

Install Git first:

```powershell
winget install --id Git.Git -e --source winget
```

Then run:

```powershell
cd "C:\Users\hasan\OneDrive\Рабочий стол\telegram-bankruptcy-bot"
git init
git add .
git commit -m "Initial commit: Telegram bankruptcy bot"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/telegram-bankruptcy-bot.git
git push -u origin main
```

## Recommended Repository Description

```text
Telegram AI bot for bankruptcy lead capture, FAQ support, and Google Sheets integration
```

## Recommended Topics

```text
telegram-bot
openai
rag
google-sheets
lead-generation
nodejs
telegraf
legal-tech
```

## Recommended Files in the Repo

- `README.md`
- `GITHUB_SETUP.md`
- `.env.example`
- `package.json`
- `package-lock.json`
- `src/`

## Suggested First Commit Message

```text
Initial commit: Telegram bankruptcy bot with RAG and Google Sheets
```

## If You Want a Public Repository

Do this first:

1. Rotate all exposed secrets.
2. Confirm `.env` is not tracked.
3. Make sure no keys are hardcoded in source files.
4. Only then publish as public.
