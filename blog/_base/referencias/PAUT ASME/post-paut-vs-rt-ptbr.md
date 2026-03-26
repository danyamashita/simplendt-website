# Phased Array (PAUT) em Substituição à Radiografia: Guia Completo conforme ASME

**Requisitos, custos, qualificação de procedimento e o dilema do Nível 3 no Brasil**

**Tags:** Phased Array PAUT, radiografia RT, ASME BPVC, selo ASME, procedimento de END, Nível 3 ASNT, qualificação de inspetores

**Por Dan Yamashita · Nível 3 ASNT/PCN · SimpleNDT**

---

## O que é Ultrassom Phased Array (PAUT)

O Ultrassom Phased Array (PAUT) é uma técnica avançada de ensaio não destrutivo (END) que utiliza transdutores multielementos para gerar e direcionar feixes ultrassônicos eletronicamente. Diferente do ultrassom convencional — que usa um único cristal emitindo um feixe fixo — o PAUT controla individualmente dezenas de elementos piezelétricos, aplicando atrasos programáveis (*time delays*) que permitem focalizar, defletir e varrer o feixe em múltiplos ângulos simultaneamente.

O resultado prático: uma única varredura de PAUT produz imagens setoriais (S-scan) ou lineares (E-scan) em tempo real, cobrindo todo o volume da solda com resolução e rastreabilidade superiores ao ultrassom manual. Quando combinado com encoders e scanners mecanizados, o PAUT gera registros digitais completos — os chamados *raw data* — que podem ser reanalisados a qualquer momento, oferecendo uma auditabilidade que a radiografia tradicional só alcança com o próprio filme físico.

A técnica é normatizada pelo ASME Boiler and Pressure Vessel Code (ASME BPVC), Section V, Article 4, que estabelece requisitos específicos para exame ultrassônico de soldas, incluindo apêndices mandatórios dedicados ao Phased Array. A possibilidade formal de substituir a radiografia pelo PAUT em vasos de pressão foi introduzida pelo histórico Code Case 2235 e hoje está incorporada diretamente na ASME BPVC Section VIII, Division 2, Parágrafo 7.5.5.

---

## RT vs. PAUT: Vantagens e Desvantagens

A escolha entre radiografia (RT) e Phased Array (PAUT) não é uma questão de superioridade absoluta de um método sobre o outro. Cada técnica tem domínios onde é inerentemente superior.

### Onde a Radiografia (RT) é superior

A radiografia é mais confiável na detecção de **defeitos volumétricos** como porosidades agrupadas e inclusões de escória. O contraste de densidade que esses defeitos geram na imagem é inconfundível. Além disso, o filme radiográfico (ou a imagem digital DR/CR) fornece um registro visual permanente, intuitivo e de fácil interpretação — inclusive para auditores que não dominam acústica. A RT também é menos sensível à rugosidade superficial e à geometria da peça: se o feixe de radiação penetra, a imagem aparece.

Outro ponto raramente discutido: a curva de aprendizado do intérprete de RT é mais curta. Um Nível II competente em radiografia aprende a avaliar filmes em meses. A interpretação de dados volumétricos de PAUT (C-scan, S-scan, B-scan sobrepostos) exige uma maturidade técnica significativamente maior.

### Onde o Phased Array (PAUT) é superior

O PAUT é dramaticamente superior na detecção de **defeitos planares** — trincas, falta de fusão e falta de penetração. Esses são exatamente os defeitos que a mecânica da fratura classifica como críticos para a integridade estrutural. Uma trinca com abertura de décimos de milímetro pode ser completamente invisível à radiografia se o feixe de raios-X não incidir perfeitamente paralelo ao plano da falha. Para o PAUT, essa mesma trinca é um espelho acústico que reflete massivamente o som de volta ao transdutor.

Adicionalmente, o PAUT oferece:

- **Resultados em tempo real**, sem necessidade de processamento químico ou espera.
- **Capacidade de dimensionamento** (sizing) — medição direta de altura e comprimento do defeito, essencial para avaliação por mecânica da fratura conforme ASME VIII Div. 2.
- **Ausência de radiação ionizante**, eliminando toda a cadeia de controles de proteção radiológica: licenciamento CNEN, dosimetria, isolamento de área, bunkers.
- **Inspeção paralela à produção** — não exige paralisação do chão de fábrica para isolamento, como a radiografia.

