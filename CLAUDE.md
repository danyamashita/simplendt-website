# SimpleNDT Website — Project Instructions

## Project Overview
Bilingual (PT-BR / EN) static website for SimpleNDT, an independent NDT Level 3 consulting firm based in São Paulo, Brazil. Owner: Dan Yamashita — Naval Engineer, MSc Mechatronics (Ultrasound), IWE, ASNT and PCN Level 3.

Primary goal: generate inbound leads through SEO and AI discoverability for NDT Level 3 services — ASME audits, PED/RTPO inspections, SNT-TC-1A qualification, procedure development, and digital radiography transition.

## Tech Stack
- Pure HTML + CSS + vanilla JS (no frameworks, no build tools)
- Static site — no backend, no database
- Hosted on Netlify via GitHub deploy
- CSS custom properties for theming
- Google Fonts loaded via `<link>` (Instrument Serif, DM Sans, JetBrains Mono)

## Architecture

```
simplendt/
├── index.html                    # PT-BR homepage
├── style.css                     # Global stylesheet (single file)
├── sobre.html                    # About page
├── contato.html                  # Contact page
├── certificacoes.html            # Certifications page
├── servicos/
│   ├── procedimentos.html        # Procedures service
│   ├── qualificacoes.html        # Personnel qualification
│   ├── auditorias-asme.html      # ASME audits
│   ├── ped.html                  # PED/RTPO compliance
│   ├── phased-array.html         # PAUT service
│   └── treinamento.html          # Training
├── blog/
│   ├── index.html                # Blog listing page
│   ├── snt-tc-1a-guia-completo.html
│   └── [other articles].html
├── en/                           # English mirror
│   ├── index.html
│   ├── about.html
│   ├── services/
│   ├── blog/
│   └── ...
├── assets/
│   ├── images/
│   └── icons/
├── sitemap.xml
├── robots.txt
└── _redirects                    # Netlify redirects
```

## Design System

### Colors (CSS custom properties — defined in style.css :root)
- `--bg`: #0a0c10 (main background)
- `--bg-subtle`: #0f1117 (card/section background)
- `--accent`: #4fd1c5 (teal — primary accent)
- `--accent-dim`: rgba(79, 209, 197, 0.15) (borders, subtle highlights)
- `--text-primary`: #f1f5f9
- `--text-secondary`: #94a3b8
- `--text-tertiary`: #64748b
- `--border`: rgba(79, 209, 197, 0.08)

### Typography
- Headings: `'Instrument Serif', Georgia, serif` — weight 400, no bold
- Body: `'DM Sans', sans-serif` — weight 400-600, size 14-17px, line-height 1.7-1.9
- Technical/labels/tags: `'JetBrains Mono', monospace` — weight 500-600, size 9-12px, letter-spacing 2-4px, uppercase
- NEVER use Inter, Roboto, Arial, or system fonts

### Spacing
- Section padding: 100px vertical, 24px horizontal
- Max content width: 1100px, centered
- Section dividers: 1px gradient line (transparent → accent-dim → transparent)

### Visual Elements
- Subtle grid background (72px grid, 2.5% opacity accent lines)
- Geometric accent shapes (rotated squares, circles) at very low opacity
- Scan line animation on hero only
- Cards: 1px border (--border), 8px border-radius, subtle hover state
- Tags/badges: pill shape, 1px accent-dim border, mono font, 9px

### Animations
- Intersection Observer fade-in: translateY(28px) → 0, opacity 0 → 1
- Duration: 0.7s cubic-bezier(.22,1,.36,1)
- Stagger: 0.08-0.12s between siblings
- Nav: backdrop-filter blur on scroll

### Responsive
- Mobile breakpoint: 768px
- Use clamp() for fluid typography: `clamp(26px, 3.8vw, 44px)` for h2
- Hamburger menu on mobile, horizontal nav on desktop
- Grid columns: `repeat(auto-fit, minmax(250px, 1fr))`

## SEO Rules — CRITICAL

