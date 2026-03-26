# Base de Conhecimento — Blog SimpleNDT

Este é o ponto de partida para escrever qualquer artigo novo do blog.

---

## Como usar esta pasta

### Estrutura
```
blog/
├── _base/
│   ├── COMO-USAR.md          ← este arquivo
│   ├── TEMAS.md              ← ideias e fila de artigos
│   └── referencias/          ← cole aqui seus documentos de referência
│       ├── procedimentos/    ← procedimentos seus, templates, exemplos reais
│       ├── normas/           ← trechos de normas (ASME, ISO 9712, SNT-TC-1A...)
│       └── clientes/         ← perguntas frequentes de clientes, dúvidas reais
└── [artigos publicados].html
```

---

## Passo a passo para escrever um novo artigo

### 1. Coloque referências na pasta `referencias/` (opcional, mas recomendado)
Exemplos do que você pode colocar lá:
- Um procedimento de UT que você escreveu (PDF ou .docx)
- Trecho de norma relevante (.txt ou .pdf)
- Anotações suas sobre o tema (.txt, .md)
- Perguntas que clientes te fazem sobre o assunto

Eu leio esses arquivos antes de escrever e uso o conteúdo para garantir precisão técnica e usar a sua terminologia.

### 2. Me peça o artigo assim:
> "Escreva um artigo para o blog sobre [TEMA]. Use as referências em `referencias/`."

Ou, sem referências:
> "Escreva um artigo para o blog sobre PAUT como substituto da radiografia no ASME."

### 3. O que eu entrego
Um arquivo `.html` completo, já:
- No estilo visual da SimpleNDT (dark theme, tipografia correta)
- Com todos os SEO tags (title, description, schema JSON-LD, hreflang)
- Com FAQ ao final (5+ perguntas para rich snippets no Google)
- Com CTA linkando para o serviço relevante
- Com byline, data e tempo de leitura
- Pronto para colar na pasta `blog/` e publicar

---

## Boas práticas de conteúdo

- **Tom**: técnico mas direto. Sem enrolação. Como você fala com um engenheiro de inspeção.
- **Extensão**: 1.200–2.500 palavras por artigo
- **Público-alvo**: engenheiros, responsáveis de qualidade, gestores de inspeção
- **Diferencial**: profundidade técnica real — não é resumo de Wikipedia
- **Normas**: sempre citar a edição/versão correta (ex.: ASME BPVC Section V, 2023 Edition)
- **Linguagem**: PT-BR primário. Sempre criar versão EN junto se possível.

---

## Checklist antes de publicar

- [ ] Arquivo salvo em `blog/slug-do-artigo.html`
- [ ] Versão EN em `en/blog/slug-in-english.html`
- [ ] `sitemap.xml` atualizado com a nova URL
- [ ] `blog/index.html` atualizado com o card do novo artigo
- [ ] Artigo revisado tecnicamente por Dan

---

## Dicas de SEO para END

Os termos que mais trazem tráfego qualificado para a SimpleNDT:

**Português:**
`nível 3 END`, `RTPO Brasil`, `PED 2014/68/EU`, `selo ASME Brasil`, `SNT-TC-1A qualificação`,
`ISO 9712 nível 3`, `phased array PAUT`, `procedimento END ASME`, `qualificação de inspetores END`

**Inglês:**
`NDT Level 3`, `RTPO PED`, `ASME stamp audit`, `SNT-TC-1A qualification`,
`ISO 9712 Level 3`, `phased array PAUT`, `NDT procedure ASME`
