# Rail Service Section — Design Spec

## Overview

Add a featured service card for **Rail** (transactional email delivery) to the Ataca landing page, matching the existing Connect card's structure and prominence. Also add a footer link.

## Context

- **Rail** is a transactional email delivery service at `rail.ataca.io`
- It offers SMTP relay and HTTP API integration, both secured with mTLS (client certificates)
- The Ataca landing page (`index.html`) is a single-page static site using Tailwind CSS via CDN
- Connect currently has a full-width featured card; other services sit in a 3-column grid below it
- GitHub Issue: #2

## Changes

Two modifications to `index.html`:

### 1. Rail Featured Card

**Placement:** Immediately after the Connect card, before the 3-column services grid.

**Structure** (mirrors Connect exactly):

- **Wrapper:** `bg-gray-800/50 rounded-2xl p-6 md:p-8 border border-gray-700` inside a `mb-12 md:mb-16` container
- **Header row:**
  - Icon: Envelope SVG inside `w-10 md:w-12 h-10 md:h-12 bg-emerald-600 rounded-lg`
  - Title: `rail` (lowercase) as an `<a>` linking to `https://rail.ataca.io` with `hover:text-emerald-400 transition`
  - Subtitle: "Transactional Email Delivery" in `text-gray-400 text-sm`
- **Description paragraph:** "Simple transactional email delivery for your services. Send notifications, alerts, and receipts — Rail handles the infrastructure with mTLS-secured delivery over SMTP and HTTP API."
- **Two-column grid** (`grid md:grid-cols-2 gap-6 md:gap-8`):
  - **Left — Integration Methods** (header in `text-emerald-400`):
    - SMTP Relay (emerald bullet)
    - HTTP API (emerald bullet)
  - **Right — Features** (header in `text-emerald-400`):
    - mTLS authentication (emerald bullet)
    - Transactional delivery (emerald bullet)
    - Live status dashboard (emerald bullet)
- **CTA button:** "Learn more" linking to `https://rail.ataca.io`, styled `bg-emerald-600 hover:bg-emerald-700 text-white text-sm font-medium rounded-lg`

**Accent color:** Emerald (`bg-emerald-600`, `text-emerald-400`, `hover:bg-emerald-700`) — distinguishes Rail from Connect's indigo while echoing the "Operational" green from rail.ataca.io.

### 2. Footer Link

Add "Rail" to the Services list in the footer, immediately after "Connect":

```html
<li><a href="https://rail.ataca.io" target="_blank" class="hover:text-white transition">Rail</a></li>
```

## Out of Scope

- No version number (v0.4) on the marketing site
- No live status indicator or `/stats` integration
- No code snippets or language-specific SDK mentions
- No new pages or routes — changes are confined to `index.html`

## Acceptance Criteria

1. Rail card renders correctly on mobile and desktop
2. Card structure matches Connect's pattern (icon, title link, subtitle, description, two-column grid, CTA)
3. Emerald accent color is consistent across icon, section headers, bullets, and CTA
4. Footer lists Rail after Connect
5. All links to `rail.ataca.io` open in new tab (`target="_blank"`)
6. No visual regression to existing sections
