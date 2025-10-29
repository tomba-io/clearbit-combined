# Tomba Clearbit-Combined Actor

[![Actor](https://img.shields.io/badge/Apify-Actor-blue)](https://apify.com/actors)
[![Tomba API](https://img.shields.io/badge/Tomba-API-green)](https://tomba.io)
[![Rate Limit](https://img.shields.io/badge/Rate%20Limit-150%2Fmin-orange)](https://tomba.io/api)

A powerful Apify Actor that enriches person and company information using the **Tomba Enrichment API**. Perfect for sales teams, marketers, and researchers who need comprehensive person and company data for lead generation, market research, and business intelligence.

## Key Features

- **Person & Company Enrichment**: Get detailed person and company information from email addresses
- **Comprehensive Data**: Organization details, location, social links, and contact info
- **Industry Classification**: Company industries and business categories
- **Technology Stack**: Technologies and tools used by companies
- **Contact Information**: Phone numbers and email addresses
- **Rate Limited**: Respects Tomba's 150 requests per minute limit
- **Bulk Processing**: Process multiple emails efficiently
- **Error Handling**: Robust error handling with detailed logging

## How it works

The Actor leverages Tomba's powerful Company Enrichment API to gather comprehensive business information:

### Process Flow

1. **Authentication**: Connects to Tomba API using your credentials
2. **Email Processing**: Accepts array of emails to enrich
3. **Data Validation**: Processes and validates company information
4. **Rate Limiting**: Automatically handles 150 requests/minute limit
5. **Data Storage**: Saves results to Apify dataset

### What You Get

For each email, you'll receive:

- **Company Details**: Name, description, founding year, size
- **Location Info**: Country, city, state, address, postal code
- **Contact Data**: Phone numbers and email addresses
- **Social Presence**: Twitter, Facebook, LinkedIn profiles
- **Business Intel**: Industries, revenue, technologies used
- **Source Tracking**: Data source and processing status

## Quick Start

### Prerequisites

1. **Tomba Account**: Sign up at [Tomba.io](https://app.tomba.io/api) to get your API credentials

### Getting Your API Keys

1. Visit [Tomba API Dashboard](https://app.tomba.io/api)
2. Copy your **API Key** (starts with `ta_`)
3. Copy your **Secret Key** (starts with `ts_`)

## Input Configuration

### Required Parameters

| Parameter        | Type     | Description                     |
| ---------------- | -------- | ------------------------------- |
| `tombaApiKey`    | `string` | Your Tomba API key (ta_xxxx)    |
| `tombaApiSecret` | `string` | Your Tomba secret key (ts_xxxx) |
| `emails`         | `array`  | Array of emails to enrich       |

### Optional Parameters

| Parameter    | Type     | Default | Description                         |
| ------------ | -------- | ------- | ----------------------------------- |
| `maxResults` | `number` | `50`    | Maximum number of results to return |

### Example Input

```json
{
    "tombaApiKey": "ta_xxxxxxxxxxxxxxxxxxxx",
    "tombaApiSecret": "ts_xxxxxxxxxxxxxxxxxxxx",
    "emails": ["user1@example.com", "user2@example.com", "user3@example.com"],
    "maxResults": 100
}
```

### Best Practices

- **Email Selection**: Use clean email addresses
- **Rate Limits**: The Actor automatically handles Tomba's 150 requests/minute limit
- **Batch Size**: Process 10-50 emails at a time for optimal performance

## Output Data Structure

The Actor returns comprehensive person and company enrichment data for each email:

### Example Output

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
        "linkedin": {
            "handle": "https://www.linkedin.com/in/****"
        },
        "twitter": {
            "handle": "https://twitter.com/**"
        },
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
            "emailAddresses": ["****@ipinfo.io", "**@ipinfo.io", "**@ipinfo.io"]
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
        "linkedin": {
            "handle": "ipinfo"
        },
        "twitter": {
            "handle": "ipinfoio"
        },
        "facebook": {
            "handle": "ipinfo.io/"
        },
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
    "domain": "**@ipinfo.io",
    "source": "tomba_enrichment"
}
```

### Data Structure Overview

The output contains three main sections:

#### 👤 Person Information

- **Personal Details**: Full name, location, gender, geographic data
- **Professional Info**: Employment details, job title, company, role level
- **Contact & Social**: Email verification, phone availability, LinkedIn/Twitter profiles
- **Data Quality**: Verification status and indexing timestamps

#### 🏢 Company Information

- **Business Basics**: Company name, legal name, domain, description
- **Company Classification**: SIC codes, NAICS codes, business categories
- **Location & Contact**: Full address, phone numbers, email addresses
- **Business Intelligence**: Founded year, company size, revenue estimates
- **Digital Presence**: Social media handles, domain registration info
- **Technology Stack**: Technologies used and their categories
- **Email Infrastructure**: Email provider and system details

#### 📊 Metadata

- **Source Tracking**: Data source identifier and processing information
- **Quality Indicators**: Verification dates, data freshness, and reliability scores

### Key Benefits

- **Dual Enrichment**: Get both person and company data in one API call
- **Comprehensive Coverage**: 50+ data points per enrichment
- **Real-time Verification**: Email validation and deliverability checks
- **Rich Context**: Employment relationships, social profiles, and business intel
- **Structured Data**: Consistent JSON format for easy integration

## Use Cases

- **Lead Generation**: Enrich prospect companies with detailed business information
- **Market Research**: Analyze company profiles and industry trends
- **Sales Intelligence**: Get comprehensive company data for better targeting
- **Competitive Analysis**: Research competitors and market positioning
- **Data Enrichment**: Enhance existing company databases with fresh information

## Resources & Documentation

### API Documentation

- [Tomba API Docs](https://tomba.io/api) - Complete API reference
- [Authentication Guide](https://app.tomba.io/api) - Get your API keys
- [Pricing & Limits](https://tomba.io/pricing) - Understand rate limits and costs

## FAQ

### General Questions

**Q: What is combined person and company enrichment?**
A: Combined enrichment takes an email address and returns comprehensive information about both the person and their company, providing complete contact and organizational intelligence in one request.

**Q: What's the advantage of combined enrichment over separate requests?**
A: Combined enrichment is more efficient, cost-effective, and provides correlated data ensuring person and company information is consistent and current.

**Q: What information do I get in combined enrichment?**
A: You get complete person details (name, role, social profiles), full company information (size, industry, technologies), and verified contact data all in one response.

### Technical Questions

**Q: How does pricing work for combined enrichment?**
A: Combined enrichment typically costs less than running separate person and company enrichment requests, while providing more comprehensive data.

**Q: Can I use any email address for combined enrichment?**
A: Business email addresses work best. Personal domains (gmail.com) may return limited company information since they're not associated with specific organizations.

**Q: How many emails can I enrich at once?**
A: You can process up to 1000 emails per run. Combined enrichment is perfect for comprehensive contact database enhancement.

### Business Applications

**Q: How does this help with account-based marketing?**
A: Combined enrichment provides complete account intelligence - understanding both the person you're targeting and their company context for highly personalized campaigns.

**Q: Is this useful for sales qualification?**
A: Absolutely! Get complete lead intelligence including personal background, role, company characteristics, and organizational context for better qualification and approach strategies.

**Q: Can I use this for comprehensive lead scoring?**
A: Yes! Combined data enables sophisticated lead scoring models using both individual characteristics (role, seniority) and company attributes (size, industry, technology stack).

## Keywords

Clearbit combined, person company enrichment, contact enrichment, lead enrichment, firmographic data, demographic data, business intelligence, contact data, prospect enrichment, people and company data, professional profiles, business data, complete enrichment, unified data, contact intelligence

## Support

If you need any help, have questions, or encounter any issues while using Tomba.io, please don't hesitate to reach out to our support team. You can contact us via:

- **Email**: support@tomba.io
- **Live chat**: Available on the Tomba.io website during business hours

## Contributing

We welcome contributions to improve this actor. Please feel free to submit issues, feature requests, or pull requests to help make this tool even better for the community.

## About Tomba

Founded in 2020, Tomba prides itself on being the most reliable, accurate, and in-depth source of email address data available anywhere. We process terabytes of data to produce our Email finder API.

![Tomba Logo](https://tomba.io/logo.png)
