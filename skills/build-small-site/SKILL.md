---
name: build-small-site
description: Build a small, clean brochure-style business website (8-15 pages) using Astro 5, Tailwind CSS v4, and Cloudflare Pages. Generates a homepage, about, contact, and one page per service, with optional area pages for multi-location businesses. No service x area combo grid, no blog required. For an 80-100+ page programmatic-SEO site with a full service x area combo grid, use the build-local-site skill instead.
triggers:
  - build a simple business website
  - build a small website for my
  - build a small business website
  - brochure site
  - simple business site
  - landing page for my business
  - small business website builder
  - build a website for my small business
  - I just need a simple website
  - build a basic website for my
  - small brochure website
---

# Small Business Website Builder

This skill builds a small, clean website for a local business that doesn't need (or want) an 80-100+ page programmatic-SEO build. The output is a production-ready Astro 5 static site with roughly 8-15 pages: a homepage, about, contact, one page per service, and (only for businesses that genuinely serve multiple distinct named areas) a small number of area pages.

This is a second, independent skill alongside `build-local-site` in this plugin, not a smaller mode of it. It uses its own templates and its own agent, and does not generate a service x area combination grid. If you need that kind of large-scale local-search coverage, use `build-local-site` instead.

## What It Builds

- Homepage with hero, services grid, simple "how it works" section, testimonials, and structured data
- About page with business story and optional owner spotlight
- Contact page with form and business hours
- Individual service pages (one per service offered)
- Services directory page
- Optional: individual area pages and an areas directory, only if the business serves multiple distinct named locations (0-3 areas)
- XML sitemap, robots.txt, and canonical URLs
- JSON-LD schema markup on every page (LocalBusiness/appropriate industry type, Service, FAQPage, BreadcrumbList, AggregateRating when real reviews exist)
- Internal linking between services, about, and contact

## What You Need to Provide

**Required:**
- Business name
- Industry/business type
- Phone number
- Services offered (3-8 recommended)
- Business address (city, state, zip), or just a city/service radius for a service-area business
- Year established

**Optional (but recommended):**
- Owner name
- License or certification number (skip for businesses where this doesn't apply)
- Business website URL (for research and canonical URLs)
- Email address
- Business hours
- Whether the business serves 1-3 distinct named areas beyond its home city
- Price ranges per service
- Customer reviews (real ones only, never fabricated)
- Google Analytics ID (GA4)
- Gemini API key (for AI-generated service images)
- Cloudflare account (for free deployment)

## Quick Start

Just tell the agent about your business:

> "Build a simple website for my dog grooming business, Pawsitively Groomed, in Round Rock TX. Services: full grooming, nail trims, de-shedding, and puppy's first groom. I don't need dozens of pages, just something clean."

The agent will guide you through an interactive process to collect all necessary details, then generate the complete site.

## Tech Stack

| Tool | Purpose |
|------|---------|
| Astro 5 | Static site generator with file-based routing |
| Tailwind CSS v4 | CSS-native config via @theme, @utility, @layer |
| Cloudflare Pages | Free hosting with global CDN |
| astro-icon + Lucide | Optimized SVG icons |
| @astrojs/sitemap | Auto-generated XML sitemap |

## Page Count Formula

```
Total = 3 fixed pages (home, about, contact) + 1 services index
      + S service pages + A area pages (0-3) + 1 areas index (only if A > 0)
```

Example: 6 services, no named areas (single-location business) = 3 + 1 + 6 = **10 pages**.
Example: 6 services, 2 named areas = 3 + 1 + 6 + 1 + 2 = **13 pages**.

## When to use `build-local-site` instead

If the business wants to rank for many "[service] in [city]" long-tail searches across 8-15+ service areas, or needs a full service x area combination grid, use the `build-local-site` skill instead. This skill is intentionally capped at a brochure-sized site.

## Full Reference

The agent (`agents/small-site-builder.md`) contains the complete phase-by-phase build process: research, data gathering, scaffolding, data file generation, optional images, and build/deploy. The agent should read `${CLAUDE_PLUGIN_ROOT}/templates-small/src/data/*.template` files directly before generating each data file, they are the authoritative source for exact field shapes.
