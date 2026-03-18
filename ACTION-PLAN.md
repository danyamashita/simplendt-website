# SimpleNDT — SEO Action Plan
**Generated:** 2026-03-18
**Overall Score:** 71/100

Fixes ordered by impact/effort ratio. Execute top-to-bottom.

---

## 🔴 CRITICAL — Fix before launch

### 1. Fix duplicate `</head>` in blog article
**File:** `blog/snt-tc-1a-guia-completo.html` — lines 123–124
Remove the second `</head>` closing tag (line 124).

### 2. Delete design prototype
**File:** `SimpleNDT_Design_v2.html`
Delete this file — it's publicly accessible and should not be indexed.

---

## 🟠 HIGH — Fix within 1 week (quick wins)

### 3. Add `og:image` to every page (30 min)
1. Create `assets/images/simplendt-og-default.webp` (1200×630px)
2. Add to every page `<head>`:
   ```html
   <meta property="og:image" content="https://simplendt.com.br/assets/images/simplendt-og-default.webp">
   <meta property="og:image:width" content="1200">
   <meta property="og:image:height" content="630">
   <meta property="og:image:alt" content="SimpleNDT — Consultoria Nível 3 END">
   ```

### 4. Add favicon (15 min)
Add to all pages `<head>`:
```html
<link rel="icon" type="image/svg+xml" href="/assets/icons/favicon.svg">
<link rel="apple-touch-icon" href="/assets/icons/apple-touch-icon.png">
```

### 5. Fix Google Fonts performance (15 min)
In `index.html` and `en/index.html`, replace the current Google Fonts `<link>` with:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
```
Also verify `style.css` has `font-display: swap` on all `@font-face` declarations.

### 6. Add Certificações to PT navigation (30 min)
All 12 PT pages need "Certificações" added to nav between "Sobre" and "Blog":
```html
<li><a href="/certificacoes.html">Certificações</a></li>
```
Also fix `certificacoes.html` nav active state from "Sobre" → "Certificações".

### 7. Add `llms.txt` (20 min)
Create `/llms.txt` at project root:
```
# SimpleNDT
> NDT Level 3 consulting by Dan Yamashita. ASNT and PCN (ISO 9712) Level 3 certified. São Paulo, Brazil.

