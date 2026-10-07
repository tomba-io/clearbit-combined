# Tomba Clearbit Combined Enrichment

[![Price](https://img.shields.io/badge/Price-%243.12%20per%201K%20emails-brightgreen)](#pricing)
[![No signup](https://img.shields.io/badge/Tomba%20account-not%20needed-blue)](#quick-start)
[![No rate limit](https://img.shields.io/badge/Rate%20limit-none-brightgreen)](#built-for-big-lists)

**One email in, the person and their company out.** Paste a list of email addresses and get each person's name, job title, location and social profiles, plus a full profile of the company they work for: industry, size, revenue range, address, tech stack and more. All in one row, ready to export.

No Tomba account. No API key. No subscription. **You pay $0.00312 per email, and only when we find data.**

## Why teams choose this Actor

- **Start in 30 seconds**: Open the Actor, paste your emails, click Start. Nothing to sign up for
- **Two enrichments for the price of one**: Person and company data come back together for a single $0.00312 charge
- **Pay only for results**: Emails with no data, errors and invalid inputs are free
- **$3.12 per 1,000 emails**: No monthly plan, no credits that expire, no minimum spend
- **Built for big lists**: No rate limit. Hundreds of emails run in parallel
- **Never pay twice**: Emails you looked up in the last 24 hours come back from cache for free
- **Clean input, clean output**: Emails are trimmed and lowercased, and duplicates are removed automatically
- **Export anywhere**: Download as CSV, Excel or JSON, or send results straight to your CRM with Apify integrations

## What you can do with it

| Goal                      | How person + company data helps                                                    |
| ------------------------- | ---------------------------------------------------------------------------------- |
| **Qualify inbound leads** | See who signed up and how big their company is, then prioritize the best accounts  |
| **Score leads**           | Combine role and seniority with company size, revenue and industry in one model    |
| **Enrich your CRM**       | Fill contact and account records at the same time from just an email address       |
| **Personalize outreach**  | Reference the person's role and what their company does, where it is and its tools |
| **Account-based selling** | Map contacts to accounts and build segmented lists by industry, size and country   |
| **Route leads faster**    | Send each lead to the right rep based on company size, industry or location        |

## Quick start

1. Click **Try for free**
2. Paste your emails into **Emails to Enrich** (for example `john@stripe.com`)
3. Click **Start**, then download your results as CSV, Excel or JSON

That's it. No Tomba account or API key is needed.

## Input

| Field            | Required | Default | Description                                                   |
| ---------------- | -------- | ------- | ------------------------------------------------------------- |
| `emails`         | Yes      |         | Email addresses to enrich. Case and extra spaces don't matter |
| `maxResults`     | No       | `50`    | Maximum number of emails to enrich (up to 1,000)              |
| `maxConcurrency` | No       | `10`    | How many emails to process at the same time (1–50)            |
| `maxRetries`     | No       | `3`     | How many times to retry a temporary failure (0–10)            |
| `useCache`       | No       | `true`  | Reuse results from your previous runs for free                |
| `cacheTtlHours`  | No       | `24`    | How long cached results stay valid (`0` turns the cache off)  |

```json
{
    "emails": ["john@stripe.com", "info@tomba.io"],
    "maxResults": 500
}
```

## Output

You get one row per email, with a `person` and a `company` section:

```json
{
    "person": {
        "name": {
            "fullName": "xxx xxx",
            "givenName": "xxx",
            "familyName": "xx"
        },
        "email": "****@ipinfo.io",
        "location": "US",
        "gender": "male",
        "geo": {
            "city": null,
            "state": null,
            "country": "United States",
            "countryCode": "US"
        },
        "employment": {
            "domain": "ipinfo.io",
            "name": "IPInfo",
            "title": "founder",
            "role": "executive"
        },
        "linkedin": { "handle": "https://www.linkedin.com/in/****" },
        "twitter": { "handle": "https://twitter.com/**" },
        "verification": {
            "date": "2025-08-13T00:00:00+02:00",
            "status": "valid"
        },
        "phone": true
    },
    "company": {
        "name": "IPInfo",
        "legalName": "IPInfo",
        "domain": "ipinfo.io",
        "site": {
            "phoneNumbers": null,
            "emailAddresses": ["****@ipinfo.io", "**@ipinfo.io"]
        },
        "category": {
            "sicCode": "73",
            "sic4Codes": ["7371", "7373", "7379"],
            "naicsCode": "51"
        },
        "tags": ["ip data", "ip address api", "cybersecurity", "saas"],
        "description": "with ipinfo, you can pinpoint your users' locations, customize their experiences, prevent fraud, ensure compliance, and so much more.",
        "foundedYear": "2013",
        "location": "US",
        "geo": {
            "streetAddress": "5616 49th ave sw",
            "city": "washington",
            "state": "washington",
            "postalCode": "1120",
            "country": "United States",
            "countryCode": "US"
        },
        "linkedin": { "handle": "ipinfo" },
        "twitter": { "handle": "ipinfoio" },
        "facebook": { "handle": "ipinfo.io/" },
        "whois": {
            "registrar_name": "101domain grs limited",
            "created_date": "2013-04-23T19:30:12+02:00",
            "referral_url": "http://101domain.com"
        },
        "emailProvider": "Google Workspace",
        "type": "privately held",
        "metrics": {
            "trafficRank": "1454",
            "employees": "1-10",
            "annualRevenue": "$1M-$10M",
            "estimatedAnnualRevenue": "$1M-$10M"
        },
        "tech": ["webpack", "Next.js", "React", "Google Cloud"],
        "techCategories": ["JavaScript Libraries", "Web Frameworks", "JavaScript Frameworks", "CDN"]
    },
    "email": "****@ipinfo.io",
    "source": "tomba_enrichment",
    "charged": true,
    "cached": false
}
```

| Field                                                     | Description                                                      |
| --------------------------------------------------------- | ---------------------------------------------------------------- |
| `email`                                                   | The email you submitted (lowercased)                             |
| `person.name`                                             | Full name, first name and last name                              |
| `person.employment`                                       | Company name and domain, job title and role                      |
| `person.location`, `person.geo`                           | Country code, city, state and country                            |
| `person.gender`                                           | Gender, when known                                               |
| `person.linkedin`, `person.twitter`                       | The person's social profile links                                |
| `person.verification`                                     | Email verification status (e.g. `valid`) and when it was checked |
| `person.phone`                                            | `true` if a phone number is known for this person                |
| `company.name`, `company.legalName`, `company.domain`     | Company name, legal name and website                             |
| `company.description`, `company.tags`                     | What the company does                                            |
| `company.category`                                        | Industry codes: SIC and NAICS                                    |
| `company.foundedYear`, `company.type`                     | Year founded and company type, e.g. privately held               |
| `company.location`, `company.geo`                         | Country code and full address                                    |
| `company.metrics`                                         | Employee range, revenue range and website traffic rank           |
| `company.site`                                            | Phone numbers and email addresses published on the website       |
| `company.linkedin`, `company.twitter`, `company.facebook` | Company social profiles                                          |
| `company.tech`, `company.techCategories`                  | Technologies detected on the website and their categories        |
| `company.emailProvider`, `company.whois`                  | Email provider and domain registration details                   |
| `source`                                                  | Always `tomba_enrichment`                                        |
| `charged`                                                 | `true` if this lookup was billed                                 |
| `cached`                                                  | `true` if this result came from the cache (free)                 |
| `error`                                                   | Why no data was returned, if applicable                          |

Fields are filled when the information is publicly available, so some rows have fewer of them. Emails with no data still get a row with `email`, `charged: false` and an `error`, so nothing silently disappears from your list.

The dataset has four ready-made views: **Overview**, **Person Details**, **Company Details** and **Contact Information**.

## Pricing

**$0.00312 per email ($3.12 per 1,000).** No subscription and no Tomba account needed. Person and company data are included in the same charge.

You are only charged when Tomba returns a usable answer:

| What happens                                    | Charged |
| ----------------------------------------------- | ------- |
| Person or company data found for the email      | Yes     |
| No data found for the email                     | No      |
| Invalid email or any other error                | No      |
| Temporary failure (it is retried automatically) | No      |
| Result served from the cache                    | No      |

Every row shows `charged` and `cached`, so you always know what you paid for. To cap your spend, set **Maximum cost per run** in the run options: the Actor stops cleanly when the limit is reached.

## Built for big lists

- **No rate limit**: up to 50 emails are processed at the same time
- **Automatic retries**: temporary failures are retried for you, and never billed
- **Resumable**: if a run is interrupted, it continues where it stopped without charging you again
- **Cache**: repeat lookups within 24 hours are free

## Integrations

Run it on a schedule, call it from the Apify API, or connect it to Zapier, Make, Google Sheets, HubSpot, Slack and hundreds of other apps with [Apify integrations](https://docs.apify.com/platform/integrations). Webhooks let you trigger your own workflow as soon as a run finishes.

## FAQ

**Do I need a Tomba account or API key?**
No. Everything is built in. You only pay the per-email price on Apify.

**How much does it cost?**
$0.00312 per email with results ($3.12 per 1,000), for both the person and the company. Emails with no results, errors and cached lookups are free.

**How many emails can I enrich in one run?**
Up to 1,000 per run, processed in parallel. There is no rate limit.

**Which emails work best?**
Business emails like `jane@company.com`. Personal addresses (Gmail, Outlook) aren't tied to a company, so they return little or no company data.

**Why are some fields empty?**
We only return what is publicly known. Some rows have a complete person and company profile, others only part of it.

**Should I use this or the separate person and company Actors?**
If you start from email addresses and want both, this Actor gives you everything in one row for one charge. If you only have domains, use the Tomba Clearbit Company Actor.

**What if my run is interrupted?**
It picks up where it stopped. Emails already processed are not charged again.

**How do I limit what I spend?**
Set **Maximum cost per run** before you start. The Actor stops as soon as the limit is reached.

## Support

Questions or feedback? We're happy to help:

- **Email**: support@tomba.io
- **Live chat**: on [tomba.io](https://tomba.io) during business hours
- **Issues**: use the **Issues** tab on this Actor's page

## About Tomba

Founded in 2020, [Tomba](https://tomba.io) is a B2B data platform for finding, verifying and enriching business contacts. Our Email Finder, Domain Search and Email Verifier help sales and marketing teams reach the right people.

![Tomba Logo](https://tomba.io/logo.png)