### Every HTML page MUST have:
1. Unique `<title>` tag — max 60 chars, include primary keyword + "SimpleNDT"
2. Unique `<meta name="description">` — max 155 chars, include keywords + CTA
3. `<meta name="keywords">` — 5-7 relevant terms
4. Canonical URL: `<link rel="canonical" href="https://simplendt.com.br/...">`
5. Open Graph tags: og:title, og:description, og:image, og:url, og:type
6. `hreflang` tags linking PT and EN versions:
   ```html
   <link rel="alternate" hreflang="pt-BR" href="https://simplendt.com.br/page.html">
   <link rel="alternate" hreflang="en" href="https://simplendt.com.br/en/page.html">
   ```
7. Proper heading hierarchy: single H1, H2s for sections, H3s for subsections
8. Schema.org JSON-LD (see below)

### Schema Markup (JSON-LD) — include on EVERY page:
```json
{
  "@context": "https://schema.org",
  "@type": "ProfessionalService",
  "name": "SimpleNDT",
  "description": "NDT Level 3 Consulting — ASME, PED/RTPO, SNT-TC-1A, ISO 9712",
  "url": "https://simplendt.com.br",
  "telephone": "+5511991612503",
  "email": "contato@simplendt.com.br",
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "São Paulo",
    "addressRegion": "SP",
    "addressCountry": "BR"
  },
  "founder": {
    "@type": "Person",
    "name": "Dan Yamashita",
    "jobTitle": "NDT Level 3 Consultant"
  },
  "areaServed": ["BR", "Global"],
  "knowsAbout": ["NDT", "ASME", "PED", "RTPO", "SNT-TC-1A", "ISO 9712", "Phased Array", "Radiography"]
}
```

### Blog articles MUST also include Article schema:
```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "...",
  "author": { "@type": "Person", "name": "Dan Yamashita" },
  "publisher": { "@type": "Organization", "name": "SimpleNDT" },
  "datePublished": "YYYY-MM-DD",
  "dateModified": "YYYY-MM-DD"
}
```

### FAQ sections MUST include FAQPage schema:
```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Question text",
      "acceptedAnswer": { "@type": "Answer", "text": "Answer text" }
    }
  ]
}
```

### Priority SEO Keywords
- PT: nível 3 END, RTPO, RTPO PED Brasil, selo ASME Brasil, SNT-TC-1A qualificação, ISO 9712 nível 3, phased array PAUT, radiografia digital, ensaios não destrutivos consultoria, PED 2014/68/EU
- EN: NDT Level 3, RTPO, RTPO PED, ASME stamp audit, SNT-TC-1A qualification, ISO 9712 Level 3, phased array PAUT, digital radiography NDT, computed radiography CR

### Technical SEO
- All images: `alt` text describing content + keyword where natural, `width`/`height` attributes, WebP format preferred
- All internal links: descriptive anchor text (never "click here")
- sitemap.xml: auto-generate or manually maintain, include all pages and blog posts
- robots.txt: allow all, reference sitemap
- 404 page: create custom /404.html
- Page speed: no unnecessary JS libraries, inline critical CSS if needed, lazy-load below-fold images

## Coding Rules

### HTML
- Semantic HTML5: `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`
- One `<h1>` per page, logical heading order
- All links must have meaningful text
- Forms (if any): proper `<label>` elements
- Language attribute: `lang="pt-BR"` or `lang="en"`
- All pages share the same nav and footer structure

### CSS
- Single `style.css` file for the entire site
- Use CSS custom properties for all colors, fonts, and spacing
- Mobile-first approach where practical
- No CSS frameworks (no Tailwind, no Bootstrap)
- Class naming: descriptive, BEM-like (`.service-card`, `.service-card__title`)
- Prefer `clamp()` over media queries for fluid sizing
- Transitions: 0.3s ease for interactive elements
- No `!important` unless absolutely necessary

### JavaScript
- Vanilla JS only — no jQuery, no React, no frameworks
- Keep JS minimal: intersection observer for animations, nav scroll behavior, FAQ toggles
- Place scripts at end of `<body>` or use `defer`
- No inline `onclick` — use `addEventListener`

### File Naming
- All lowercase, hyphens for spaces: `auditorias-asme.html`, not `AuditoriasASME.html`
- Blog posts: descriptive slug: `snt-tc-1a-guia-completo.html`
- Images: descriptive names: `dan-yamashita-ndt-level-3.webp`, not `IMG_001.webp`

## Git Workflow

