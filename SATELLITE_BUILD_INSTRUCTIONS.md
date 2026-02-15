# Satellite Site Build Instructions

These instructions document the complete process used to transform the Andover AI site into the Portsmouth satellite site. Follow this same process for Southampton, Basingstoke, Winchester, and Farnborough.

## Prerequisites

1. Copy the base Andover site codebase to a new folder named after the domain (e.g., `aiautomationsouthampton.co.uk`)
2. Have the variable set ready for the target city (from the Hampshire Domination plan)

## Step-by-Step Transformation Process

### 1. Global Text Replacements

**DO NOT use simple find-replace** - these need manual verification to avoid breaking links to Antek Automation.

Replace these ONLY in content areas (not in Antek Automation references):
- Brand name throughout
- Domain in all meta tags, canonical URLs, sitemaps
- Email address in contact details and forms
- City/region references

**Keep unchanged:**
- References to "Antek Automation" (parent company)
- Links to antekautomation.com
- Links to retellai.com/partner/antek-automation
- Shared phone number: 0333 038 9960

### 2. SEO Metadata Updates

#### Head Section (`<head>`)
Update in `index.html`:

**IMPORTANT:** Keep title under 60 chars, descriptions under 155 chars for optimal SEO.

```html
<title>[BRAND_NAME] | Voice Agents & Automation</title>
<meta name="description" content="[CITY] AI agency. Voice agents, chatbots & automation for local businesses. 24/7 call handling. Certified Retell AI Partner. Book free call.">
<link rel="canonical" href="https://[DOMAIN]/">

<!-- Add Geo Tags -->
<meta name="geo.region" content="[GEO_REGION_CODE]">
<meta name="geo.placename" content="[CITY]">
<meta name="geo.position" content="[GEO_LAT];[GEO_LNG]">
<meta name="ICBM" content="[GEO_LAT], [GEO_LNG]">
```

Update Open Graph (OG title ~55 chars, OG description ~130 chars):
```html
<meta property="og:title" content="[BRAND_NAME] | Voice Agents & Automation">
<meta property="og:description" content="[CITY] AI agency. Voice agents, chatbots & automation for local businesses. 24/7 call handling. Certified Retell AI Partner.">
<meta property="og:url" content="https://[DOMAIN]/">
<meta property="og:locale" content="en_GB">
<meta property="og:site_name" content="[BRAND_NAME]">
```

Update Twitter Card (~55 chars title, ~105 chars description):
```html
<meta name="twitter:title" content="[BRAND_NAME] | Voice Agents & Automation">
<meta name="twitter:description" content="[CITY] AI agency. Voice agents, chatbots & automation for local businesses. 24/7 call handling.">
```

### 3. JSON-LD Structured Data

#### LocalBusiness Schema
```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "[BRAND_NAME]",
  "description": "AI automation agency specialising in AI voice agents, chatbots, and workflow automation for small businesses in [CITY], Hampshire, and the South of England.",
  "url": "https://[DOMAIN]",
  "telephone": "+44-333-038-9960",
  "email": "[EMAIL]",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "[CITY]",
    "addressRegion": "Hampshire",
    "addressCountry": "GB"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": [GEO_LAT],
    "longitude": [GEO_LNG]
  },
  "parentOrganization": {
    "@type": "Organization",
    "name": "Antek Automation",
    "url": "https://antekautomation.com"
  },
  "areaServed": ["[CITY]", "[NEARBY_TOWNS]", "Hampshire", "South of England"],
  "serviceType": ["AI Voice Agents", "AI Chatbots", "Workflow Automation", "Business Process Automation", "AI Receptionist", "Automated Phone Answering"],
  "priceRange": "££"
}
```

#### Organization Schema
```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "[BRAND_NAME]",
  "url": "https://[DOMAIN]",
  "logo": "https://[DOMAIN]/logo.svg",
  "sameAs": [
    "https://antekautomation.com",
    "https://retellai.com/partner/antek-automation"
  ]
}
```