## Services
- [Procedimentos de END](https://simplendt.com.br/servicos/procedimentos.html): NDT procedures per ASME Section V, API, AWS, PED
- [Qualificação de Pessoal](https://simplendt.com.br/servicos/qualificacoes.html): Personnel qualification SNT-TC-1A and ISO 9712
- [Auditorias ASME](https://simplendt.com.br/servicos/auditorias-asme.html): ASME stamp audit preparation
- [PED/RTPO](https://simplendt.com.br/servicos/ped.html): PED 2014/68/EU compliance, CE marking
- [Phased Array PAUT](https://simplendt.com.br/servicos/phased-array.html): PAUT procedures, beam plotting
- [Treinamento END](https://simplendt.com.br/servicos/treinamento.html): NDT training Level 1 and 2

## Blog
- [SNT-TC-1A: Guia Completo](https://simplendt.com.br/blog/snt-tc-1a-guia-completo.html)

## English Version
- [simplendt.com.br/en/](https://simplendt.com.br/en/)

## About
Dan Yamashita: Naval Engineer, MSc Mechatronics (Ultrasound), IWE, ASNT NDT Level III, PCN Level 3 (ISO 9712). 13+ years in NDT for oil & gas, naval, energy, nuclear.
Contact: contato@simplendt.com.br
```

### 8. Add `BreadcrumbList` schema (1h)
Every inner page has visible breadcrumbs but no schema. Add to each inner page before `</head>`. Example for `servicos/procedimentos.html`:
```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://simplendt.com.br/"},
    {"@type": "ListItem", "position": 2, "name": "Serviços", "item": "https://simplendt.com.br/servicos/procedimentos.html"},
    {"@type": "ListItem", "position": 3, "name": "Procedimentos de END"}
  ]
}
```

### 9. Update `robots.txt` with explicit AI crawler rules (10 min)
Replace current `robots.txt` with:
```
User-agent: *
Allow: /

User-agent: GPTBot
Allow: /

User-agent: OAI-SearchBot
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: PerplexityBot
Allow: /

Sitemap: https://simplendt.com.br/sitemap.xml
```

---

## 🟡 MEDIUM — Fix within 1 month

### 10. Expand all service pages to 800+ words (HIGH impact, HIGH effort)
This is the single most impactful content SEO task. Every service page needs 500–600 more words. Suggested additions per page:

**`servicos/procedimentos.html`** — Add:
- What a typical ASME procedure includes (scope, equipment, calibration, technique, acceptance criteria)
- What happens without a proper procedure during an ASME audit
- A second FAQ: "Quanto custa um procedimento END?" / "Qual o prazo de entrega?"

**`servicos/qualificacoes.html`** — Add:
- Step-by-step qualification process under SNT-TC-1A
- What documents are generated (certificates, exam records, written practice)
- Comparison: SNT-TC-1A vs ISO 9712 qualification

**`servicos/auditorias-asme.html`** — Add:
- What the Authorized Inspector checks for NDT
- Common NDE audit findings that get companies deferred
- Stamps covered (U, U2, S, R, PP) and what each requires from NDT

**`servicos/ped.html`** / **`en/services/ped.html`** — Add:
- Which equipment categories (Cat I–IV) trigger PED NDT requirements
- Timeline for getting a PED-compliant NDT program in place
- Difference between EN and ASME procedures (specific clauses)

**`servicos/phased-array.html`** — Add:
- Technical explanation of beam steering/focusing vs. conventional UT
- What a scan plan includes (refracted angles, focal depth, index point)
- Real application example

**`servicos/treinamento.html`** — Add:
- What happens on a typical training day
- How the Prática Escrita is connected to the training
- What documentation is issued (training hours log, exam records)

### 11. Add `WebSite` schema to homepages (20 min)
Add to `index.html` and `en/index.html` JSON-LD:
```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "SimpleNDT",
  "url": "https://simplendt.com.br",
  "inLanguage": ["pt-BR", "en"],
  "description": "Consultoria independente em Ensaios Não Destrutivos Nível 3"
}
```

### 12. Add `image` to Article schema in blog posts (15 min)
Once `og:image` is created, add to both blog article schemas:
```json
"image": {
  "@type": "ImageObject",
  "url": "https://simplendt.com.br/assets/images/simplendt-og-default.webp",
  "width": 1200,
  "height": 630
}
```

### 13. Expand blog article to 1,500+ words (1h)
Add ~100 words — suggested: a "Conclusão" section or expand the Recertificação section to include what documentation is required for ASME performance evaluation before recertification.

### 14. Add reading time to blog byline (5 min)
In `blog/snt-tc-1a-guia-completo.html` byline:
```
POR DAN YAMASHITA · NÍVEL 3 ASNT/PCN · SIMPLE NDT · <time datetime="2025-01-15">15 JAN 2025</time> · LEITURA: 8 MIN
```
Same pattern for EN version.

### 15. Add `og:type="profile"` to About pages (5 min)
Change `og:type` from `website` to `profile` on `sobre.html` and `en/about.html`.

---

## 🟢 LOW — Backlog

### 16. Add photos (HIGH long-term impact)
Minimum set:
- `dan-yamashita-ndt-level-3.webp` — professional headshot
- `simplendt-og-default.webp` — branded OG image (1200×630)
- `paut-inspection.webp` — equipment in use

### 17. Add testimonials section
Even 2–3 anonymous client quotes ("Gerente de QA, Oil & Gas, RJ") on the homepage and/or service pages significantly improves Authoritativeness score.

### 18. `ItemList` schema on blog index pages
Add to `blog/index.html` and `en/blog/index.html`:
```json
{
  "@context": "https://schema.org",
  "@type": "Blog",
  "name": "SimpleNDT Blog",
  "url": "https://simplendt.com.br/blog/",
  "blogPost": [
    {
      "@type": "BlogPosting",
      "headline": "SNT-TC-1A: Guia Completo de Qualificação ASNT",
      "url": "https://simplendt.com.br/blog/snt-tc-1a-guia-completo.html",
      "datePublished": "2025-01-15"
    }
  ]
}
```

### 19. Strip `priority` and `changefreq` from `sitemap.xml`
Both are ignored by Google. Optional — no ranking impact either way.

### 20. Long-term brand authority (ongoing)
- LinkedIn: publish 1 article/month on NDT topics → builds brand mentions
- YouTube: short explanation videos on PAUT, SNT-TC-1A, PED — highest AI citation correlation
- Reddit: contribute to r/NDT, r/engineering — builds community presence

---

## DNS / Deployment Note

The live `simplendt.com.br` currently serves the old WordPress site. Before any SEO effort goes live, the Netlify DNS must be pointed to the new static site. Until then, all improvements exist only in the GitHub repo and are invisible to Google.

**Recommended steps:**
1. Complete Critical + High fixes above
2. Update Netlify DNS settings to point `simplendt.com.br` to new site
3. Submit sitemap to Google Search Console
4. Submit sitemap to Bing Webmaster Tools
5. Monitor indexing via Search Console Coverage report
