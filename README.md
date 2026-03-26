# 🤖 AI Digest Bot

> A fully automated Telegram bot that delivers a daily morning digest of AI & tech news, summarized in Ukrainian using Groq AI — built with n8n, no code required.

![n8n](https://img.shields.io/badge/n8n-workflow-orange?logo=n8n)
![Groq](https://img.shields.io/badge/Groq-LLaMA_3.3_70b-blue)
![Telegram](https://img.shields.io/badge/Telegram-Bot-2CA5E0?logo=telegram)
![NewsAPI](https://img.shields.io/badge/NewsAPI-free_tier-green)

---

## 📋 Overview

Every morning at **9:00 AM**, this bot automatically:

1. Fetches the **5 latest AI & technology news articles** from NewsAPI
2. Sends each article to **Groq AI (LLaMA 3.3 70b)** for summarization
3. Delivers **concise Ukrainian-language summaries** directly to Telegram

---

## 🏗️ Workflow Architecture

```
Schedule Trigger (9:00 AM)
        ↓
HTTP Request → NewsAPI
(fetch 5 AI/tech articles)
        ↓
Code in JavaScript
(extract title, description, url, source)
        ↓
HTTP Request → Groq API
(summarize each article in Ukrainian)
        ↓
Telegram → Send Message
(deliver digest to chat)
```

---

## 🛠️ Tech Stack

| Tool | Purpose | Cost |
|------|---------|------|
| [n8n](https://n8n.io) | Workflow automation | Free (cloud) |
| [NewsAPI](https://newsapi.org) | News data source | Free (100 req/day) |
| [Groq API](https://groq.com) | AI summarization (LLaMA 3.3 70b) | Free tier |
| [Telegram Bot API](https://core.telegram.org/bots/api) | Message delivery | Free |

> 💡 **100% free stack** — no paid services required.

---

## ⚙️ Setup Instructions

### Prerequisites

- [n8n account](https://app.n8n.cloud) (free)
- [NewsAPI key](https://newsapi.org/register) (free)
- [Groq API key](https://console.groq.com) (free)
- Telegram Bot token from [@BotFather](https://t.me/BotFather)

### Step 1 — Import the Workflow

1. Download `digest-bot-workflow.json` from this repo
2. In n8n, go to **Workflows → Import from file**
3. Select the downloaded JSON file

### Step 2 — Configure Credentials

**NewsAPI** — in the HTTP Request node, replace `YOUR_NEWSAPI_KEY` in the URL:
```
https://newsapi.org/v2/everything?q=artificial+intelligence&language=en&sortBy=publishedAt&pageSize=5&apiKey=YOUR_NEWSAPI_KEY
```

**Groq API** — in HTTP Request1 node, update the Authorization header:
```
Bearer YOUR_GROQ_API_KEY
```

**Telegram** — set up a Telegram credential with your bot token, and set your Chat ID in the "Send a text message" node.

### Step 3 — Set Schedule

The Schedule Trigger is set to `0 0 9 * * *` (9:00 AM daily). Adjust the cron expression as needed.

### Step 4 — Publish

Click **Publish** in the top right corner to activate the workflow.

---

## 📱 Example Output

```
Компанія OpenAI оголосила про закриття свого додатку Sora для 
створення відео. Незважаючи на широкий резонанс після релізу, 
продукт не зміг утримати аудиторію та буде припинений у лютому 
2024 року.

---

Позов про авторські права проти Anthropic наближається до фінальної 
стадії — близько 100 000 авторів подали скарги щодо використання 
їхніх творів для навчання моделі Claude.
```

---

## 📁 Repository Structure

```
📦 ai-digest-bot
 ┣ 📄 README.md
 ┣ 📄 digest-bot-workflow.json   # n8n workflow export
```

---

## 🚀 Future Improvements

- [ ] Add more news topics (crypto, Ukraine, world news)
- [ ] Format digest with emoji and headers per topic
- [ ] Add inline keyboard buttons for "Read more"
- [ ] Support multiple users / group chats
- [ ] Weekly digest summary on Sundays

---

## 👤 Author

Built by **Emil** as part of an n8n automation portfolio.

---

## 📄 License

MIT — feel free to use, modify, and share.
