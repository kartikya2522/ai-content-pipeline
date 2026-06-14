# AI Content Pipeline: RSS to LinkedIn via Gemini

Automated AI content pipeline that fetches daily tech news, processes it through 4 Gemini AI agents, and delivers ready-to-publish LinkedIn posts via branded HTML email.

Built with n8n, Gemini 2.5 Flash Lite, Google Sheets, and Gmail. Runs fully automatically. Zero manual work. Zero cost.

---

## What it does

- Fetches fresh tech news daily from Marktechpost and TechCrunch RSS feeds
- Filters articles older than 7 days automatically
- Checks Google Sheets to skip already-processed articles (duplicate detection)
- Routes each article through 4 sequential Gemini AI agents
- Delivers output as a branded HTML email via Gmail
- Logs everything to Google Sheets with timestamp

---

## Architecture

```
Schedule Trigger (daily)
↓
RSS Feed 1 (Marktechpost) + RSS Feed 2 (TechCrunch)
↓
Merge → Filter by date → Sort → Limit
↓
Google Sheets (duplicate check) → If exists → Skip/Continue
↓
Agent 1: Content Analysis → Agent 2: Hashtags → Agent 3: LinkedIn Post → Agent 4: Image Prompt
↓
Gmail + Google Sheets Log + QR Code
```

---

## Stack

| Tool | Purpose |
|------|---------|
| n8n | Workflow automation |
| Gemini 2.5 Flash Lite | AI content generation |
| Google Sheets | Duplicate detection + logging |
| Gmail | Branded HTML email delivery |
| QR Server API | QR code generation |
| Marktechpost RSS | Tech news source 1 |
| TechCrunch RSS | Tech news source 2 |

---

## How to use

1. Import the JSON file into your n8n instance
2. Create a free Gemini API key at aistudio.google.com
3. Connect your Google account (Sheets + Gmail)
4. Update the Google Sheets URL to your own sheet
5. Set your email address in the Gmail node
6. Activate the workflow

---

## Output

Every run produces:
- A fully branded HTML email with the AI-generated LinkedIn post
- A new row logged to Google Sheets with date, source, headline, post content
- A QR code linking to the original article

---

## Cost

₹0. Every tool used has a free tier.
