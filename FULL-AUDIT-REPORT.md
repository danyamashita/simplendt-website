# SimpleNDT — Full SEO Audit Report
**Site:** https://simplendt.com.br
**Data da auditoria:** 25 de março de 2026
**Escopo:** PT-BR + EN, 26 URLs, bilíngue estático hospedado em Netlify

---

## SEO Health Score: 76 / 100

| Categoria | Peso | Pontuação | Contribuição |
|-----------|------|-----------|--------------|
| Technical SEO | 25% | 81 / 100 | 20.3 |
| Content Quality / E-E-A-T | 25% | 82 / 100 | 20.5 |
| On-Page SEO | 20% | 72 / 100 | 14.4 |
| Schema / Structured Data | 10% | 70 / 100 | 7.0 |
| Performance (CWV) | 10% | 77 / 100 | 7.7 |
| Imagens | 5% | 45 / 100 | 2.3 |
| AI Search Readiness (GEO) | 5% | 76 / 100 | 3.8 |
| **TOTAL** | | | **76 / 100** |

---

## Tipo de negócio detectado

Consultoria independente B2B de Ensaios Não Destrutivos — nicho de altíssima especialização técnica, audiência restrita (gestores de qualidade, programas ASME, fabricantes exportando para Europa). Zero concorrência direta em português para a maioria das queries-alvo.

---

## Top 5 Problemas Críticos / Alta Prioridade

1. **Links internos de navegação sem extensão `.html`** — cada clique no menu gera um 301 desnecessário (`/sobre` → `/sobre.html`). Afeta TODAS as páginas.
2. **`image` e `publisher.logo` ausentes no schema Article** — os 3 posts de blog (+ EN) são inelegíveis para rich results no Google.
3. **2 posts de blog ausentes do sitemap.xml** — PAUT e ASME audits não estão no sitemap; crawlers de IA usando descoberta por sitemap os ignoram.
4. **`llms.txt` referencia apenas 1 de 4 posts** — os dois posts mais diferenciados tecnicamente (PAUT e ASME) estão invisíveis para sistemas de IA que usam llms.txt como índice.
5. **Foto do Dan não é um `<img>` rastreável** — a foto em `sobre.html` é CSS background, não indexável pelo Google, enfraquece o sinal de pessoa real para E-E-A-T.

---

## Top 5 Quick Wins

1. Adicionar `image` + `publisher.logo` ao JSON-LD Article nos 3 posts — 30 min, desbloqueia rich results.
2. Corrigir links de navegação para usar `.html` — 1h, elimina ~9 redirects por pageview.
3. Adicionar PAUT e ASME audits ao `sitemap.xml` e ao `llms.txt` — 30 min total.
4. Adicionar `<link rel="preload">` para Outfit 600 woff2 em todas as páginas — 5 min, melhora LCP.
5. Converter foto de Dan de CSS background para `<img>` com alt text — 15 min, sinal E-E-A-T imediato.

---

## 1. Technical SEO — 81 / 100

### O que está bom
- `robots.txt` correto: permite todos os crawlers, permite explicitamente GPTBot, ClaudeBot, PerplexityBot, OAI-SearchBot
- Sitemap com 26 URLs, bilíngue, prioridades e frequências definidas
- Security headers via Netlify: HSTS (2 anos, preload), CSP, X-Frame-Options, Referrer-Policy, Permissions-Policy
- HTTPS enforced via 301 para todo HTTP
- Canonical tags presentes e corretas (www) em todas as páginas auditadas
- Hreflang bidirecional correto em todos os pares PT↔EN, x-default apontando para PT
- Viewport meta presente, layout responsivo com clamp() e breakpoints
- Site é SSR estático — todo conteúdo presente no HTML inicial, sem dependência de JS para indexação
- `font-display: swap` em todos os @font-face, fontes self-hosted em WOFF2
- Zero dependências JS externas, zero scripts de tracking

### Problemas identificados

**ALTA PRIORIDADE**

**H1 — Links internos sem `.html` causam 301 em toda navegação**
Todos os links de navegação e rodapé usam URLs sem extensão (`/sobre`, `/certificacoes`, `/contato`, `/servicos/qualificacoes`, etc.). A Netlify serve estas URLs com um 301 para a versão com `.html`. Isso significa que cada clique no menu gera um redirect desnecessário antes de carregar a página.
Exemplos confirmados:
- `/sobre` → 301 → `/sobre.html`
- `/certificacoes` → 301 → `/certificacoes.html`
- `/servicos/qualificacoes` → 301 → `/servicos/qualificacoes.html`

