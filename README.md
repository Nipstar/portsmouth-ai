# Andover AI Automation

Marketing website for **Andover AI Automation** — an AI automation agency based in Andover, Hampshire, UK, specialising in AI voice agents, chatbots, and workflow automation for local small businesses.

**Live site:** [aiautomationandover.co.uk](https://aiautomationandover.co.uk)

## Tech Stack

- Single `index.html` with inline CSS and JavaScript
- No build step, no frameworks, no dependencies
- Vanilla JS (IntersectionObserver for animations, accordion, contact form)
- Google Fonts (Sora + DM Sans)

## Features

- Dark premium theme with animated gradient orb hero
- Responsive design (320px to 1440px+)
- Interactive demo section with live chatbot and AI voice agent phone numbers
- Bolt Electrical case study strip
- Contact form (POST to n8n webhook)
- Cal.com embedded booking widget
- FAQ accordion (single-open-at-a-time)
- Animated stat counters
- Smooth scroll navigation

## SEO

- Semantic HTML5 with proper heading hierarchy
- JSON-LD structured data (LocalBusiness, Organization, FAQPage)
- Open Graph and Twitter Card meta tags
- `robots.txt` and `sitemap.xml` included
- Target keywords from Google Search Console data woven into copy

## Deployment

No build step required. Deploy the root directory to any static hosting provider:

- **GitHub Pages** — push to `main`, enable Pages in repo settings
- **Netlify** — connect the repo, publish directory: `/`
- **Vercel** — import the repo, framework preset: Other
- **Any web server** — upload `index.html`, `robots.txt`, `sitemap.xml`, and the `images/` folder

## Project Structure

```
.
├── index.html                  # Complete single-page website
├── robots.txt                  # Search engine crawl rules
├── sitemap.xml                 # Sitemap for search engines
├── images/
│   └── bolt.png                # Bolt Electrical case study screenshot
├── andover-ai-site-prompt_1.md # Original project specification
├── CLAUDE.md                   # Claude Code project guidance
└── README.md                   # This file
```

## Contact

**Email:** hello@antekautomation.com
