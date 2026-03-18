# SimpleNDT — Full SEO Audit Report
**Date:** 2026-03-18
**Site:** https://simplendt.com.br
**Audited against:** Local project files `/Simplendt V1/`
**Note:** The live domain still points to the old WordPress install. This audit covers the new static site that was pushed to GitHub and is pending Netlify DNS migration.

---

## SEO Health Score: 71 / 100

| Category              | Score  | Weight | Weighted |
|-----------------------|--------|--------|----------|
| Technical SEO         | 72/100 | 22%    | 15.8     |
| Content Quality       | 62/100 | 23%    | 14.3     |
| On-Page SEO           | 80/100 | 20%    | 16.0     |
| Schema / Structured Data | 74/100 | 10%  | 7.4      |
| Performance (CWV)     | 65/100 | 10%    | 6.5      |
| AI Search Readiness   | 58/100 | 10%    | 5.8      |
| Images                | 50/100 | 5%     | 2.5      |

---

## Executive Summary

The new static site is a solid SEO foundation: every page has canonical, meta description, keywords, Open Graph, hreflang and JSON-LD schema — all properly implemented. The bilingual structure (PT-BR / EN) is correct. The blog article is well-written with real depth and strong E-E-A-T signals.

**Top 5 critical issues:**
1. `og:image` is completely missing across all 25 pages — zero social sharing previews and no image signal for Google/AI
2. All service pages are far too thin (120–350 words vs. 800-word minimum) — Google's content quality threshold
3. No `llms.txt` — AI crawlers (ChatGPT, Perplexity) have no structured understanding of the site
4. Duplicate `</head>` tag in `blog/snt-tc-1a-guia-completo.html` — invalid HTML
5. `SimpleNDT_Design_v2.html` is a publicly accessible prototype file in the root — should be removed

**Top 5 quick wins:**
1. Add `og:image` to every page (one image, referenced everywhere — 30 min fix)
2. Add `<link rel="icon">` favicon (missing on all pages)
3. Add `BreadcrumbList` JSON-LD schema (breadcrumbs exist in HTML but have no structured data)
4. Fix duplicate `</head>` in blog article
5. Add `llms.txt` (20 min, big AI discoverability gain)

---

## 1. Technical SEO — 72/100

### ✅ PASS
- `robots.txt` — present, allows all crawlers, references sitemap correctly
- `sitemap.xml` — present, valid XML, covers all 26 pages (PT + EN), has `xhtml:link` hreflang entries
- Canonical tags — present and self-referencing on every page, absolute URLs ✅
- `lang` attribute — `html lang="pt-BR"` on all PT pages, `lang="en"` on all EN pages ✅
- Viewport meta — `width=device-width, initial-scale=1.0` on all pages ✅
- HTTPS canonical URLs — all canonicals point to `https://` ✅
- No `noindex` tags found anywhere ✅
- URL structure — clean hyphenated slugs, lowercase, descriptive ✅
- Heading hierarchy — single H1 per page, logical H2/H3 structure ✅
- Static HTML — no JavaScript rendering required, fully crawlable ✅
- Breadcrumbs — visible in HTML on all inner pages ✅

### ❌ FAIL / Issues Found

**[CRITICAL] Duplicate `</head>` tag — `blog/snt-tc-1a-guia-completo.html` lines 123–124**
Two consecutive `</head>` closing tags. Invalid HTML. Browsers recover but it signals malformed markup.

**[HIGH] `og:image` missing — ALL 25 pages**
Not a single page has `<meta property="og:image" ...>`. This means:
- WhatsApp/LinkedIn/Twitter share previews show no image
- Google may not include the site in image-enriched snippets
- AI Overviews that use og:image signals miss this page

**[HIGH] No `<link rel="icon">` anywhere**
No favicon defined. Browsers show blank tab icon; Google Search Console may flag it; trust signal missing.