#### FAQPage Schema
Update all 10 FAQ questions with city-specific versions (see FAQ section below).

### 4. Navigation Logo

Update the nav logo text:
```html
<span>[CITY_SHORT] <span class="nav__logo-accent">AI</span></span>
```
Example: `Portsmouth AI`, `Southampton AI`, `Basingstoke AI`

### 5. Hero Section - MUST BE UNIQUE

**Badge:**
```html
[BRAND_NAME] — [CITY] & Hampshire
```

**H1:**
```html
AI Voice Agents, Chatbots & Automation for <span class="gradient-text">[CITY] Businesses</span>
```

**Subheadline (CRITICAL - Make Unique):**
Write a completely new paragraph using:
- Specific local landmarks from LOCAL_LANDMARKS variable
- Reference to BUSINESS_VIBE
- Different wording/structure than other satellites

Portsmouth example:
> "Serving Portsmouth's vibrant business community from Gunwharf to Southsea. AI-powered phone systems that never miss a customer, intelligent chatbots that work while you sleep, and smart automation that frees your team to focus on what matters most."

**Trust Bar:**
```html
Powered by Antek Automation — Certified Retell AI Partner — Serving [CITY], [NEARBY_TOWNS]
```

### 6. Pain Points Section - MUST BE UNIQUE

**Subtitle:**
Rewrite using BUSINESS_VIBE context. Different structure than other sites.

Portsmouth example:
> "Whether you're a tradesperson working across Portsea Island, a professional practice in Southsea, or running a busy hospitality business near the waterfront — these challenges drain your revenue and steal your time."

**Card Descriptions:**
Rewrite all 3 card descriptions with:
- Different wording than base site
- City-specific examples (neighborhoods, local context)
- Same themes (missed calls, admin burden, 24/7 coverage)

Portsmouth examples:
- "When you're installing a boiler in Cosham or advising a client in Gunwharf..."
- "Booking confirmations, quote follow-ups, payment reminders..."
- "A full-time receptionist costs £25k+ per year. Emergency calls at midnight, weekend enquiries..."

### 7. Services Section

**H2:**
```html
AI Services for [CITY] Businesses
```

**Subtitle (CRITICAL - Make Unique):**
Use specific local examples from different industries.

Portsmouth example:
> "From emergency plumbers serving the naval base to estate agents managing viewings in Southsea, solicitors in Old Portsmouth to HVAC engineers covering Havant — custom AI that fits your workflow, not the other way around."

