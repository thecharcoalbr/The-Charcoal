# THE CHARCOAL OS — PRODUCT & SAAS STRATEGY

**Documento:** TCOS-020
**Fase:** 020 — Product & SaaS Strategy
**Natureza:** Documento exclusivamente de estratégia de produto e de negócio comercial (Camada de Produto). NÃO constitui arquitetura, NÃO constitui implementação, NÃO constitui código, NÃO define tecnologia. NÃO cria, altera ou remove nenhum módulo, Serviço, tela, componente, Fluxo, Funcionalidade ou Regra de Negócio. NÃO altera nenhum documento oficial congelado — atua exclusivamente **acima** da arquitetura já aprovada, como a camada que transforma o sistema já especificado em um produto SaaS comercializável.
**Baseline referenciada:** v1.0.0 (TCOS-000 a TCOS-018, congelados) + TCOS-019A (Fases 1 e 2 aprovadas — Identidade Visual e Biblioteca Visual Oficial) + Auditoria Arquitetural Corretiva de 2026-08-02 (registrada no `PROJECT_MEMORY.md`), sob a autoridade da Constituição Permanente do Projeto.
**Documentos-fonte desta fase:** Constituição Permanente; `THE_CHARCOAL_OS_PROJECT_CONSTITUTION.md`; `THE_CHARCOAL_OS_DOMAIN_MODEL.md` (TCOS-002); `THE_CHARCOAL_OS_BUSINESS_RULES_SPECIFICATION.md` (TCOS-002A); `THE_CHARCOAL_OS_SYSTEM_ARCHITECTURE.md` (TCOS-006); `THE_CHARCOAL_OS_AI_ARCHITECTURE.md` (TCOS-013); `THE_CHARCOAL_OS_INFRASTRUCTURE_ARCHITECTURE.md` (TCOS-014, Capítulos 25–26 — Multiempresa/Multitenancy); `THE_CHARCOAL_OS_SECURITY_AND_PRIVACY_ARCHITECTURE.md` (TCOS-012); `THE_CHARCOAL_OS_UX_UI_SPECIFICATION.md` (TCOS-005); `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018); `THE_CHARCOAL_OS_EXECUTIVE_GLOBAL_AUDIT.md` (TCOS-016); `PROJECT_MEMORY.md`.
**Status:** Em construção — primeira apresentação completa das 30 seções solicitadas, aguardando Auditoria Estratégica e aprovação do proprietário.

---

## EXECUTIVE MEMORY

Esta fase inicia oficialmente a **Camada de Produto** do THE CHARCOAL OS: a camada que decide como o sistema já especificado (27 módulos, 15 Serviços, 30 telas, identidade visual e biblioteca de componentes já oficiais) é embalado, precificado, comunicado, vendido, adotado e retido como um **produto SaaS comercial**, capaz de competir internacionalmente. Nada nesta camada modifica o que o sistema *é* (arquitetura, dado, regra, tela) — apenas define como o sistema *chega ao mercado, gera receita recorrente e se sustenta como negócio*.

**Auditoria de Abertura (executada antes de qualquer definição):**
- Constituição Permanente: relida integralmente — nenhuma cláusula de governança impede a criação de uma camada de produto/negócio; a Política de Change Request (Capítulo 15) permanece a única via de alteração de documento já congelado, não invocada aqui, pois nenhum documento congelado é alterado.
- Confirmado, por busca em todos os 24 documentos oficiais já existentes: **nenhum documento anterior define estratégia comercial, precificação, planos, ICP, personas, GTM (go-to-market), métricas SaaS ou modelo de monetização.** Este é, portanto, um documento genuinamente novo, sem sobreposição com nenhum já existente — não há risco de duplicidade.
- **Achado crítico herdado, aplicável a esta fase com força total:** o risco **R-000-03** — "hipótese de domínio de negócio (produção culinária em brasa/carvão via Eventos) nunca formalmente confirmada pelo proprietário" — é classificado no TCOS-016 como **"o risco mais relevante do projeto"**, e permanece **ativo**. Toda a Camada de Arquitetura já foi construída sobre essa hipótese, de forma consciente e registrada. Esta fase, ao definir ICP, Personas, Posicionamento, Diferenciais Competitivos, SWOT e Moat, **herda a mesma hipótese com o mesmo grau de incerteza** — não a resolve, não a confirma, e não pode fingir que ela foi resolvida. Todo conteúdo desta fase que dependa do domínio de negócio específico (produção artesanal/culinária via Eventos, ex.: churrascarias, casas de eventos, catering) está e permanece condicionado à confirmação do proprietário. Onde isso for relevante, o texto reafirma essa condição explicitamente, em vez de apenas marcar `[Inferência estratégica]` uma única vez e presumir a leitura implícita.
- Pendências herdadas adicionais diretamente relevantes a esta fase: decisão de negócio sobre Multiempresa/Multifilial (M-006-01/M-007-01), já refletida na reserva estrutural do atributo "Organização" (TCOS-007 §7.6) e nos dois modelos de Multitenancy já formalizados (TCOS-014, Capítulo 26) — usados nesta fase apenas como **restrição de compatibilidade** (o que a estratégia de planos/expansão pode assumir como já sustentado pela infraestrutura), nunca como decisão de negócio tomada por este documento.
- Nenhuma inconsistência, sobreposição ou conflito com documento já oficial foi encontrado. A construção desta fase está autorizada a prosseguir.

**Convenção de rastreabilidade desta fase:** todo conteúdo que extrapola diretamente de um fato já documentado é identificado como **[Inferência estratégica]** — a mesma disciplina já usada no TCOS-018 (`[Inferência visual]`) e no TCOS-019A, aplicada agora a decisões de negócio em vez de decisões visuais. Nenhuma inferência estratégica altera, substitui ou contradiz nenhum documento já oficial.

---

## 1. Visão do Produto

O THE CHARCOAL OS é o sistema operacional de gestão para negócios de produção artesanal e eventos — a ponte entre o ofício (a Receita, a Ficha Técnica, o ponto exato da execução) e a gestão (o caixa, a margem, o cliente, a decisão). **[Inferência estratégica, condicionada a R-000-03]** A visão de produto assume, como toda a arquitetura já assume, que o segmento-alvo é o de negócios cuja operação central gira em torno de Produção sob demanda vinculada a Eventos — o exemplo ilustrativo mais recorrente em todo o corpus documental é o de churrascarias, casas de eventos e operações de catering, mas a arquitetura (Capítulo 2, Filosofia Arquitetural, TCOS-006) já foi deliberadamente construída para não travar em um único subsegmento.

**Visão de 10 anos (síntese, detalhada no Capítulo 30):** tornar-se o sistema de gestão de referência para negócios de produção artesanal e eventos, primeiro no Brasil, depois na América Latina e em mercados de culinária tradicional/artesanal com estrutura comercial semelhante — reconhecido não por ser genérico, mas por ser **profundamente correto** para este tipo específico de operação, onde sistemas de gestão genéricos (ERPs horizontais, planilhas, sistemas de ponto de venda) sistematicamente falham em capturar a relação entre Ficha Técnica, Produção e margem real.

## 2. Posicionamento de Mercado

**Categoria:** não um ERP genérico, não um sistema de ponto de venda, não uma ferramenta de agendamento de eventos isolada — um **sistema operacional vertical** que une, em um único modelo de dados coerente (já unificado desde o TCOS-002, Domain Model), o ciclo completo: Lead → Cliente → Orçamento → Contrato → Evento → Produção → Suprimentos → Financeiro → Indicadores.

**Contra quem o produto se posiciona [Inferência estratégica]:**
- *Planilhas e controles manuais* — o concorrente real da maioria dos negócios deste porte hoje. O produto vence por eliminar retrabalho e erro de cálculo de margem, não por ter mais funcionalidades.
- *ERPs genéricos horizontais* — vencem em abrangência contábil/fiscal, perdem em não entender o que é uma Ficha Técnica, um Lote com validade, ou a diferença entre Financeiro Pessoal e Empresarial de um negócio familiar (RN documentada desde o TCOS-002A). O produto vence por já vir modelado para este domínio, sem meses de customização.
- *Sistemas de PDV/comanda* — vencem no balcão, não entendem produção sob encomenda, ficha técnica versionada, nem gestão de Evento. O produto vence por cobrir o ciclo de produção e evento que o PDV nunca tenta resolver.

**Afirmação de posicionamento:** "O sistema que entende que cada Evento começa numa Receita e termina numa margem real."

## 3. ICP (Ideal Customer Profile)

**[Inferência estratégica, condicionada a R-000-03 — este ICP é construído sobre a mesma hipótese de domínio ainda não confirmada pelo proprietário; deve ser revalidado no momento em que R-000-03 for formalmente resolvido.]**

| Dimensão | Perfil |
|---|---|
| Porte | Pequeno a médio negócio de produção artesanal/eventos — de operação individual/familiar até equipe de 15–40 pessoas (compatível com os Perfis de Segurança já modelados no TCOS-012: Proprietário, Administrativo, Operacional, Comercial, BI/Direção) |
| Estrutura societária | Frequentemente familiar ou com poucos sócios — justifica a separação já modelada entre Financeiro Pessoal e Empresarial (Módulos 02/03) como diferencial reconhecível, não genérico |
| Maturidade de gestão | Já sente dor de controle (planilhas, WhatsApp, caderno), mas ainda não tem orçamento ou apetite para um ERP horizontal complexo |
| Ciclo de operação | Produção vinculada a Evento/encomenda — não apenas venda de prateleira |
| Geografia inicial | Brasil, mercado doméstico — expansão internacional tratada no Capítulo 15 |

**Anti-ICP (quem o produto não deve tentar atender neste horizonte):** indústria de produção em larga escala com múltiplas fábricas (exigiria MES/SCM dedicado); redes de franquia com centenas de unidades simultâneas (exigiria multiempresa/multitenancy já além do que M-006-01 decidiu); negócios sem nenhum componente de Produção ou Evento (o modelo de dados perde a maior parte do seu diferencial).

## 4. Personas

**[Inferência estratégica, condicionada a R-000-03]** Personas construídas diretamente sobre os 5 Perfis de acesso já formalizados no TCOS-012 (Segurança e Privacidade) — não são personas novas inventadas para marketing, são a mesma modelagem de usuário já oficial, lida sob a ótica de produto:

1. **A Proprietária/o Proprietário** (Perfil Proprietário) — dona da visão consolidada (Dashboard CEO), decide sobre Metas, aprova Fechamento de Período, é quem sente o problema de "não saber a margem real" com mais intensidade. É a persona de maior valor percebido e maior propensão a pagar.
2. **O Administrativo/Financeiro** (Perfil Administrativo) — opera o dia a dia do Financeiro Pessoal e Empresarial, Compras, Contratos. Sensível a redução de retrabalho e erro manual.
3. **O Operacional/Produção** (Perfil Operacional) — usa Fichas Técnicas, Produção, Estoque, Escalas. Sensível a facilidade de uso em campo/cozinha, não a relatórios.
4. **O Comercial** (Perfil Comercial) — usa CRM, Leads, Orçamentos. Sensível a velocidade de resposta ao cliente e taxa de conversão.
5. **A Direção/Sócios sem operação diária** (Perfil BI/Direção, "Herança Consolidada") — consome apenas Indicadores e Dashboards. É a persona de maior propensão a upsell para planos com Inteligência Artificial e Metas avançadas.

## 5. Jobs To Be Done

Formulados a partir das Regras de Negócio e Funcionalidades já oficiais (TCOS-002A/TCOS-003), não inventados:

- "Quando eu fecho um Evento, quero saber, sem calcular na mão, se ele realmente deu lucro." (Ficha Técnica → Custo → Margem, RN já documentadas)
- "Quando um Lote está perto de vencer, quero saber antes de perder o produto." (Módulo 17, já com alerta de vencimento)
- "Quando fecho o mês, quero separar o que é retirada minha do que é da empresa, sem misturar." (Módulos 02/03, isolamento já documentado)
- "Quando decido um novo Evento, quero saber se tenho capacidade de produção e estoque antes de confirmar, não depois." (RN-006, já arquiteturalmente prevista)
- "Quando olho meu Dashboard, quero uma resposta, não um relatório para interpretar." (Cadeia de atualização automática de Indicadores, TCOS-009 Capítulo 7)

## 6. Diferenciais Competitivos

1. **Modelo de dados verticalizado desde a origem** — Ficha Técnica, Lote, Evento e margem já nascem conectados; concorrentes genéricos exigem customização para simular o mesmo.
2. **Separação nativa Financeiro Pessoal × Empresarial** — resposta direta a uma dor real de negócios familiares, ausente na maioria dos ERPs genéricos.
3. **IA como assistente, nunca como caixa-preta autônoma** — toda sugestão de IA exige confirmação humana (TCOS-013, Capítulo 8) e é visualmente distinguível (Roxo-IA, PF-06) — diferencial de confiança, não apenas de funcionalidade.
4. **Cadeia única e auditável de atualização de Indicadores** — nenhum Dashboard "desatualizado" ou calculado por caminho divergente (TCOS-009, Capítulo 7).
5. **Arquitetura já pronta para Multiempresa/Multitenancy** sem reconstrução (TCOS-014, Capítulos 25–26) — permite expansão para redes pequenas sem reescrever o produto.
6. **Identidade visual e Design System profissionais desde o dia 1** (TCOS-018/019A) — percepção de qualidade compatível com produtos internacionais de referência, sem parecer "sistema de pequena empresa".

## 7. Proposta Única de Valor (UVP)

**"O único sistema que transforma cada Ficha Técnica em margem real, e cada Evento em decisão informada — sem exigir que você vire contador."**

Decomposição: (a) unifica produção e finanças em um único modelo, eliminando a planilha-ponte; (b) separa vida pessoal e empresarial do proprietário, um problema real e mal resolvido no mercado; (c) entrega inteligência (IA) como sugestão explicável, não como promessa vaga de automação.

## 8. Estratégia de Monetização

Modelo recomendado: **assinatura recorrente (SaaS puro), por Organização, com cobrança mensal ou anual**, alinhado ao modelo de custo previsível já esperado pelo ICP (Capítulo 3). Nenhuma cobrança por módulo isolado no lançamento (aumentaria fricção de adoção); expansão para add-ons tratada no Capítulo 9 (Planos) e Capítulo 11 (Marketplace, oportunidade futura).

**Alavancas de receita recorrente identificadas:**
- Assinatura base por Plano (Capítulo 9).
- Upsell por volume de uso (nº de Usuários/Perfis ativos, nº de Eventos/mês) — compatível com a modelagem já existente de Perfis (TCOS-012) sem exigir nova arquitetura.
- Upsell de módulos de Inteligência Artificial (Capítulo 12) como camada premium — compatível com a arquitetura de IA já desacoplada (TCOS-013), que permite ativar/desativar por Organização sem afetar o núcleo.
- Cross-sell de Multiempresa/Multifilial (Capítulo 14) quando M-006-01 for resolvido — apoiado por infraestrutura já preparada (TCOS-014, Capítulo 26).

## 9. Planos do SaaS

**[Inferência estratégica]** Estrutura de 3 planos, construída exclusivamente sobre agrupamentos dos 27 módulos já existentes — nenhum módulo novo, nenhuma funcionalidade nova:

| Plano | Público | Módulos incluídos (dos 27 já oficiais) |
|---|---|---|
| **Essencial** | Operação individual/familiar iniciando a digitalização | Núcleo comercial e operacional: Clientes, Leads, Orçamentos, Contratos, Eventos, Receitas, Fichas Técnicas, Compras, Estoque, Financeiro Pessoal, Financeiro Empresarial, Bancos, Configurações, Administração do Sistema |
| **Profissional** | Operação estabelecida, já com equipe | Tudo do Essencial + Engenharia de Custos, Precificação, Lotes, Equipamentos, Funcionários, Escalas, Documentos, Dashboard CEO completo, Metas |
| **Avançado** | Operação madura, múltiplos sócios/BI | Tudo do Profissional + CRM, Marketing, Inteligência Artificial (Capítulo 12), Herança Consolidada de BI/Direção (TCOS-012) |

Nenhum Perfil de segurança já existente é reservado a um plano específico — a segmentação ocorre por **módulo habilitado por Organização**, um conceito de produto novo que **não exige alteração de arquitetura**: tecnicamente equivale a um subconjunto dos 15 Serviços já habilitado por Organização, mecanismo já compatível com o isolamento lógico por "Organização" (TCOS-007 §7.6).

## 10. Módulos por Plano

Detalhamento do Capítulo 9 por módulo individual (numeração igual à do TCOS-006, Capítulo 4):

| Módulo | Essencial | Profissional | Avançado |
|---|:---:|:---:|:---:|
| 01 Dashboard CEO (básico) | ✓ | ✓ | ✓ |
| 02/03 Financeiro Pessoal/Empresarial | ✓ | ✓ | ✓ |
| 04 CRM | — | — | ✓ |
| 05/06 Clientes/Leads | ✓ | ✓ | ✓ |
| 07 Eventos | ✓ | ✓ | ✓ |
| 08/09 Orçamentos/Contratos | ✓ | ✓ | ✓ |
| 10 Produção | ✓ | ✓ | ✓ |
| 11 Engenharia de Custos | — | ✓ | ✓ |
| 12/13 Receitas/Fichas Técnicas | ✓ | ✓ | ✓ |
| 14 Precificação | — | ✓ | ✓ |
| 15/16 Compras/Estoque | ✓ | ✓ | ✓ |
| 17 Lotes | — | ✓ | ✓ |
| 18/19/20 Equipamentos/Funcionários/Escalas | — | ✓ | ✓ |
| 21 Marketing | — | — | ✓ |
| 22 Inteligência Artificial | — | — | ✓ |
| 23 Documentos | — | ✓ | ✓ |
| 24/25 Configurações/Administração | ✓ | ✓ | ✓ |
| 26 Metas | — | ✓ | ✓ |
| 27 Bancos | ✓ | ✓ | ✓ |

Esta tabela é uma decisão **comercial de empacotamento**, não uma alteração da Matriz de Dependências entre Módulos (TCOS-006, Capítulo 4) — todo módulo habilitado continua respeitando integralmente suas dependências já documentadas, independentemente do plano.

## 11. Marketplace Futuro

**Oportunidade estratégica (Backlog Estratégico — nenhuma arquitetura autorizada nesta fase):** um marketplace de extensões — templates de Ficha Técnica por segmento culinário, integrações com meios de pagamento/bancos além dos já previstos (TCOS-009), e futuramente conectores de terceiros — é uma via natural de expansão de receita (comissão/assinatura de extensão) e de aumento do Moat (Capítulo 29), aproveitando o Event Bus já desacoplado (TCOS-006, Capítulo 7) como ponto de extensão natural sem reconstrução. Registrado exclusivamente como oportunidade futura — nenhuma Funcionalidade, Módulo, Serviço ou API pública é criada por este documento.

## 12. Estratégia de Inteligência Artificial

A IA já é, por desenho arquitetural (TCOS-013), um diferencial competitivo pronto para ser comercializado, não uma promessa futura:
- **Confiança como posicionamento:** toda sugestão exige confirmação humana (Capítulo 8, TCOS-013) e é visualmente marcada (Roxo-IA, PF-06) — mensagem comercial: "IA que sugere, você decide."
- **6 Extensões Estruturais já preparadas** (M-013-03, priorização de negócio ainda pendente): Produção, Estoque, Eventos, CRM, Marketing, Indicadores — cada uma é um candidato natural a feature de upsell dentro do Plano Avançado (Capítulo 9), sem exigir nova arquitetura de IA, apenas priorização de qual extensão ativar primeiro.
- **Explicabilidade (TCOS-013, Capítulo 25) como argumento de venda** em mercados regulados/sensíveis a IA — diferencia de concorrentes que oferecem "IA" como caixa-preta.
- Nenhuma nova capacidade de IA é definida nesta fase — apenas a priorização comercial das já arquiteturalmente previstas.

## 13. Roadmap de Produto

**[Inferência estratégica]** Roadmap de **empacotamento e go-to-market**, não de construção técnica (que segue o TCOS-017, Implementation Master Plan, já aprovado e não alterado por este documento):

| Horizonte | Foco comercial |
|---|---|
| Lançamento (Plano Essencial) | Validar UVP (Capítulo 7) com o núcleo comercial/operacional/financeiro — cadência de Entregas já definida no TCOS-017 |
| +2–3 entregas | Plano Profissional — Precificação, Lotes, Recursos Humanos, Metas |
| +4–5 entregas | Plano Avançado — CRM, Marketing, primeira Extensão de IA priorizada (M-013-03) |
| Pós-MVP | Multiempresa/Multifilial (após M-006-01 resolvido) e primeira exploração de Marketplace (Capítulo 11) |

Este roadmap não reordena o Plano Mestre de Implementação (TCOS-017) — apenas mapeia cada Entrega técnica já definida a um marco comercial.

## 14. Estratégia de Escalabilidade

Herdada diretamente da arquitetura já aprovada, sem redefinição técnica: cada um dos 15 Serviços escala de forma independente (TCOS-006, Capítulo 9; TCOS-010, Capítulo 22); a estratégia de Multitenancy (TCOS-014, Capítulo 26) já oferece dois modelos — **tenant compartilhado**, adequado ao volume esperado dos Planos Essencial/Profissional, e **tenant isolado**, reservável comercialmente como diferencial do Plano Avançado ou de contratos enterprise futuros, sem exigir uma segunda arquitetura. **Nota de rastreabilidade (herdada da Auditoria Corretiva de 2026-08-02):** os Serviços de Indicadores e Dashboards e de Auditoria têm carga de processamento agregada por definição arquitetural (Risco R-COR-01, `PROJECT_MEMORY.md`) — relevante para o dimensionamento comercial de SLA em planos de maior volume, sem antecipar aqui nenhuma solução técnica.

## 15. Estratégia Internacional

**[Inferência estratégica, condicionada a R-000-03 e a M-006-01]** Expansão internacional é tratada como sequência de mercados com estrutura de negócio semelhante à do ICP (Capítulo 3) — culinária artesanal/tradicional com forte componente de Evento — antes de qualquer mercado genérico. Pré-condições já satisfeitas pela arquitetura: nenhuma entidade assume moeda, idioma ou jurisdição fiscal única (Filosofia de Evolução do Framework, já referenciada em TCOS-006 Capítulo 9); Multiempresa (Capítulo 25, TCOS-014) sustenta múltiplas Organizações sem reconstrução. Pré-condições **não satisfeitas ainda** e fora do escopo desta fase: localização de idioma/moeda/tributação (decisão de tecnologia, TCOS-017), adequação regulatória por país (fora do escopo conceitual). Sequência recomendada: consolidar mercado doméstico → países de língua portuguesa/espanhola com perfil de negócio semelhante → mercados mais distantes, apenas após validação de tração.

## 16. Estratégia de Onboarding

Construída sobre o fluxo de dados já modelado (Cadeia de Valor, TCOS-006 Capítulo 5): Configurações → Cadastros básicos (Clientes, Produtos, Receitas) → primeira Ficha Técnica → primeiro Orçamento → primeiro Evento. Meta de ativação: **primeira Ficha Técnica com custo calculado**, não apenas login — é o primeiro momento em que o usuário vê o diferencial central do produto (Capítulo 7) funcionando. Onboarding assistido por sugestões de IA (Capítulo 12) desde o primeiro uso é um diferencial de ativação, condicionado à priorização de M-013-03.

## 17. Estratégia de Customer Success

Estruturada por Persona (Capítulo 4): sucesso da Proprietária/Proprietário é medido pela confiança na margem exibida no Dashboard CEO; sucesso do Operacional é medido pela ausência de retrabalho manual de Ficha Técnica; sucesso da Direção/BI é medido pela frequência de consulta a Indicadores sem precisar pedir relatório manual. Alertas Inteligentes já previstos (TCOS-013, Capítulo 22) e o Banner de Alerta Crítico (RN-047, já visual desde o TCOS-018) são pontos de contato proativos naturais para Customer Success, sem exigir nenhum canal novo de comunicação.

## 18. Estratégia de Retenção

Ancorada no mesmo raciocínio de Moat (Capítulo 29): quanto mais Fichas Técnicas, Lotes históricos e Indicadores acumulados uma Organização tem, maior o custo de troca (dado histórico, PF-04, já obrigatório em toda a arquitetura) — retenção é uma consequência natural do modelo de dados, não apenas de funcionalidade. Alavancas adicionais: Metas (Módulo 26) como mecanismo de engajamento recorrente; Dashboards que se tornam parte da rotina de decisão do proprietário reduzem a propensão a migrar para outra ferramenta.

## 19. Estratégia de Comunidade

**[Inferência estratégica — oportunidade, não compromisso de roadmap]** Comunidade entre proprietários do mesmo segmento (ICP, Capítulo 3) é uma alavanca natural de aquisição e retenção — compartilhamento de boas práticas de Ficha Técnica, benchmarking anônimo de Indicadores entre Organizações (mediante consentimento explícito, compatível com a Governança de Privacidade já definida no TCOS-012, Capítulo 31, ainda pendente de decisão formal). Registrado como oportunidade estratégica futura — nenhuma funcionalidade de comparação entre Organizações é criada por este documento.

## 20. Estratégia de Feedback

Recomenda-se um ciclo estruturado ancorado nas Personas (Capítulo 4): captura in-product (não especificada tecnicamente aqui — decisão de UX/tecnologia futura), priorização confrontada contra a Matriz de Rastreabilidade de Regras de Negócio já existente (TCOS-010, Capítulo 30) para garantir que todo pedido de mudança seja avaliado quanto à sua compatibilidade arquitetural antes de virar compromisso comercial — evitando prometer ao cliente algo que exigiria reabrir um documento congelado sem passar pela Política de Change Request (Constituição, Capítulo 15).

## 21. Estratégia de Evolução Contínua

Toda evolução de produto segue o mesmo critério de sucesso já registrado na Filosofia de Evolução do Framework (TCOS-006, Capítulo 9): **extensão, nunca reconstrução**. Nenhuma decisão de produto deste documento pressupõe reescrever o Event Bus, os 15 Serviços ou o modelo de dados — toda evolução comercial (novo plano, novo add-on, nova região) deve ser absorvível como extensão aditiva, sob pena de invalidar a proposta desta fase de operar estritamente acima da arquitetura.

## 22. Métricas SaaS

Métricas recomendadas para acompanhamento comercial (nenhuma requer novo dado além do já modelado — todas deriváveis de eventos e entidades já existentes):

| Métrica | Fonte conceitual (já existente) |
|---|---|
| MRR / ARR | Assinatura por Organização (Capítulo 8) — dado comercial, não uma entidade do Domain Model |
| Churn de Organização | Cancelamento de assinatura — dado comercial |
| Ativação | Primeira Ficha Técnica com custo calculado (Capítulo 16) |
| Adoção por módulo | Frequência de uso por Módulo habilitado (Capítulo 10) |
| NRR (Net Revenue Retention) | Upsell de Plano/módulo/Usuário (Capítulo 8) |
| Tempo até primeiro Evento confirmado | Onboarding (Capítulo 16) |
| Frequência de consulta a Dashboards | Indicador de engajamento de retenção (Capítulo 18) |

## 23. North Star Metric

**Número de Eventos com margem real calculada e confirmada pelo proprietário, por mês, por Organização ativa.**

Justificativa: captura simultaneamente ativação (a Organização está usando o núcleo do produto), retenção (uso recorrente) e a UVP central (Capítulo 7) — diferente de métricas de vaidade como login ou nº de telas acessadas, mede exatamente o momento em que o produto entrega o valor prometido.

## 24. KPIs do Produto

Derivados da North Star Metric (Capítulo 23) e das Métricas SaaS (Capítulo 22): % de Organizações com ao menos 1 Evento com margem calculada no primeiro mês (ativação); MRR por Plano; % de Organizações no Plano Avançado (indicador de maturidade de upsell); nº médio de módulos habilitados por Organização acima do mínimo do Plano contratado (indicador de expansão); tempo médio entre cadastro e primeiro Orçamento (velocidade de ativação comercial).

## 25. Backlog Estratégico

Consolidação de todas as oportunidades identificadas nesta fase, nenhuma autorizada a virar arquitetura sem nova decisão explícita do proprietário:

- OE-020-01: Marketplace de extensões/templates (Capítulo 11).
- OE-020-02: Comunidade e benchmarking anônimo entre Organizações (Capítulo 19), condicionado à decisão de Governança de Privacidade (TCOS-012, Capítulo 31).
- OE-020-03: Add-on comercial de Multiempresa/Multifilial após M-006-01 (Capítulo 14).
- OE-020-04: Priorização comercial das 6 Extensões Estruturais de IA (M-013-03) como features de upsell (Capítulo 12).
- OE-020-05: Modelo de tenant isolado (TCOS-014, Capítulo 26) como oferta comercial diferenciada para contratos maiores.

## 26. Oportunidades Futuras

Além do Backlog Estratégico (Capítulo 25): parcerias com fornecedores do setor (ex.: integração futura de Compras com catálogos de fornecedores — sem criar Funcionalidade nova nesta fase); certificações setoriais como selo de confiança comercial; programa de indicação entre Organizações do mesmo segmento (alavanca de aquisição de baixo custo, compatível com a Estratégia de Comunidade, Capítulo 19).

## 27. Riscos do Produto

| Risco | Descrição | Mitigação possível (sem nova arquitetura) |
|---|---|---|
| RP-020-01 | Herda integralmente R-000-03: se o domínio de negócio real divergir da hipótese assumida, ICP, Personas e Posicionamento (Capítulos 2–4) precisarão de revisão completa | Validação de mercado antes de comprometer investimento comercial pesado |
| RP-020-02 | Empacotamento por Plano (Capítulo 9) pode não refletir disposição real de pagamento do ICP | Validação de preço/pacote com clientes reais antes do lançamento comercial |
| RP-020-03 | Dependência de decisão pendente M-006-01 para habilitar expansão comercial via Multiempresa | Roadmap comercial (Capítulo 13) já isola essa dependência, sem bloquear o lançamento inicial |
| RP-020-04 | Concorrência de ERPs horizontais com maior orçamento de marketing | Posicionamento (Capítulo 2) focado em profundidade vertical, não em amplitude |

## 28. Análise SWOT

**[Inferência estratégica, condicionada a R-000-03]**

- **Forças:** modelo de dados verticalizado e já maduro (24 documentos oficiais); separação Financeiro Pessoal/Empresarial; IA com confirmação humana obrigatória; identidade visual e Design System de nível internacional já definidos (TCOS-018/019A).
- **Fraquezas:** ausência de tração/clientes reais até o momento; ICP e Personas ainda não validados externamente (R-000-03 aberto); nenhuma decisão de tecnologia tomada ainda (fase pré-implementação).
- **Oportunidades:** mercado de negócios de produção artesanal/eventos mal atendido por ERPs genéricos; Marketplace e Comunidade (Capítulos 11 e 19); expansão internacional para mercados de perfil semelhante (Capítulo 15).
- **Ameaças:** ERPs horizontais adicionando verticalização superficial; sensibilidade de preço do ICP (negócios de pequeno/médio porte); mudança regulatória de dado pessoal/fiscal por país na expansão internacional.

## 29. Moat (Barreiras Competitivas)

1. **Moat de dados:** histórico obrigatório e nunca apagado (PF-04) — quanto mais tempo de uso, maior o valor acumulado de Fichas Técnicas, Lotes e Indicadores, e maior o custo de troca.
2. **Moat de modelo de domínio:** replicar a coerência entre Ficha Técnica → Produção → Custo → Margem exige que um concorrente reconstrua, não apenas adicione, seu modelo de dados.
3. **Moat de confiança em IA:** confirmação humana obrigatória e explicabilidade (TCOS-013) como padrão desde a origem, difícil de replicar de forma crível por um concorrente que já vendeu "IA autônoma" como promessa.
4. **Moat de identidade de produto:** Design System e identidade visual coesos (TCOS-018/019A) elevam a percepção de qualidade acima do padrão do segmento, dificultando a percepção de "mais um sistema genérico".

## 30. Plano de Crescimento para os Próximos 10 Anos

**[Inferência estratégica, condicionada a R-000-03 — plano direcional, não compromisso técnico ou financeiro]**

| Horizonte | Foco |
|---|---|
| Anos 1–2 | Validação de mercado doméstico, Planos Essencial/Profissional, consolidação da North Star Metric (Capítulo 23), primeira Extensão de IA priorizada |
| Anos 3–4 | Plano Avançado consolidado, resolução de M-006-01 e lançamento comercial de Multiempresa/Multifilial, início de exploração de Marketplace (Capítulo 11) |
| Anos 5–6 | Expansão internacional para mercados de perfil semelhante (Capítulo 15), Comunidade e benchmarking entre Organizações (Capítulo 19, sujeito à Governança de Privacidade) |
| Anos 7–8 | Marketplace maduro como segunda fonte de receita recorrente; tenant isolado como oferta enterprise consolidada (Capítulo 25, OE-020-05) |
| Anos 9–10 | Posição de referência no segmento de produção artesanal/eventos nos mercados atendidos; todo crescimento adicional avaliado sob o mesmo critério de "extensão, nunca reconstrução" (Capítulo 21) |

Este plano não compromete nenhuma decisão técnica, financeira ou de investimento — é uma direção estratégica a ser revisitada a cada fase de produto, condicionada à confirmação de R-000-03 e às decisões de negócio ainda pendentes (M-006-01 e demais, Capítulo 27).

---

## AUDITORIA ESTRATÉGICA FINAL

**Oportunidades encontradas:** Marketplace de extensões (OE-020-01); Comunidade/benchmarking (OE-020-02); Multiempresa comercial pós-M-006-01 (OE-020-03); priorização comercial das 6 Extensões de IA (OE-020-04); tenant isolado como oferta enterprise (OE-020-05); parcerias setoriais e programa de indicação (Capítulo 26). Todas registradas como Backlog Estratégico — nenhuma implica criação de arquitetura, módulo ou funcionalidade nesta fase.

**Riscos encontrados:** RP-020-01 a RP-020-04 (Capítulo 27), com destaque para a herança total de R-000-03 (o risco mais relevante do projeto, TCOS-016) sobre todo o conteúdo de ICP/Personas/Posicionamento/SWOT desta fase — nenhum desses riscos é novo em sua origem, mas seu impacto comercial é formalizado pela primeira vez nesta fase.

**Diferenciais competitivos:** modelo de dados verticalizado desde a origem; separação nativa Financeiro Pessoal/Empresarial; IA com confirmação humana obrigatória e explicável; cadeia única e auditável de Indicadores; arquitetura já pronta para Multiempresa/Multitenancy sem reconstrução; identidade visual de nível internacional (Capítulo 6).

**Potencial de mercado:** condicionado a R-000-03 — assumindo o domínio de produção artesanal/eventos confirmado, o mercado endereçável é o universo de negócios deste perfil ainda dependentes de planilha/controle manual (Capítulo 2), hoje mal atendido tanto por ERPs genéricos quanto por sistemas de PDV. Dimensionamento numérico (TAM/SAM/SOM) não é estimado nesta fase por ausência de dado de mercado validado — seria uma inferência estratégica sem lastro, e este documento não inventa números de mercado sem fonte.

**Potencial de escalabilidade:** alto, sustentado por arquitetura já madura (15 Serviços independentes, Multitenancy já formalizado, TCOS-014 Capítulo 26) — a limitação identificada não é arquitetural, mas comercial (validação de ICP) e de um risco técnico já registrado (R-COR-01, carga agregada de Indicadores/Auditoria), sem impacto no horizonte dos Planos Essencial/Profissional.

**Potencial de valuation:** **[Inferência estratégica]** para um SaaS vertical B2B com retenção ancorada em dado histórico (moat, Capítulo 29) e expansão multi-região prevista, o potencial de valuation cresce primariamente com: (a) validação de PMF (product-market fit) no ICP (Capítulo 3); (b) NRR acima de 100% via upsell de Planos/IA/Multiempresa; (c) redução de dependência de um único mercado geográfico. Nenhum múltiplo ou valor numérico de valuation é estimado — dependeria de tração real ainda inexistente.

**Possíveis fontes de receita recorrente:** assinatura por Plano (Capítulo 9); upsell de volume (usuários/Eventos); upsell de módulos de IA (Capítulo 12); Multiempresa/Multifilial comercial (Capítulo 14); Marketplace (Capítulo 11, oportunidade futura); tenant isolado como oferta premium (OE-020-05).

**Impacto esperado para os próximos 10 anos:** consolidação como sistema de referência para negócios de produção artesanal/eventos (Capítulo 30), com expansão faseada de planos, geografias e fontes de receita — todo o impacto permanece condicionado à confirmação do domínio de negócio (R-000-03) e às decisões de negócio ainda em aberto (Capítulo 27), sem as quais este plano é direcional, não comprometido.

---

## RESUMO PARA O PROPRIETÁRIO

Este documento (TCOS-020) responde à pergunta: **agora que o THE CHARCOAL OS está completamente especificado e visualmente validado, como ele se torna um negócio SaaS capaz de competir internacionalmente?**

O que foi construído: as 30 seções solicitadas — visão de produto, posicionamento, ICP, Personas, Jobs To Be Done, diferenciais competitivos, UVP, monetização, planos e empacotamento de módulos, oportunidade de marketplace, estratégia de IA como diferencial comercial, roadmap comercial, escalabilidade, expansão internacional, onboarding, customer success, retenção, comunidade, feedback, evolução contínua, métricas SaaS, North Star Metric, KPIs, backlog estratégico, oportunidades futuras, riscos de produto, SWOT, moat e um plano direcional de 10 anos.

Por que isso é importante: até aqui, o THE CHARCOAL OS era um sistema completamente especificado, mas nunca havia sido tratado explicitamente como um **negócio**. Esta camada não muda nada do que o sistema faz — decide como ele é embalado, vendido, adotado e mantido rentável.

Como isso conecta com tudo que já foi construído: nenhum módulo, Serviço, tela, componente, Fluxo, Funcionalidade ou Regra de Negócio foi criado ou alterado. Os "Planos do SaaS" (Capítulo 9) são reagrupamentos comerciais dos 27 módulos já existentes; a "Estratégia de Escalabilidade" (Capítulo 14) reafirma, sem redefinir, o que já está na Infraestrutura; a "Estratégia de IA" (Capítulo 12) prioriza comercialmente capacidades já arquiteturalmente previstas, sem criar nenhuma nova.

**Alerta de transparência mais importante desta fase:** boa parte do conteúdo de mercado (ICP, Personas, Posicionamento, SWOT) herda diretamente o risco **R-000-03** — a hipótese de domínio de negócio nunca formalmente confirmada, classificada pelo próprio TCOS-016 como o risco mais relevante do projeto. Este documento não resolve esse risco; ele o torna comercialmente visível pela primeira vez.

Como isso prepara o próximo passo: com este documento aprovado, o proprietário tem uma camada de produto coerente para orientar decisões comerciais futuras — precificação real, validação de mercado, priorização de investimento — sem qualquer necessidade de retrabalho arquitetural.

---

## TCOS QUALITY GATE EXECUTIVO

**1. Resumo Executivo**
Criada a Camada de Produto do THE CHARCOAL OS: visão, posicionamento, ICP, Personas, JTBD, diferenciais, UVP, monetização, planos, IA como vantagem comercial, roadmap, escalabilidade, expansão internacional, onboarding, customer success, retenção, comunidade, feedback, métricas, North Star Metric, KPIs, backlog estratégico, riscos, SWOT, moat e plano de 10 anos. Nenhum documento oficial congelado foi alterado.

**2. Estado atual do projeto**
Fases 000 a 018 encerradas e oficiais; TCOS-019A com Fases 1 e 2 aprovadas; Auditoria Arquitetural Corretiva de 2026-08-02 concluída; Fase 020 (este documento) em primeira apresentação, aguardando Auditoria Estratégica e aprovação do proprietário. Refinamento visual das 30 telas (Fase iniciada na Tela 05) permanece pausado, sem relação de dependência com esta fase.

**3. Documentos oficiais existentes**
24 Documentos Oficiais (23 já existentes + este, ainda não congelado) + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) + 1 Constituição Permanente.

**4. Dependências desta fase**
Domain Model (TCOS-002), Business Rules Specification (TCOS-002A), System Architecture (TCOS-006), AI Architecture (TCOS-013), Infrastructure Architecture (TCOS-014, Capítulos 25–26), Security and Privacy Architecture (TCOS-012), UX/UI Specification (TCOS-005), Visual Blueprint (TCOS-018), Executive Global Audit (TCOS-016) — todos referenciados, nenhum reescrito.

**5. Pendências abertas**
As mesmas pendências substantivas já consolidadas (confirmação do domínio de negócio R-000-03 — com impacto comercial agora explicitado nesta fase; Multiempresa/Multifilial M-006-01/M-007-01; demais pendências herdadas do TCOS-016) — nenhuma nova pendência técnica. Nova pendência de produto: validação externa de ICP/Personas/Posicionamento com o mercado real.

**6. Dúvidas encontradas**
Nenhuma de arquitetura. Uma dúvida de negócio já esperada foi reforçada: a real disposição a pagar do ICP por Plano (Capítulo 9), sem dado de mercado ainda disponível.

**7. Riscos ativos**
Os riscos já consolidados (R-000-03 com destaque, R-002-01, R-001-01, R-002-02, R-002A-01) — herdados, agora com impacto comercial explicitado nos Capítulos 27 e 28.

**8. Novos riscos encontrados**
RP-020-01 a RP-020-04 (Capítulo 27) — todos de natureza comercial/de produto, nenhum de arquitetura.

**9. Inconsistências encontradas**
Nenhuma com documento já oficial — confirmado por busca em todos os 24 documentos antes da construção (Auditoria de Abertura).

**10. Conflitos entre documentos**
Nenhum.

**11. Escopo técnico alterado**
Nenhum — confirmado que nenhum módulo, Serviço, tela, componente, Fluxo, Funcionalidade, Regra de Negócio ou decisão arquitetural foi criado, removido ou modificado por este documento.

---

*Este documento aguarda a Auditoria Estratégica apresentada acima e a decisão do proprietário antes de qualquer nova fase da Camada de Produto.*