### Resumo comparativo

| Critério | Radiografia (RT) | Phased Array (PAUT) |
|---|---|---|
| Defeitos volumétricos (porosidade, escória) | Superior | Adequado |
| Defeitos planares (trinca, falta de fusão) | Limitada | Superior |
| Registro permanente e auditável | Filme/imagem digital | Raw data digital |
| Radiação ionizante | Sim (Ir-192, Se-75, Raio-X) | Não |
| Resultados em tempo real | Não | Sim |
| Dimensionamento de defeito (sizing) | Não direto | Sim |
| Impacto na produção (isolamento de área) | Alto | Nenhum |
| Sensibilidade à rugosidade/geometria | Baixa | Média a alta |

---

## Custos: Investimento Inicial vs. Custo Operacional

A análise de custos entre RT e PAUT se inverte dependendo de onde se olha — e é aqui que muitos gestores erram o planejamento.

### Custo de equipamento (CAPEX)

O PAUT exige investimento inicial significativamente maior. Equipamentos de Phased Array com capacidade para substituição de RT conforme ASME (como Olympus OmniScan, Eddyfi Gekko/Mantis, ou equivalentes) custam tipicamente de US$ 50.000 a US$ 150.000, dependendo da configuração. Some-se a isso o custo de transdutores, sapatas, scanners mecanizados e software de análise. Para um setup completo de campo com scanner, encoder e software de beam plotting, o investimento pode facilmente superar US$ 200.000.

Em comparação, uma fonte de Irídio-192 com colimador e acessórios de segurança, ou um gerador de Raio-X portátil, exige um investimento inicial menor — tipicamente entre US$ 30.000 e US$ 80.000.

### Custo operacional (OPEX)

É aqui que a conta vira. O custo por metro de solda inspecionada com PAUT é drasticamente inferior ao da radiografia:

- **RT:** Filmes ou placas de fósforo, produtos químicos de revelação (se filme convencional), reposição periódica de fontes radioativas (meia-vida do Ir-192: ~74 dias), dosímetros, monitoração ambiental, equipes maiores (operador + auxiliar de segurança), licenciamento junto à CNEN. Soma-se o custo indireto da paralisação de fábrica para isolamento da área.
- **PAUT:** Acoplante (gel ou água) e desgaste mecânico de sapatas. Não há consumíveis significativos. Uma equipe de PAUT é tipicamente menor e pode operar continuamente sem impactar outras atividades.

### Impacto na produtividade

Estimativas de chão de fábrica apontam que uma equipe de PAUT pode inspecionar cerca de **60 soldas por turno de 10 horas**, enquanto uma equipe de RT costuma atingir aproximadamente **30 soldas no mesmo período** — metade da produtividade. A diferença vem do tempo morto da radiografia: montagem de fonte/filme, isolamento de área, tempo de exposição, processamento e avaliação do filme.

Para fabricantes com produção seriada e alto volume de soldas, o PAUT se paga rapidamente. Para quem inspeciona poucas peças por ano, a radiografia pode ser economicamente mais racional — especialmente considerando o custo de qualificação de procedimento, como veremos a seguir.

---

## Qualificação de Procedimento: RT vs. PAUT — Uma Diferença Drástica

Este é o ponto que separa a teoria da prática e onde muitos fabricantes se surpreendem.

### Radiografia: qualificação contínua e simplificada

A "qualificação" da radiografia é, na prática, contínua e autoverificável. O ASME BPVC Section V, Article 2 exige que cada exposição radiográfica contenha um Indicador de Qualidade de Imagem (IQI, também chamado penetrômetro). Se o filme ou imagem digital revela o furo ou arame exigido pelo código com a densidade óptica correta, o procedimento demonstrou sua sensibilidade naquela exposição. Não há exigência de blocos com trincas artificiais. Não há Demonstração de Performance formal.

Isso significa que a qualificação de um procedimento de RT é **padrão e direta**. Para uma fábrica em processo de certificação ou recertificação do selo ASME (U stamp, U2, S, R, PP), a demonstração ao Authorized Inspector (AI) durante a auditoria é relativamente simples: o procedimento escrito, os IQIs, a técnica de exposição e os filmes falam por si.

### Phased Array: Demonstração de Performance formal (PDQ)

