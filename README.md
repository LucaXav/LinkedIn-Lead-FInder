# LinkedIn Lead Finder for n8n
<img width="1907" height="946" alt="image" src="https://github.com/user-attachments/assets/881c7652-dffb-409f-a7a9-d7c48d57874e" />

Generate targeted lead lists from Google Search results, score them with OpenAI, save them to Google Sheets, and send a daily email digest.

This repo packages an n8n workflow that:

- runs multiple Google Custom Search queries against public LinkedIn profile results
- filters out non-profile results and junk
- scores leads against a custom goal using GPT-4o-mini
- writes qualified leads into Google Sheets with deduplication
- emails a formatted digest of the top results

## What it does

- 10 custom Google searches across 3 result pages each
- roughly 100 real LinkedIn profiles per run after filtering
- AI relevance scoring from 0.0 to 1.0 against your target persona
- personalized reach-out reason for each lead
- Google Sheets upsert flow designed for repeat daily runs
- polished email digest of the top leads

## Stack

- n8n
- Google Custom Search API
- OpenAI
- Google Sheets
- Gmail

## Repo contents

- `workflow/linkedin-lead-finder.workflow.json` — importable n8n workflow
- `docs/setup.md` — setup and credential wiring
- `docs/customization.md` — how to adapt the workflow for any niche
- `docs/security.md` — what was sanitized before publishing
- `.env.example` — placeholder environment values for local reference

## Security and sanitization

This repository has been prepared for public sharing:

- personal email placeholders replaced with generic values
- OAuth credential bindings removed from the exported workflow
- API key and search engine ID moved to environment-style placeholders
- instance-specific metadata removed
- no personal contact details included

You must reconnect your own credentials inside n8n after import.

## Import into n8n

1. Open n8n.
2. Import `workflow/linkedin-lead-finder.workflow.json`.
3. Create or connect credentials for:
   - OpenAI
   - Google Sheets
   - Gmail
4. Update the Google Custom Search HTTP node with your credential strategy if you do not use environment variables.
5. Fill out the values in `⚙️ CONFIGURE HERE`.
6. Create a Google Sheet with the required columns listed in `docs/setup.md`.
7. Run the workflow manually once, then enable the schedule if desired.

## Required config fields

In the `⚙️ CONFIGURE HERE` node, set:

- `YOUR_EMAIL`
- `SEARCH_GOAL`
- `IDEAL_LEAD_DESCRIPTION`
- `SEARCH_QUERIES`
- `SHEET_URL`

## Example use cases

- early-career VC professionals in San Francisco
- startup CTO lead lists
- open-to-work engineers in a specific city
- community builders in a niche ecosystem

## Notes

- Google Custom Search free tier gives 100 queries per day.
- This workflow uses 30 queries per run by default.
- The workflow relies on public Google search results rather than scraping LinkedIn directly.

## License

MIT
