# SimpleNDT — Action Plan
**Baseado no Full SEO Audit de 25/03/2026**
**SEO Health Score atual: 76 / 100**

---

## CRÍTICO — Corrigir imediatamente

### C1. Adicionar `image` + `publisher.logo` ao schema Article dos posts de blog
**Impacto:** Desbloqueia rich results no Google Search para todos os posts
**Esforço:** 30 min
**Páginas:** todos os 3 posts PT + 3 posts EN

Em cada bloco Article JSON-LD, adicionar:
```json
"image": {
  "@type": "ImageObject",
  "url": "https://www.simplendt.com.br/assets/images/simplendt-og-default.png",
  "width": 1200,
  "height": 630
},
```
E expandir o nó `publisher`:
```json
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

---

### C2. Adicionar PAUT e ASME audits ao sitemap.xml
**Impacto:** Esses 2 posts ficam invisíveis para crawlers de IA que usam sitemap como índice
**Esforço:** 20 min
**Ação:** Adicionar ao `sitemap.xml`:
- `/blog/phased-array-substituicao-radiografia-asme.html`
- `/blog/selo-asme-requisitos-end-auditorias.html`
- `/en/blog/phased-array-replacing-radiography-asme.html`
- `/en/blog/asme-certification-nde-requirements-audits.html`

---

### C3. Expandir llms.txt com todos os 4 posts + dados verificáveis
**Impacto:** Dois dos melhores posts estão invisíveis para sistemas de IA que usam llms.txt
**Esforço:** 15 min
**Ação:** Adicionar à seção Blog do llms.txt:
- Post PAUT com descrição de 1 frase
- Post ASME audits com descrição de 1 frase
- Adicionar à seção Key Technical Distinctions: PCN 340677 e aprovação LRQA-CASL como fatos verificáveis

---

## ALTA PRIORIDADE — Corrigir em 1 semana

### H1. Corrigir links de navegação para usar extensão `.html`
**Impacto:** Elimina ~9 redirects 301 por pageview em toda a navegação do site
**Esforço:** 1–2h (mudança em template de nav/footer em todas as páginas)
**Páginas afetadas:** TODAS — nav e footer de cada arquivo HTML

Links a corrigir em todos os `<nav>` e `<footer>`:
- `/sobre` → `/sobre.html`
- `/certificacoes` → `/certificacoes.html`
- `/contato` → `/contato.html`
- `/servicos/qualificacoes` → `/servicos/qualificacoes.html`
- `/servicos/phased-array` → `/servicos/phased-array.html`
- `/servicos/treinamento` → `/servicos/treinamento.html`
- `/servicos/ped` → `/servicos/ped.html`
- `/servicos/auditorias-asme` → `/servicos/auditorias-asme.html`
- `/servicos/procedimentos` → `/servicos/procedimentos.html`
- `/sobre` (EN) → `/en/about.html`
- `/certificacoes` (EN) → `/en/certifications.html`
- etc.

---

### H2. Adicionar preload de CSS e remover preconnect morto em páginas internas
**Impacto:** Reduz LCP estimado em 100–300ms nos posts e páginas de serviço
**Esforço:** 30 min
**Páginas:** Todos os arquivos que não são homepage

Em todas as páginas internas, antes do `<link rel="stylesheet">`:
```html
<link rel="preload" href="/style.css" as="style">
```
E remover (se presentes):
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```

---

### H3. Adicionar preload para fontes críticas
**Impacto:** Reduz CLS por FOUT (Flash of Unstyled Text), melhora LCP em páginas internas
**Esforço:** 20 min
**Páginas:** Todas

Adicionar no `<head>` de todas as páginas:
```html
<link rel="preload" href="/assets/fonts/outfit-v15-latin-regular.woff2" as="font" type="font/woff2" crossorigin>
<link rel="preload" href="/assets/fonts/outfit-v15-latin-600.woff2" as="font" type="font/woff2" crossorigin>
```
*(confirmar os nomes exatos dos arquivos woff2 em `/assets/fonts/`)*

---

### H4. Converter foto do Dan para `<img>` rastreável em sobre.html
**Impacto:** Sinal E-E-A-T de "autor real verificável" — Google não indexa CSS background images
**Esforço:** 20 min
**Página:** `sobre.html`

Substituir o uso de CSS background para a foto por um `<img>` visível no conteúdo da página:
```html
<img src="/assets/images/foto-dy.jpeg"
     alt="Dan Yamashita, Engenheiro Naval e Nível 3 END"
     width="400" height="400"
     loading="lazy">
```

---

### H5. Upgradar nó ProfessionalService em todas as páginas
**Impacto:** Habilita Business Knowledge Panel, aumenta entity resolution para sistemas de IA
**Esforço:** 1h
**Páginas:** index.html, en/index.html e o template base de todas as páginas

Adicionar ao bloco ProfessionalService sitewide:
```json
"@id": "https://www.simplendt.com.br/#organization",
"logo": {
  "@type": "ImageObject",
  "url": "https://www.simplendt.com.br/assets/images/favicon.svg"
},
"sameAs": [
  "https://www.linkedin.com/in/danyamashita/"
],
```
Corrigir:
```json
"areaServed": [
  { "@type": "Country", "name": "Brazil" },
  { "@type": "Place", "name": "Worldwide" }
]
```

---