Para substituir a radiografia, o ASME BPVC Section V, Article 4, Mandatory Appendix IX exige uma **Demonstração de Performance (PDQ)** formal. Na prática, isso significa:

1. **Fabricar blocos de demonstração (mockups)** — réplicas da junta de produção (mesmo material, espessura, configuração de chanfro e processo de soldagem).
2. **Inserir defeitos artificiais** — no mínimo 3 falhas (superficiais e subsuperficiais) com dimensões controladas.
3. **Executar a varredura e provar detecção** — o operador deve detectar e dimensionar as falhas dentro de tolerâncias milimétricas (tipicamente ±0,5 mm para altura).

Além disso, o PAUT possui uma **lista extensa de Variáveis Essenciais** (Tabela T-421 do ASME V Art. 4). Qualquer mudança em:

- Configuração e espessura da junta
- Ângulos de propagação e técnica (S-scan, E-scan)
- Leis focais (profundidade, plano, número de elementos)
- Tipo, frequência e tamanho do transdutor/sapata
- Método de dimensionamento (sizing)

...exige que **todo o processo de demonstração seja refeito.** Isso inclui fabricar novos mockups se o material ou espessura mudar.

### Implicação prática: quando cada método faz mais sentido

A conclusão é direta:

**A radiografia é mais adequada para:**
- Processos de certificação e recertificação do selo ASME, onde a demonstração ao AI precisa ser rápida e padronizada.
- Inspeção de **poucas peças**, peças não seriadas ou com grande variedade de configurações de junta — já que cada configuração diferente de PAUT exigiria uma qualificação específica.
- Fabricantes com baixo volume ou grande diversidade de produtos.

**O Phased Array é mais adequado para:**
- Fabricação seriada com **alto volume de soldas em configurações repetitivas** — onde o investimento na qualificação do procedimento se dilui.
- Projetos sob ASME Section VIII, Division 2, onde a avaliação por mecânica da fratura exige dimensionamento preciso de defeitos.
- Ambientes onde a radiação ionizante é restritiva (plataformas offshore, plantas em operação, refinarias).

