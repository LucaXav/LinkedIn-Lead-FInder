# Setup

## 1) Accounts and services

You need:

- n8n
- Google Custom Search API key
- Google Programmable Search Engine ID (`cx`)
- OpenAI API access
- Google Sheets OAuth connected in n8n
- Gmail OAuth connected in n8n

## 2) Create the Google search engine

1. Go to Google Programmable Search Engine.
2. Create a new engine.
3. Add `linkedin.com` as the site to search.
4. Enable searching the entire web in the engine settings.
5. Copy the Search Engine ID (`cx`).

## 3) Enable the API

1. Open Google Cloud Console.
2. Enable the Custom Search API.
3. Create an API key.
4. Restrict the key appropriately before production use.

## 4) Connect n8n credentials

After import, reconnect these nodes manually in n8n:

- `AI Score + Enrich` → OpenAI credential
- `Upsert to Sheet` → Google Sheets OAuth credential
- `Send Email Digest` → Gmail OAuth credential

## 5) Prepare the sheet

Create a Google Sheet with a tab named `Leads` and these exact columns:

- First Name
- Last Name
- LinkedIn
- Role
- Company
- Role Category
- Location
- Relevance Score
- Reach Out Reason
- Query Group
- Is Duplicate
- Date Added
- Dedupe Key

## 6) Fill in the config node

Open `⚙️ CONFIGURE HERE` and update:

- `YOUR_EMAIL`
- `SEARCH_GOAL`
- `IDEAL_LEAD_DESCRIPTION`
- `SEARCH_QUERIES`
- `SHEET_URL`

## 7) Add secrets

This export uses environment-style placeholders in the HTTP request node:

- `GOOGLE_CUSTOM_SEARCH_API_KEY`
- `GOOGLE_CUSTOM_SEARCH_ENGINE_ID`

If you do not manage secrets via environment variables in n8n, replace those placeholders with your preferred credential approach.

## 8) Test safely

Before enabling the schedule:

1. Run the workflow manually.
2. Confirm the search node returns results.
3. Confirm the OpenAI node returns valid JSON arrays.
4. Confirm rows write into your sheet.
5. Confirm the Gmail digest renders correctly.