### H6. Expandir auditorias-asme.html para 900+ palavras
**Impacto:** Remove risco de conteúdo fino para a página de maior valor comercial
**Esforço:** 1–2h de conteúdo
**Ação:** Adicionar seção "Tipos de selo ASME (U, U2, S, R, PP) e o que cada um exige de END" + expandir os itens de não-conformidade de listas para parágrafos curtos (consequência + remediação).

---

## MÉDIA PRIORIDADE — Corrigir em 1 mês

### M1. Upgrada Person schema em sobre.html
Adicionar: `alumniOf` (Escola Politécnica USP), `image` (foto), `description`, completar `hasCredential` com PED/RTPO e ASME, adicionar `@id`.

### M2. Adicionar Person + EducationalOccupationalCredential em certificacoes.html
A página com os dados mais ricos de credenciais não tem schema para eles. Adicionar schema com todos os 11 PCN (números individuais, datas de validade, `recognizedBy` BINDT/PCN) e os badges ASNT.

### M3. Expandir respostas FAQ para 134–167 palavras nos posts mais valiosos
Targets prioritários:
- "O que é RTPO na PED?" — expandir de ~90 para ~150 palavras
- "A certificação ISO 9712 emitida pela ABENDI atende à PED?" — expandir de ~60 para ~150 palavras
- "O ASME permite substituir radiografia por Phased Array?" — expandir de ~80 para ~150 palavras

### M4. Expandir blog SNT-TC-1A para 1.500+ palavras
Adicionar seções: SNT-TC-1A vs. CP-189, implementação de Prática Escrita do zero, requisitos ASME específicos vs. SNT-TC-1A base.

### M5. Adicionar seção ISO 9712 vs. SNT-TC-1A em servicos/qualificacoes.html
Aumenta profundidade tópica e captura segundo cluster de keywords.

### M6. Adicionar BreadcrumbList schema nos posts de blog
3 itens: Home > Blog > Título do artigo. Melhora aparência no SERP (breadcrumb trail).

### M7. Adicionar WebSite schema nas homepages PT e EN
Habilita elegibilidade para Sitelinks Searchbox.
```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "@id": "https://www.simplendt.com.br/#website",
  "name": "SimpleNDT",
  "url": "https://www.simplendt.com.br",
  "publisher": { "@id": "https://www.simplendt.com.br/#organization" }
}
```

### M8. Consolidar redirect HTTP non-www para single hop
Adicionar a `_redirects`:
```
http://simplendt.com.br/* https://www.simplendt.com.br/:splat 301!
```

### M9. Adicionar tempo de leitura e data visível nos posts
Bylines com "Publicado em [data]" visível no HTML (não apenas no schema) e "X min de leitura".

### M10. Adicionar política de privacidade
Necessária para visitantes europeus (audiência PED). URL sugerida: `/politica-de-privacidade.html`

### M11. Corrigir `href="style.css"` relativo em sobre.html → `/style.css`

### M12. Adicionar visibility guard ao loop rAF do canvas
```js
document.addEventListener('visibilitychange', () => {
  if (document.hidden) cancelAnimationFrame(rafId);
  else rafId = requestAnimationFrame(loop);
});
```

### M13. Reduzir animation-delay do H1 na homepage de 0.32s para 0.1s
Economiza ~220ms no LCP sem impacto visual perceptível.

---

## BAIXA PRIORIDADE — Backlog

### L1. Criar posts de blog em inglês para PAUT e ASME audits
Os clientes internacionais mais valiosos buscam em inglês. Dois dos melhores posts só existem em PT.

### L2. Criar 3 novos posts PT com gaps de alta demanda
- "NR-13 e END: o que a norma exige de qualificação de inspetores"
- "Transição de radiografia convencional para DR/CR: requisitos ASME"
- "ABENDI, SNQC, CEBRACI vs PCN vs ASNT: qual certificação aceitar"

### L3. Criar canal YouTube com 3–4 vídeos curtos técnicos
Correlação de 0.737 entre menções no YouTube e frequência de citação por IA — maior gap de autoridade de marca do site. Sugestões:
- "RTPO vs. Organismo Notificado: o que o fabricante brasileiro precisa saber"
- "SNT-TC-1A: responsabilidade do empregador na prática"
- "PAUT em vez de radiografia: quando o ASME permite"

### L4. Automatizar pings IndexNow após deploy Netlify
Build plugin ou post-deploy webhook para `api.indexnow.org`.

### L5. Adicionar atribuição de fonte nos dados de custo do post PAUT
Referências como "valores de referência de mercado 2025–2026" ou citar catálogos de fabricantes (Olympus, Eddyfi).

### L6. Adicionar sameAs com BINDT verification URL no Person schema
```json
"sameAs": [
  "https://www.linkedin.com/in/danyamashita/",
  "https://www.bindt.org/Certification/pcn-certificate-verification/"
]
```

### L7. Adicionar `<time datetime="">` nas datas de validade em certificacoes.html

### L8. Adicionar `og:type = "profile"` em sobre.html (atualmente `website`)

### L9. Buscar publicação externa: newsletter ABENDI, coluna em publicação industrial
Uma citação externa "Dan Yamashita, ASNT Level III, SimpleNDT" vale mais para entity resolution de IA do que 100 listagens internas de credenciais.

---

## Pontuação esperada pós-implementação

| Fase | Ações | Score estimado |
|------|-------|----------------|
| Atual | — | 76 / 100 |
| Após Crítico + Alta | C1–C3 + H1–H6 | ~82 / 100 |
| Após Médio | M1–M13 | ~87 / 100 |
| Após Baixo (parcial) | L1–L4 | ~91 / 100 |
