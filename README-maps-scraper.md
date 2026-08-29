# Google Maps Lead Scraper (n8n + SerpApi + AI Tagging)

An automated lead generation tool that turns "find me dentists in Lahore" into a clean, enriched spreadsheet of real business leads — in minutes, not hours.

Built for marketing agencies, web design freelancers, and sales teams who need to find and qualify local business leads without manual research.

## The Problem

Finding local business leads manually means hours of searching Google Maps, copy-pasting names/numbers/addresses into a spreadsheet, and still having no idea which leads are actually worth pursuing.

## The Solution

A client fills out one simple form — business type + city — and the system automatically:

1. **Scrapes Google Maps** for matching businesses (with pagination for 80+ results per search)
2. **Filters out low-quality leads** (minimum rating/review thresholds)
3. **Flags businesses with no website** — the single highest-value insight for any marketing or web design pitch
4. **Extracts contact emails** directly from each lead's website
5. **Delivers everything** to a live, shareable Google Sheet — ready to use immediately

## Architecture

```
Client Search Form (name + city input)
        │
        ▼
Generate Page Requests (pagination: 0, 20, 40, 60)
        │
        ▼
Search Google Maps (SerpApi)
        │
        ▼
Split Into Individual Leads
        │
        ▼
Clean Lead Data
        │
        ▼
Filter Low-Quality Leads (rating & review thresholds)
        │
        ▼
Tag Marketing Opportunity (no-website flag)
        │
        ▼
Has Website? ──┬─ Yes ─► Fetch Website Page ─► Extract Email
               └─ No  ─► Skip Email
        │
        ▼
Combine Results
        │
        ▼
Save to Google Sheet
```

## What You Get Per Lead

| Field | Description |
|---|---|
| business_name | Business name |
| phone | Phone number |
| address | Full address |
| rating | Google rating |
| reviews | Number of reviews |
| website | Website URL (if any) |
| type | Business category |
| opportunity_tag | "No Website — Marketing Opportunity" or "Has Website" |
| extracted_email | Contact email pulled from the business's website |
| search_query | Which search this lead came from |

## Tech Stack

- **n8n** — workflow orchestration
- **SerpApi** — Google Maps data (Places API alternative)
- **Google Sheets** — client-facing output, zero setup required
- **JavaScript (Code node)** — email extraction logic

## Who This Is For

- **Marketing agencies** — cut lead research time by ~90%
- **Web design freelancers** — target businesses that provably need a website
- **Sales & BD teams** — replace manual data entry with a 2-minute form submission

## About

Built by **CodeWithBisma** — freelance AI automation & full-stack developer specializing in AI chatbots, CRM systems, and workflow automation with n8n, Django, and Groq/OpenAI.

- GitHub: [Bismashoukat](https://github.com/Bismashoukat)