**[HIGH] `SimpleNDT_Design_v2.html` in root**
An old design prototype is publicly accessible and potentially indexable (it's not in robots.txt disallow and not in sitemap). Should be deleted or at minimum have `<meta name="robots" content="noindex">`.

**[MEDIUM] PT navigation missing "Certificações" link**
The EN nav was fixed (Certifications was added), but the PT nav still only shows: Home / Serviços / Sobre / Blog / Contato — Certificações is absent. The `certificacoes.html` page also incorrectly marks "Sobre" as `class="active"`.

**[MEDIUM] Google Fonts loaded without `preconnect` or `font-display: swap`**
`index.html` loads Google Fonts (Outfit + Space Mono) with a plain `<link>` — no `rel="preconnect"` hints and no `font-display: swap` in the CSS. This causes render-blocking behavior and flash of invisible text (FOIT) on slow connections, hurting LCP.

**[MEDIUM] No `IndexNow` implementation**
Bing (and Yandex) use IndexNow for instant indexing. Simple to add via Netlify plugin or a manual key file. Especially relevant when pushing new blog posts.

**[MEDIUM] hreflang x-default consistency**
PT pages correctly set `x-default` to the PT URL. However, `blog/index.html` sets x-default to the blog index itself — technically fine, but consider pointing x-default to the site homepage for maximum clarity.

**[LOW] `priority` and `changefreq` in sitemap.xml**
Both tags are officially ignored by Google (documented since 2023). They add noise but cause no penalty. Can be safely stripped to simplify the sitemap.

**[LOW] No `lastmod` on non-blog pages**
Only blog articles have `<lastmod>`. Adding accurate lastmod to all pages helps crawl prioritization, especially after updates.

---

## 2. Content Quality (E-E-A-T) — 62/100

### E-E-A-T Breakdown

| Factor | Score | Notes |
|--------|-------|-------|
| Experience | 70/100 | First-person blog, hands-on training hours table, "13 anos" on About page |
| Expertise | 82/100 | ASNT + PCN Level 3, IWE, Naval Engineering MSc — all explicitly stated |
| Authoritativeness | 45/100 | No testimonials, no case studies, no external citations, LinkedIn linked but no Wikipedia/press |
| Trustworthiness | 75/100 | Full contact info (phone, email, WhatsApp), São Paulo address, real person named |

**E-E-A-T Total: 68/100**

### Content Depth Analysis

| Page | Est. Words | Minimum | Status |
|------|-----------|---------|--------|
| `index.html` | ~600 | 500 | ✅ |
| `sobre.html` | ~400 | 500 | ⚠️ slightly thin |
| `certificacoes.html` | ~350 | 500 | ⚠️ thin |
| `contato.html` | ~150 | 300 | ⚠️ thin (contact pages can be shorter) |
| `servicos/procedimentos.html` | ~280 | 800 | ❌ thin |
| `servicos/qualificacoes.html` | ~250 | 800 | ❌ thin |
| `servicos/auditorias-asme.html` | ~180 | 800 | ❌ thin |
| `servicos/ped.html` | ~300 | 800 | ❌ thin |
| `servicos/phased-array.html` | ~320 | 800 | ❌ thin |
| `servicos/treinamento.html` | ~180 | 800 | ❌ thin |
| `blog/snt-tc-1a-guia-completo.html` | ~1,400 | 1,500 | ⚠️ close — add ~100 words |
| `en/*` service pages | ~180–320 | 800 | ❌ thin (same issue as PT) |

### ❌ Content Issues

**[HIGH] All 12 service pages (PT + EN) are thin**
Every service page has 150–320 words, well below the 800-word minimum for service pages. These pages cover high-value queries ("procedimentos END ASME", "phased array PAUT", "PED/RTPO Brasil") and are competing against more detailed pages. Thin service pages are the single biggest content-SEO risk.

**[HIGH] No testimonials or case studies anywhere**
Zero social proof. For an expert B2B service targeting ASME stamp holders and European exporters, client testimonials (even anonymized: "Oil & Gas company, Rio de Janeiro") dramatically improve E-E-A-T Authoritativeness and conversion.

**[MEDIUM] Blog article is ~100 words short of 1,500 minimum**
The SNT-TC-1A article is around 1,400 words. Adding a "Conclusão" section or expanding the recertification section would close the gap.

**[MEDIUM] No reading time indicator on blog article**
Expected in technical blogs. Add "Leitura: 7 min" to the byline.

**[MEDIUM] `sobre.html` slightly thin**
Dan's bio and credentials are mentioned but not fully expanded. Adding a brief professional narrative (not just bullet points of certifications) improves E-E-A-T Experience signals.

**[LOW] No related articles section on blog posts**
The blog article links to services inline but has no structured "Related Articles" section. This is both a UX and internal linking gap for future blog growth.

**[LOW] PT blog index (`blog/index.html`) has no schema for `ItemList` or `Blog`**
Blog listing pages benefit from `ItemList` or `Blog` schema for AI/search discoverability.

---

## 3. On-Page SEO — 80/100

### ✅ PASS
- All 25 pages have unique `<title>` tags
- All titles include primary keyword + "SimpleNDT"
- All titles are within 60 characters ✅
- All pages have `<meta name="description">` within 155 characters ✅
- All pages have `<meta name="keywords">` ✅
- Open Graph: og:title, og:description, og:url, og:type, og:site_name present everywhere ✅
- hreflang: PT-BR ↔ EN + x-default on all pages ✅
- Internal links use descriptive anchor text ✅

### ❌ Issues

**[HIGH] `og:image` missing on all pages** (also in Technical section — top priority)

**[MEDIUM] PT nav missing "Certificações"**
All PT inner pages link to the main sections but Certificações is unreachable from the PT navigation menu.

**[MEDIUM] `certificacoes.html` — nav `class="active"` is on "Sobre" not "Certificações"**
Pre-existing bug. "Sobre" is highlighted when on the Certificações page. (Certificações isn't even in the PT nav.)

**[LOW] `sobre.html` OG type is `website` instead of `profile`**
For personal/about pages, `og:type` = `"profile"` is more semantically correct and better parsed by social platforms.

---

## 4. Schema / Structured Data — 74/100

### ✅ PASS
- `ProfessionalService` schema on all 25 pages ✅
- Required properties present: name, url, telephone, email, address, founder ✅
- `@context` is `https://schema.org` ✅
- All URLs absolute ✅
- No deprecated schema types used ✅
- `Person` schema with `hasCredential` on `sobre.html` and `en/about.html` ✅ (excellent E-E-A-T signal)
- `Article` schema on both blog posts with author, publisher, datePublished ✅
- `FAQPage` schema on 10 pages — valid implementation ✅
- `OfferCatalog` on `procedimentos.html` ✅
- `ContactPoint` nested in ProfessionalService on `contato.html` ✅

### ❌ Issues

**[HIGH] No `BreadcrumbList` schema**
All inner pages display visible breadcrumb navigation in HTML (e.g., "Home / Serviços / Procedimentos") but none have `BreadcrumbList` JSON-LD. Google can display breadcrumbs in search results — this is a missed rich result opportunity.

**[MEDIUM] No `WebSite` schema on homepages**
Neither `index.html` nor `en/index.html` has `WebSite` schema with a `SearchAction`. Recommended for:
```json
{
  "@type": "WebSite",
  "url": "https://simplendt.com.br",
  "potentialAction": {
    "@type": "SearchAction",
    "target": "https://simplendt.com.br/?q={search_term_string}",
    "query-input": "required name=search_term_string"
  }
}
```

**[MEDIUM] `Article` schema missing `image` property**
Google recommends (and often requires for rich results) an `image` property on Article schema. Currently absent. Blocked by the missing `og:image`.

**[INFO] `FAQPage` on commercial site**
As of August 2023, Google restricts FAQPage rich results to government and healthcare sites. The existing FAQ schemas do NOT qualify for Google FAQ rich results but **still benefit AI/LLM citation** (Perplexity, ChatGPT, Google SGE). No action needed — keep them for GEO value.

**[INFO] `ProfessionalService` could be enriched with `ServiceType`**
Adding `"@type": ["ProfessionalService", "LocalBusiness"]` makes the schema more specific. Also consider adding `priceRange` ("$$") if applicable.

---

## 5. Performance (Core Web Vitals) — 65/100

*Note: Cannot measure actual runtime CWV without a live URL. Assessment is based on HTML/CSS/JS source analysis.*

### ✅ Positive signals
- Pure static HTML — no server-side rendering latency
- Single CSS file (`style.css`) — minimal render-blocking
- Minimal vanilla JS — no heavy frameworks
- Intersection Observer for animations — no layout shift triggers
- Images: none currently loaded — no LCP image risk (but also no visual content)

### ⚠️ Risk Factors

**[HIGH] Google Fonts without `preconnect`**
`index.html` loads Outfit + Space Mono from Google Fonts without `rel="preconnect"` hints. This adds 150–300ms DNS/TLS latency to font loading, directly impacting LCP. Fix:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```

**[MEDIUM] No `font-display: swap` in font loading**
Without `font-display: swap`, text is invisible until fonts load (FOIT — Flash of Invisible Text). This hurts both perceived performance and LCP. Add `&display=swap` to the Google Fonts URL.

**[MEDIUM] Inline `<style>` block on `index.html` and `en/index.html`**
Both homepages have a massive inline `<style>` block (~500 lines) that duplicates or partially overlaps `style.css`. This increases HTML file size and is a maintenance complexity. It does not cause CWV issues but adds ~15KB to the initial payload unnecessarily.

**[LOW] No `loading="lazy"` attributes ready for future images**
When images are added, ensure all below-fold images have `loading="lazy"` to avoid LCP demotion.

---

## 6. AI Search Readiness (GEO) — 58/100

### GEO Dimension Scores

| Dimension | Score | Notes |
|-----------|-------|-------|
| Citability | 65/100 | Blog article excellent; service pages too short |
| Structural Readability | 70/100 | FAQ sections, H2/H3 hierarchy, good |
| Multi-Modal Content | 20/100 | No images, no video, no infographics |
| Authority & Brand Signals | 45/100 | LinkedIn linked; no Reddit/YouTube/Wikipedia |
| Technical Accessibility | 85/100 | Static HTML, no JS rendering, schema present |

### ✅ Positive signals
- Static HTML — fully crawlable by GPTBot, ClaudeBot, PerplexityBot ✅
- `robots.txt` `Allow: /` covers all AI crawlers ✅
- Schema.org structured data present on all pages ✅
- FAQ Q&A format on 10 pages — high AI citation value ✅
- Definition pattern in blog: "A SNT-TC-1A é um documento..." — extractable by AI ✅
- Direct answers in first paragraphs of blog sections ✅
- Author identity clear (Dan Yamashita + credentials visible) ✅
- LinkedIn profile linked ✅

### ❌ Issues

**[HIGH] No `llms.txt` file**
`/llms.txt` is a new standard (2024) that helps LLMs understand which pages to prioritize and how to describe the site. Perplexity and some ChatGPT crawlers check for this file. Missing = missed opportunity.

Example `llms.txt` for this site:
```
# SimpleNDT
> NDT Level 3 consulting by Dan Yamashita (ASNT + PCN Level 3, IWE). São Paulo, Brazil.

## Services
- [NDT Procedures](https://simplendt.com.br/servicos/procedimentos.html)
- [Personnel Qualification](https://simplendt.com.br/servicos/qualificacoes.html)
- [ASME Audits](https://simplendt.com.br/servicos/auditorias-asme.html)
- [PED/RTPO Compliance](https://simplendt.com.br/servicos/ped.html)
- [Phased Array PAUT](https://simplendt.com.br/servicos/phased-array.html)
- [NDT Training](https://simplendt.com.br/servicos/treinamento.html)

## Blog
- [SNT-TC-1A Complete Guide](https://simplendt.com.br/blog/snt-tc-1a-guia-completo.html)

## About
- [Dan Yamashita](https://simplendt.com.br/sobre.html): Naval Engineer, MSc Mechatronics, ASNT Level III, PCN Level 3 (ISO 9712), IWE
```

**[HIGH] Service pages too short for AI citation**
Optimal passage length for AI citation is 134–167 words per self-contained section. Most service pages have only 1–2 short paragraphs total — not enough for Perplexity/ChatGPT to extract a meaningful answer.

**[MEDIUM] No explicit AI crawler directives in `robots.txt`**
While `User-agent: * Allow: /` does allow all crawlers, best practice is to explicitly list AI search crawlers with allow:
```
User-agent: GPTBot
Allow: /

User-agent: OAI-SearchBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: PerplexityBot
Allow: /
```

**[MEDIUM] Zero multi-modal content**
No images, no video, no diagrams. AI Overviews correlate with multi-modal content presence. Even 1–2 professional photos (Dan performing an inspection, PAUT equipment) would significantly boost GEO score.

**[MEDIUM] No brand mention on external platforms**
- No YouTube channel
- No Reddit presence (r/NDT, r/engineering)
- No Wikipedia entity
- No press coverage

Brand mentions correlate with AI citation frequency. YouTube has the strongest correlation (~0.737).

**[LOW] No question-based H2 headings on service pages**
The blog article uses implicit question framing; service pages use statement headings ("O que é PAUT", "O que está incluído"). Converting some H2s to explicit questions ("O que é phased array e quando usar?") improves AI extraction.

---

## 7. Images — 50/100

**[HIGH] No images anywhere on the site**
The entire site has zero `<img>` tags (confirmed by grep). This means:
- No visual E-E-A-T signals (no photo of Dan, no equipment photos)
- No LCP image candidate (LCP will be text-based — acceptable but suboptimal)
- `og:image` cannot be set properly
- AI Overviews and Google Image Search cannot index anything

**Recommended minimum image set:**
1. `assets/images/dan-yamashita-ndt-level-3.webp` — professional headshot for `sobre.html` and bylines
2. `assets/images/simplendt-og-default.webp` — 1200×630px OG image for social sharing
3. `assets/images/paut-inspection.webp` — PAUT equipment photo for phased-array page

---

## Summary Table

| Issue | Priority | Effort | Impact |
|-------|----------|--------|--------|
| Add `og:image` to all pages | HIGH | Low (30 min) | High |
| Add favicon | HIGH | Low (15 min) | Medium |
| Add `BreadcrumbList` schema | HIGH | Low (1h) | Medium |
| Fix duplicate `</head>` in blog | CRITICAL | Low (5 min) | Low |
| Delete `SimpleNDT_Design_v2.html` | HIGH | Low (5 min) | Medium |
| Add `llms.txt` | HIGH | Low (20 min) | High |
| Add Certificações to PT nav | HIGH | Low (30 min) | High |
| Fix `certificacoes.html` active nav state | MEDIUM | Low (5 min) | Low |
| Add `preconnect` + `font-display: swap` | HIGH | Low (15 min) | High (LCP) |
| Expand service pages to 800+ words | HIGH | High (days) | Very High |
| Add testimonials/case studies | HIGH | Medium | High |
| Add `WebSite` schema on homepages | MEDIUM | Low (20 min) | Medium |
| Add `image` to Article schema | MEDIUM | Low (15 min) | Medium |
| Add AI crawlers to robots.txt | MEDIUM | Low (10 min) | Medium |
| Add reading time to blog byline | LOW | Low (5 min) | Low |
| Add photos (headshot + equipment) | MEDIUM | Medium (1 day) | High |
| Add `ItemList` schema to blog index | LOW | Low (30 min) | Low |
| Create YouTube / Reddit presence | LOW | High (ongoing) | High (long-term) |