Para fabricantes que precisam de [procedimentos de PAUT conforme ASME V](https://simplendt.com.br/servicos/phased-array), a SimpleNDT elabora documentação completa incluindo scan plan, beam plotting e qualificação de pessoal.

---

## O Nível 3 para Phased Array sob ASME: O Dilema do Ovo e da Galinha

Aqui está um dos pontos mais críticos — e menos discutidos — da implementação do PAUT conforme ASME.

### Responsabilidades do Nível 3 em PAUT

Conforme o ASME BPVC, o Nível 3 responsável pelo programa de PAUT acumula as seguintes atribuições:

- Desenvolvimento e aprovação do **procedimento de exame** e do **Scan Plan** (modelagem acústica e geométrica da cobertura do feixe sobre a junta).
- **Especificação dos blocos de calibração e demonstração** conforme os requisitos do código (material, espessura, tipo e dimensão dos defeitos artificiais).
- Condução ou supervisão da **Demonstração de Performance (PDQ)**.
- **Qualificação e certificação de pessoal** Nível I e Nível II em Phased Array, conforme a Written Practice da empresa.

### O requisito ASME para o Nível 3

O ASME BPVC Section V e a prática recomendada SNT-TC-1A exigem que o Nível 3 responsável pela [qualificação de pessoal](https://simplendt.com.br/servicos/qualificacoes) em Phased Array atenda a requisitos específicos de competência no método. Isso inclui, de forma geral, ser certificado ou ter demonstrado competência prática em UT Phased Array — não basta ser Nível 3 em ultrassom convencional.

No esquema SNT-TC-1A (employer-based), o Nível 3 da empresa é quem treina, avalia e certifica os Níveis I e II. Mas aqui surge o dilema: **para um profissional Nível 3 se submeter ao exame prático de Nível II em PAUT — necessário para demonstrar competência no método — ele precisa ser avaliado por outro Nível 3 que já cumpra com os requisitos ASME para Phased Array.**

E onde está esse outro Nível 3? Se poucos profissionais no país cumprem integralmente os requisitos ASME para PAUT, o primeiro Nível 3 que tenta se qualificar encontra uma barreira circular: precisa de alguém qualificado para qualificá-lo, mas esse alguém enfrenta o mesmo problema. É, na essência, um **dilema do ovo e da galinha**.

### A solução: ir à fonte

A saída para esse impasse é buscar a qualificação diretamente nos centros de exame que detêm a infraestrutura e os profissionais já qualificados — o que, na prática, significa **ir aos Estados Unidos** para se submeter aos exames em condições que atendam integralmente aos requisitos ASME e ASNT.

Foi o caminho que a [SimpleNDT](https://simplendt.com.br/sobre) adotou. Dan Yamashita realizou os exames de Phased Array nos EUA, obtendo dupla certificação Nível 3 — ASNT (SNT-TC-1A) e PCN (ISO 9712) — em UT convencional e Phased Array, em conformidade integral com os requisitos do código ASME.

O ponto relevante aqui é estrutural, não comercial: na cadeia employer-based da SNT-TC-1A, **toda a legitimidade do programa de PAUT de uma empresa depende da qualificação do seu Nível 3.** Se o Nível 3 não cumpre os requisitos, toda a cadeia abaixo — Níveis II e I — fica comprometida. É exatamente isso que auditores ASME verificam durante a [auditoria de selo](https://simplendt.com.br/servicos/auditorias-asme).

---

## FAQ — Perguntas Frequentes

### O ASME permite substituir radiografia por Phased Array em qualquer situação?

Não. A substituição é permitida sob condições específicas estabelecidas pelo ASME BPVC Section V, Article 4, Mandatory Appendix IX, e referenciada pelo Section VIII (Div. 1 e Div. 2). O Code Case 2235 foi o marco original, hoje incorporado na Div. 2, Par. 7.5.5. A substituição exige técnicas avançadas (PAUT e/ou TOFD) com varredura encodada — ultrassom manual convencional não é aceito como substituto. Além disso, a organização deve completar uma Demonstração de Performance (PDQ) formal com blocos de demonstração contendo defeitos artificiais.

Existem também **restrições de espessura mínima**. O ASME Section VIII, Division 2 permite a substituição para juntas com espessura igual ou superior a 6 mm (¼ in.). Já o ASME Section I exige espessura mínima de 13 mm (½ in.), embora existam Code Cases que estendem a aplicação para a faixa de 6 a 13 mm. Os limites variam conforme a seção do código aplicável, e devem ser verificados caso a caso.

### Qual método é melhor para obter o selo ASME: radiografia ou Phased Array?

Depende do contexto. Para processos de certificação e recertificação do selo ASME — especialmente se a fábrica tem produção variada e baixo volume — a radiografia é mais prática porque a qualificação do procedimento é mais simples e universal. O Phased Array é mais vantajoso quando há produção seriada com configurações de junta repetitivas, onde o investimento na qualificação do procedimento se justifica pelo ganho de produtividade e pela eliminação da radiação ionizante.

### Preciso de um Nível 3 específico em Phased Array ou basta Nível 3 em UT convencional?

Para atender aos requisitos do ASME, o Nível 3 responsável pelo programa de PAUT deve demonstrar competência específica no método. Ser Nível 3 apenas em UT convencional não é suficiente para aprovar scan plans, validar Demonstrações de Performance e certificar Níveis II em Phased Array. Essa é uma das não conformidades mais comuns em auditorias ASME envolvendo PAUT.

### O que acontece se meu Nível 3 não cumprir os requisitos ASME para PAUT?

Toda a cadeia de certificação de pessoal fica comprometida. Se o auditor (Authorized Inspector) constatar que o Nível 3 não possui qualificação demonstrável em PAUT, os laudos emitidos por Níveis II certificados por esse profissional podem ser invalidados retroativamente. Isso pode resultar em findings graves na auditoria e, no pior caso, na suspensão do selo ASME.

### Por que tão poucos Níveis 3 no Brasil são qualificados em PAUT conforme ASME?

Porque o processo é circular: para se qualificar em PAUT como Nível 3 no esquema SNT-TC-1A, é preciso ser avaliado por outro Nível 3 já qualificado no método. Como o PAUT é uma especialização relativamente recente e o mercado brasileiro historicamente se apoiou mais na radiografia, poucos profissionais iniciaram o ciclo. A solução prática é buscar a qualificação diretamente nos EUA, onde a infraestrutura e os profissionais qualificados já existem — exatamente o caminho que a SimpleNDT adotou.

### O Phased Array é sempre mais caro que a radiografia?

Não. O PAUT tem custo de equipamento (CAPEX) maior, mas custo operacional (OPEX) drasticamente menor. Para alto volume de soldas, o PAUT é significativamente mais barato por metro inspecionado. Para baixo volume ou peças unitárias, a radiografia pode ser mais econômica considerando que não exige o investimento em qualificação de procedimento específico por configuração de junta.

### A qualificação de procedimento PAUT vale para qualquer espessura e material?

Não. Cada combinação de material, faixa de espessura e configuração de junta é uma Variável Essencial conforme a Tabela T-421 do ASME V Art. 4. Mudar qualquer uma dessas variáveis exige uma nova Demonstração de Performance com mockups específicos. Por isso o PAUT é mais econômico em produção seriada — a qualificação é feita uma vez e aplicada a centenas de juntas idênticas.

Vale reforçar que a substituição de RT por PAUT tem **limites mínimos de espessura** que variam por seção do código: 6 mm (¼ in.) para ASME Section VIII Div. 2, e 13 mm (½ in.) para ASME Section I (com Code Cases disponíveis para a faixa intermediária de 6 a 13 mm). Juntas abaixo desses limites não são elegíveis para a substituição e devem continuar utilizando radiografia.

### Posso usar ultrassom convencional manual para substituir a radiografia conforme ASME?

Não. O ASME restringe a substituição exclusivamente a técnicas avançadas com varredura encodada e registro digital contínuo — PAUT e/ou TOFD. O ultrassom convencional puramente manual não possui a rastreabilidade e a reprodutibilidade exigidas pelo código para substituir o registro permanente que a radiografia fornece.

---

## Próximo Passo

Se sua empresa está avaliando a transição de radiografia para Phased Array, ou precisa de um Nível 3 qualificado em PAUT conforme ASME para auditorias, procedimentos ou qualificação de pessoal, a [SimpleNDT](https://simplendt.com.br/servicos/phased-array) pode ajudar.

Dan Yamashita é certificado Nível 3 ASNT e PCN em UT convencional e Phased Array, com exames realizados nos Estados Unidos em conformidade integral com os requisitos ASME. Atua em elaboração de procedimentos, scan plans, Demonstração de Performance e suporte a auditorias de selo.

[Fale com a SimpleNDT pelo WhatsApp](https://wa.me/+5511991612503) ou visite [simplendt.com.br/contato](https://simplendt.com.br/contato).

---

## Meta Dados — PT-BR

- **Title tag:** Phased Array vs Radiografia ASME: Guia Completo PAUT
- **Meta description:** Guia técnico sobre substituição de radiografia por Phased Array (PAUT) conforme ASME: vantagens, custos, qualificação de procedimento e requisitos do Nível 3.
- **URL slug:** phased-array-substituicao-radiografia-asme
- **Tags:** Phased Array PAUT, radiografia RT, ASME BPVC, selo ASME, Nível 3 ASNT, procedimento de END, qualificação de inspetores
- **Keywords principais:** Phased Array substituição radiografia ASME, PAUT vs RT, procedimento PAUT ASME
- **Keywords secundárias:** Code Case 2235, scan plan, Demonstração de Performance, Nível 3 Phased Array, selo ASME auditoria, SNT-TC-1A, ASME Section V Article 4

## Links Internos Utilizados

1. simplendt.com.br/servicos/phased-array
2. simplendt.com.br/servicos/qualificacoes
3. simplendt.com.br/servicos/auditorias-asme
4. simplendt.com.br/sobre
5. simplendt.com.br/contato

## Posts Relacionados Futuros (sugestão)

1. **Scan Plan para PAUT conforme ASME: O que o Nível 3 precisa entregar** → foco em beam plotting, cobertura angular e documentação
2. **Demonstração de Performance (PDQ) ASME: Passo a Passo para Qualificação de PAUT** → mockups, defeitos artificiais, tolerâncias
3. **Auditoria ASME e END: Os 5 Findings Mais Comuns em Fabricantes Brasileiros** → non-conformidades recorrentes, incluindo PAUT
4. **ASME Section VIII Div. 1 vs. Div. 2: Impacto nos Ensaios Não Destrutivos** → workmanship vs. fitness-for-service, eficiência de junta
5. **Qualificação de Pessoal END conforme SNT-TC-1A: O Papel Real do Nível 3** → responsabilidades, Written Practice, armadilhas comuns
