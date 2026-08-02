# THE CHARCOAL OS — CUSTOMER EXPERIENCE & LIFECYCLE STRATEGY

**Documento:** TCOS-021
**Fase:** 021 — Customer Experience & Lifecycle Strategy (Camada de Produto, Parte 2)
**Natureza:** Documento exclusivamente de estratégia de experiência e ciclo de vida do cliente SaaS (Camada de Produto). NÃO constitui arquitetura, NÃO constitui implementação, NÃO constitui código, NÃO define tecnologia. NÃO cria, altera ou remove nenhum módulo, Serviço, tela, componente, Fluxo, Funcionalidade ou Regra de Negócio. NÃO altera nenhum documento oficial congelado — atua exclusivamente **acima** da arquitetura já aprovada, complementando o TCOS-020 com o detalhamento operacional da jornada e do ciclo de vida do cliente enquanto assinante do SaaS.
**Baseline referenciada:** v1.0.0 (TCOS-000 a TCOS-018, congelados) + TCOS-019A (Fases 1 e 2 aprovadas) + TCOS-020 v1.1.0 (Product & SaaS Strategy — Austrália como mercado primário, Brasil como expansão posterior), sob a autoridade da Constituição Permanente do Projeto.
**Documentos-fonte desta fase:** `THE_CHARCOAL_OS_PRODUCT_AND_SAAS_STRATEGY.md` (TCOS-020); `THE_CHARCOAL_OS_SECURITY_AND_PRIVACY_ARCHITECTURE.md` (TCOS-012, Capítulos 8–11 — Perfis e Permissões); `THE_CHARCOAL_OS_SYSTEM_ARCHITECTURE.md` (TCOS-006, Capítulo 8); `THE_CHARCOAL_OS_DATABASE_SPECIFICATION.md` (TCOS-008, Backup/Soft Delete); `THE_CHARCOAL_OS_INFRASTRUCTURE_ARCHITECTURE.md` (TCOS-014, Capítulos 25–26); `THE_CHARCOAL_OS_UX_UI_SPECIFICATION.md` (TCOS-005); `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018); `PROJECT_MEMORY.md`.
**Status:** Em construção — primeira apresentação completa, aguardando Auditoria Estratégica e aprovação do proprietário.

---

## ANÁLISE DE ORQUESTRAÇÃO E PRIORIZAÇÃO ESTRATÉGICA (executada antes da construção)

- **Natureza da tarefa:** documentação de estratégia de produto/experiência do cliente — síntese e organização de conteúdo já dominado neste projeto, sem necessidade de leitura extensa de documento novo.
- **Disciplinas envolvidas:** Produto, SaaS, UX Strategy, Customer Success, Governança/Auditoria.
- **Capacidades especializadas avaliadas:** nenhuma Skill ou subagente traz ganho objetivo nesta etapa — não há gráfico, dado externo ou leitura massiva de documento envolvida; a tarefa é redação estratégica fundamentada em documentos já profundamente conhecidos nesta sessão (TCOS-020, TCOS-012, TCOS-006). **Nenhuma capacidade especializada foi utilizada.**
- **Priorização:** esta etapa não bloqueia nem depende da conclusão das telas (Camada de Produto opera acima e em paralelo à Camada Visual, por definição do TCOS-020) — compatível com a instrução explícita do proprietário de evoluir o produto "sem interromper a construção visual". O Achado #1 da Tela 05 permanece o item de maior prioridade bloqueante da trilha visual, independente desta entrega.

## AUDITORIA DE ABERTURA (executada antes de qualquer definição)

- Confirmado, por busca em todos os 25 documentos oficiais já existentes (incluindo o TCOS-020): nenhum documento define hoje o detalhamento operacional de Customer Journey, Lifecycle, trial, cobrança, renovação ou cancelamento. O TCOS-020 (Capítulos 16–20) já estabelece a estratégia de Onboarding, Customer Success, Retenção e Feedback em nível **diretivo** — este documento aprofunda em nível **operacional**, sem duplicar nem contradizer o que já é oficial.
- **Achado (Erro, não corrigido nesta fase — fora do escopo autorizado do `CONTINUAR` que originou este documento):** ao fundamentar o Capítulo 17 (Matriz de Perfis), foi identificado que o **TCOS-020, Capítulo 4 (Personas)**, afirma que as Personas são construídas sobre **"os 5 Perfis de acesso já formalizados no TCOS-012"**, citando Proprietário, Administrativo, Operacional, Comercial e BI/Direção. Isso não corresponde ao que o TCOS-012 (Capítulo 8–9) e o TCOS-006 (Capítulo 8) realmente definem: **10 Perfis por Área da Empresa** (Comercial/CRM, Produção, Compras/Suprimentos, Estoque/Logística, Eventos/Operações, Financeiro, Marketing, Pessoas/Mão de Obra, Administrativo/Documentos, BI/Direção Executiva) **mais o perfil transversal Administrador do Sistema** — 11 papéis nomeados ao todo, nenhum deles literalmente chamado "Proprietário" ou "Operacional". Classificação: Erro / Severidade Média / Documento relacionado: TCOS-020, Capítulo 4 / Impacto: as Personas do TCOS-020 continuam estrategicamente válidas como agrupamento de propósito, mas a citação da fonte está factualmente incorreta. **Este documento usa a estrutura de Perfis correta e oficial (TCOS-012/TCOS-006) em todo o seu conteúdo**, para não propagar o erro — a correção do TCOS-020 Capítulo 4 permanece pendente de autorização explícita do proprietário, registrada também no Resumo Executivo desta entrega.
- Nenhuma outra inconsistência, sobreposição ou conflito com documento já oficial foi encontrada. A construção desta fase está autorizada a prosseguir.

**Convenção de rastreabilidade:** todo conteúdo que extrapola diretamente de um fato já documentado é identificado como **[Inferência estratégica]**, na mesma disciplina do TCOS-020.

---

## 1. Papel deste Documento

O TCOS-020 respondeu "que produto SaaS o THE CHARCOAL OS é, e como ele gera receita". Este documento (TCOS-021) responde à pergunta seguinte: **como é, na prática, a experiência de um cliente desde o primeiro contato até se tornar (ou deixar de ser) um assinante recorrente?** É a segunda parte da Camada de Produto — opera sobre a mesma base do TCOS-020 (Planos, Módulos por Plano, Personas, North Star Metric), sem redefinir nada dela.

## 2. Fronteira entre a Camada de Experiência/Assinatura e os 27 Módulos de Domínio

**Regra explícita, aplicada a todo este documento:** a relação comercial entre o THE CHARCOAL OS (fornecedor do SaaS) e o cliente (a Organização assinante) — trial, cobrança, renovação, cancelamento de assinatura — é um conceito de **produto/comercial**, existente **acima e fora** dos 27 módulos de domínio já oficiais. Os 27 módulos (incluindo Financeiro Pessoal/Empresarial, Módulos 02/03/27) modelam o negócio **do cliente**, nunca a relação de cobrança **do cliente com o THE CHARCOAL OS**. Essa distinção evita duas armadilhas: (a) confundir a receita de assinatura do fornecedor com uma Receita Financeira do próprio cliente (Módulo 03), o que contaminaria o domínio de negócio do cliente com dado que não é dele; (b) criar um módulo novo de "Assinatura/Cobrança" — não autorizado nesta fase. Onde este documento menciona cobrança, trial ou renovação, refere-se sempre a essa camada comercial externa aos 27 módulos, cuja eventual implementação técnica (plataforma de billing) é decisão de tecnologia, fora do escopo conceitual deste documento, a ser tratada em extensão futura do TCOS-017.

## 3. Jornada Completa do Cliente (Customer Journey)

| Etapa | Descrição | Módulo/Perfil já existente envolvido |
|---|---|---|
| Descoberta | Cliente identifica a dor (planilha, controle manual) e encontra o THE CHARCOAL OS | Camada comercial externa (Capítulo 2) |
| Avaliação/Trial | Cliente testa o produto com dado real ou de exemplo | Camada comercial externa + Módulo 24/25 (Configurações/Administração, para o primeiro acesso) |
| Onboarding | Primeira Ficha Técnica com custo calculado (TCOS-020, Capítulo 16) | Módulos 12/13 (Receitas/Fichas Técnicas), 24 (Configurações) |
| Ativação | North Star Metric atingida pela primeira vez (TCOS-020, Capítulo 23) | Módulo 07 (Eventos), 11/14 (Custos/Precificação) |
| Adoção | Uso recorrente dos módulos do Plano contratado | Todos os módulos habilitados (TCOS-020, Capítulo 10) |
| Expansão | Upsell de Plano/módulo/usuário (TCOS-020, Capítulo 8) | Camada comercial externa + Módulo 25 (novos usuários/Perfis) |
| Renovação ou Cancelamento | Decisão de continuidade da assinatura | Camada comercial externa (Capítulo 2) |

Esta jornada não cria nenhuma tela, fluxo (FL-XXX) ou funcionalidade nova — é uma leitura comercial sobre o uso real dos módulos e Perfis já existentes.

## 4. Ciclo de Vida do Cliente (Lifecycle)

**[Inferência estratégica]** Modelo de 6 estágios, cada um com um critério de saída objetivo, todos deriváveis de dado já modelado (nenhum dado novo exigido):

1. **Prospect** → sai ao iniciar o Trial.
2. **Trial** → sai ao converter (assinatura paga) ou expirar sem conversão.
3. **Onboarding** → sai ao atingir a primeira Ficha Técnica com custo calculado (TCOS-020, Capítulo 16).
4. **Ativo** → permanece enquanto a North Star Metric (TCOS-020, Capítulo 23) for atingida com regularidade.
5. **Em risco** → entra quando a frequência de uso ou a North Star Metric cai abaixo de um limiar (Capítulo 12, Retenção) — estágio de atenção de Customer Success, não um estado do sistema.
6. **Encerrado** → sai por cancelamento (Capítulo 11) ou por não-renovação (Capítulo 10).

Nenhum destes estágios é uma entidade nova do Domain Model — são uma **leitura comercial** sobre dado e evento já existentes (frequência de Caso de Uso, Indicadores já calculados).

## 5. Onboarding

Aprofunda o TCOS-020 (Capítulo 16). Sequência recomendada, seguindo a Cadeia de Valor já oficial (TCOS-006, Capítulo 5): (1) primeiro acesso e criação de usuário via Administrador do Sistema (Módulo 25); (2) Configurações mínimas (Módulo 24); (3) primeiro cadastro de Cliente/Produto/Receita; (4) primeira Ficha Técnica com custo calculado — o momento de ativação (Capítulo 4); (5) primeiro Orçamento e primeiro Evento. **Meta de tempo até ativação:** menor tempo possível entre (1) e (4), sem número específico definido nesta fase por ausência de dado real de uso (seria inferência sem lastro).

## 6. Ativação

Idêntica à definição já oficial no TCOS-020 (Capítulo 16: primeira Ficha Técnica com custo calculado) — este capítulo apenas formaliza os sinais operacionais que a antecedem: pelo menos 1 Produto/Receita cadastrado, pelo menos 1 Ficha Técnica associada, Configurações mínimas preenchidas (Módulo 24, sem as quais o cálculo de custo não é possível, RN já existentes). Nenhum sinal novo de dado é exigido além do que os Módulos 12/13/24 já capturam.

## 7. Trial

**[Inferência estratégica]** Período de avaliação com acesso ao Plano Essencial completo (TCOS-020, Capítulo 9), permitindo que o cliente atinja a Ativação (Capítulo 6) antes de decidir pela assinatura — sem isso, o Trial nunca demonstraria a UVP central (TCOS-020, Capítulo 7). Duração e mecanismo de expiração são decisão comercial/técnica não definida nesta fase (pertence à Camada de Assinatura, Capítulo 2). Ao expirar sem conversão, o dado do cliente segue a mesma regra de nenhuma entidade fisicamente excluída (CG-01/PF-04) — nunca um tratamento de exclusão diferente do já oficial.

## 8. Conversão

Momento em que o cliente em Trial (Capítulo 4, estágio 2) passa a Ativo mediante contratação de um Plano pago (TCOS-020, Capítulos 8–9). **Indicador de propensão à conversão [Inferência estratégica]:** cliente que atinge a Ativação (Capítulo 6) durante o Trial converte com maior probabilidade do que um que não atinge — por isso Onboarding (Capítulo 5) é a alavanca mais direta de conversão, não uma campanha comercial isolada.

## 9. Cobrança

Pertence integralmente à Camada de Assinatura (Capítulo 2), nunca aos Módulos 02/03/27 do cliente. Princípio herdado do TCOS-020 (Capítulo 8): assinatura recorrente por Organização, mensal ou anual. Nenhum mecanismo de cobrança, gateway de pagamento ou fluxo de inadimplência é definido nesta fase — são decisões de tecnologia (TCOS-017) e de parceiro de pagamento, fora do escopo conceitual deste documento.

## 10. Renovação

Decisão do estágio "Ativo" (Capítulo 4) de continuar a assinatura ao final do ciclo de cobrança (Capítulo 9). **Sinal de risco de não-renovação [Inferência estratégica]:** transição para o estágio "Em risco" (Capítulo 4) antes do vencimento do ciclo é o gatilho recomendado para ação de Customer Success (Capítulo 14) — nunca uma ação automática sobre a assinatura, que permanece sempre sob decisão do cliente.

## 11. Cancelamento

Transição do estágio "Ativo" ou "Em risco" para "Encerrado" (Capítulo 4). **Regra explícita, herdada sem alteração da arquitetura já oficial:** nenhuma entidade de negócio do cliente é fisicamente excluída no cancelamento (CG-01/PF-04, TCOS-002; TCOS-008, Capítulo 8) — o mesmo Soft Delete e histórico obrigatório já aplicado a qualquer entidade continuam valendo; cancelamento é um evento da Camada de Assinatura (Capítulo 2), nunca uma operação de exclusão de dado dentro dos 27 módulos. Retenção de dado pós-cancelamento por prazo determinado é decisão de governança de privacidade ainda pendente (TCOS-012, Capítulo 31, já registrada como pendência herdada) — não definida nesta fase.

## 12. Retenção

Aprofunda o TCOS-020 (Capítulo 18). Alavanca operacional principal: o estágio "Em risco" (Capítulo 4) como sinal antecipado, derivado da queda de frequência de uso ou da North Star Metric (TCOS-020, Capítulo 23) — nunca um número novo de dado, apenas leitura sobre o que já é calculado. O Moat de dados já registrado (TCOS-020, Capítulo 29) — histórico acumulado de Fichas Técnicas, Lotes e Indicadores — permanece a alavanca estrutural de retenção de mais longo prazo.

## 13. Expansão (Upsell/Cross-sell)

Aprofunda o TCOS-020 (Capítulo 8). Gatilhos operacionais recomendados, todos derivados de uso real e não de campanha isolada: Organização usando 100% dos módulos do Plano atual de forma consistente (candidata a upgrade de Plano); Organização com mais de um Usuário ativo por Perfil-Área além do previsto no Plano (candidata a upsell de volume); Organização no Perfil BI/Direção Executiva consultando Indicadores com alta frequência (candidata à Extensão de IA priorizada, TCOS-020 Capítulo 12).

## 14. Customer Success

Aprofunda o TCOS-020 (Capítulo 17), agora estruturado pelos 11 Perfis reais (Auditoria de Abertura). Cada Perfil-Área tem um sinal de sucesso operacional próprio, todos deriváveis de uso já existente: Comercial/CRM — taxa de conversão de Orçamento em Contrato; Produção — ausência de retrabalho manual de Ficha Técnica; Financeiro — fechamento de período sem pendência; Estoque/Logística — ausência de ruptura por falta de alerta de reposição; BI/Direção Executiva — frequência de consulta a Dashboards sem pedido manual de relatório. Alertas Inteligentes (TCOS-013, Capítulo 22) e o Banner de Alerta Crítico (RN-047) permanecem os pontos de contato proativos naturais, sem exigir canal novo.

## 15. Suporte

**[Inferência estratégica — camada comercial, não um módulo]** Estrutura de suporte por criticidade, não por Perfil: (a) autoatendimento — documentação e conteúdo de ajuda, fora dos 27 módulos (não é o Módulo 23 Documentos, que é exclusivo para documentos formais do negócio do cliente — contrato, comprovante, nota); (b) suporte assistido — canal humano para dúvida operacional; (c) suporte crítico — indisponibilidade ou erro que impede uso do sistema, com SLA mais agressivo. Nenhum destes canais é modelado como entidade ou módulo nesta fase — são infraestrutura comercial/operacional, decisão de tecnologia futura.

## 16. Feedback Contínuo

Aprofunda o TCOS-020 (Capítulo 20). Ciclo recomendado: captura por Perfil-Área (cada Perfil vê e usa um subconjunto diferente do sistema, logo tem feedback distinto); priorização confrontada contra a Matriz de Rastreabilidade de Regras de Negócio (TCOS-010, Capítulo 30), já usada no TCOS-020 com a mesma finalidade — garantir que todo pedido seja avaliado quanto à compatibilidade arquitetural antes de virar compromisso comercial.

## 17. Matriz de Integração com Perfis e Módulos Já Existentes

Confirmação de cobertura: todo estágio do Ciclo de Vida (Capítulo 4) e toda etapa da Jornada (Capítulo 3) foi mapeada exclusivamente a Perfis e Módulos já oficiais — nenhuma linha desta tabela exige módulo, Perfil, entidade ou Funcionalidade nova.

| Perfil-Área (TCOS-012/TCOS-006, Cap. 8) | Módulos primários já existentes |
|---|---|
| Comercial/CRM | 04, 05, 06, 08, 09 |
| Produção | 10, 12, 13 |
| Compras/Suprimentos | 15, 16, 17 |
| Estoque/Logística | 16, 17 |
| Eventos/Operações | 07, 18, 20 |
| Financeiro | 02, 03, 27 |
| Marketing | 21 |
| Pessoas/Mão de Obra | 19, 20 |
| Administrativo/Documentos | 23, 24 |
| BI/Direção Executiva | 01, 26 (Herança Consolidada sobre os demais) |
| Administrador do Sistema (transversal) | 24, 25 |

## 18. Riscos e Achados desta Fase

- **RC-021-01 (Erro, herdado da Auditoria de Abertura):** TCOS-020, Capítulo 4, cita incorretamente "5 Perfis" em vez dos 11 papéis reais (10 por Área + Administrador do Sistema). Não corrigido nesta fase — fora do escopo autorizado. Recomenda-se `CORRIGIR` dedicado ao TCOS-020 Capítulo 4.
- **RC-021-02 (Risco):** a ausência de definição técnica da Camada de Assinatura (Capítulo 2) — trial, cobrança, renovação — significa que nenhuma estimativa de esforço de implementação existe ainda; deverá ser endereçada quando o TCOS-017 for estendido para tecnologia de billing.
- **RC-021-03 (Risco, herdado):** retenção de dado pós-cancelamento (Capítulo 11) depende da mesma decisão de Governança de Privacidade já pendente desde o TCOS-012 (Capítulo 31) — sem novidade nesta fase, apenas reafirmado como relevante ao Cancelamento.

---

## AUDITORIA ESTRATÉGICA FINAL

**Oportunidades encontradas:** Onboarding como maior alavanca de conversão (Capítulo 8); estágio "Em risco" como sinal antecipado de churn, reutilizável tanto para Retenção quanto para Renovação (Capítulos 10 e 12); gatilhos de expansão 100%-uso-do-Plano e alta frequência de BI/Direção como upsell natural (Capítulo 13).

**Riscos encontrados:** RC-021-01 a RC-021-03 (Capítulo 18), com destaque para o Erro herdado no TCOS-020 Capítulo 4 (Perfis), que deve ser corrigido para manter a Camada de Produto internamente coerente.

**Compatibilidade com o TCOS-020:** total — nenhuma definição de Plano (Capítulo 9), Monetização (Capítulo 8), North Star Metric (Capítulo 23) ou Backlog Estratégico (Capítulo 25) foi contrariada; este documento apenas aprofunda operacionalmente o que o TCOS-020 já havia estabelecido em nível diretivo (Capítulos 16–20).

**Impacto esperado:** reduz o risco de ambiguidade na futura implementação técnica da experiência do cliente, ao já mapear cada estágio de Lifecycle e cada etapa de Jornada a Perfis e Módulos reais — nenhuma decisão de tecnologia foi tomada, mas o espaço de decisão futura ficou mais estreito e mais seguro.

---

## RESUMO PARA O PROPRIETÁRIO

Este documento (TCOS-021) responde à pergunta: **como é, de fato, a experiência de alguém que descobre, testa, adota, expande ou eventualmente cancela o THE CHARCOAL OS como assinante?** Ele complementa o TCOS-020 com o detalhamento operacional de Jornada, Ciclo de Vida, Onboarding, Ativação, Trial, Conversão, Cobrança, Renovação, Cancelamento, Retenção, Expansão, Customer Success, Suporte e Feedback — todos mapeados exclusivamente sobre os 27 módulos e os 11 Perfis já oficiais, sem criar nenhum módulo, tela, regra de negócio ou entidade nova.

**Achado mais importante desta entrega:** ao fundamentar a Matriz de Perfis (Capítulo 17), identifiquei que o TCOS-020 (Capítulo 4, Personas) cita incorretamente "5 Perfis" do TCOS-012, quando a estrutura real e oficial é de 10 Perfis por Área da Empresa mais o Administrador do Sistema (11 ao todo). Este documento já usa a estrutura correta em todo o seu conteúdo, para não propagar o erro adiante — mas a correção do próprio TCOS-020 permanece pendente de sua autorização explícita.

**Fronteira mais importante estabelecida nesta fase:** toda a relação comercial de assinatura (trial, cobrança, renovação, cancelamento) foi explicitamente definida como uma camada **acima e fora** dos 27 módulos de domínio — nunca contaminando o Financeiro do próprio cliente (Módulos 02/03/27) com a receita de assinatura do fornecedor, e nunca exigindo um módulo novo de "Assinatura".

Confirmado via `git status` que apenas este novo arquivo foi criado — nenhum dos 25 documentos oficiais existentes foi alterado.

---

## TCOS QUALITY GATE EXECUTIVO

**1. Resumo Executivo** — Criada a segunda parte da Camada de Produto: jornada, ciclo de vida e operação da experiência do cliente, 100% compatível com o TCOS-020, sem alterar nenhum documento oficial congelado.

**2. Estado atual do projeto** — Fases 000–018 congeladas; TCOS-019A Fases 1–2 aprovadas; TCOS-020 v1.1.0 aguardando aprovação final; TCOS-021 (este documento) em primeira apresentação. Refinamento visual das 30 telas permanece pausado na Tela 05, sem relação de dependência com esta fase.

**3. Documentos oficiais existentes** — 25 Documentos Oficiais (24 já existentes + este, ainda não congelado) + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) + 1 Constituição Permanente.

**4. Dependências desta fase** — TCOS-020, TCOS-012 (Capítulos 8–11), TCOS-006 (Capítulo 8), TCOS-008 (Soft Delete), TCOS-014 (Capítulos 25–26) — todos referenciados, nenhum reescrito.

**5. Pendências abertas** — Aprovação do TCOS-020 e deste TCOS-021; correção pendente do TCOS-020 Capítulo 4 (RC-021-01); demais pendências substantivas já consolidadas, sem nenhuma nova de arquitetura.

**6. Dúvidas encontradas** — Nenhuma de arquitetura. Duração de Trial e mecanismo técnico de cobrança permanecem indefinidos por serem decisão de tecnologia futura (Capítulos 7 e 9).

**7. Riscos ativos** — Os já consolidados (R-000-03 com destaque) — herdados, sem alteração de impacto por esta fase.

**8. Novos riscos encontrados** — RC-021-01 a RC-021-03 (Capítulo 18) — nenhum de arquitetura.

**9. Inconsistências encontradas** — RC-021-01 (Capítulo 4 do TCOS-020) — a única, já detalhada, não corrigida nesta fase.

**10. Conflitos entre documentos** — Nenhum além do já registrado em RC-021-01.

**11. Escopo técnico alterado** — Nenhum — confirmado que nenhum módulo, Serviço, tela, componente, Fluxo, Funcionalidade, Regra de Negócio ou decisão arquitetural foi criado, removido ou modificado por este documento.

**Capacidades utilizadas:** nenhuma Skill, Agent ou ferramenta especializada foi utilizada nesta fase — tarefa de síntese estratégica sobre documentos já dominados, sem ganho objetivo identificado em nenhuma capacidade disponível (Análise de Orquestração, acima).

---

*Este documento aguarda a decisão do proprietário sobre seu conteúdo e, separadamente, sobre a correção do TCOS-020 Capítulo 4 (RC-021-01).*