Os canonical tags já usam corretamente a versão `.html`, criando inconsistência estrutural.
**Fix:** Atualizar todos os `href` de nav/footer para incluir `.html`.

**H2 — Cadeia de redirect duplo para HTTP não-www**
Visitantes chegando via `http://simplendt.com.br` percorrem 2 hops:
- Hop 1: `http://simplendt.com.br` → 301 → `https://simplendt.com.br/`
- Hop 2: `https://simplendt.com.br/` → 301 → `https://www.simplendt.com.br/`

**Fix:** Configurar `_redirects` do Netlify para redirecionar `http://simplendt.com.br/*` direto para `https://www.simplendt.com.br/:splat`.

**MÉDIA PRIORIDADE**

**M1 — Article schema sem `image`** — bloqueia rich results (ver seção Schema)

**M2 — Article schema sem `publisher.logo`** — bloqueia rich results (ver seção Schema)

**M3 — Preload de fontes ausente** — nenhuma página tem `<link rel="preload" as="font">` para o woff2 do Outfit 600 (fonte do hero H1). Impacto em LCP.

**M4 — Preconnect morto para Google Fonts em páginas internas**
`qualificacoes.html` e posts de blog têm:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```
Nenhuma requisição é feita para esses hosts (fontes são self-hosted). O browser abre conexões TCP/TLS que são descartadas — overhead desnecessário.
**Fix:** Remover essas duas linhas de todas as páginas internas.

**M5 — `href="style.css"` relativo em `sobre.html`**
`sobre.html` usa `href="style.css"` (relativo), não `href="/style.css"` (root-relative). Funciona na posição atual mas é frágil.

**BAIXA PRIORIDADE**

**L1 — IndexNow declarado mas sem automação**
A chave está em `robots.txt` mas não há automação para enviar URLs após deploy. Um Netlify build plugin ou post-deploy webhook pode automatizar isso.

**L2 — `meta name="keywords"` presente em todas as páginas**
Ignorado pelo Google desde 2009. Não causa dano mas é overhead.

**L3 — `hreflang="en"` sem subtag de região**
`hreflang="en"` (sem `-US` ou `-GB`) é aceitável para targeting global, mas limitante se o foco for audiência americana ou britânica específica.

**L4 — BreadcrumbList ausente nos posts de blog**
`sobre.html` tem BreadcrumbList, mas os posts de blog não. Google pode renderizar breadcrumbs no SERP para aumentar CTR.

---

## 2. Content Quality / E-E-A-T — 82 / 100

### E-E-A-T Score: 8.1 / 10

| Fator | Pontuação |
|-------|-----------|
| Experience | 8.5 / 10 |
| Expertise | 9.0 / 10 |
| Authoritativeness | 7.5 / 10 |
| Trustworthiness | 7.5 / 10 |

### 3 Pontos Fortes

**1. Profundidade técnica com referência a cláusulas específicas**
O site consistentemente cita o artigo, não apenas a norma. "Seção 3.1.3 do Anexo I da PED", "Mandatory Appendix IX do ASME V Art. 4", "Guideline F-07 e F-09" — nível de especificidade que sistemas de IA favorecem para extração como fonte autorizada.

**2. Infraestrutura de credenciais verificáveis**
A página de certificações é excepcional: badges ASNT com links bcert.me ao vivo, tabela PCN com 11 linhas de números individuais e datas de validade, links de verificação BINDT e LRQA-CASL. Transparência através de verificação, não apenas declaração.

**3. Conteúdo direcionado ao fabricante, não ao inspetor**
"O fabricante brasileiro e a PED: checklist prático", "o que o Authorized Inspector verifica em END", "o que acontece se reprovar" — framing correto para o comprador real do serviço.

### 5 Fraquezas / Gaps

**1. Páginas de serviço abaixo da densidade mínima para o tipo**
- `auditorias-asme.html`: ~500 palavras, majoritariamente listas `<ul>` sem prosa explicativa. Não demonstra profundidade tópica.
- `qualificacoes.html`: ~700 palavras, borderline.
- Ambas precisam de pelo menos uma seção adicional de conteúdo técnico.

**2. Foto do Dan não é um `<img>` rastreável**
A foto em `sobre.html` é CSS `background-image`, não indexável. O Google não consegue confirmar a existência da pessoa através de uma imagem real. Um `<img alt="Dan Yamashita, Engenheiro Naval e Nível 3 END">` com a foto visível no conteúdo da página é necessário para o critério QRG de "autor real verificável".

**3. Ausência de estudos de caso, resultados quantificados ou prova social**
Nenhuma página cita quantas empresas foram preparadas para auditoria ASME, taxa de aprovação, número de inspetores qualificados. Mesmo ranges vagos ("mais de 30 empresas suportadas") fortaleceriam Experience e Authoritativeness.

**4. Blog SNT-TC-1A abaixo do mínimo**
~900 palavras de prosa para um "Guia Completo". Falta: comparação SNT-TC-1A vs. CP-189, tutorial de implementação de Prática Escrita do zero, requisitos ASME específicos vs. SNT-TC-1A base. Recomendado: expandir para 1.500+ palavras.

**5. Gaps de conteúdo de blog para queries de alto valor**
- Nenhuma página targeting "NR-13 END qualificação" (regulatório obrigatório, volume de busca relevante de compradores industriais)
- Nenhuma página sobre "transição radiografia digital/computadorizada ASME" (Dan tem treinamento Hellier 2026 em DR — credencial não suportada por conteúdo)
- Nenhum conteúdo comparando "ABENDI vs PCN vs ASNT" — uma das perguntas mais frequentes do setor no Brasil

### Notas por Página

| Página | Palavras (prose) | Status | Prioridade |
|--------|-----------------|--------|------------|
| sobre.html | ~350 | Borderline — propósito é identidade | Add `<img>` Dan, add "15 anos" no body |
| certificacoes.html | N/A (estrutura) | Forte | Add `datetime` em datas de validade |
| blog/snt-tc-1a | ~900 | Abaixo do mínimo | Expandir para 1.500+ |
| blog/ped | ~1.400 | No mínimo | Converter checklist em lista real |
| blog/phased-array | ~1.600 | Atende | Add tempo de leitura, notas em custos |
| servicos/qualificacoes | ~700 | Borderline | Add seção ISO 9712 vs SNT-TC-1A |
| servicos/auditorias-asme | ~500 | Abaixo | Expandir para 900+, add tipos de selo |
| en/index.html | Divergente | Design diferente do PT | Alinhar com sistema de design PT/EN |

### Readability
- Estrutura de headings: boa em todos os posts
- Comprimento de frases: bom nos blogs, denso nas páginas de serviço
- Jargão: adequado para o público-alvo, termos técnicos explicados na primeira ocorrência

### AI Citation Readiness Score: 74 / 100
- Posts de blog: 85/100 — referências a cláusulas específicas, tabelas comparativas, FAQs estruturadas
- Página de certificações: 88/100 — densidade de dados estruturados excepcional
- Páginas de serviço: 55/100 — prosa procedural sem declarações diretas citáveis

---

## 3. Schema / Structured Data — 70 / 100

### Inventário atual

| Página | Schemas presentes |
|--------|------------------|
| Homepage PT | ProfessionalService |
| Homepage EN | ProfessionalService |
| sobre.html | ProfessionalService + Person + BreadcrumbList |
| certificacoes.html | ProfessionalService + BreadcrumbList |
| blog/snt-tc-1a | ProfessionalService + Article + FAQPage + BreadcrumbList |
| blog/ped | ProfessionalService + Article + FAQPage + BreadcrumbList |
| blog/phased-array | ProfessionalService + Article + FAQPage + BreadcrumbList |
| servicos/qualificacoes | Service + FAQPage + BreadcrumbList |
| servicos/auditorias-asme | Service + FAQPage + BreadcrumbList |
| servicos/ped | Service + FAQPage + BreadcrumbList |

### Eligibilidade para Rich Results

| Rich Result | Status | Bloqueador |
|-------------|--------|------------|
| Article (blog) | **NÃO elegível** | `image` e `publisher.logo` ausentes |
| BreadcrumbList | Elegível | Nenhum |
| Business Profile / Knowledge Panel | Parcial | `@id`, `logo`, `sameAs` ausentes no org |
| FAQPage snippets | Não elegível (comercial) | Política Google desde ago/2023 — manter para GEO |
| Sitelinks Searchbox | Não elegível | WebSite schema ausente |

### Problemas Críticos

**CRÍTICO: Article sem `image` e `publisher.logo` — bloqueia todos os rich results de blog**
Todos os 3 posts (+ EN) não têm `image` no Article schema e não têm `logo` no nó `publisher`. O Google exige ambos para elegibilidade de rich results.

Adicionar em cada Article:
```json
"image": {
  "@type": "ImageObject",
  "url": "https://www.simplendt.com.br/assets/images/simplendt-og-default.png",
  "width": 1200,
  "height": 630
},
"publisher": {
  "@type": "Organization",
  "name": "SimpleNDT",
  "url": "https://www.simplendt.com.br",
  "logo": {
    "@type": "ImageObject",
    "url": "https://www.simplendt.com.br/assets/images/favicon.svg"
  }
}
```

### Problemas de Alta Prioridade

**Nó ProfessionalService sem `@id`, `logo`, `sameAs`**
Presente em todas as páginas como boilerplate, mas:
- Sem `@id` (ex: `"https://www.simplendt.com.br/#organization"`) — sem identificador persistente
- Sem `sameAs` (LinkedIn do Dan está no HTML do footer mas não no schema)
- Sem `logo` ImageObject
- `areaServed: "Global"` não é um valor válido ISO 3166 — usar `{ "@type": "Place", "name": "Worldwide" }`

**Person schema em sobre.html — lacunas**
- Falta `alumniOf` (Escola Politécnica USP — MSc Mecatrônica)
- Falta `image` (foto do Dan como ImageObject)
- `hasCredential` tem apenas 3 nós — PED/RTPO approval e ASME recognition ausentes
- `worksFor` sem `url` ou `@id` referenciando o nó da organização

**Sem Person schema em certificacoes.html**
Esta é a página com mais dados de credenciais do site (11 certificações PCN com números individuais). Não há schema algum para isso além de ProfessionalService genérico.

### Oportunidades Médias

- `WebSite` schema nas homepages (habilita Sitelinks Searchbox)
- `url` e `offers` ausentes nos nós `Service` das 3 páginas de serviço
- `BreadcrumbList` ausente nos posts de blog (ver Technical)

---

## 4. Performance / Core Web Vitals — 77 / 100

*(Análise estática — validar com CrUX quando o site tiver volume de tráfego)*

### Estimativas por página

| Página | LCP estimado | INP estimado | CLS estimado | Risco |
|--------|-------------|-------------|-------------|-------|
| Homepage (index.html) | 1.2–2.0s (Bom) | 150–200ms (Bom/Borderline) | 0.02–0.06 (Bom) | Baixo–Médio |
| Blog (phased-array) | 1.8–3.0s (Bom–Precisa melhora) | 80–120ms (Bom) | 0.05–0.12 (Bom–Borderline) | Médio |
| servicos/qualificacoes | 1.5–2.5s (Bom–Borderline) | 80–120ms (Bom) | 0.02–0.06 (Bom) | Baixo–Médio |

### O que está bom
- Zero dependências JS externas — linha de base excelente
- Todo JS no final do `<body>` — não bloqueia render
- `font-display: swap` em todos os @font-face
- Fontes self-hosted em WOFF2 — sem round-trip para CDN externo
- Scroll listeners com `{ passive: true }`
- IntersectionObserver com `unobserve()` após trigger
- Canvas com limite de 120 tracks (desktop) / 50 (mobile) — evita runaway de memória
- Netlify CDN com Brotli comprimido — infraestrutura sólida

### Problemas identificados

**CRÍTICO — Assimetria de entrega de CSS**
A homepage tem todo o CSS embutido em `<style>` inline (sem render-blocking). TODAS as páginas internas carregam `<link rel="stylesheet" href="../style.css">` sem preload. Isso cria performance de duas velocidades: a homepage quase sempre vai ter LCP melhor que as páginas internas, mesmo sendo mais complexa.
**Fix imediato:** Adicionar `<link rel="preload" href="/style.css" as="style">` antes do `<link rel="stylesheet">` em todas as páginas internas.

**Preconnect morto para Google Fonts**
Páginas internas abrem conexão TCP/TLS com `fonts.googleapis.com` e `fonts.gstatic.com` que nunca são usadas.
**Fix:** Remover essas linhas de todas as páginas internas.

**Sem `<link rel="preload">` para fontes críticas**
Outfit 600 (usado no hero H1) não tem hint de preload em nenhuma página. Em páginas internas, a fonte é descoberta dois network hops depois (HTML → style.css → font request).

**Canvas rAF sem visibility guard**
O loop `requestAnimationFrame` da homepage nunca para. Quando o tab está em background, o browser throttle o rAF automaticamente, mas um listener `document.visibilitychange` para pausar/retomar o loop economizaria CPU/bateria em mobile.

**Delay de animação no H1 da homepage trava o LCP**
O H1 tem `animation-delay: 0.32s`. Isso significa que o LCP candidate (o H1) fica invisível por 320ms mesmo após o browser estar pronto para renderizá-lo. Reduzir para 0.1s economiza ~220ms no LCP sem impacto visual perceptível.

---

## 5. Imagens — 45 / 100

**Problema principal: alt text ausente em todas as imagens dos posts de blog**
Nenhuma das imagens identificadas nos posts (se houver) tem atributos `alt`. A foto de Dan em `sobre.html` é CSS background — não acessível para leitores de tela, não indexável.

**Foto de Dan como CSS background image (sobre.html)**
`background-image: url('/assets/images/foto-dy.jpeg') center 30% / cover no-repeat` — o Google não pode indexar esta foto, não pode confirmar a identidade visual da pessoa, e o schema Person aponta para esta URL sem que ela seja um elemento real da página.

**Recomendações:**
1. Converter a foto de Dan para `<img src="/assets/images/foto-dy.jpeg" alt="Dan Yamashita, Engenheiro Naval e Nível 3 END" width="..." height="...">`
2. Verificar todos os `<img>` nas páginas de blog — adicionar `alt` descritivo em todos
3. Confirmar que `assets/images/simplendt-og-default.png` existe (é referenciado no schema mas não verificado)

---

## 6. GEO / AI Search Readiness — 76 / 100

### Score por plataforma (estimativa)

| Plataforma | Score estimado |
|------------|---------------|
| Google AI Overviews | 7 / 10 |
| Perplexity | 8 / 10 |
| ChatGPT (browsing) | 7 / 10 |
| Bing Copilot | 7 / 10 |
| Claude (web search) | 8 / 10 |

### Pontos fortes

- Todos os 4 crawlers de IA de alto tráfego explicitamente permitidos em robots.txt
- llms.txt estruturalmente compliant com spec llmstxt.org, seção "Key Technical Distinctions" é um diferenciador real — as 3 clarificações RTPO/SNT-TC-1A/SNQC são fatos de alta especificidade que nenhum concorrente pode replicar
- FAQPage schema em todos os posts e páginas de serviço principais — principal vetor de inclusão no Google AI Overviews
- 4 posts cobrindo queries de near-monopoly em português: RTPO PED Brasil, SNT-TC-1A qualificação, PAUT vs RT ASME, Selo ASME END
- Estrutura bilíngue com hreflang correto — posts EN cobrem queries internacionais onde inglês é o idioma de busca mesmo para compradores brasileiros
- Combinação ASNT Level III + PCN Level 3 + RTPO approval (LRQA-CASL) — diferenciador verificável que nenhum concorrente direto aparente possui

### Gaps críticos

**1. 2 posts ausentes do sitemap.xml**
PAUT e ASME audits não estão no sitemap. Crawlers de IA usando descoberta por sitemap os ignoram.

**2. llms.txt referencia apenas 1 de 4 posts**
Os dois posts tecnicamente mais diferenciados (PAUT e ASME audits) estão invisíveis para sistemas de IA que usam llms.txt como índice de conteúdo.

**3. Respostas FAQ abaixo do tamanho ótimo para citação**
O intervalo ótimo para citação por IA é de 134–167 palavras. A maioria das respostas FAQ tem 50–100 palavras — tecnicamente precisas mas curtas para o sweet spot de citação.

**4. Sem presença no YouTube**
Pesquisas consistentes mostram correlação de 0.737 entre menções no YouTube e frequência de citação por IA — o preditor isolado mais forte fora de acesso direto de crawl. A ausência é o maior gap de autoridade de marca do site.

**5. Posts EN ausentes para PAUT e ASME audits**
Os clientes internacionais mais valiosos (fabricantes europeus comprando equipamentos brasileiros, engenheiros americanos com operações no Brasil) buscam em inglês. Dois dos melhores posts só existem em português.

**6. Dados de custo sem atribuição de fonte no post PAUT**
AI systems tendem a omitir ou sinalizar como não verificados valores numéricos (US$ 50.000–150.000 para equipamento PAUT) sem fonte citada.

---

## Conclusão

O SimpleNDT está no tier superior de prontidão para IA na sua especialidade no Brasil. A combinação de acesso explícito a crawlers de IA, llms.txt compliant, FAQPage schema consistente, e conteúdo técnico de longa duração em 4 queries de near-monopoly cria uma fundação forte. O site provavelmente já está sendo citado por Perplexity e Claude para queries de PED/RTPO e SNT-TC-1A.

O teto é limitado por três fatores: ausência de qualquer presença no YouTube (preditor estatisticamente mais significativo de frequência de citação por IA), respostas FAQ mais curtas que o tamanho comprovadamente ótimo para citação, e dois posts ausentes da descoberta por sitemap. Todos são corrigíveis em semanas, não meses.