**Service Cards:**
Keep bullet points the same (they're feature lists). These can be identical across sites.

### 8. Demo Section

Keep unchanged - Bolt Electrical is the universal case study.

### 9. How It Works

Keep unchanged - the 3-step process is universal.

### 10. Who We Help (Industries)

**H2:**
```html
Industries We Serve Across [CITY] & Hampshire
```

**Subtitle (Make Unique):**
Reference local business context from BUSINESS_VIBE.

Portsmouth example:
> "From naval city trades to Southsea hospitality and professional services across Portsea Island — we help Portsmouth businesses in every sector capture more leads and work smarter."

**Industry Cards:**
Keep the same 8 industry cards - these are universal.

### 11. Why Choose Us Section

**H2:**
```html
Why [CITY] Businesses Choose Us
```

**Subtitle:**
Make unique.

Portsmouth example:
> "We're not a faceless tech company. We're a dedicated AI automation partner helping Portsmouth businesses compete and grow with enterprise-grade technology."

**Local Card (CRITICAL - Completely Rewrite):**

Card title:
```html
[CITY]'s AI Automation Partner
```

Card description - Use BUSINESS_VIBE to write a unique paragraph:

Portsmouth example:
> "Portsmouth's dense small business community — from maritime trades servicing the naval heritage to bustling Southsea hospitality and Commercial Road professional firms — demands reliable, responsive service. We're backed by Antek Automation (Andover, Hampshire) and serve clients UK-wide, but our focus is right here in Portsmouth."

**Other Cards:**
Keep unchanged:
- 2+ Years in AI Automation
- Certified Retell AI Partner
- 24/7 AI That Never Calls in Sick

**Stats:**
Keep unchanged - they're universal metrics.

### 12. FAQ Section - MUST BE UNIQUE

**H2:**
```html
Frequently Asked Questions About AI Services in [CITY]
```

**Subtitle:**
Update with city name.

**All 10 FAQ Answers - REWRITE COMPLETELY**

This is critical to avoid duplicate content penalties. Every answer must:
- Use different wording/sentence structure than other satellites
- Include city-specific context where natural
- Cover the same information but expressed differently

**Question List (keep these questions):**
1. What is an AI voice agent?
2. How much does it cost?
3. How long does it take to set up?
4. Will it sound robotic?
5. Can it book appointments in my calendar?
6. Do I need technical knowledge?
7. What happens if the AI can't handle a call?
8. What AI services do you offer in [CITY]?
9. Is there an AI automation agency in [CITY]?
10. How much does AI automation cost for a [CITY] business?
11. Can AI answer phone calls for my [CITY] business?
12. Do you serve businesses near [LOCAL_LANDMARKS]?
13. How quickly can you set up AI for my [CITY] business?
14. Do you work with businesses outside [CITY]?
15. What industries do you work with in [CITY]?
16. How is [BRAND_NAME] connected to Antek Automation?

**Answer Writing Guidelines:**
- Start sentences differently (e.g., "Think of it as...", "Yes.", "Absolutely.", "No.", "Zero.", etc.)
- Use different examples and phrasing
- Vary sentence length and structure
- Include specific details (salary figures, timelines) that differ slightly
- Reference local areas naturally

Portsmouth answer examples (for inspiration):
- "Think of it as a virtual receptionist powered by artificial intelligence..."
- "Pricing depends on your requirements — call volume, features needed..."
- "Simple voice agents typically launch within a week..."
- "Zero. We handle the complete technical setup..."

### 13. Contact Form

Update hidden fields:
```html
<input type="hidden" name="source" value="[DOMAIN]">
<input type="hidden" name="city" value="[CITY]">
```

Form heading and description can stay the same.

### 14. GEO/AI Statement (Above Footer)

Replace the about-micro section content:

```html
<article class="about-micro">
  <div class="container">
    <p>[BRAND_NAME], part of Antek Automation, provides AI automation services to businesses in [CITY] and across Hampshire. As a Certified Retell AI Partner, we specialise in AI voice agents, chatbots, and workflow automation for small businesses. Our services include AI call handling, automated phone answering, AI customer service agents, and business process automation. We serve businesses in [CITY], [NEARBY_TOWNS], and throughout Hampshire.</p>
  </div>
</article>
```

Make the wording unique but include all:
- Brand name
- Connection to Antek Automation
- City and region
- Retell AI Partner status
- Services list
- Areas served

### 15. Footer Updates

**Brand Section:**
```html
<div class="footer__brand">
  <h4>[BRAND_NAME]</h4>
  <p>Serving [CITY], [NEARBY_TOWNS] & Hampshire<br>
  <a href="mailto:[EMAIL]">[EMAIL]</a> | <a href="tel:+443330389960">0333 038 9960</a></p>
</div>
```

**Partner Line:**
```html
Powered by <a href="https://antekautomation.com" target="_blank" rel="noopener noreferrer">Antek Automation</a> <span class="footer__partner-divider">|</span> <a href="https://retellai.com/partner/antek-automation" target="_blank" rel="noopener noreferrer">Certified Retell AI Partner</a> <span class="footer__partner-divider">|</span> Serving [CITY], [NEARBY_TOWNS] & Hampshire
```

**Cross-Links Section:**
Add this CSS (if not already present):
```css
.footer__satellite-links {
  margin-top: 20px;
  padding-top: 20px;
  border-top: 1px solid var(--border);
  text-align: center;
}
.footer__satellite-label {
  font-size: 0.75rem;
  color: var(--text-muted);
  margin-bottom: 8px;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}
.footer__satellite-list {
  font-size: 0.8rem;
}
.footer__satellite-list a {
  color: var(--text-secondary);
  text-decoration: none;
  transition: color 0.2s;
}
.footer__satellite-list a:hover {
  color: var(--accent-secondary);
}
.footer__satellite-divider {
  margin: 0 8px;
  opacity: 0.3;
}
```

Add this HTML (exclude current site from list):
```html
<div class="footer__satellite-links">
  <p class="footer__satellite-label">We Also Serve:</p>
  <div class="footer__satellite-list">
    <a href="https://aiserviceshampshire.co.uk" target="_blank" rel="noopener noreferrer">Hampshire</a>
    <span class="footer__satellite-divider">|</span>
    <a href="https://aiautomationandover.co.uk" target="_blank" rel="noopener noreferrer">Andover</a>
    <span class="footer__satellite-divider">|</span>
    <a href="https://aiautomationsouthampton.co.uk" target="_blank" rel="noopener noreferrer">Southampton</a>
    <span class="footer__satellite-divider">|</span>
    <!-- EXCLUDE THE CURRENT SITE -->
    <span class="footer__satellite-divider">|</span>
    <a href="https://aiautomationbasingstoke.co.uk" target="_blank" rel="noopener noreferrer">Basingstoke</a>
    <span class="footer__satellite-divider">|</span>
    <a href="https://aiserviceswinchester.co.uk" target="_blank" rel="noopener noreferrer">Winchester</a>
    <span class="footer__satellite-divider">|</span>
    <a href="https://aiautomationfarnborough.co.uk" target="_blank" rel="noopener noreferrer">Farnborough</a>
  </div>
</div>
```

**Copyright:**
```html
<p class="footer__copy">&copy; 2025 Antek Automation Ltd. Trading as [BRAND_NAME].</p>
```

### 16. Privacy Policy & Terms Pages

**privacy-policy.html:**
- Update title, meta description, canonical URL
- Replace all instances of brand name
- Replace email address

**terms.html:**
- Update title, meta description, canonical URL
- Replace all instances of brand name
- Replace email address

### 17. robots.txt

Already correct format (just verify domain):
```
User-agent: *
Allow: /
Sitemap: https://[DOMAIN]/sitemap.xml
```

### 18. sitemap.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://[DOMAIN]/</loc>
    <lastmod>2026-02-15</lastmod>
    <changefreq>monthly</changefreq>
    <priority>1.0</priority>
  </url>
  <url>
    <loc>https://[DOMAIN]/privacy-policy.html</loc>
    <lastmod>2026-02-15</lastmod>
    <changefreq>yearly</changefreq>
    <priority>0.3</priority>
  </url>
  <url>
    <loc>https://[DOMAIN]/terms.html</loc>
    <lastmod>2026-02-15</lastmod>
    <changefreq>yearly</changefreq>
    <priority>0.3</priority>
  </url>
</urlset>
```

Update date to current date when building.

## Content Uniqueness Checklist

**CRITICAL:** Google penalizes duplicate content. Every satellite must pass this test:

- [ ] Hero subheadline completely rewritten
- [ ] Pain points subtitle uses different sentence structure
- [ ] All 3 pain point card descriptions reworded with city examples
- [ ] Services subtitle has unique wording and local examples
- [ ] Industries subtitle references local business context
- [ ] Why Us local card completely rewritten with BUSINESS_VIBE
- [ ] All 10 FAQ answers use different wording/structure
- [ ] GEO/AI statement reworded (same info, different expression)
- [ ] Each paragraph reads like it was written fresh, not templated

**Test:** Read the Portsmouth and new site side-by-side. If any paragraph sounds identical or uses the same sentence patterns, rewrite it.

## Variable Reference Format

For each city, use variables from the Hampshire Domination plan:

```
CITY            = [City Name]
REGION          = Hampshire
COUNTRY_PART    = [Regional descriptor]
DOMAIN          = [Full domain]
BRAND_NAME      = [Brand name]
EMAIL           = hello@[domain]
GEO_LAT         = [Latitude]
GEO_LNG         = [Longitude]
GEO_REGION_CODE = [GB region code]
NEARBY_TOWNS    = [Comma-separated list]
LOCAL_LANDMARKS = [2-3 specific landmarks]
BUSINESS_VIBE   = [Paragraph describing local business context]
TARGET_KEYWORDS = [List of keywords to naturally include]
```

## Git & GitHub Process

After completing all edits:

```bash
# Navigate to directory
cd "/path/to/[domain]"

# Initialize git if needed
git init

# Stage all files
git add .

# Commit with descriptive message
git commit -m "Initial commit: [BRAND_NAME] satellite site

- [CITY]-specific branding and content
- Unique copy throughout to avoid duplicate content penalties
- SEO optimized for [CITY], [NEARBY_TOWNS]
- JSON-LD structured data with [CITY] coordinates
- Cross-links to Hampshire satellite network
- Contact form with [CITY] tracking

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"

# Add remote (create GitHub repo first)
git remote add origin https://github.com/[username]/[repo-name].git

# Rename branch and push
git branch -M main
git push -u origin main
```

## Quality Control Checklist

Before deploying:

- [ ] All [VARIABLES] replaced - zero brackets remaining
- [ ] Brand name used consistently throughout
- [ ] Domain in all meta tags, canonical, schema, sitemap
- [ ] Correct geo coordinates for the city
- [ ] Both phone numbers present (if applicable)
- [ ] All 10+ FAQ questions localized
- [ ] NEARBY_TOWNS mentioned at least 3 times
- [ ] LOCAL_LANDMARKS referenced naturally
- [ ] Antek Automation linked (trust bar, Why Us, footer)
- [ ] Retell AI linked (trust bar, Why Us, footer)
- [ ] Cross-links to other satellites in footer (excluding current site)
- [ ] Design identical to Portsmouth site
- [ ] UK English spelling throughout
- [ ] Mobile responsive
- [ ] CTAs solid green (#10b981) with black text
- [ ] JSON-LD validates
- [ ] No horizontal scroll on mobile
- [ ] Content reads uniquely (not templated)
- [ ] Committed to git with proper attribution
- [ ] Pushed to GitHub

## Build Order (from plan)

1. ✅ **Portsmouth** (Priority 2) - COMPLETE
2. **Southampton** (Priority 1) - 252k population
3. **Basingstoke** (Priority 3) - 113k population
4. **Winchester** (Priority 4) - 48k population
5. **Farnborough** (Priority 5) - 65k population

## Post-Launch Actions (Manual)

After each site goes live:

1. Submit to Google Search Console
2. Submit sitemap
3. Request indexing for homepage
4. Set up Google Business Profile (if possible)
5. Submit to Bing Webmaster Tools
6. Link from antekautomation.com
7. Share on social media
8. Monitor rankings in GSC
9. Check for keyword cannibalization between satellites

---

## Notes

- **Phone:** One shared 0333 number across all satellites (no need for unique numbers per site)
- **Email:** Unique per site, all forward to main Antek inbox (set up via Cloudflare email routing)
- **Lead tracking:** Hidden form fields capture site source and city
- **Design:** Must stay identical across all satellites (CSS/animations unchanged)
- **Antek references:** Always preserved - it's the parent company
- **Content uniqueness:** The single most important factor for SEO success

---

**Last Updated:** 2026-02-15 (Portsmouth build)