### Branch Strategy
- `main` — production, deploys automatically to Netlify
- `develop` — staging/integration branch
- Feature branches: `feature/blog-rtpo-article`, `feature/service-ped-page`
- Fixes: `fix/nav-mobile-menu`, `fix/seo-meta-tags`

### Commit Messages
Use conventional commits:
- `feat: add PED/RTPO service page`
- `content: add blog post on SNT-TC-1A vs ISO 9712`
- `fix: correct canonical URL on English pages`
- `style: adjust card spacing on mobile`
- `seo: add FAQ schema to certification page`
- `i18n: add English version of about page`

### Before Every Commit
1. Validate HTML (no broken tags, proper nesting)
2. Check all internal links work
3. Verify meta tags are present and unique
4. Confirm hreflang tags match between PT and EN versions
5. Test responsive layout at 375px and 1440px widths

### Pull Request Rules
- PR title matches conventional commit format
- Description includes: what changed, why, which pages affected
- If adding a new page: confirm SEO checklist is complete (title, description, schema, sitemap updated)

## Content Guidelines

### Tone (Portuguese)
- Technical but accessible — Dan explains complex standards clearly
- Direct, no filler — respect the reader's time
- First person where appropriate ("Atuo como RTPO...")
- Never salesy or generic — demonstrate expertise through specificity

### Tone (English)
- Same principles, natural English (not translated-sounding)
- Use standard NDT terminology (not British spellings unless PCN-specific)

### Blog Articles
- Every article needs: H1 title, author byline, date, reading time, tags
- Include FAQ section with at least 3-5 questions (for FAQ schema)
- Internal links to relevant service pages
- CTA band at the bottom linking to services or contact
- Code/standard references must be accurate — Dan will verify

## Bilingual Structure
- Portuguese is the primary language (root domain)
- English pages mirror Portuguese under `/en/`
- Every page must have hreflang pointing to its counterpart
- Language switcher in nav: "PT / EN" linking to equivalent page
- URLs: PT uses Portuguese slugs, EN uses English slugs
  - `/servicos/procedimentos.html` ↔ `/en/services/procedures.html`
  - `/blog/snt-tc-1a-guia-completo.html` ↔ `/en/blog/snt-tc-1a-complete-guide.html`

## Security Rules — MANDATORY

### Secrets Management
- NEVER hardcode credentials, API keys, passwords, tokens, or any sensitive values in HTML, CSS, or JS files
- If any service requires a key (analytics, forms, etc.), use Netlify environment variables, not code
- NEVER create, read, or modify .env files
- NEVER include real email addresses in JavaScript — use Netlify Forms or obfuscation
- The contact email (contato@simplendt.com.br) may appear in HTML `mailto:` links but NEVER in JS variables

### Files That Must NEVER Be Committed
- .env, .env.*, .env.local, .env.production
- Any file containing passwords, tokens, or API keys
- .DS_Store, Thumbs.db, node_modules/
- IDE config: .vscode/, .idea/

### .gitignore (must exist in repo root)
```
.env
.env.*
.DS_Store
Thumbs.db
node_modules/
.claude/
*.log
```

### .claude/settings.json (must exist in repo)
```json
{
  "permissions": {
    "deny": [
      "Read(./.env)",
      "Read(./.env.*)",
      "Read(./**/.env)",
      "Read(./**/secrets/**)",
      "Read(./**/*.key)",
      "Bash(curl:*)",
      "Bash(wget:*)"
    ]
  }
}
```

### If Adding Third-Party Services
- Google Analytics: use Netlify environment variable for measurement ID, inject via build
- Contact forms: use Netlify Forms (no backend needed) or Formspree
- Any future API integration: keys go in Netlify dashboard > Site settings > Environment variables
- NEVER put tracking IDs or service keys directly in HTML — use a build-time injection or Netlify snippet injection

### Before Every Push to GitHub
- Run `git diff --cached` and visually check for any hardcoded secrets
- Verify .gitignore is present and complete
- Confirm no .env files exist in the staging area

## Do NOT
- Use any CSS framework or JS framework
- Add cookie banners or analytics without explicit request
- Use stock photos or placeholder images from external URLs
- Create pages without complete SEO meta tags
- Use generic headings like "Welcome" or "Our Services" — be specific
- Use AI-generated filler text — all content must be factually accurate NDT content
- Hardcode colors or fonts — always use CSS variables
- Create inline styles except for truly one-off cases
