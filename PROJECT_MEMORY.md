# MEMÓRIA CUMULATIVA DO PROJETO — THE CHARCOAL OS

> Histórico obrigatório de consulta antes de qualquer nova fase, conforme
> Seção 17 do THE_CHARCOAL_OS_DEVELOPMENT_FRAMEWORK.md.

---

## FASE 000 — Governança do Projeto

**Status:** APROVADA pelo proprietário em 2026-08-01 (comando `APROVADO`), na versão 1.1.0 do Framework
**Data:** 2026-08-01

### Decisões tomadas
- D-000-01: Adotado o modelo de "Comitê Executivo multi-especialista" como postura de trabalho para todas as fases futuras. Motivo: garantir que decisões técnicas sejam avaliadas sob múltiplas perspectivas (arquitetura, dados, segurança, UX, negócio) antes de aprovação.
- D-000-02: Nenhum código, banco de dados, tela ou API será produzido antes da aprovação formal desta Fase 000. Motivo: instrução explícita do proprietário; evita retrabalho por ausência de regras estabelecidas.
- D-000-03: Adotado versionamento semântico (MAJOR.MINOR.PATCH) para o Framework, módulos e releases. Motivo: padrão amplamente utilizado por empresas de referência citadas (Microsoft, Apple, Google, Oracle, SAP), com rastreabilidade clara de impacto de mudanças.
- D-000-04: Toda fase exige auditoria de abertura e revisão de encerramento, com aprovação exclusiva do proprietário via comandos formais (`APROVADO`, `CORRIGIR`, `ALTERAR`, `REMOVER`, `CONTINUAR`). Motivo: instrução explícita do proprietário; garante controle final e rastreabilidade de todas as decisões relevantes.
- D-000-05: Complementado o Framework (v1.0.0 → v1.1.0) com Manifesto, Princípios Fundamentais, Documentos Oficiais, Glossário Oficial e Filosofia de Evolução, sem remover ou alterar conteúdo pré-existente. Motivo: comando `ALTERAR` do proprietário.
- D-000-06: Os "Documentos Oficiais do Projeto" (Project Memory, ADR, Changelog, Risk Register, Improvement Backlog, Glossary, Integration Map, Version History) foram definidos como os nomes de mercado formais dos artefatos já exigidos nas Seções 7–16 do Framework, e não como artefatos adicionais. Motivo: evitar duplicidade de mecanismos de governança, identificada na auditoria da Seção 26.
- D-000-07: Fixada a regra de nomenclatura de que o termo "Receita" isolado refere-se sempre ao contexto de Produção (culinário), e todo valor financeiro de entrada deve ser referido explicitamente como "Receita Financeira". Motivo: ambiguidade de domínio identificada na auditoria da Seção 26; regra deverá ser propagada a banco de dados, telas e APIs a partir da primeira fase técnica.
- D-000-08: Fase 000 formalmente aprovada pelo proprietário (comando `APROVADO`) na versão 1.1.0 do Framework. Motivo: constituição considerada completa após a complementação da v1.1.0.
- D-000-09: A Fase 001, originalmente prevista como "Arquitetura Macro e Stack Tecnológica", foi **redefinida** pelo proprietário. A Fase 001 oficial passa a ser **BUSINESS DISCOVERY** — compreensão profunda do funcionamento real do negócio antes de qualquer decisão técnica (arquitetura, stack ou modelo de dados). Motivo: instrução explícita do proprietário; nenhuma decisão técnica deve anteceder o entendimento completo do negócio. O escopo detalhado da Fase 001 será formalizado mediante Prompt Oficial ainda a ser recebido do proprietário; até lá, a Fase 001 permanece não iniciada.

### Alterações
- ALT-000-01: Framework atualizado de v1.0.0 para v1.1.0 (MINOR — adição compatível). Seções 21–26 adicionadas ao final do corpo normativo (antes das Regras Permanentes). Nenhuma seção pré-existente foi removida, renumerada ou reescrita.

### Melhorias sugeridas (Backlog)
- M-000-01: Considerar, a partir da Fase 001, a criação de um repositório de artefatos vivos (Decision Log/ADR, Changelog, Registro de Riscos, Backlog de Melhorias, Mapa de Integrações, Glossário de Domínio) como arquivos versionados separados, em vez de seções soltas, para facilitar rastreamento incremental por fase.
- M-000-02: Avaliar, antes da Fase 001, se o projeto seguirá arquitetura modular monolítica ou modular distribuída (microsserviços) — decisão estrutural de alto impacto que deve ser tomada com registro formal de vantagens/desvantagens antes de qualquer definição de banco de dados.

### Riscos encontrados
- R-000-01: Ausência de repositório de código pré-existente (repositório vazio, sem commits). Impacto: nenhuma inconsistência herdada, mas também nenhuma referência arquitetural prévia — todas as convenções (nomenclatura, padrões de dados, estrutura de módulos) precisarão ser definidas do zero na primeira fase técnica. Status: aberto, a ser tratado na Fase 001.
- R-000-02: O framework define processos rigorosos de auditoria e aprovação; risco de a governança se tornar um gargalo se o proprietário não estiver disponível para validar cada fase tempestivamente. Mitigação proposta: manter fases com escopo objetivo e relatórios concisos para agilizar a validação. Status: aberto, monitorar.
- R-000-03: O Manifesto (Seção 21) e o Glossário Oficial (Seção 24) assumem, a partir do vocabulário de negócio fornecido (Ingrediente, Receita, Ficha Técnica, Produção, Lote, Evento, Pacote), que o domínio do negócio é produção alimentícia/artesanal e eventos. Impacto: caso este não seja o segmento real ou completo do negócio, Manifesto e Glossário precisarão de correção antes da Fase 001. Status: aberto — requer confirmação do proprietário.

### Pendências
- P-000-01: ~~Aprovação formal do proprietário sobre este documento de governança.~~ **Resolvida** — aprovado em 2026-08-01 (comando `APROVADO`, v1.1.0).
- P-000-02: ~~Definição do escopo da Fase 001 como Arquitetura Macro/Stack Tecnológica.~~ **Superada** — a Fase 001 foi redefinida pelo proprietário para **BUSINESS DISCOVERY** (D-000-09). Nova pendência: aguardar o Prompt Oficial da Fase 001 antes de iniciar qualquer atividade dessa fase.
- P-000-03: Confirmação do proprietário de que o domínio de negócio assumido no Manifesto e no Glossário Oficial (produção/eventos) está correto (ver R-000-03) — permanece em aberto; deverá naturalmente ser esclarecida durante a própria Fase 001 (Business Discovery), caso ainda não confirmada antes disso.

### Funcionalidades aprovadas
- Nenhuma (fase de governança; nenhuma funcionalidade de produto foi proposta ou aprovada).

### Funcionalidades rejeitadas
- Nenhuma.

### Módulos existentes
- Nenhum (projeto ainda não possui módulos técnicos; apenas governança).

### Integrações
- Nenhuma.

---

## FASE 001 — Business Discovery

**Status:** APROVADA E ENCERRADA pelo proprietário em 2026-08-01 (comando `APROVADO`). Todos os documentos produzidos na Fase 001 (`THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md`, `THE_CHARCOAL_OS_BUSINESS_DISCOVERY_QUESTIONNAIRE.md`, `THE_CHARCOAL_OS_DISCOVERY_INTERVIEW_ROADMAP.md`) tornam-se Documentação Oficial do THE CHARCOAL OS; nenhum pode ser alterado sem criação de nova versão.
**Data:** 2026-08-01

**Nota de encerramento (achado de auditoria, ver Fase 002):** o encerramento ocorreu **antes** da execução da entrevista de descoberta (Fase 001B) e das respostas às perguntas Q1–Q110, contrariando o plano registrado em P-001B-02. Isso decorreu de instrução explícita e direta do proprietário, sendo por isso válido e definitivo — mas o risco R-000-03/P-000-03 (hipótese de domínio de negócio ainda não confirmada) permanece formalmente aberto e passa a ser herdado também pela Fase 002 e por todo documento que reutilize o vocabulário de entidades da Fase 001.

Conforme D-000-09, esta fase substitui a proposta original de "Arquitetura Macro e Stack Tecnológica" como próxima fase do projeto. Recebido o Prompt Oficial (Documento TCOS-001), foi executada a auditoria de abertura (Seção 17 do Framework) sem novas inconsistências além do já registrado R-000-03/P-000-03, e produzido o documento `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md`, mapeando o domínio de negócio hipotético (produção culinária em brasa/carvão comercializada via Eventos) em 25 capítulos de processos e um conjunto de entidades de negócio. Nenhuma decisão técnica foi tomada, em conformidade com a restrição da fase.

### Decisões tomadas
- D-001-01: Adotada a hipótese de trabalho de que o negócio opera no domínio de produção culinária em brasa/carvão comercializada majoritariamente via Eventos, mantendo-a explicitamente como hipótese a confirmar (não como fato), com pergunta formal Q1 ao proprietário. Motivo: coerência com o vocabulário já aprovado no Glossário Oficial (Seção 24 do Framework) e com R-000-03.
- D-001-02: Estabelecida a estrutura de 25 capítulos de processos organizados por natureza (Principais, Apoio, Administrativos, Financeiros, Marketing, Operacionais, Produção, Eventos, Compras, Estoque, Clientes, Fornecedores, Documentos, Receitas, Engenharia de Custos, Precificação, Mão de Obra, Pós-venda, Crescimento), conforme exigido pelo Prompt Oficial TCOS-001.
- D-001-03: Aplicada de forma consistente a regra de nomenclatura D-000-07 ("Receita" = culinário; "Receita Financeira" = entrada financeira) em todo o novo documento, evitando reintroduzir a ambiguidade já resolvida na Fase 000.

### Alterações
- ALT-001-01: Criado o documento `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` (v1.0.0), complementar ao Framework e à Memória — nenhum conteúdo pré-existente foi alterado.

### Melhorias sugeridas (Backlog)
- M-001-01: Considerar, em fase futura, transformar o Mapa de Processos (Seção 6 do Domain Discovery) em um diagrama visual (fluxograma) além do formato textual/tabular, para facilitar comunicação com stakeholders não técnicos.
- M-001-02: Após confirmação das respostas às perguntas Q1–Q18, revisar o Glossário Oficial (Seção 24 do Framework) para incorporar eventuais entidades/termos adicionais confirmados pelo proprietário (ex.: Pagamento, Banco, Conta, Meta, Indicador, Campanha, já detalhados no Domain Discovery mas ainda não presentes no Glossário formal do Framework).

### Riscos encontrados
- R-001-01: O custo de Ficha Técnica pode não incluir hoje mão de obra e insumos de apoio (carvão, gás, embalagem), o que subestimaria o custo real de produção caso confirmado. Status: aberto — depende da resposta à Q12/Q17.
- R-001-02: Ausência de rastreabilidade formal por Lote e de processo estruturado de escala de Mão de Obra são gargalos identificados que, se não corrigidos ainda na fase de processos, tendem a ser herdados como falhas de dado quando o sistema for modelado. Status: aberto — mitigação proposta nas Seções 28–29 do Domain Discovery.
- R-000-03/P-000-03 (herdado da Fase 000): permanece aberto, tratado formalmente como pergunta Q1 desta fase.

### Pendências
- P-001-01: Validação do proprietário sobre o documento `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` (comando formal).
- P-001-02: Respostas às perguntas Q1–Q18 registradas na Seção "Perguntas ao Proprietário" do Domain Discovery — nenhuma foi assumida por suposição.

### Funcionalidades aprovadas / rejeitadas
- Nenhuma (fase de descoberta de negócio; nenhuma funcionalidade de sistema foi proposta).

### Processos identificados
- 25 grupos de processos mapeados (Seções 7–25 do Domain Discovery), cobrindo o ciclo completo do negócio da captação de Lead ao Crescimento/expansão.

### Entidades identificadas
- 29 entidades de negócio detalhadas (Seção 26 do Domain Discovery): Cliente, Lead, Orçamento, Contrato, Campanha, Produto, Ingrediente, Receita, Ficha Técnica, Produção, Fornecedor, Compra, Estoque, Lote, Equipamento, Veículo, Despesa, Receita Financeira, Pagamento, Banco, Conta, Fluxo de Caixa, Funcionário, Documento, Meta, Indicador, Dashboard, Pacote, Evento.

### Módulos existentes
- Nenhum (ainda não houve decisão técnica; apenas mapeamento de domínio).

### Integrações
- Nenhuma (fora de escopo desta fase).

---

## FASE 001B — Business Discovery Questionnaire

**Status:** Questionário entregue — aguardando respostas do proprietário
**Data:** 2026-08-01

O proprietário respondeu `ALTERAR` à Fase 001, considerando o `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` um mapeamento genérico de catering, insuficiente para um ERP totalmente personalizado. Foi criada a subfase 001B, cujo único entregável é o `THE_CHARCOAL_OS_BUSINESS_DISCOVERY_QUESTIONNAIRE.md` — o Business Discovery em si **não foi alterado**, conforme instrução explícita.

### Decisões tomadas
- D-001B-01: O Business Discovery (Fase 001) permanece formalmente em aberto e não aprovado até que as respostas ao questionário sejam incorporadas. Motivo: comando `ALTERAR` do proprietário.
- D-001B-02: O questionário foi estruturado em 35 categorias fixas (definidas pelo proprietário no Prompt Oficial), com perguntas abertas, específicas e práticas, evitando perguntas de sim/não, cada uma acompanhada de justificativa de por que a informação importa para o sistema. Motivo: instrução explícita do Prompt Oficial da subfase 001B.

### Alterações
- ALT-001B-01: Criado o documento `THE_CHARCOAL_OS_BUSINESS_DISCOVERY_QUESTIONNAIRE.md` (v1.0.0). Nenhum outro documento do projeto foi alterado.

### Melhorias sugeridas (Backlog)
- M-001B-01: Após as respostas do proprietário, revisar o `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` linha a linha contra cada resposta, e não apenas incorporar trechos novos — a Fase 001 pode exigir reescrita, não apenas complementação, caso o modelo de negócio real divirja da hipótese inicial (ver R-000-03).

### Riscos encontrados
- Nenhum risco novo. Os riscos R-000-03/P-000-03 (hipótese de domínio de negócio) e R-001-01/R-001-02 (herdados da Fase 001) permanecem em aberto e serão diretamente endereçados pelas respostas a este questionário.

### Pendências
- P-001B-01: Respostas do proprietário às 110 perguntas do questionário (por categoria ou aos poucos, conforme sua conveniência).
- P-001B-02: Após as respostas, reavaliar e possivelmente reescrever o `THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` antes de submetê-lo novamente à aprovação da Fase 001.

### Processos/Entidades identificados
- Nenhum processo ou entidade novo foi formalmente identificado nesta subfase — ela é um instrumento de coleta, não de mapeamento; o mapeamento permanece o do documento da Fase 001, sujeito a revisão.

### Revisão — Roteiro de Entrevista Otimizado (v2.0)

O proprietário aprovou o conteúdo do questionário, mas solicitou (`ALTERAR`), antes de iniciar qualquer entrevista, a reorganização das 110 perguntas em uma sequência estratégica de Fases de Descoberta dependentes entre si. Produzido o documento `THE_CHARCOAL_OS_DISCOVERY_INTERVIEW_ROADMAP.md` (v1.0.0).

**Decisões tomadas:**
- D-001B-03: As 110 perguntas foram organizadas em 12 Fases de Entrevista, cada uma com objetivo e dependência explícita da fase anterior, seguindo a mesma sequência de Cadeia de Valor já registrada na Seção 4 do Domain Discovery (Fornecedor/Compra/Estoque → Produção → Recursos → Custo/Preço). Motivo: instrução explícita do proprietário; reforça consistência entre os documentos da Fase 001 (Seção 9 do Framework — Como Evitar Inconsistências).
- D-001B-04: A pergunta Q94 ("qual evento/produto dá mais lucro") foi movida da categoria Financeiro da Empresa para a Fase 7 (Engenharia de Custos e Precificação), por ser, na prática, a pergunta-síntese do raciocínio de custo/preço, não do raciocínio de caixa.
- D-001B-05: Foram adicionadas 5 perguntas novas, claramente marcadas `[NOVA]`, cobrindo lacunas identificadas apenas ao montar o fluxo contínuo da entrevista: operação em múltiplos locais (Fase 1), identidade visual (Fase 1), controle de acesso a informações sensíveis (Fase 6), enquadramento legal/tributário (Fase 10), e nível de conforto da equipe com tecnologia (Fase 12).
- D-001B-06: O `THE_CHARCOAL_OS_BUSINESS_DISCOVERY_QUESTIONNAIRE.md` original foi mantido intacto como registro histórico da versão aprovada; o roteiro de entrevista é um documento complementar, não substitutivo.

**Alterações:**
- ALT-001B-02: Criado o documento `THE_CHARCOAL_OS_DISCOVERY_INTERVIEW_ROADMAP.md` (v1.0.0). Nenhum outro documento foi alterado.

**Pendências:**
- P-001B-03: Autorização do proprietário para iniciar a Fase 1 da entrevista ("Identidade e Propósito da Empresa"). Nenhuma pergunta foi feita ao proprietário até o momento.
- P-001B-04 (protocolo permanente): ao final de cada Fase de entrevista futura, é obrigatório resumir aprendizados, listar inconsistências, listar dúvidas, listar oportunidades, atualizar este `PROJECT_MEMORY.md` e aguardar nova autorização antes da fase seguinte (ver Seção 3 do Roadmap).

---

## FASE 002 — Domain Model

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_DOMAIN_MODEL.md` v1.0.0)
**Data:** 2026-08-01

Recebido o Prompt Oficial (Documento TCOS-002), foi executada a auditoria de abertura (Seção 17 do Framework) sobre todos os documentos oficiais até então aprovados, e produzido o `THE_CHARCOAL_OS_DOMAIN_MODEL.md`: o Modelo de Domínio Oficial do THE CHARCOAL OS, detalhando 30 entidades de negócio (16 campos cada), Relacionamentos do Domínio, Regras Globais (9 categorias) e 89 Eventos do Domínio catalogados. Nenhuma decisão técnica (banco de dados, classes, código) foi tomada, em conformidade com a restrição da fase.

### Decisões tomadas
- D-002-01: Adotadas 7 "Convenções Gerais" (CG-01 a CG-07), derivadas diretamente dos Princípios Fundamentais PF-01 a PF-12 do Framework, aplicadas por padrão a todas as 30 entidades para evitar repetição e garantir consistência. Motivo: Seção 9 do Framework (Como Evitar Inconsistências).
- D-002-02: Adicionada a entidade **Alocação de Funcionário** (30ª entidade), não presente nas 29 da Fase 001, para formalizar o vínculo entre Funcionário e Evento/Produção. Motivo: lacuna identificada na auditoria de abertura desta fase — já implícita nos capítulos de Mão de Obra/Escalas do Domain Discovery, mas nunca modelada como entidade própria.
- D-002-03: Os campos "Quem pode criar/alterar/excluir/visualizar" de cada entidade foram expressos em termos de áreas de negócio (Comercial, Produção, Financeiro etc.), nunca de perfis técnicos de acesso, para não antecipar decisão técnica fora do escopo desta fase.
- D-002-04: Registrado formalmente que o encerramento da Fase 001 ocorreu antes da execução da entrevista de descoberta, e que o risco R-000-03/P-000-03 (hipótese de domínio de negócio) é herdado por este Domain Model, não apenas pela Fase 001 — qualquer futura confirmação divergente exigirá nova versão deste documento.
- D-002-05: O Fluxo de Caixa foi modelado com uma ressalva explícita de que não é uma entidade transacional discreta, e sim uma visão agregada e derivada — decisão de modelagem de domínio, não uma decisão técnica de arquitetura.

### Alterações
- ALT-002-01: Criado o documento `THE_CHARCOAL_OS_DOMAIN_MODEL.md` (v1.0.0). Nenhum documento da Fase 001 ou do Framework foi alterado.
- ALT-002-02: Atualizados os cabeçalhos de status dos três documentos da Fase 001 (Domain Discovery, Questionnaire, Interview Roadmap) para refletir sua aprovação/encerramento formal, sem alterar qualquer outro conteúdo desses documentos.

### Melhorias sugeridas (Backlog)
- M-002-01: Quando o Framework for revisado para uma futura v1.2.0, incorporar ao Glossário Oficial (Seção 24) os termos ainda ausentes frente às 30 entidades deste Domain Model (Campanha, Ingrediente, Produção, Fornecedor, Compra, Lote, Equipamento, Veículo, Pagamento, Banco, Conta, Fluxo de Caixa, Funcionário, Alocação de Funcionário, Meta, Indicador) — consolida M-001-02, já registrada.
- M-002-02: Retomar formalmente a execução da Fase 001B (entrevista de descoberta) em algum momento futuro — mesmo com a Fase 001 encerrada, as respostas às perguntas Q1–Q110 continuam valiosas para validar ou corrigir este Domain Model.

### Riscos encontrados
- R-002-01 (crítico, herdado): R-000-03/P-000-03 — hipótese de domínio de negócio (produção culinária em brasa/carvão via Eventos) permanece sem confirmação do proprietário, apesar de a Fase 001 estar encerrada e este Domain Model já construído sobre ela. Status: aberto, herdado por toda fase futura que reutilize este vocabulário.
- R-002-02 (herdado): R-001-01 — custo de mão de obra e insumos de apoio podem não estar hoje incorporados ao custo real de produção; tratado como condicionalidade explícita na Regra Global de Engenharia de Custos deste Domain Model. Status: aberto.
- R-002-03: o Glossário Oficial do Framework (20 termos, já aprovado e congelado) está desatualizado frente às 30 entidades deste Domain Model; como o Framework não pode ser alterado sem nova versão formal, a divergência permanece registrada como pendência, não como erro corrigido. Status: aberto — ver M-002-01.

### Pendências
- P-002-01: Validação do proprietário sobre o `THE_CHARCOAL_OS_DOMAIN_MODEL.md` (comando formal).
- P-002-02: Decisão do proprietário sobre M-002-02 — retomar ou não a entrevista de descoberta (Fase 001B) antes de avançar para uma futura fase técnica.

### Entidades identificadas
- 30 entidades detalhadas (29 herdadas da Fase 001 + 1 nova): Cliente, Lead, Orçamento, Contrato, Campanha, Produto, Ingrediente, Receita, Ficha Técnica, Produção, Fornecedor, Compra, Estoque, Lote, Equipamento, Veículo, Despesa, Receita Financeira, Pagamento, Banco, Conta, Fluxo de Caixa, Funcionário, **Alocação de Funcionário (nova)**, Documento, Meta, Indicador, Dashboard, Pacote, Evento.

### Eventos de domínio identificados
- 89 eventos de domínio catalogados (Seção 6 do Domain Model), cobrindo o ciclo de vida completo das 30 entidades.

### Módulos existentes
- Nenhum (ainda não houve decisão técnica; apenas modelagem de domínio).

### Integrações
- Nenhuma (fora de escopo desta fase).

---

## FASE 002A — Business Rules Specification

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_BUSINESS_RULES_SPECIFICATION.md` v1.0.0)
**Data:** 2026-08-01

O proprietário aprovou conceitualmente o Domain Model (comando `ALTERAR`, tratando-o como referência oficial e imutável) e solicitou um documento complementar, TCOS-002A, especificando o comportamento do sistema ("o que o sistema deve fazer quando..."). Produzido o `THE_CHARCOAL_OS_BUSINESS_RULES_SPECIFICATION.md`, com 47 Regras de Negócio (RN-001 a RN-047) cobrindo as 36 áreas exigidas. O `THE_CHARCOAL_OS_DOMAIN_MODEL.md` não foi alterado.

### Decisões tomadas
- D-002A-01: as 47 regras foram organizadas por área, na mesma ordem solicitada pelo proprietário, cada uma com os 12 campos obrigatórios (nome, objetivo, evento disparador, condições, ação do sistema, módulos afetados, entidades alteradas, impacto financeiro, impacto operacional, exceções, alertas, auditoria/histórico).
- D-002A-02: toda regra que dependeria de um parâmetro numérico de negócio ainda não confirmado (consumo por pessoa, fatores de perda de limpeza/produção, margem-alvo de precificação, proporção de escala) foi especificada como lógica de cálculo com o parâmetro **configurável e pendente**, nunca com um valor numérico inventado. Motivo: princípio de governança "nada é assumido, tudo é registrado", e o risco R-000-03 ainda em aberto.
- D-002A-03: "Engenharia de Custos" foi mantida, nesta especificação, como função especializada dentro de Produção/Financeiro, coerente com o já registrado no Domain Model — não foi criada como Área de Empresa própria, evitando inconsistência com a Seção 5 do Domain Discovery.
- D-002A-04: os "módulos afetados" de toda regra usam exatamente os nomes das Áreas da Empresa já definidos na Seção 5 do Domain Discovery, garantindo rastreabilidade entre os três documentos (Domain Discovery, Domain Model, Business Rules).

### Alterações
- ALT-002A-01: criado o documento `THE_CHARCOAL_OS_BUSINESS_RULES_SPECIFICATION.md` (v1.0.0). Nenhum documento anterior foi alterado, incluindo o Domain Model, conforme instrução explícita do proprietário.

### Melhorias sugeridas (Backlog)
- M-002A-01: quando os parâmetros pendentes forem confirmados, criar uma tabela de parâmetros de negócio como anexo vivo deste documento, sem reescrever as regras em si.
- M-002A-02: considerar, em fase técnica futura, um mecanismo de regras configuráveis (não codificadas rigidamente) para os parâmetros numéricos aqui identificados.

### Riscos encontrados
- R-002A-01 (novo): diversas regras de cálculo (consumo por pessoa/tipo/acompanhamento, perdas de limpeza/produção, rendimento, precificação, proporção de escala) dependem de parâmetros de negócio ainda não confirmados pelo proprietário. Enquanto pendentes, as regras especificam que o sistema deve alertar e exigir definição manual — nunca assumir um valor. Risco de retrabalho caso os parâmetros reais divirjam substancialmente da estrutura de cálculo prevista. Status: aberto.
- R-000-03/R-002-01 e R-001-01/R-002-02 (herdados): permanecem abertos e diretamente relevantes a este documento — ver Seção "Dúvidas encontradas" do TCOS-002A.

### Pendências
- P-002A-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_BUSINESS_RULES_SPECIFICATION.md`.
- P-002A-02: fechamento formal da Fase 002 (Domain Model + Business Rules Specification) com comando `APROVADO`.
- P-002A-03: confirmação dos parâmetros de negócio listados no risco R-002A-01 — idealmente via retomada da entrevista de descoberta (Fase 001B).

### Regras de negócio identificadas
- 47 Regras de Negócio (RN-001 a RN-047) especificadas, cobrindo Dashboard CEO, Financeiro Pessoal, Financeiro Empresarial, Integração Pessoa/Empresa, Eventos, CRM, Clientes, Leads, Orçamentos, Contratos, Produção, Engenharia de Custos, Receitas, Fichas Técnicas, Precificação, Consumo (por pessoa/tipo de evento/acompanhamentos), Perdas (limpeza/produção), Rendimento, Compras, Estoque, Lotes, Equipamentos, Funcionários, Escalas, Marketing, Dashboards, Indicadores, Inteligência Artificial, Importação de Extrato Bancário, Conciliação Bancária, Lançamentos Manuais, Metas e Alertas.

### Módulos existentes
- Nenhum (ainda não houve decisão técnica; apenas especificação de comportamento de negócio).

### Integrações
- Nenhuma (fora de escopo desta fase).

---

## FASE 002A (complemento) — Padrão de Documentação do Projeto (Framework v1.2.0)

**Status:** Rascunho entregue — aguardando validação do proprietário
**Data:** 2026-08-01

O proprietário aprovou o conteúdo técnico do `THE_CHARCOAL_OS_BUSINESS_RULES_SPECIFICATION.md` (nenhuma regra, estrutura, numeração ou comportamento do sistema foi alterado) e solicitou (`ALTERAR`) a evolução do padrão de documentação do projeto, via atualização do Framework para v1.2.0.

### Decisões tomadas
- D-002A-05: Adicionadas as Seções 27–30 ao Framework (v1.1.0 → v1.2.0, MINOR), tornando obrigatórias para **todo documento futuro** do projeto: (27) uma seção de abertura "EXECUTIVE MEMORY"; (28) uma seção "RESUMO PARA O PROPRIETÁRIO" em linguagem simples, de no máximo uma página, antes do Quality Gate; (29) o Quality Gate como seção formal obrigatória de todo documento, não apenas do relatório de fase; (30) métricas de encerramento obrigatórias do Quality Gate (páginas, entidades, regras, processos, eventos, decisões, riscos, pendências, melhorias e percentual de maturidade). Motivo: instrução explícita do proprietário.
- D-002A-06: A Seção 27 (Executive Memory) formaliza, com nome único, a prática já exercida sob nomes distintos ("Nota de Auditoria de Abertura") nas Fases 001, 002 e 002A — reconhecidas retroativamente como precedentes válidas, sem necessidade de reformulação retroativa desses documentos já aprovados.
- D-002A-07: A Seção 29 formaliza, como exigência de documento (não apenas de relatório de chat), o Quality Gate já praticado nos encerramentos de fase desde a Fase 000.
- D-002A-08: Nenhuma alteração foi feita em `THE_CHARCOAL_OS_BUSINESS_RULES_SPECIFICATION.md`, `THE_CHARCOAL_OS_DOMAIN_MODEL.md` ou em qualquer outro documento além do Framework, conforme instrução explícita.

### Alterações
- ALT-002A-02: Framework atualizado de v1.1.0 para v1.2.0 (MINOR — adição compatível). Seções 27–31 adicionadas após a Seção 26, antes das Regras Permanentes. Nenhuma seção 1–26 pré-existente foi removida, renumerada ou reescrita.

### Melhorias sugeridas (Backlog)
- M-002A-03: a partir do próximo documento produzido, aplicar as Seções 27–30 na prática e usar essa aplicação real como validação de que a regra é operacionalmente viável (ex.: o limite de "uma página" para o Resumo ao Proprietário pode exigir ajuste conforme a complexidade do documento).

### Riscos encontrados
- Nenhum risco novo. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem inalterados por esta atualização puramente procedimental.

### Pendências
- P-002A-04: validação formal do proprietário sobre a v1.2.0 do Framework.
- P-002A-05 (permanente, a partir de agora): todo documento futuro do projeto deve conter as seções Executive Memory (Seção 27), Resumo para o Proprietário (Seção 28) e Quality Gate com métricas de encerramento (Seções 29–30) do Framework.

### Módulos existentes
- Nenhum (alteração puramente de governança/documentação).

### Integrações
- Nenhuma.

---

## FASE 003 — Functional Specification

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_FUNCTIONAL_SPECIFICATION.md` v1.0.0)
**Data:** 2026-08-01

O proprietário aprovou formalmente o TCOS-002A e autorizou o avanço para o TCOS-003, definindo todas as funcionalidades do THE CHARCOAL OS (o que o usuário faz no sistema), em 25 módulos obrigatórios. Seguindo o Framework v1.2.0, o documento abre com Executive Memory e encerra com Resumo para o Proprietário e Quality Gate.

### Decisões tomadas
- D-003-01: as 47 Regras de Negócio do TCOS-002A foram todas mapeadas a pelo menos uma funcionalidade deste documento, para que nenhuma regra fique "sem tela" (funcionalidade) correspondente.
- D-003-02: CRM, Clientes e Leads foram tratados como três módulos distintos (conforme solicitado), evitando duplicidade ao definir CRM como visão consolidada de funil/atribuição, e Leads/Clientes como o cadastro e ciclo de vida específico de cada entidade.
- D-003-03: foi criado o Módulo 24 (Configurações) como o local funcional explícito onde os parâmetros de negócio ainda pendentes (R-002A-01) serão definidos — cada parâmetro tem uma funcionalidade própria (F-075 a F-079), mantendo o princípio de nunca assumir um valor não confirmado.
- D-003-04: foi criado o Módulo 25 (Administração do Sistema) com um papel transversal "Administrador do Sistema", necessário para gestão de usuários/permissões e do mecanismo de Alertas (RN-047), sem antecipar nenhuma decisão técnica de autenticação/autorização.

### Alterações
- ALT-003-01: criado o documento `THE_CHARCOAL_OS_FUNCTIONAL_SPECIFICATION.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-003-01: considerar um "assistente de configuração inicial" que guie o preenchimento de todos os parâmetros pendentes do Módulo 24 de uma só vez.
- M-003-02: reavaliar as Funcionalidades Futuras do Roadmap (Seção 4.4 do TCOS-003) após a maturidade dos 25 módulos atuais.

### Riscos encontrados
- Nenhum risco novo. R-000-03/R-002-01, R-001-01/R-002-02 e R-002A-01 permanecem abertos e diretamente relevantes — o Módulo 24 (Configurações) é a mitigação funcional planejada para R-002A-01.

### Pendências
- P-003-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_FUNCTIONAL_SPECIFICATION.md`.
- P-003-02: preenchimento real dos parâmetros do Módulo 24 (Configurações) — idealmente via retomada da entrevista de descoberta.

### Funcionalidades identificadas
- 83 funcionalidades (F-001 a F-083) especificadas em 25 módulos obrigatórios (Dashboard CEO, Financeiro Pessoal, Financeiro Empresarial, CRM, Clientes, Leads, Eventos, Orçamentos, Contratos, Produção, Engenharia de Custos, Receitas, Fichas Técnicas, Precificação, Compras, Estoque, Lotes, Equipamentos, Funcionários, Escalas, Marketing, Inteligência Artificial, Documentos, Configurações, Administração do Sistema).

### Módulos existentes
- 25 módulos funcionais especificados (ainda sem decisão técnica de implementação).

### Integrações
- Nenhuma técnica; dependências entre módulos mapeadas em nível de negócio (Seção 4.2 do TCOS-003).

---

## FASE 003 (complemento) — Validação de Cobertura Funcional (TCOS-003 v1.1.0)

**Status:** Rascunho entregue — aguardando validação do proprietário
**Data:** 2026-08-01

O proprietário aprovou conceitualmente o conteúdo do TCOS-003 (nenhuma funcionalidade, módulo, regra, integração ou numeração foi alterada) e solicitou (`ALTERAR`) a adição de um capítulo permanente de Validação de Cobertura Funcional, cruzando as 30 entidades do Domain Model e as 47 Regras de Negócio contra as 83 funcionalidades já aprovadas.

### Decisões tomadas
- D-003A-01: adicionado o capítulo 7 "Validação de Cobertura Funcional" ao TCOS-003 (v1.0.0 → v1.1.0, MINOR), com duas matrizes de cobertura (entidades e regras), funcionalidades dependentes de parâmetros/integrações, consolidação de críticas/opcionais/roadmap, gaps e melhorias. Nenhum conteúdo da v1.0.0 foi alterado.

### Alterações
- ALT-003A-01: `THE_CHARCOAL_OS_FUNCTIONAL_SPECIFICATION.md` atualizado de v1.0.0 para v1.1.0. Nenhum outro documento foi tocado.

### Melhorias sugeridas (Backlog)
- M-003A-01: incluir, em versão futura, funcionalidades de cadastro de Banco/Conta.
- M-003A-02: decidir com o proprietário se "Metas" (RN-046) deve virar um 26º módulo funcional próprio ou permanecer como configuração da Direção dentro do Dashboard CEO.
- M-003A-03: incluir, em versão futura, funcionalidades explícitas de cadastro para Produto (catálogo), Ingrediente, Fornecedor, Pacote, e de definição de fórmula de Indicador.

### Riscos encontrados
- Nenhum risco novo. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem, agora com rastreabilidade explícita de quais funcionalidades cada um afeta (Seção 7.3 do TCOS-003).

### Gaps encontrados (auditoria de cobertura)
- G-001: entidade Banco sem funcionalidade de cadastro (usada apenas como dado).
- G-002: entidade Meta e Regra RN-046 sem cobertura funcional nesta fase — diferença legítima de escopo entre os 36 temas do TCOS-002A e os 25 módulos mínimos do TCOS-003, não um erro de execução.
- G-003: Produto, Ingrediente, Fornecedor, Conta, Indicador e Pacote são usados por funcionalidades existentes, mas nenhuma funcionalidade os cadastra/cria explicitamente.
- G-004: RN-010 (Fidelização de Cliente) citada apenas na descrição do Módulo 05, sem funcionalidade dedicada (regra 100% automática).

### Pendências
- P-003A-01: validação formal do proprietário sobre a v1.1.0 do TCOS-003.
- P-003A-02: decisão do proprietário sobre M-003A-02 (módulo de Metas).
- P-003A-03: tratamento dos gaps G-001 a G-004 em uma futura versão do TCOS-003, antes de avançar para fases técnicas.

### Módulos existentes
- 25 módulos funcionais (inalterados); nenhum novo módulo criado nesta complementação.

### Integrações
- Nenhuma nova; dependências de integração futura documentadas na Seção 7.4 do TCOS-003 (extrato bancário).

---

## FASE 003 (complemento 2) — Módulos Metas e Bancos (TCOS-003 v1.2.0)

**Status:** Rascunho entregue — aguardando validação do proprietário
**Data:** 2026-08-01

O proprietário confirmou que os gaps G-001 (Banco) e G-002 (Meta) identificados na v1.1.0 representam evolução natural do sistema, não falhas, e solicitou (`ALTERAR`) a criação dos Módulos 26 (Metas) e 27 (Bancos), com atualização automática de todas as matrizes e estatísticas do documento.

### Decisões tomadas
- D-003B-01: criado o Módulo 26 — Metas (F-084 a F-091), resolvendo o gap G-002 e dando cobertura direta à Regra RN-046. O Dashboard CEO (Módulo 01) passa a apenas consumir/apresentar Metas (F-091), nunca geri-las — toda gestão ocorre exclusivamente no Módulo 26, conforme instrução explícita.
- D-003B-02: criado o Módulo 27 — Bancos (F-092 a F-098), resolvendo o gap G-001 (Banco) e parte do G-003 (Conta), centralizando cadastro de Banco/Conta/Cartão que os Módulos 02 e 03 já utilizavam como dado.
- D-003B-03: "Cartão" e "Conta Internacional" foram modelados como tipo/atributo da entidade Conta já existente no Domain Model, não como novas entidades — para respeitar a restrição de não alterar entidades nesta fase. Registrada nova melhoria (M-003A-04) para avaliar se Cartão deveria ser uma entidade própria em uma futura revisão do Domain Model.
- D-003B-04: todas as matrizes de cobertura (entidades, regras), a Matriz Funcional, o Índice Geral e as Estatísticas do Documento foram atualizados para refletir os 27 módulos e 98 funcionalidades — sem alterar nenhum conteúdo de módulos 01–25, funcionalidades F-001–F-083, regras de negócio ou entidades.

### Alterações
- ALT-003B-01: `THE_CHARCOAL_OS_FUNCTIONAL_SPECIFICATION.md` atualizado de v1.1.0 para v1.2.0. Nenhum outro documento foi tocado.

### Melhorias sugeridas (Backlog)
- M-003A-01 e M-003A-02: concluídas nesta fase.
- M-003A-03 (mantida): cadastro explícito de Produto/Ingrediente/Fornecedor/Pacote e definição de fórmula de Indicador.
- M-003A-04 (nova): avaliar se Cartão deve virar entidade própria no Domain Model.

### Riscos encontrados
- Nenhum risco novo. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) inalterados.

### Gaps encontrados
- G-001 e G-002: **resolvidos** por esta complementação.
- G-003 (parcial: Conta): **resolvido**; Produto/Ingrediente/Fornecedor/Pacote/Indicador permanecem parciais (fora do escopo desta complementação).
- G-004 (RN-010): mantido como observação, não como falha.
- G-005 (novo): Cartão/Conta Internacional modelados como tipo de Conta, não como entidade própria — decisão registrada, não um erro.

### Pendências
- P-003B-01: validação formal do proprietário sobre a v1.2.0 do TCOS-003.
- P-003B-02: decisão sobre M-003A-04 (Cartão como entidade própria).
- Pendências herdadas: M-003A-03, parâmetros do Módulo 24, confirmação do domínio de negócio (R-000-03).

### Módulos existentes
- 27 módulos funcionais especificados (25 já existentes + Metas + Bancos).

### Funcionalidades identificadas
- 98 funcionalidades no total (F-001 a F-098); 15 novas nesta fase (F-084 a F-098).

### Integrações
- Nenhuma técnica; Módulo 27 documentado como fonte de dado para Módulos 02, 03 e 22 (Seção 4.2/7.11 do TCOS-003).

---

## FASE 003 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-01 (comando `APROVADO`)
**Data:** 2026-08-01

O `THE_CHARCOAL_OS_FUNCTIONAL_SPECIFICATION.md` (v1.2.0) passa a ser documentação oficial do THE CHARCOAL OS. Nenhuma alteração futura sem criação de nova versão.

---

## FASE 004 — User Journeys & System Flows

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_USER_JOURNEYS_AND_SYSTEM_FLOWS.md` v1.0.0)
**Data:** 2026-08-01

Recebido o Prompt Oficial (TCOS-004), executada a auditoria de abertura sobre todos os documentos oficiais (Framework v1.2.0, Domain Discovery, Questionnaire, Interview Roadmap, Domain Model, Business Rules Specification, Functional Specification v1.2.0), e produzido o documento com 30 fluxos operacionais completos, Matriz de Integração entre Módulos e Mapa Operacional em linguagem simples. Nenhum documento anterior foi alterado.

### Decisões tomadas
- D-004-01: os 30 fluxos foram documentados com os 19 campos obrigatórios cada, referenciando por nome/número as entidades, Regras de Negócio, módulos e funcionalidades já oficiais, sem redefini-los. Sobreposições aparentes entre fluxos explicitamente solicitados em separado (Evento vs. Encerramento de Evento; os quatro fluxos de Dashboards/Indicadores) foram resolvidas por escopo (visão geral vs. detalhamento), com referência cruzada em vez de repetição de conteúdo.

### Alterações
- ALT-004-01: criado o documento `THE_CHARCOAL_OS_USER_JOURNEYS_AND_SYSTEM_FLOWS.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-004-01: unificar, em fase técnica futura, os mecanismos de FL-026/FL-027/FL-028 em um único motor de recálculo de Indicadores/Dashboards.
- M-004-02: aprofundar a jornada de Pós-venda (FL-030) quando a entrevista de descoberta for retomada — hoje a mais fracamente sustentada por Regras/Funcionalidades dedicadas (apenas RN-010 e F-014).

### Riscos encontrados
- Nenhum risco novo. R-000-03/R-002-01, R-001-01/R-002-02 e R-002A-01 permanecem abertos, agora rastreáveis a jornadas específicas (FL-007, FL-013, FL-014, FL-015 dependem de parâmetros ainda não confirmados).

### Gaps/observações de auditoria
- Confirmado (não é gap novo): F-072–F-074 (Documentos) e F-080/F-081/F-083 (Administração do Sistema) são transversais, sem jornada de negócio própria entre os 30 fluxos — esperado.
- Confirmado (não é gap novo): RN-004 e RN-047 são processos periódicos/administrativos sem jornada própria.
- Reforçado: a jornada de Pós-venda (FL-030) é a mais fracamente sustentada por Regras/Funcionalidades dedicadas — consistente com as perguntas Q79–Q81 do Business Discovery, ainda sem resposta.
- Confirmado: nenhuma dependência circular entre os 27 módulos; grafo de dependências é acíclico.

### Pendências
- P-004-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_USER_JOURNEYS_AND_SYSTEM_FLOWS.md`.
- Pendências herdadas: parâmetros do Módulo 24, M-003A-03, M-003A-04, confirmação do domínio de negócio (R-000-03).

### Fluxos identificados
- 30 fluxos completos (FL-001 a FL-030), cobrindo todas as jornadas obrigatórias solicitadas, mais Matriz de Integração entre Módulos (15 relações mapeadas) e Mapa Operacional consolidado.

### Módulos existentes
- 27 módulos (inalterados nesta fase).

### Integrações
- 15 relações módulo-a-módulo documentadas na Matriz de Integração (Seção 4.1 do TCOS-004); nenhuma dependência circular encontrada.

---

## FASE 004 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-01 (comando `APROVADO`)
**Data:** 2026-08-01

O `THE_CHARCOAL_OS_USER_JOURNEYS_AND_SYSTEM_FLOWS.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS. Nenhuma alteração futura sem criação de nova versão.

---

## FASE 005 — UX/UI Specification

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_UX_UI_SPECIFICATION.md` v1.0.0)
**Data:** 2026-08-01

Recebido o Prompt Oficial (TCOS-005), executada a auditoria de abertura sobre todos os 8 documentos oficiais, e produzido o documento com as 30 telas obrigatórias (11 Dashboards + 19 telas de módulo), Navegação do Sistema, Design System completo e capítulo de Experiência do Usuário. Nenhum documento anterior foi alterado.

### Decisões tomadas
- D-005-01: as 30 telas foram documentadas com os 25 campos obrigatórios cada (Dashboards com detalhamento adicional de layout/origem de dado/integração com IA), referenciando por nome/número as entidades, Regras, funcionalidades e fluxos já oficiais. Módulo 23 (Documentos) foi servido por um componente reutilizável "Documentos Anexados" em vez de tela própria; CRM, Marketing e Inteligência Artificial tiveram suas funcionalidades de gestão incorporadas aos respectivos Dashboards, sem tela de gestão separada — ambas decisões de design explicitamente registradas, não gaps.

### Alterações
- ALT-005-01: criado o documento `THE_CHARCOAL_OS_UX_UI_SPECIFICATION.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-005-01: barra de busca global unificada (Cliente, Evento, Orçamento, Contrato).
- M-005-02: assistente de configuração inicial guiado no Módulo 24 (reforça M-003A-01).
- M-005-03: perfis de acesso pré-configurados por função no Módulo 25 (Administração).

### Riscos encontrados
- Nenhum risco novo. R-000-03/R-002-01, R-001-01/R-002-02 e R-002A-01 permanecem abertos; nenhum bloqueia o design de UX/UI, pois toda tela dependente de parâmetro pendente já prevê um estado de interface "parâmetro não definido" (bloqueio com link direto para Configurações).

### Pendências
- P-005-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_UX_UI_SPECIFICATION.md`.
- Pendências herdadas: parâmetros do Módulo 24, M-003A-03, M-003A-04, M-004-01/02, confirmação do domínio de negócio (R-000-03).

### Telas identificadas
- 30 telas completas (11 Dashboards + 19 telas de módulo), Design System com 15 componentes reutilizáveis catalogados, e capítulo de Navegação cobrindo entrada, busca, filtro, criação, edição, exclusão (sempre inativação), impressão, exportação, importação, uso de IA, histórico e notificações.

### Módulos existentes
- 27 módulos (inalterados); 26 com tela própria, 1 (Documentos) servido por componente reutilizável.

### Integrações
- 15 relações módulo-a-módulo reutilizadas da Matriz de Integração do TCOS-004; nenhuma nova.

---

## FASE 005 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-01 (comando `APROVADO`)
**Data:** 2026-08-01

O `THE_CHARCOAL_OS_UX_UI_SPECIFICATION.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS. Nenhuma alteração futura sem criação de nova versão.

---

## FASE 006 — System Architecture

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_SYSTEM_ARCHITECTURE.md` v1.0.0)
**Data:** 2026-08-01

Recebido o Prompt Oficial (TCOS-006), executada a auditoria de abertura sobre todos os 9 documentos oficiais, e produzido o documento com a arquitetura conceitual completa: 5 camadas, 18 integrações de domínio, matriz de dependências dos 27 módulos, fluxo global de dados, 15 Serviços Conceituais, Event Bus, segurança conceitual e escalabilidade. Nenhuma tecnologia (linguagem, banco de dados, framework, API, nuvem, infraestrutura) foi definida. Nenhum documento anterior foi alterado.

### Decisões tomadas
- D-006-01: os 27 módulos funcionais foram agrupados em 15 Serviços Conceituais coesos (14 correspondentes a grupos de módulos + 1 transversal, Auditoria), evitando o antipadrão de um serviço por módulo/tela. Toda comunicação entre Serviços ocorre por evento publicado (Event Bus) ou consulta ao contrato público — nunca por acesso direto ao dado interno de outro Serviço.
- D-006-02: a orquestração de confirmação de Evento (RN-006), até então descrita funcionalmente como uma sequência de ações, foi modelada arquiteturalmente como um único evento publicado ("Evento confirmado") com múltiplos Serviços assinantes independentes — resolvendo um risco de acoplamento identificado na auditoria de abertura.
- D-006-03: criado o Serviço de Indicadores e Dashboards como único ponto de consumo de dado para todos os Dashboards (CEO e especializados), resolvendo estruturalmente a melhoria M-004-01 (unificação dos três mecanismos de atualização de Dashboard/Indicador do TCOS-004).
- D-006-04: criado o Serviço de Auditoria, transversal e sem módulo funcional próprio, que assina todos os eventos do Event Bus sem exceção — materialização arquitetural do Princípio PF-04 (histórico obrigatório).

### Alterações
- ALT-006-01: criado o documento `THE_CHARCOAL_OS_SYSTEM_ARCHITECTURE.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-006-01 (nova): quando a dimensão "Organização/Unidade" (múltiplas filiais/empresas) for implementada, revisar o contrato de consulta de todos os 15 Serviços para incluí-la desde o início.
- M-004-01 (herdada): marcada como **resolvida estruturalmente** por esta arquitetura.

### Riscos encontrados
- Nenhum risco novo de negócio. Dois riscos técnicos foram identificados e resolvidos dentro da própria fase (acoplamento na orquestração de Evento; acoplamento no consumo do Dashboard CEO) — ver Auditoria de Abertura do TCOS-006.
- Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem abertos, sem impedir a arquitetura conceitual.

### Pendências
- P-006-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_SYSTEM_ARCHITECTURE.md`.
- Pendências herdadas: parâmetros do Módulo 24, M-003A-03/04, M-005-01/02/03, confirmação do domínio de negócio (R-000-03).

### Dependências/Integrações identificadas
- 27 relações módulo→Serviço mapeadas na Matriz de Dependências; 18 integrações de domínio documentadas; 15 Serviços Conceituais; 23 eventos internos arquiteturalmente destacados (subconjunto dos 89 já catalogados no Domain Model).

### Módulos existentes
- 27 módulos (inalterados), agora organizados em 15 Serviços Conceituais.

---

## FASE 006 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-01 (comando `APROVADO`)
**Data:** 2026-08-01

O `THE_CHARCOAL_OS_SYSTEM_ARCHITECTURE.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS. Nenhuma alteração futura sem criação de nova versão.

---

## FASE 007 — Data Architecture

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_DATA_ARCHITECTURE.md` v1.0.0)
**Data:** 2026-08-01

Recebido o Prompt Oficial (TCOS-007), executada a auditoria de abertura sobre todos os 10 documentos oficiais, e produzido o documento com a arquitetura de dados completa: 7 Domínios de Dados, 24 Agregados, as 30 entidades documentadas nos 12 campos exigidos, Dados Configuráveis/Históricos/Auditoria/Analíticos/IA, Mapa Global dos Dados, Governança dos Dados, 8 Estratégias e Classificação dos Dados em 7 categorias. Nenhuma tecnologia de persistência foi definida. Nenhum documento anterior foi alterado.

### Decisões tomadas
- D-007-01: introduzidos metadados universais (Identificador Global estável e nunca reutilizado; autor/data de criação e última alteração; escopo organizacional reservado) aplicáveis a todas as 30 entidades sem exceção — lacuna real identificada na auditoria de abertura (nenhum documento anterior havia formalizado isso).
- D-007-02: Despesa, Receita Financeira e Pagamento foram consolidados em um único "Agregado Financeiro" com três entidades-membro, em vez de três estruturas de integridade isoladas — simplificação concreta identificada na auditoria.
- D-007-03: fixada a regra geral de soft delete: nenhuma entidade que já participou de um processo de negócio é fisicamente excluída (CG-01/PF-04); apenas registros puramente transitórios e nunca confirmados (ex.: rascunho abandonado) podem ser removidos fisicamente.
- D-007-04: reservado o escopo "Organização/Unidade" como atributo transversal aditivo (não uma entidade nova), preparando a dimensão multiempresa/multifilial (M-006-01) sem exigir redesenho de nenhuma entidade quando implementada.

### Alterações
- ALT-007-01: criado o documento `THE_CHARCOAL_OS_DATA_ARCHITECTURE.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-007-01 (nova): ao confirmar a decisão de negócio sobre compartilhamento de catálogo (Produto/Receita/Ficha Técnica) entre futuras Unidades/Filiais, atualizar esta arquitetura antes de iniciar o TCOS-008.
- M-006-01 (herdada): permanece pendente de implementação, agora com mecanismo de adição aditiva já definido.

### Riscos encontrados
- Nenhum risco novo. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem abertos, sem impedir a arquitetura de dados.

### Dúvidas encontradas
- Se Produto/Receita/Ficha Técnica devem ser compartilhados entre futuras Unidades/Filiais ou específicos de cada uma — decisão de negócio ainda não confirmada (ligada a R-000-03).

### Pendências
- P-007-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_DATA_ARCHITECTURE.md`.
- Pendências herdadas: parâmetros do Módulo 24, M-003A-03/04, M-005-01/02/03, M-006-01, confirmação do domínio de negócio (R-000-03).

### Estrutura de dados identificada
- 7 Domínios de Dados, 24 Agregados, 30 entidades (0 novas, todas herdadas do Domain Model com camada de dados definida), 30+ relacionamentos mapeados no Mapa Global dos Dados, 7 categorias de Classificação dos Dados.

---

## FASE 007 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-01 (comando `APROVADO`)
**Data:** 2026-08-01

O `THE_CHARCOAL_OS_DATA_ARCHITECTURE.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS. Nenhuma alteração futura sem criação de nova versão.

---

## FASE 008 — Database Specification

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_DATABASE_SPECIFICATION.md` v1.0.0)
**Data:** 2026-08-01

Recebido o Prompt Oficial (TCOS-008), executada a auditoria de abertura sobre todos os 11 documentos oficiais, e produzido o documento com a especificação conceitual completa do banco de dados: 9 Esquemas, 32 estruturas conceituais de tabela (30 de entidade + Log de Auditoria + Parâmetros de Configuração), cada uma nos 15 campos exigidos, mais os 12 capítulos de estratégia obrigatórios (Modelo Conceitual, Esquemas, Chaves, Integridade Referencial, Versionamento, Auditoria, Histórico, Performance, Backup, Escalabilidade, Multiempresa, Multifilial). Nenhum SGBD, SQL ou código foi definido. Nenhum documento anterior foi alterado.

### Decisões tomadas
- D-008-01: as 30 entidades foram organizadas em 9 Esquemas lógicos (7 de Domínio de Dados + `auditoria` + `configuracao`, ambos transversais), espelhando os Serviços Conceituais já definidos no System Architecture.
- D-008-02: Fluxo de Caixa e Indicador foram formalmente definidos como estruturas de leitura derivada/cache, nunca como cópia armazenada do dado de origem — resolvendo uma duplicidade estrutural que só estava implícita até esta fase.
- D-008-03: cardinalidade explícita foi adicionada a todo relacionamento do Mapa Global dos Dados (TCOS-007) — atributo que nenhum documento anterior havia formalizado.
- D-008-04: identificadas estruturas de alto volume de escrita (Log de Auditoria, Pagamento, Produção, Alocação de Funcionário, Despesa, Receita Financeira) como candidatas a particionamento conceitual por período, sem definir a tecnologia que implementaria isso.

### Alterações
- ALT-008-01: criado o documento `THE_CHARCOAL_OS_DATABASE_SPECIFICATION.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-008-01 (nova): ao escolher a tecnologia de banco de dados, avaliar mecanismos nativos de particionamento para as 6 estruturas de alto volume identificadas.
- M-007-01 (herdada): decisão de negócio sobre compartilhamento de catálogo entre Unidades permanece pendente, com impacto direto em 4 estruturas (`tb_produto`, `tb_receita`, `tb_ficha_tecnica`, `tb_ingrediente`).

### Riscos encontrados
- Nenhum risco novo. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem abertos, sem impedir a especificação do banco.

### Pendências
- P-008-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_DATABASE_SPECIFICATION.md`.
- Pendências herdadas: parâmetros do Módulo 24 (agora com estrutura de dado definida), M-003A-03/04, M-005-01/02/03, M-006-01, M-007-01, confirmação do domínio de negócio (R-000-03).

### Estrutura de banco identificada
- 9 Esquemas, 32 estruturas conceituais (30 de entidade + 2 transversais), 30+ relacionamentos com cardinalidade explícita, 96 índices conceituais recomendados, 32 restrições de integridade.

---

## FASE 008 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-01 (comando `APROVADO`)
**Data:** 2026-08-01

O `THE_CHARCOAL_OS_DATABASE_SPECIFICATION.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS. Nenhuma alteração futura sem criação de nova versão.

*Nota de auditoria (registrada na Fase 010): este fechamento formal não havia sido registrado no momento da aprovação — corrigido agora, por adição, sem alterar nenhum conteúdo já existente neste arquivo.*

---

## FASE 009 — Integration and API Contract

**Data:** 2026-08-01

Recebido o Prompt Oficial (TCOS-009), executada a auditoria de abertura sobre todos os 12 documentos oficiais, e produzido o documento com o contrato conceitual de integração entre módulos: 20 Integrações (IN-001 a IN-020) cobrindo os 18 tópicos de comunicação exigidos, mais 7 capítulos de amarração (Matriz Geral de Integração, Mapa Global das Comunicações, Mapa dos Eventos do Sistema, Cadeia de Atualização dos Dashboards, Cadeia de Atualização da IA, Matriz de Dependências entre Serviços, Fluxo de Sincronização entre Módulos). Nenhuma API, endpoint, protocolo, formato de mensagem ou tecnologia foi definido. Nenhum documento anterior foi alterado.

### Decisões tomadas
- D-009-01: IN-016 (Indicadores) e IN-017 (Dashboards) foram documentadas como duas Integrações formalmente distintas (por exigência do Prompt Oficial), mas unidas em uma única cadeia explícita no Capítulo 7 — evitando que um leitor futuro as trate como dois mecanismos independentes.
- D-009-02: IN-005 (Produção) e IN-019 (Pessoas/Escalas) foram confirmadas como ramificações paralelas e independentes de uma única publicação do evento "Evento confirmado" (parte de IN-001), documentadas separadamente apenas pela exigência de detalhamento por tópico do Prompt Oficial — comportamento esclarecido no Capítulo 10 (Fluxo de Sincronização).
- D-009-03: distinção formal entre "Eventos de Domínio" (89, catalogados no TCOS-002, ciclo de vida de entidade) e "Eventos Arquiteturais do Event Bus" (ex.: "Indicador recalculado", "Custo recalculado", "Sugestão gerada (IA)", já previstos no TCOS-006) — nenhum dos dois catálogos foi alterado, apenas esclarecidos lado a lado no Capítulo 6.

### Alterações
- ALT-009-01: criado o documento `THE_CHARCOAL_OS_INTEGRATION_AND_API_CONTRACT.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-009-01 (nova): ao desenhar o mecanismo real de mensageria em fase técnica futura, avaliar se os eventos arquiteturais do Event Bus (Custo recalculado, Indicador recalculado, Sugestão gerada) devem ser incorporados ao catálogo oficial de eventos de domínio em uma eventual v1.1.0 do TCOS-002, por clareza de nomenclatura única.

### Riscos encontrados
- Nenhum risco novo. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem abertos, sem impedir o contrato conceitual de integração — nenhuma integração dependente de parâmetro pendente foi documentada sem seu comportamento de bloqueio/alerta correspondente.

### Pendências
- P-009-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_INTEGRATION_AND_API_CONTRACT.md`.
- Pendências herdadas: parâmetros do Módulo 24, M-003A-03/04, M-005-01/02/03, M-006-01, M-007-01, M-008-01, confirmação do domínio de negócio (R-000-03).

### Estrutura de integração identificada
- 20 Integrações, 27 de 27 módulos cobertos (100%), 15 de 15 Serviços cobertos (100%), 30 de 30 entidades conectadas (100%), 16 eventos formalmente referenciados (13 de domínio + 3 arquiteturais), 30 das 47 Regras de Negócio com cadeia multi-Serviço documentada. Maturidade estimada do projeto: 80%.

---

## FASE 009 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-01 (comando `APROVADO`)
**Data:** 2026-08-01

O `THE_CHARCOAL_OS_INTEGRATION_AND_API_CONTRACT.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS. Nenhuma alteração futura sem criação de nova versão.

---

## FASE 010 — Backend Architecture

**Status:** Rascunho aguardando validação do proprietário (comando `CORRIGIR` recebido e executado; ainda não aprovada)
**Data:** 2026-08-01

Recebido o Prompt Oficial (TCOS-010), executada a auditoria de abertura sobre os 13 documentos oficiais congelados, e produzido o documento com a arquitetura lógica interna de backend: organização em 4 camadas por Serviço, os 15 Serviços Conceituais detalhados nos 8 campos exigidos (Objetivo, Responsabilidades, Entradas, Saídas, Dependências, Regras de funcionamento, Restrições, Impacto nos demais módulos), o conceito de Caso de Uso, orquestração coreografada, processamento síncrono/assíncrono, e 10 componentes transversais formalizados (3 deles genuinamente novos: Jobs Agendados, Filas Conceituais, e a separação Logs/Auditoria/Observabilidade/Tolerância a Falhas). Nenhuma linguagem, framework, banco físico ou API foi definida. Nenhum documento anterior foi alterado.

### Decisões tomadas (primeira rodada)
- D-010-01: o backend ocupa 4 das 5 camadas macro já definidas no System Architecture (todas exceto Apresentação); cada um dos 15 Serviços é internamente organizado nessas mesmas 4 camadas, escopadas à sua própria responsabilidade.
- D-010-02: o Caso de Uso foi definido como a menor unidade de execução de backend, sempre correspondente a uma funcionalidade (F-XXX) já aprovada, e sempre operando sobre exatamente um Agregado (TCOS-007) por transação — nunca dois Agregados na mesma transação, mesmo dentro do mesmo Serviço.
- D-010-03: a orquestração multi-Serviço (ex.: confirmação de Evento) é formalmente **coreografada** (cada Serviço reage a um evento público por conta própria), nunca **centralizada** — nenhum Caso de Uso de origem aguarda a conclusão de Casos de Uso reativos em outros Serviços.
- D-010-04: três lacunas técnicas reais, nunca antes formalizadas em nenhum documento aprovado, foram identificadas e resolvidas nesta fase por adição: (1) Jobs Agendados; (2) Filas Conceituais; (3) separação explícita entre Auditoria de negócio e Logs técnicos, com Observabilidade e Tolerância a Falhas como camadas transversais adicionais.

### Auditoria Corretiva (comando `CORRIGIR`, executada após a primeira entrega)

O proprietário determinou uma segunda rodada de auditoria antes de aprovar. Inconsistências encontradas e correções executadas:

- **Contagem de Documentos Oficiais:** a Executive Memory listava 14 artefatos, mas o restante do documento alternava entre "13" e "os 13" sem declarar critério. Corrigido: **13 Documentos Oficiais Congelados** (entregáveis de Fase, imutáveis sem nova versão) **+ 1 Documento Oficial Vivo** (`PROJECT_MEMORY.md`) = **14 Documentos Oficiais no total**, critério agora explícito em todas as ocorrências do TCOS-010.
- **Regra Transacional de Agregados:** reformulada para a versão oficial de 6 pontos determinada pelo proprietário (consulta apenas via contrato público; uma transação por Agregado; nenhuma transação distribuída; alteração em outro Agregado sempre via novo Caso de Uso iniciado por Evento; consulta nunca amplia a transação; assíncrono sempre com retry/idempotência/fila de falhas/reconciliação) — propagada sem contradição pelos Capítulos 7, 8, 9, 10, 11, 12 e 16 do TCOS-010.
- **Cobertura das 47 Regras de Negócio:** a estatística anterior ("34 das 47") foi substituída por uma Matriz de Rastreabilidade completa (novo Capítulo 30 do TCOS-010), demonstrando rastreabilidade **47/47** — Serviço, Caso de Uso, tipo de execução, Agregado, evento publicado, Integração relacionada e capítulo responsável para cada regra, com justificativa formal para as 2 regras (RN-004, RN-007) sem evento/Integração dedicada.
- **Catálogo de Jobs Agendados:** ampliado de 5 para **8 Jobs** — 3 regras dependentes de tempo (RN-011, RN-030, RN-042) haviam sido omitidas na primeira rodada.
- **Referências cruzadas internas:** mais de 60 ocorrências de "Capítulo N" verificadas uma a uma contra os cabeçalhos reais do TCOS-010; 2 estavam desatualizadas ("Jobs Agendados, Capítulo 13" e "Filas Conceituais, Capítulo 14" — corretos: 15 e 16) e foram corrigidas.
- **Nomenclatura do `PROJECT_MEMORY.md`:** verificado via `git ls-files` — um único arquivo com esse nome exato no repositório; nenhuma divergência ou duplicata encontrada.
- **Declarações absolutas:** frases como "todos os documentos foram lidos integralmente" e "nenhuma inconsistência encontrada" foram substituídas por afirmações com escopo declarado; a promessa de "implementação integral a partir deste único documento" (Capítulo 1 do TCOS-010) foi reformulada para descrever exatamente o que o documento fornece.

Nenhuma Regra de Negócio foi criada; nenhum documento das Fases 000-009 foi alterado; nenhuma tecnologia foi escolhida; a Fase 011 não foi criada.

### Alterações
- ALT-010-01: criado o documento `THE_CHARCOAL_OS_BACKEND_ARCHITECTURE.md` (v1.0.0, rascunho). Nenhum documento anterior foi alterado.
- ALT-010-02: aplicadas, no mesmo arquivo em rascunho, as correções da Auditoria Corretiva acima (nenhuma alteração de documento já congelado).

### Melhorias sugeridas (Backlog)
- M-010-01 (mantida): ao escolher a tecnologia de mensageria em fase técnica futura, avaliar mecanismos nativos de garantia de entrega/ordem/idempotência antes de implementar o Barramento de Eventos e Filas de forma customizada.
- M-010-02 (mantida): o parâmetro "X dias antes do Evento" usado pelo Job de alerta de escala não confirmada ainda não está definido — associado à mesma pendência já registrada para o Módulo 24 (Configurações).
- M-010-03 (nova, desta auditoria corretiva): o Integration and API Contract (TCOS-009) não formalizou uma Integração dedicada para "Evento cancelado" (RN-007) nem para "Lead marcado como perdido" (RN-011) — sugerido para avaliação em uma eventual v1.1.0 daquele documento; nenhuma alteração feita agora, pois o TCOS-009 está congelado.

### Riscos encontrados
- Nenhum risco novo de negócio. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem abertos, sem impedir a arquitetura de backend.

### Pendências
- P-010-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_BACKEND_ARCHITECTURE.md` (documento ainda em rascunho após a auditoria corretiva).
- Pendências herdadas: parâmetros do Módulo 24 (incluindo os 2 novos parâmetros identificados nesta auditoria: periodicidade do Job de previsão de demanda e período de inatividade de Lead), M-003A-03/04, M-005-01/02/03, M-006-01, M-007-01, M-008-01, M-009-01, confirmação do domínio de negócio (R-000-03).

### Estrutura de backend identificada (corrigida)
- 15/15 Serviços detalhados (100%), 47/47 Regras de Negócio rastreadas (100%, Capítulo 30 do TCOS-010), 20/20 Integrações preservadas (100%), 24/24 Agregados respeitados pela Regra Transacional (100%), 25 componentes com os 8 campos obrigatórios (15 Serviços + 10 transversais), 4 camadas por Serviço, 8 Jobs Agendados catalogados, 14 Documentos Oficiais no total (13 congelados + 1 vivo). Maturidade estimada do projeto: 84% (inalterada — esta rodada corrigiu precisão e rastreabilidade, sem alterar escopo arquitetural).

---

## FASE 010 — Encerramento Oficial

**Status:** APROVADA E ENCERRADA pelo proprietário em 2026-08-02 (comando `APROVADO`), após a auditoria corretiva registrada acima na Fase 010.
**Data:** 2026-08-02

O `THE_CHARCOAL_OS_BACKEND_ARCHITECTURE.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS. Nenhuma alteração futura sem criação de nova versão. A partir deste momento, a base de Documentos Oficiais Congelados passa de 13 para **14** (mais o registro vivo `PROJECT_MEMORY.md`, totalizando 15 Documentos Oficiais para efeito de contagem em fases futuras).

O proprietário confirmou que o objetivo do TCOS-010 foi atendido após a rodada corretiva: Arquitetura Conceitual de Backend, Organização dos 15 Serviços Conceituais, Camadas da Aplicação, Comunicação entre Serviços, Casos de Uso, Regra Transacional de Agregados, Processamento Síncrono e Assíncrono, Event Bus, Jobs Agendados, Filas Conceituais, Auditoria, Logs, Observabilidade, Tratamento de Erros, Controle Transacional, Versionamento, Cache, Configuração, Segurança, Inteligência Artificial, Componentes Transversais, Matriz de Rastreabilidade das 47 Regras de Negócio e Quality Gate Final — todos aprovados sem ressalva.

**Percentual de maturidade do projeto:** mantido em **84%** — a aprovação formal confirma o escopo já entregue e corrigido na auditoria; não há novo conteúdo arquitetural introduzido pela aprovação em si, apenas a mudança de status de "rascunho corrigido" para "oficial e congelado".

Pendência P-010-01 (validação formal do proprietário) está **encerrada** por este comando `APROVADO`. Pendências herdadas permanecem em aberto: parâmetros do Módulo 24 (incluindo periodicidade do Job de previsão de demanda e período de inatividade de Lead), M-003A-03/04, M-005-01/02/03, M-006-01, M-007-01, M-008-01, M-009-01, M-010-01/02/03, confirmação do domínio de negócio (R-000-03).

---

## FASE 011 — Frontend Architecture

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_FRONTEND_ARCHITECTURE.md` v1.0.0)
**Data:** 2026-08-02

Recebido o Prompt Oficial (TCOS-011), executada a auditoria de abertura sobre os 14 Documentos Oficiais Congelados, e produzido o documento com a arquitetura lógica interna de frontend: 5 sub-camadas de apresentação, as 30 telas (TCOS-005) organizadas em 4 Templates formais (Dashboard, Lista, Detalhe, Modal), comunicação com o backend por contrato público (espelhando o TCOS-010), consumo formalizado das 20 Integrações (TCOS-009) e dos 15 Serviços Conceituais (TCOS-006/TCOS-010), e 8 conceitos genuinamente novos formalizados por adição (Gerenciamento de Estado, Estados de Carregamento, Estados Vazios, Acessibilidade, Internacionalização, Cache da Interface, Funcionamento Offline, Observabilidade da Interface, Performance da Interface). Nenhuma linguagem, framework, biblioteca ou tecnologia de UI foi definida. Nenhum documento anterior foi alterado.

### Decisões tomadas
- D-011-01: o frontend ocupa a camada de Apresentação reservada (mas não detalhada) no System Architecture (TCOS-006), organizada em 5 sub-camadas internas (Telas, Componentes, Estado, Comunicação, Transversal) — nunca uma estrutura paralela aos Serviços/Domínios já definidos.
- D-011-02: a hierarquia de tela já implícita no Design System (TCOS-005, Seção 5.2: Dashboard → Lista → Detalhe → Modal) foi elevada a 4 Templates formais de arquitetura, cada um com composição fixa de componentes — nenhuma das 30 telas foge a esses 4 Templates.
- D-011-03: a comunicação do frontend com o backend adota exatamente o mesmo padrão de contrato público e Regra Transacional de Agregados já definidos no TCOS-010 (Capítulo 20) — nenhuma consulta síncrona do frontend jamais amplia uma transação do backend.
- D-011-04: 8 lacunas conceituais reais, nunca antes formalizadas em nenhum documento aprovado, foram identificadas e resolvidas nesta fase por adição: Gerenciamento de Estado, Estados de Carregamento/Vazios (generalizando padrões pontuais já citados no TCOS-005), Acessibilidade, Internacionalização (reservada, no mesmo padrão de Multiempresa/Multifilial do TCOS-007), Cache da Interface (distinto do Cache do backend, TCOS-010), Funcionamento Offline (conectado ao Roadmap mobile do Framework), Observabilidade da Interface e Performance da Interface.

### Alterações
- ALT-011-01: criado o documento `THE_CHARCOAL_OS_FRONTEND_ARCHITECTURE.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-011-01 (nova): ao escolher a tecnologia de frontend em fase técnica futura, avaliar mecanismos nativos de cache de interface e de fila de ações offline antes de implementá-los de forma customizada.
- M-011-02 (nova): validar formalmente o nível de contraste AA sobre a paleta de cores já aprovada (TCOS-005) assim que a tecnologia de UI for escolhida.
- M-011-03 (nova): a decisão de negócio sobre suporte a múltiplos idiomas/moedas permanece não confirmada (relacionada a R-000-03) — registrada como pendência de negócio, não como lacuna de arquitetura.

### Riscos encontrados
- Nenhum risco novo de negócio. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem abertos, sem impedir a arquitetura de frontend.

### Pendências
- P-011-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_FRONTEND_ARCHITECTURE.md`.
- Pendências herdadas: parâmetros do Módulo 24, M-003A-03/04, M-005-01/02/03, M-006-01, M-007-01, M-008-01, M-009-01, M-010-01/02/03, confirmação do domínio de negócio (R-000-03).

### Estrutura de frontend identificada
- 30/30 telas cobertas (100%), 27/27 módulos representados na interface (100%, 26 com tela própria + 1 via componente), 15/15 Serviços consumidos (100%), 20/20 Integrações observadas (100%), 4 Templates formalizados, 18 componentes reutilizáveis (15 herdados do TCOS-005 + 3 novos), 8 conceitos novos formalizados por adição. Maturidade estimada do projeto: 88%.

---

## FASE 011 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-02 (comando `APROVADO`)
**Data:** 2026-08-02

O `THE_CHARCOAL_OS_FRONTEND_ARCHITECTURE.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS, como o **15º Documento Oficial Congelado**. Nenhuma alteração futura sem criação de nova versão.

O proprietário confirmou que os objetivos do TCOS-011 foram atendidos sem ressalva: organização conceitual da camada de apresentação, cobertura das 30 telas oficiais, representação dos 27 módulos, os 4 Templates de interface, estrutura de navegação, gerenciamento conceitual de estado, ciclo de vida das telas, componentes reutilizáveis, Design System conceitual, comunicação com o Backend, observação das 20 Integrações, consumo dos 15 Serviços Conceituais, estados de carregamento/vazio/erro, validações, permissões, auditoria visual, responsividade, acessibilidade, internacionalização, cache, funcionamento offline conceitual, observabilidade, performance, integração com IA, consistência Frontend/Backend e os padrões obrigatórios de experiência do usuário.

**Nova contagem oficial de Documentos Oficiais** (critério em vigor a partir desta fase):
- **15 Documentos Oficiais Congelados:** Development Framework, Enterprise Domain Discovery, Business Discovery Questionnaire, Discovery Interview Roadmap, Domain Model, Business Rules Specification, Functional Specification, User Journeys and System Flows, UX/UI Specification, System Architecture, Data Architecture, Database Specification, Integration and API Contract, Backend Architecture, **Frontend Architecture (novo)**.
- **1 Documento Oficial Vivo:** `PROJECT_MEMORY.md`.
- **16 Documentos Oficiais no total.**

**Percentual de maturidade do projeto:** mantido em **88%**, sem alteração adicional decorrente desta aprovação formal. Critério verificável: a maturidade já registrada na entrega do TCOS-011 refletia o escopo completo e auditado do documento (30/30 telas, 27/27 módulos, 15/15 Serviços, 20/20 Integrações, 4 Templates, 8 conceitos novos — todos já contabilizados); a aprovação confirma esse escopo como oficial, mas não introduz nenhum conteúdo arquitetural adicional que justifique um novo incremento percentual. O percentual seguirá recalculado apenas quando uma fase futura acrescentar escopo novo e verificável.

Pendência P-011-01 (validação formal do proprietário) está **encerrada** por este comando `APROVADO`. Permanecem abertas, sem alteração, todas as pendências, riscos e melhorias herdadas que não foram efetivamente resolvidos nesta fase: parâmetros do Módulo 24 (incluindo periodicidade do Job de previsão de demanda e período de inatividade de Lead), M-003A-03/04, M-005-01/02/03, M-006-01, M-007-01, M-008-01, M-009-01, M-010-01/02/03, M-011-01/02/03, confirmação do domínio de negócio (R-000-03), e os riscos R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01.

**Nota informativa (direção planejada, não autorizada):** o proprietário sinalizou que o próximo documento previsto é o TCOS-012 — `THE_CHARCOAL_OS_SECURITY_AND_PRIVACY_ARCHITECTURE.md` (Security and Privacy Architecture). Este registro é apenas informativo; a Fase 012 não foi iniciada e somente poderá começar mediante um novo Prompt Oficial formal do proprietário.

---

## FASE 012 — Security and Privacy Architecture

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_SECURITY_AND_PRIVACY_ARCHITECTURE.md` v1.0.0)
**Data:** 2026-08-02

Recebido o Prompt Oficial (TCOS-012), executada a auditoria de abertura sobre os 15 Documentos Oficiais Congelados, e produzido o documento com a arquitetura conceitual completa de segurança e privacidade: 40 tópicos obrigatórios cobertos, 11 Perfis (10 Áreas da Empresa + Administrador do Sistema) consolidados em Matriz de Responsabilidades, 9 capítulos de segurança por domínio de negócio (Financeiro, Custos, Produção, Estoque, Eventos, Dashboards, IA, Integrações, Documentos), e 2 fluxos conceituais consolidados (Segurança e Auditoria). Nenhuma autenticação específica, criptografia específica, infraestrutura ou tecnologia foi definida. Nenhum documento anterior foi alterado.

### Decisões tomadas
- D-012-01: princípio de **negação padrão (fail-closed)** formalizado como regra geral — toda checagem de permissão que não puder ser concluída com certeza resulta em acesso negado, nunca concedido por omissão ou indisponibilidade. Achado de segurança mais relevante desta fase, por adição, sem contradizer nenhum documento anterior.
- D-012-02: **Herança de Permissões** formalizada em exatamente dois padrões observáveis no Domain Model — Herança Consolidada (Direção, somente leitura) e Herança Administrativa (Administrador do Sistema, apenas sobre Perfis/Permissões, nunca sobre dado de negócio sensível).
- D-012-03: **Sessões** e **Expiração de Sessão** formalizadas pela primeira vez — criadas na autenticação, expiram por inatividade ou duração máxima, com reautenticação exigível para Operações Críticas mesmo dentro de uma Sessão válida.
- D-012-04: **Operações Críticas** catalogadas sob um critério único (impacto financeiro, irreversibilidade, alteração de permissão, exposição de dado sensível, ou aceite de sugestão de IA) — 8 operações já existentes nos documentos anteriores reunidas pela primeira vez sob esse critério.

### Alterações
- ALT-012-01: criado o documento `THE_CHARCOAL_OS_SECURITY_AND_PRIVACY_ARCHITECTURE.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-012-01 (nova): ao escolher a tecnologia de autenticação em fase técnica futura, avaliar mecanismos nativos de expiração de sessão e reautenticação para Operações Críticas antes de implementá-los de forma customizada.
- M-012-02 (nova): confirmar com o proprietário o parâmetro de duração de Sessão/inatividade — hoje modelado como Configuração pendente, sem valor assumido.
- M-012-03 (nova): decisão de governança sobre anonimização de dado pessoal permanece pendente — recomenda-se tratá-la antes de uma eventual exigência legal, não apenas reativamente.

### Riscos encontrados
- Nenhum risco novo de arquitetura. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem abertos, sem impedir a arquitetura de segurança. Um risco de governança (não técnico) foi identificado: ausência de decisão sobre anonimização de dado pessoal — tratado como pendência (não como risco de arquitetura), pois a Exclusão Lógica já protege a integridade do histórico independentemente dessa decisão.

### Pendências
- P-012-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_SECURITY_AND_PRIVACY_ARCHITECTURE.md`.
- Pendências herdadas: parâmetros do Módulo 24 (incluindo o novo parâmetro de duração de Sessão/inatividade), M-003A-03/04, M-005-01/02/03, M-006-01, M-007-01, M-008-01, M-009-01, M-010-01/02/03, M-011-01/02/03, confirmação do domínio de negócio (R-000-03), decisão de governança sobre anonimização de dado pessoal.

### Estrutura de segurança identificada
- 40/40 tópicos obrigatórios cobertos, 11 Perfis consolidados em Matriz de Responsabilidades, 9 capítulos de segurança por domínio, 6 Eventos de Segurança catalogados (1 herdado + 5 novos), 8 Operações Críticas catalogadas, 2 fluxos conceituais (Segurança, Auditoria), 30 entidades e 12 Regras de Negócio referenciadas (0 novas, 0 alteradas). Maturidade estimada do projeto: 91%.

---

## FASE 012 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-02 (comando `APROVADO`)
**Data:** 2026-08-02

O `THE_CHARCOAL_OS_SECURITY_AND_PRIVACY_ARCHITECTURE.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS, como o **16º Documento Oficial Congelado**. Nenhuma alteração futura sem criação de nova versão.

**Nova contagem oficial de Documentos Oficiais** (critério em vigor a partir desta fase): 16 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) = **17 Documentos Oficiais no total**.

**Percentual de maturidade do projeto:** mantido em **91%**, sem alteração adicional decorrente desta aprovação formal — a aprovação confirma o escopo já entregue e auditado do TCOS-012, sem introduzir conteúdo arquitetural novo.

Pendência P-012-01 (validação formal do proprietário) está **encerrada** por este comando `APROVADO`. Permanecem abertas, sem alteração, todas as pendências, riscos e melhorias herdadas que não foram efetivamente resolvidos nesta fase: parâmetros do Módulo 24 (incluindo o novo parâmetro de duração de Sessão/inatividade), M-003A-03/04, M-005-01/02/03, M-006-01, M-007-01, M-008-01, M-009-01, M-010-01/02/03, M-011-01/02/03, M-012-01/02/03, confirmação do domínio de negócio (R-000-03), decisão de governança sobre anonimização de dado pessoal.

**Confirmação de integridade:** nenhum conteúdo técnico do `THE_CHARCOAL_OS_SECURITY_AND_PRIVACY_ARCHITECTURE.md` foi alterado nesta ação — apenas as 3 linhas de status (cabeçalho, Quality Gate, linha final). Nenhum documento das Fases 000-011 foi tocado.

---

## FASE 013 — AI Architecture

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_AI_ARCHITECTURE.md` v1.0.0)
**Data:** 2026-08-02

Recebido o Prompt Oficial (TCOS-013), executada a auditoria de abertura sobre os 16 Documentos Oficiais Congelados, e produzido o documento com a arquitetura conceitual completa de Inteligência Artificial: 31 tópicos obrigatórios cobertos, 4 Tipos de Agentes Inteligentes (Classificação, Previsão, Recomendação, Monitoramento), 2 categorias de Memória (Operacional, Estratégica), atuação detalhada em 10 domínios de negócio, catálogo de 8 Limites da IA, e integração consolidada com os 27 módulos, 15 Serviços, Event Bus e os 16 Documentos Oficiais Congelados. Nenhum modelo de IA, API, linguagem, banco de dados ou infraestrutura foi definida. Nenhum documento anterior foi alterado.

### Decisões tomadas
- D-013-01: 4 Tipos de Agentes Inteligentes formalizados (Classificação, Previsão, Recomendação, Monitoramento), generalizando os padrões já existentes nas funcionalidades F-068 a F-071 sem criar comportamento novo.
- D-013-02: Memória Operacional (consulta de curto prazo, por contrato público, ao dado de origem) e Memória Estratégica (síntese de longo prazo para recomendações à Direção) formalizadas como conceitos distintos, ambas nunca uma cópia paralela do dado de negócio (PF-01/PF-03).
- D-013-03: conceito de **Extensão Estrutural Preparada** adotado como disciplina de governança para resolver, sem inventar funcionalidade nova, o pedido de atuação da IA em 6 domínios (Produção, Estoque, Eventos, CRM, Marketing, Indicadores) que ainda não têm funcionalidade F-XXX formal — a criação de funcionalidade real permanece pendente de uma futura nova versão do Functional Specification (TCOS-003).
- D-013-04: catálogo de 8 Limites da IA consolidado a partir de restrições já espalhadas por 5 documentos anteriores (TCOS-002A, TCOS-006, TCOS-010, TCOS-011, TCOS-012) — nenhuma restrição nova, apenas reunidas em lista única.

### Alterações
- ALT-013-01: criado o documento `THE_CHARCOAL_OS_AI_ARCHITECTURE.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-013-01 (nova): ao escolher o modelo/provedor de IA em fase técnica futura, avaliar a viabilidade de cada Extensão Estrutural Preparada como candidata a uma futura nova versão do Functional Specification antes de implementá-la.
- M-013-02 (nova): formalizar, em fase técnica futura, o mecanismo concreto de cálculo de "nível de confiança" — hoje descrito apenas como conceito.
- M-013-03 (nova): avaliar, junto à Direção, a prioridade de negócio entre as 6 Extensões Estruturais Preparadas sem funcionalidade formal (Produção, Estoque, Eventos, CRM, Marketing, Indicadores).

### Riscos encontrados
- Nenhum risco novo de negócio ou de arquitetura. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem abertos, sem impedir a arquitetura de IA.

### Pendências
- P-013-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_AI_ARCHITECTURE.md`.
- Pendências herdadas: parâmetros do Módulo 24, M-003A-03/04, M-005 a M-012 (melhorias ainda não resolvidas), confirmação do domínio de negócio (R-000-03), decisão de governança sobre anonimização de dado pessoal.

### Estrutura de IA identificada
- 31/31 tópicos obrigatórios cobertos, 4 Tipos de Agentes Inteligentes, 2 categorias de Memória, 10 domínios de negócio detalhados (4 com funcionalidade formal já aprovada + 6 como Extensão Estrutural Preparada), 8 Limites da IA catalogados, 3 Regras de Negócio referenciadas (RN-041 a RN-043, 0 novas, 0 alteradas), 4 funcionalidades de IA já oficiais (F-068 a F-071, 0 novas). Maturidade estimada do projeto: 93%.

---

## FASE 013 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-02 (comando `APROVADO`)
**Data:** 2026-08-02

O `THE_CHARCOAL_OS_AI_ARCHITECTURE.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS, como o **17º Documento Oficial Congelado**. Nenhuma alteração futura sem criação de nova versão.

**Nova contagem oficial de Documentos Oficiais** (critério em vigor a partir desta fase): 17 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) = **18 Documentos Oficiais no total**.

**Percentual de maturidade do projeto:** mantido em **93%**, sem alteração adicional decorrente desta aprovação formal — a aprovação confirma o escopo já entregue e auditado do TCOS-013, sem introduzir conteúdo arquitetural novo.

Pendência P-013-01 (validação formal do proprietário) está **encerrada** por este comando `APROVADO`. Permanecem abertas, sem alteração, todas as pendências, riscos e melhorias herdadas que não foram efetivamente resolvidos nesta fase: parâmetros do Módulo 24, M-003A-03/04, M-005 a M-013 (melhorias ainda não resolvidas), confirmação do domínio de negócio (R-000-03), decisão de governança sobre anonimização de dado pessoal.

**Confirmação de auditoria (executada antes deste commit):** verificado programaticamente que nenhum conteúdo técnico do `THE_CHARCOAL_OS_AI_ARCHITECTURE.md` foi alterado — apenas 3 linhas de status foram trocadas (cabeçalho, Quality Gate, linha final); as 33 seções/capítulos permanecem intactas; nenhuma referência cruzada foi modificada (0 quebras confirmadas por verificação automática); nenhuma seção foi removida. Nenhum documento das Fases 000-012 foi tocado.

---

## FASE 014 — Infrastructure Architecture

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_INFRASTRUCTURE_ARCHITECTURE.md` v1.0.0)
**Data:** 2026-08-02

Recebido o Prompt Oficial (TCOS-014), executada a auditoria de abertura sobre os 17 Documentos Oficiais Congelados, e produzido o documento com a arquitetura conceitual completa de infraestrutura: 28 tópicos obrigatórios cobertos, 4 Ambientes formalizados (Development, Test, Staging, Production), consolidação física de Escalabilidade/Backup/Disponibilidade/Observabilidade já definidos em fases anteriores, e formalização de 6 conceitos novos (Ambientes, Estrutura de Deploy, Recuperação de Desastres, Health Checks, Gestão de Segredos, Capacidade, Multitenancy). Nenhum cloud provider, linguagem, banco de dados, container, orquestração ou infraestrutura física foi definida. Nenhum documento anterior foi alterado.

### Decisões tomadas
- D-014-01: 4 Ambientes formalizados (Development, Test, Staging, Production), cada um com propósito e nível de dado real distinto — nenhuma mudança avança entre Ambientes sem validação do anterior.
- D-014-02: **Recuperação de Desastres** formalizada como distinta de Backup — Backup protege dado pontual; Recuperação de Desastres trata da perda de um Ambiente inteiro, com dois indicadores conceituais (Tempo de Recuperação esperado, Perda de Dado aceitável).
- D-014-03: **Multitenancy** (estratégia de infraestrutura) formalizada como distinta de **Multiempresa** (decisão de negócio já reservada no TCOS-007) — dois modelos conceituais apresentados (Tenant compartilhado, Tenant isolado), nenhum escolhido nesta fase.
- D-014-04: Gestão de Segredos, Health Checks e Capacidade formalizados como conceitos próprios, consolidando requisitos que antes apareciam apenas implicitamente em Segurança, Tolerância a Falhas e Escalabilidade.

### Alterações
- ALT-014-01: criado o documento `THE_CHARCOAL_OS_INFRASTRUCTURE_ARCHITECTURE.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-014-01 (nova): ao escolher o cloud provider em fase técnica futura, avaliar mecanismos nativos de Health Check, Balanceamento e Recuperação de Desastres antes de implementá-los de forma customizada.
- M-014-02 (nova): definir, junto à Direção, os valores concretos de Tempo de Recuperação esperado e Perda de Dado aceitável.
- M-014-03 (nova): revisitar a decisão entre Tenant compartilhado e Tenant isolado assim que a decisão de negócio sobre Multiempresa (M-006-01) for confirmada.

### Riscos encontrados
- Nenhum risco novo de negócio ou de arquitetura. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem abertos, sem impedir a arquitetura de infraestrutura.

### Pendências
- P-014-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_INFRASTRUCTURE_ARCHITECTURE.md`.
- Pendências herdadas: parâmetros do Módulo 24, M-003A-03/04, M-005 a M-013 (melhorias ainda não resolvidas), confirmação do domínio de negócio (R-000-03), decisão de governança sobre anonimização de dado pessoal, decisão de negócio sobre Multiempresa/Multifilial (M-006-01/M-007-01).

### Estrutura de infraestrutura identificada
- 28/28 tópicos obrigatórios cobertos, 4 Ambientes formalizados, 6 conceitos novos (Ambientes, Deploy, Recuperação de Desastres, Health Checks, Segredos, Capacidade/Multitenancy), consolidação de Escalabilidade/Backup/Disponibilidade/Observabilidade já definidos em 5 documentos anteriores. Maturidade estimada do projeto: 95%.

---

## FASE 014 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-02 (comando `APROVADO`)
**Data:** 2026-08-02

O `THE_CHARCOAL_OS_INFRASTRUCTURE_ARCHITECTURE.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS, como o **18º Documento Oficial Congelado**. Nenhuma alteração futura sem criação de nova versão.

**Nova contagem oficial de Documentos Oficiais** (critério em vigor a partir desta fase): 18 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) = **19 Documentos Oficiais no total**.

**Percentual de maturidade do projeto:** mantido em **95%**, sem alteração adicional decorrente desta aprovação formal — a aprovação confirma o escopo já entregue e auditado do TCOS-014, sem introduzir conteúdo arquitetural novo.

Pendência P-014-01 (validação formal do proprietário) está **encerrada** por este comando `APROVADO`. Permanecem abertas, sem alteração, todas as pendências, riscos e melhorias herdadas que não foram efetivamente resolvidos nesta fase: parâmetros do Módulo 24, M-003A-03/04, M-005 a M-014 (melhorias ainda não resolvidas), confirmação do domínio de negócio (R-000-03), decisão de governança sobre anonimização de dado pessoal, decisão de negócio sobre Multiempresa/Multifilial.

**Confirmação de auditoria (executada antes deste commit):** verificado programaticamente que nenhum conteúdo técnico do `THE_CHARCOAL_OS_INFRASTRUCTURE_ARCHITECTURE.md` foi alterado — apenas 3 linhas de status foram trocadas (cabeçalho, Quality Gate, linha final); as 30 seções/capítulos permanecem intactas; nenhuma referência cruzada foi modificada (0 quebras confirmadas por verificação automática); nenhuma seção foi removida. Nenhum documento das Fases 000-013 foi tocado.

---

## FASE 015 — DevOps & Operational Architecture

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_DEVOPS_AND_OPERATIONAL_ARCHITECTURE.md` v1.0.0)
**Data:** 2026-08-02

Recebido o Prompt Oficial (TCOS-015), executada a auditoria de abertura sobre os 18 Documentos Oficiais Congelados, e produzido o documento com a arquitetura conceitual completa de DevOps e Operação: 27 tópicos obrigatórios cobertos, Pipeline Conceitual de Entrega de 6 estágios (Construção, Verificação Automatizada, Verificação Manual, Aprovação, Implantação, Operação), distinção formal entre Incidente/Problema/Mudança, e consolidação operacional de Capacidade, Disponibilidade e Continuidade já definidas nas fases de infraestrutura e segurança. Nenhum CI/CD, ferramenta de pipeline, container ou infraestrutura física foi definida. Nenhum documento anterior foi alterado.

### Decisões tomadas
- D-015-01: Pipeline Conceitual de Entrega formalizado em 6 estágios sequenciais (Construção, Verificação Automatizada, Verificação Manual, Aprovação, Implantação, Operação) — nenhum estágio é pulado, mesmo sob urgência.
- D-015-02: Incidente, Problema e Mudança formalizados como três conceitos distintos e relacionados — Incidente (evento não planejado), Problema (causa raiz recorrente), Mudança (alteração planejada) — nunca tratados como sinônimos.
- D-015-03: Observabilidade/Monitoramento Operacional (Capítulos 18-19) definidos como reaproveitamento de uso, nunca de mecanismo, dos mesmos sinais técnicos já coletados pelo TCOS-010/TCOS-014 — evitando uma segunda infraestrutura de coleta paralela.
- D-015-04: Critérios de Aprovação formalizados crescendo em rigor a cada Ambiente (Development→Test→Staging→Production), culminando em aprovação humana explícita para Production, espelhando a disciplina de Operação Crítica já exigida para ações de negócio (TCOS-012).

### Alterações
- ALT-015-01: criado o documento `THE_CHARCOAL_OS_DEVOPS_AND_OPERATIONAL_ARCHITECTURE.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- M-015-01 (nova): ao escolher a ferramenta de CI/CD em fase técnica futura, avaliar mecanismos nativos de Pipeline, Gestão de Artefatos e Rollback antes de implementá-los de forma customizada.
- M-015-02 (nova): definir, junto à Direção, os níveis esperados de Disponibilidade e os tempos-alvo de resposta a Incidente.
- M-015-03 (nova): estabelecer, em fase técnica futura, a cadência concreta de revisão de Capacidade e de Evolução Contínua.

### Riscos encontrados
- Nenhum risco novo de negócio ou de arquitetura. Riscos herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01) permanecem abertos, sem impedir a arquitetura de DevOps e Operação.

### Pendências
- P-015-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_DEVOPS_AND_OPERATIONAL_ARCHITECTURE.md`.
- Pendências herdadas: parâmetros do Módulo 24, M-003A-03/04, M-005 a M-014 (melhorias ainda não resolvidas), confirmação do domínio de negócio (R-000-03), decisão de governança sobre anonimização de dado pessoal, decisão de negócio sobre Multiempresa/Multifilial.

### Estrutura de DevOps e Operação identificada
- 27/27 tópicos obrigatórios cobertos, Pipeline de 6 estágios, 3 conceitos operacionais formalizados (Incidente, Problema, Mudança), consolidação de Capacidade/Disponibilidade/Continuidade já definidas em 2 documentos anteriores (TCOS-012, TCOS-014). Maturidade estimada do projeto: 97%.

---

## FASE 015 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-02 (comando `APROVADO`)
**Data:** 2026-08-02

O `THE_CHARCOAL_OS_DEVOPS_AND_OPERATIONAL_ARCHITECTURE.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS, como o **19º Documento Oficial Congelado**. Nenhuma alteração futura sem criação de nova versão.

**Nova contagem oficial de Documentos Oficiais** (critério em vigor a partir desta fase): 19 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) = **20 Documentos Oficiais no total**.

**Percentual de maturidade do projeto:** mantido em **97%**, sem alteração adicional decorrente desta aprovação formal — a aprovação confirma o escopo já entregue e auditado do TCOS-015, sem introduzir conteúdo arquitetural novo.

Pendência P-015-01 (validação formal do proprietário) está **encerrada** por este comando `APROVADO`. Permanecem abertas, sem alteração, todas as pendências, riscos e melhorias herdadas que não foram efetivamente resolvidos nesta fase: parâmetros do Módulo 24, M-003A-03/04, M-005 a M-015 (melhorias ainda não resolvidas), confirmação do domínio de negócio (R-000-03), decisão de governança sobre anonimização de dado pessoal, decisão de negócio sobre Multiempresa/Multifilial.

**Confirmação de auditoria (executada antes deste commit):** verificado programaticamente que nenhum conteúdo técnico do `THE_CHARCOAL_OS_DEVOPS_AND_OPERATIONAL_ARCHITECTURE.md` foi alterado — apenas 3 linhas de status foram trocadas (cabeçalho, Quality Gate, linha final); as 29 seções/capítulos permanecem intactas; nenhuma referência cruzada foi modificada (0 quebras confirmadas por verificação automática); nenhuma seção foi removida. Nenhum documento das Fases 000-014 foi tocado.

---

## FASE 016 — Executive Global Audit

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_EXECUTIVE_GLOBAL_AUDIT.md` v1.0.0)
**Data:** 2026-08-02

Recebido o Prompt Oficial (TCOS-016), executada a auditoria executiva global de todos os 19 Documentos Oficiais Congelados: verificação mecânica de 258 referências cruzadas entre documentos (0 quebradas) e de mais de 545 referências internas (0 quebradas, após confirmação manual de 6 falsos positivos), validação de todas as contagens-chave do projeto (30 entidades, 47 regras, 98 funcionalidades, 27 módulos, 15 Serviços, 20 Integrações, 24 Agregados, 32 estruturas de banco, entre outras), e consolidação de riscos, pendências e melhorias acumuladas em 16 fases. Esta fase não criou arquitetura nova e não alterou nenhum documento já aprovado, conforme mandato explícito do Prompt Oficial.

### Achados registrados (sem correção, conforme mandato da fase)
- **Achado 1 (gravidade baixa):** System Architecture (TCOS-006), Seção 3.4, cita "13 Serviços Conceituais" — divergente do número correto (15), já usado consistentemente no Capítulo 6 e na Seção 19 (Quality Gate) do próprio TCOS-006, e em todos os 14 documentos posteriores. Sem propagação a nenhum outro documento.
- **Achado 2 (gravidade baixa):** System Architecture (TCOS-006), Quality Gate item 1, cita "13 integrações de domínio" — divergente do número correto (18), confirmado pela contagem direta das subseções 3.1-3.18 do próprio documento, pela Seção 19 (Quality Gate) do mesmo TCOS-006, e pelo Integration and API Contract (TCOS-009). Sem propagação a nenhum outro documento.
- Nenhum outro achado de gravidade Média ou Alta foi encontrado. Nenhuma duplicidade, conflito, funcionalidade/entidade órfã ou módulo sem integração foi identificado.

### Decisões tomadas
- D-016-01: metodologia de auditoria mecânica (extração programática de referências e contagens, não apenas releitura) adotada como padrão desta fase — permitiu encontrar os 2 achados acima, que uma releitura visual muito provavelmente não teria identificado.
- D-016-02: os 2 achados no TCOS-006 são registrados como melhoria de correção editorial (M-016-01, M-016-02) para uma futura v1.1.0 desse documento — não corrigidos agora, por não ser mandato desta fase alterar documento já congelado.
- D-016-03: Score Geral do Projeto calculado em 9,6/10, como média ponderada dos Quality Scores individuais das 16 fases já aprovadas, ajustada por 0,1 ponto pelos 2 achados de baixa gravidade.

### Alterações
- ALT-016-01: criado o documento `THE_CHARCOAL_OS_EXECUTIVE_GLOBAL_AUDIT.md` (v1.0.0). Nenhum documento anterior foi alterado — confirmado que esta é uma fase exclusivamente de auditoria, sem criação de arquitetura nova.

### Melhorias sugeridas (Backlog)
- M-016-01 (nova): corrigir, em uma futura v1.1.0 do System Architecture (TCOS-006), "13" para "15" Serviços Conceituais na Seção 3.4.
- M-016-02 (nova): corrigir, na mesma futura v1.1.0 do TCOS-006, "13" para "18" integrações de domínio no item 1 do Quality Gate.

### Riscos encontrados
- Nenhum risco novo. Os 5 códigos de risco já ativos (R-000-03, R-002-01, R-001-01, R-002-02, R-002A-01) permanecem consolidados e reafirmados nesta auditoria como a totalidade dos riscos do projeto.

### Pendências
- P-016-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_EXECUTIVE_GLOBAL_AUDIT.md`.
- Pendências substantivas consolidadas nesta auditoria (8 no total): confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; decisão de negócio sobre Multiempresa/Multifilial; decisão de governança sobre anonimização de dado pessoal; lacuna de cobertura do TCOS-009 (M-010-03); priorização de negócio das Extensões Estruturais de IA (M-013-03); decisão sobre retomar a entrevista de descoberta.

### Estrutura de auditoria identificada
- 19/19 Documentos Oficiais Congelados revisados, 258 referências cruzadas verificadas (0 quebradas), 545+ referências internas verificadas (0 quebradas), 2 achados de inconsistência registrados (gravidade baixa, sem propagação), 0 duplicidades, 0 conflitos, 0 órfãos, rastreabilidade de Regras de Negócio 47/47 reafirmada, 43 melhorias históricas + 2 novas consolidadas, 5 códigos de risco consolidados, 8 pendências substantivas consolidadas. Score Geral do Projeto: 9,6/10. Maturidade estimada do projeto: 97% (sem alteração — esta fase validou, não ampliou, o escopo já entregue).

---

## FASE 016 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-02 (comando `APROVADO`)
**Data:** 2026-08-02

O `THE_CHARCOAL_OS_EXECUTIVE_GLOBAL_AUDIT.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS, como o **20º Documento Oficial Congelado**. Nenhuma alteração futura sem criação de nova versão.

**Nova contagem oficial de Documentos Oficiais** (critério em vigor a partir desta fase): 20 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) = **21 Documentos Oficiais no total**.

**Percentual de maturidade do projeto:** mantido em **97%**, sem alteração adicional decorrente desta aprovação formal.

Pendência P-016-01 (validação formal do proprietário) está **encerrada** por este comando `APROVADO`. Os 2 achados registrados (M-016-01, M-016-02) permanecem como melhoria de correção editorial para uma futura v1.1.0 do System Architecture (TCOS-006) — nenhuma correção feita agora.

**Confirmação de auditoria (executada antes deste commit):** verificado programaticamente que nenhum conteúdo técnico do `THE_CHARCOAL_OS_EXECUTIVE_GLOBAL_AUDIT.md` foi alterado — apenas 3 linhas de status foram trocadas (cabeçalho, Quality Gate, linha final); as 12 seções/capítulos permanecem intactas; nenhuma referência cruzada foi modificada; nenhuma seção foi removida. Nenhum documento das Fases 000-015 foi tocado.

---

## CONSTITUIÇÃO PERMANENTE — Registro Oficial

**Status:** Oficial — Registrada e Vigente desde 2026-08-02
**Data:** 2026-08-02
**Documento:** `THE_CHARCOAL_OS_PROJECT_CONSTITUTION.md` (v1.0.0)

Criado, por determinação explícita do proprietário (comando `ALTERAR`, recebido imediatamente após a conclusão da Fase 016), o documento de maior autoridade do THE CHARCOAL OS: a Constituição Permanente do Projeto. Este documento **não representa uma nova Fase** e **não substitui nenhum documento oficial existente** — estabelece a governança permanente que protege e disciplina a evolução de toda a documentação já construída.

### Auditoria de pré-criação executada
Antes de escrever qualquer conteúdo, foram lidos integralmente os 20 Documentos Oficiais Congelados (TCOS-000 a TCOS-016) e este `PROJECT_MEMORY.md`, com verificação específica de que: nenhuma decisão arquitetural foi perdida; nenhuma regra de negócio foi omitida; nenhuma política de governança existente seria contrariada; nenhuma referência cruzada seria quebrada; nenhuma diretriz já aprovada seria substituída; nenhuma informação seria duplicada desnecessariamente. **Resultado: nenhuma inconsistência encontrada** — a criação prosseguiu sem interrupção.

### Baseline Oficial v1.0.0 — registrada oficialmente
A Baseline Oficial v1.0.0 do THE CHARCOAL OS é definida, por esta Constituição (Capítulo 5), como o conjunto fechado de: os 20 Documentos Oficiais Congelados (TCOS-000 a TCOS-016), o `PROJECT_MEMORY.md` no estado desta entrada, e a própria Constituição como documento de governança. Representa 100% da arquitetura conceitual do projeto, 0% de tecnologia escolhida, 0% de implementação iniciada — maturidade 97%, Score Geral 9,6/10 (herdados do TCOS-016, sem alteração).

### Decisões tomadas
- D-CONST-01: Hierarquia Oficial dos Documentos formalizada — a Constituição tem autoridade máxima sobre governança/versionamento/processo de mudança; o Development Framework (TCOS-000) mantém autoridade sobre o método de trabalho; os demais 18 documentos técnicos mantêm autoridade plena sobre seus próprios domínios; o `PROJECT_MEMORY.md` mantém autoridade de registro histórico, nunca de decisão técnica nova.
- D-CONST-02: Política Oficial de Change Request (CR) instituída como único caminho válido para qualquer alteração futura a um documento já congelado — substituindo, a partir de agora, qualquer correção direta, mesmo para achados já identificados (M-016-01/M-016-02).
- D-CONST-03: os 2 achados do TCOS-006 (M-016-01, M-016-02) permanecem não corrigidos — sua correção formal exigirá o primeiro Change Request executado sob esta Constituição.

### Confirmações formais desta entrada
- **Confirmado:** nenhum documento oficial existente (TCOS-000 a TCOS-016) foi alterado pela criação desta Constituição.
- **Confirmado:** todos os 20 Documentos Oficiais Congelados permanecem congelados, sem nenhuma modificação de conteúdo ou de status.
- **Confirmado:** a partir desta data, futuras alterações a qualquer documento oficial somente poderão ocorrer através de Solicitação Oficial de Mudança (Change Request — CR), conforme o processo definido no Capítulo 14 da Constituição.
- **Confirmado:** toda a Constituição foi construída em conformidade com a totalidade dos documentos oficiais previamente aprovados, sem introduzir nenhuma contradição.

### Pendências
- Nenhuma pendência de validação nova — este documento não é uma Fase e não está sujeito ao ciclo `APROVADO`/`CORRIGIR` de encerramento de Fase; passa a viger imediatamente como documento de governança, por determinação já explícita do proprietário.
- Pendências substantivas do projeto permanecem inalteradas (8 no total, consolidadas na Fase 016): confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; decisão de negócio sobre Multiempresa/Multifilial; decisão de governança sobre anonimização de dado pessoal; lacuna de cobertura do TCOS-009 (M-010-03); priorização das Extensões Estruturais de IA (M-013-03); decisão sobre retomar a entrevista de descoberta.

### Riscos e melhorias
- Nenhum risco novo. Nenhuma melhoria nova. Os 5 riscos e 45 melhorias já consolidados na Fase 016 permanecem, sem alteração, a totalidade do backlog do projeto.

**Não iniciada:** nenhuma nova Fase, nenhuma implementação técnica, nenhum código, banco físico, API real, backend, frontend, IA em produção ou infraestrutura física. O projeto aguarda autorização explícita do proprietário para iniciar a implementação técnica.

---

## FASE 017 — Implementation Master Plan

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_IMPLEMENTATION_MASTER_PLAN.md` v1.0.0)
**Data:** 2026-08-02

Recebido o Prompt Oficial (TCOS-017), executada a Auditoria de Consistência sobre os 20 Documentos Oficiais Congelados, a Constituição Permanente e o `PROJECT_MEMORY.md`, e produzido o Plano Mestre de Implementação: os 27 módulos organizados em 9 Camadas de Implementação por dependência técnica (derivadas da Matriz de Dependências já oficial, TCOS-006 Capítulo 4), MVP definido em 18 módulos, Pós-MVP em 9 módulos distribuídos em 3 entregas adicionais, e estratégia completa de Sprint, testes, homologação, validação, migração, implantação, treinamento e evolução contínua. Nenhuma tecnologia foi escolhida; nenhum código foi escrito; nenhum documento da Baseline Oficial foi alterado.

### Decisões tomadas
- D-017-01: ordem de implementação dos 27 módulos organizada em 9 Camadas, derivadas exclusivamente da Matriz de Dependências já oficial (TCOS-006, Capítulo 4) — nenhum critério novo de dependência foi criado.
- D-017-02: dependência mútua de operação entre Produção (10) e Estoque (16), já registrada no TCOS-006, resolvida para fins de implementação colocando os dois módulos no mesmo bloco (Camada 3), junto com Precificação (14) — sem alterar a documentação original, apenas definindo a ordem prática de construção.
- D-017-03: MVP definido em 18 módulos (Camadas 0-7), incluindo deliberadamente a Engenharia de Custos (Módulo 11) — apurar a margem por Evento é tratado como núcleo do valor de negócio, não um refinamento posterior.
- D-017-04: confirmação do domínio de negócio (R-000-03) formalizada como critério explícito de início do primeiro Sprint (Capítulo 11) e item do Checklist Obrigatório antes de qualquer desenvolvimento (Capítulo 22) — o tratamento mais direto já dado a esse risco em qualquer fase do projeto.
- D-017-05: Estratégia de Migração de Dados e Estratégia de Treinamento do Usuário formalizadas pela primeira vez nesta fase, por adição, sem tecnologia definida.

### Alterações
- ALT-017-01: criado o documento `THE_CHARCOAL_OS_IMPLEMENTATION_MASTER_PLAN.md` (v1.0.0). Nenhum documento anterior foi alterado.

### Melhorias sugeridas (Backlog)
- Nenhuma nova. Este plano organiza a execução da Baseline já completa, sem identificar lacunas de arquitetura adicionais às já registradas nas Fases 000-016.

### Riscos encontrados
- Nenhum risco novo de arquitetura. R-000-03 (domínio de negócio não confirmado) recebe, nesta fase, o tratamento de maior impacto prático já dado a ele: pré-requisito explícito e não contornável do primeiro Sprint de implementação.

### Pendências
- P-017-01: validação formal do proprietário sobre o `THE_CHARCOAL_OS_IMPLEMENTATION_MASTER_PLAN.md`.
- Pendências herdadas: as mesmas 8 pendências substantivas consolidadas na Fase 016, sem nenhuma nova.

### Estrutura de implementação identificada
- 27/27 módulos organizados (100%) em 9 Camadas de Implementação, MVP de 18 módulos, Pós-MVP de 9 módulos em 3 entregas, 8 Entregas de Roadmap no total, 6 riscos de implementação catalogados, 5 critérios de aceite formalizados. Maturidade estimada do projeto: 97% (inalterada — este plano organiza a execução, sem ampliar o escopo conceitual da Baseline).

---

## FASE 017 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-02 (comando `APROVADO`)
**Data:** 2026-08-02

O `THE_CHARCOAL_OS_IMPLEMENTATION_MASTER_PLAN.md` (v1.0.0) passa a ser documentação oficial do THE CHARCOAL OS, como o **21º Documento Oficial Congelado**. Nenhuma alteração futura sem criação de nova versão.

**Nova contagem oficial de Documentos Oficiais** (critério em vigor a partir desta fase): 21 Documentos Oficiais Congelados (TCOS-000 a TCOS-017) + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) + a Constituição Permanente (documento de governança, não contado como Fase) = **22 Documentos Oficiais + 1 Constituição**.

**Percentual de maturidade do projeto:** mantido em **97%**, sem alteração adicional decorrente desta aprovação formal.

Pendência P-017-01 (validação formal do proprietário) está **encerrada** por este comando `APROVADO`. Permanecem abertas, sem alteração, as mesmas 8 pendências substantivas consolidadas na Fase 016.

**Confirmação de auditoria (executada antes deste commit):** verificado programaticamente que nenhum conteúdo técnico do `THE_CHARCOAL_OS_IMPLEMENTATION_MASTER_PLAN.md` foi alterado — apenas 3 linhas de status foram trocadas (cabeçalho, Quality Gate, linha final); as 22 seções/capítulos permanecem intactas; nenhuma referência cruzada foi modificada; nenhuma dependência entre módulos foi alterada; a ordem oficial de implementação (Camadas 0-8) permanece byte-idêntica à versão aprovada; nenhuma seção foi removida. Nenhum documento das Fases 000-016 nem a Constituição foram tocados.

---

---

## FASE 018 — Visual Blueprint (Progresso: Partes 1 e 2 aprovadas)

**Status:** Em construção por partes — Parte 1 APROVADA, Parte 2 APROVADA (inclui validação visual complementar dos 11 Dashboards)
**Data:** 2026-08-02

Autorizada pelo proprietário (comando `AUTORIZADO`) a criação de um novo documento oficial fora da lógica de fase única: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018), com a finalidade exclusiva de representar visualmente o sistema para validação de UX antes de qualquer implementação técnica — não constitui Frontend, não constitui código. Por determinação expressa do proprietário, o documento é construído em 8 partes, cada uma com Auditoria de Consistência prévia e posterior, Resumo Executivo e aprovação formal antes da parte seguinte.

Antes do início da Parte 1, foi executada Auditoria de Consistência completa sobre toda a documentação oficial relevante para a experiência visual (UX/UI Specification, Frontend Architecture, Functional Specification, User Journeys, Domain Model, Business Rules Specification, System Architecture, Data Architecture). O proprietário determinou (comando `ALTERAR`) que as 3 divergências cosméticas encontradas (nomenclatura "Dashboard Metas" vs. "Dashboard de Metas"; contagem interna 14 vs. 15 componentes no UX/UI Specification; uso não desambiguado de "Dashboard Financeiro" no User Journeys) não impedem a construção do documento, não geram melhoria permanente nem Change Request nesta fase, e ficam catalogadas para um único Relatório Consolidado de Padronização ao final das 8 partes.

**Parte 1** (Capítulos 1–11): Papel do Documento, Legenda, Visão Geral do Sistema, Arquitetura Visual (mapeamento das 5 sub-camadas já aprovadas do Frontend Architecture, sem camada nova), Mapa Geral de Navegação (com o agrupamento dos 27 módulos nas 10 Áreas da Empresa identificado explicitamente como inferência visual), Fluxo Principal do Usuário, Estrutura dos Menus, Barra Superior, Barra Lateral, Navegação Mobile, Navegação Desktop.

**Parte 2** (Capítulos 12–23): Estrutura Visual comum aos 11 Dashboards e o detalhamento individual de cada um (CEO, Financeiro Pessoal, Financeiro Empresarial, Produção, Estoque, Engenharia de Custos, Eventos, CRM, Marketing, Metas, Inteligência Artificial), todos ancorados nos códigos F-XXX/RN-XXX/PF-XX já oficiais. Complementarmente, por determinação do proprietário, foi produzida uma validação visual (wireframe estrutural, sem paleta/tipografia oficial — ambas permanecem pendentes de confirmação) dos 11 Dashboards, apresentada como Artifact e aprovada antes do início da Parte 3.

### Decisões tomadas
- D-018-01: em caso de divergência de nomenclatura entre documentos oficiais, prevalecem UX/UI Specification (TCOS-005) e Frontend Architecture (TCOS-011) como referência visual canônica desta fase — sem alterar nenhum documento congelado.
- D-018-02: o agrupamento dos 27 módulos em 10 Áreas da Empresa para fins de menu lateral é uma inferência visual desta fase, derivada de Enterprise Domain Discovery §5, System Architecture Cap. 8 e Security and Privacy Architecture — nunca uma nova regra de negócio ou redefinição de Perfil de acesso.
- D-018-03: as divergências cosméticas identificadas na Auditoria de Consistência pré-construção não geram melhoria permanente nem Change Request nesta fase — ficam catalogadas para um único Relatório Consolidado de Padronização ao final das 8 partes.

### Alterações
- ALT-018-01: criado o documento `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md`, em construção (Partes 1–2 de 8 aprovadas). Nenhum documento oficial congelado foi alterado.

### Melhorias sugeridas (Backlog)
- Nenhuma nova melhoria permanente registrada nesta fase, por determinação expressa do proprietário (ver Decisão D-018-03). As 3 divergências cosméticas permanecem em registro interno de acompanhamento dentro do próprio `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md`.

### Riscos encontrados
- Nenhum risco novo. Os 5 riscos já consolidados na Fase 016 permanecem, sem alteração.

### Pendências
- P-018-01: aprovação formal do proprietário para as Partes 3 a 8 do `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (em andamento, parte a parte).
- Pendências herdadas: as mesmas 8 pendências substantivas consolidadas na Fase 016, sem nenhuma nova.

**Confirmação de auditoria (executada antes deste registro):** verificado programaticamente que a numeração dos 23 capítulos já construídos é sequencial e íntegra; todos os códigos F-XXX (31 citados), RN-XXX (4 citados) e PF-XX (2 citados) existem nos documentos oficiais de origem; todos os módulos citados correspondem ao mapeamento oficial; 3 erros de citação cruzada de capítulo cometidos durante a própria redação desta fase foram encontrados e corrigidos antes deste registro (nunca em documento congelado — sempre no `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md`, ainda em construção). Confirmado via `git status` que nenhum documento além do `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` foi modificado. Nenhuma funcionalidade, regra de negócio ou decisão arquitetural foi criada, alterada ou removida.

---

## FASE 018 — Visual Blueprint (Progresso: Sub-Parte 3a aprovada)

**Status:** Em construção por partes — Parte 1 APROVADA, Parte 2 APROVADA (com validação visual dos 11 Dashboards), Parte 3 em construção: sub-parte 3a APROVADA
**Data:** 2026-08-02

Aprovada pelo proprietário a **sub-parte 3a** do Capítulo 24 (Blueprint Completo das 30 Telas), que entregou o índice completo das 30 telas (Cap. 24.1, com toda classificação de Template identificada explicitamente como `[Inferência visual]`) e o detalhamento visual de 7 telas de módulo: Leads, Clientes, Eventos, Orçamentos, Contratos, Produção e Receitas (Cap. 24.2–24.8), grounded exclusivamente nos perfis já oficiais do UX/UI Specification, §3.12–3.18.

### Decisões tomadas
- D-018-04: dado o volume do Capítulo 24 (30 telas × 14 aspectos visuais), a construção foi subdividida em 3 sub-partes (3a, 3b, 3c) dentro da Parte 3 do roteiro de 8 partes, sem alterar o escopo total já comunicado.

### Alterações
- ALT-018-02: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` avança para a sub-parte 3a aprovada (Cap. 24.1–24.8). Nenhum documento oficial congelado foi alterado.

### Melhorias sugeridas (Backlog)
- Nenhuma nova. As 3 divergências cosméticas já catalogadas na Fase 018 (registro interno do próprio Visual Blueprint) permanecem sem alteração de tratamento.

### Riscos encontrados
- Nenhum risco novo.

### Pendências
- P-018-01 (aprovação parte a parte do Visual Blueprint) segue em andamento — sub-partes 3b e 3c do Capítulo 24, e Partes 4 a 8, ainda pendentes.
- Pendências herdadas: as mesmas 8 pendências substantivas consolidadas na Fase 016, sem nenhuma nova.

**Confirmação de auditoria (executada antes deste registro):** verificados programaticamente os 10 pontos solicitados pelo proprietário — estrutura sequencial dos 24 capítulos íntegra; todas as referências cruzadas (incluindo referências futuras aos Capítulos 25–28, já declaradas no roteiro) consistentes; todos os 53 códigos F-XXX, 16 códigos RN-XXX, 2 códigos PF-XX e todos os módulos citados confirmados existentes nos documentos oficiais de origem; nenhuma tela, funcionalidade, componente, fluxo, botão ou comportamento criado além da documentação oficial; nenhuma funcionalidade removida; nenhuma regra de negócio ou decisão arquitetural alterada; confirmado via `git status` que apenas o `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` foi modificado.

---

## FASE 018 — Visual Blueprint (Progresso: Sub-Parte 3b aprovada)

**Status:** Em construção por partes — Partes 1 e 2 APROVADAS, Parte 3 em construção: sub-partes 3a e 3b APROVADAS
**Data:** 2026-08-02

Aprovada pelo proprietário a **sub-parte 3b** do Capítulo 24, com o detalhamento visual de 6 telas de módulo: Fichas Técnicas, Precificação, Compras, Estoque, Lotes e Equipamentos (Cap. 24.9–24.14), grounded exclusivamente nos perfis já oficiais do UX/UI Specification, §3.19–3.24.

### Decisões tomadas
- Nenhuma decisão nova além da já registrada em D-018-04 (subdivisão do Capítulo 24 em 3a/3b/3c).

### Alterações
- ALT-018-03: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` avança para a sub-parte 3b aprovada (Cap. 24.9–24.14). Nenhum documento oficial congelado foi alterado.

### Melhorias sugeridas (Backlog)
- Nenhuma nova.

### Riscos encontrados
- Nenhum risco novo.

### Pendências
- P-018-01 segue em andamento — sub-parte 3c do Capítulo 24, e Partes 4 a 8, ainda pendentes.
- Pendências herdadas: as mesmas 8 pendências substantivas consolidadas na Fase 016, sem nenhuma nova.

**Confirmação de auditoria (executada antes deste registro):** verificados programaticamente os 10 pontos solicitados — estrutura sequencial dos 24 capítulos e das 14 subseções 24.1–24.14 íntegra; todos os 67 códigos F-XXX, 22 códigos RN-XXX, 2 códigos PF-XX e todos os módulos citados confirmados existentes nos documentos oficiais de origem; nenhuma tela, funcionalidade, componente, fluxo, botão ou comportamento criado além da documentação oficial; nenhuma funcionalidade removida; nenhuma regra de negócio ou decisão arquitetural alterada; confirmado via `git status` que apenas o `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` foi modificado.

---

## FASE 018 — Visual Blueprint (Progresso: Capítulo 24 concluído — Partes 1-3 aprovadas)

**Status:** Em construção por partes — Partes 1, 2 e 3 APROVADAS (Parte 3 = Capítulo 24, as 30 telas, em sub-partes 3a/3b/3c, todas aprovadas)
**Data:** 2026-08-02

Aprovada pelo proprietário a **sub-parte 3c**, última do Capítulo 24, com o detalhamento visual de 6 telas de módulo: Funcionários, Escalas, Bancos, Conciliação Bancária, Configurações e Administração (Cap. 24.15–24.20). Com esta aprovação, o **Capítulo 24 (Blueprint Completo das 30 Telas) está oficialmente concluído**: as 30 telas do sistema (11 Dashboards, Capítulos 13–23, mais 19 telas de módulo, Capítulos 24.2–24.20) estão documentadas visualmente, cada uma exatamente uma única vez.

### Decisões tomadas
- Nenhuma decisão nova além das já registradas em D-018-04 (subdivisão em sub-partes).

### Alterações
- ALT-018-04: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` conclui a Parte 3 (Capítulo 24, sub-partes 3a/3b/3c todas aprovadas). Nenhum documento oficial congelado foi alterado.

### Melhorias sugeridas (Backlog)
- Nenhuma nova.

### Riscos encontrados
- Nenhum risco novo.

### Pendências
- P-018-01 segue em andamento — Partes 4 a 8 do Visual Blueprint ainda pendentes.
- Pendências herdadas: as mesmas 8 pendências substantivas consolidadas na Fase 016, sem nenhuma nova.

**Confirmação de auditoria (executada antes deste registro):** verificados programaticamente os 10 pontos solicitados — estrutura sequencial dos 24 capítulos e das 20 subseções 24.1–24.20 íntegra; todos os 83 códigos F-XXX, 26 códigos RN-XXX, 2 códigos PF-XX, 2 códigos FL-XXX e os 27 módulos citados confirmados existentes/corretos; as 30 telas confirmadas documentadas exatamente uma única vez, sem omissão ou duplicação; nenhum elemento visual criado além da documentação oficial; nenhuma funcionalidade removida; nenhuma regra de negócio ou decisão arquitetural alterada; confirmado via `git status` que apenas o `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` foi modificado.

---

## FASE 018 — Encerramento Oficial

**Status:** APROVADA E CONGELADA pelo proprietário em 2026-08-02 (comando `APROVADO`)
**Data:** 2026-08-02

O `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018) passa a ser documentação oficial do THE CHARCOAL OS, como o **22º Documento Oficial Congelado**. Construído em 6 Partes (mais 2 correções pontuais aprovadas via `CORRIGIR`), cada uma com Auditoria de Consistência prévia e posterior, o documento representa visualmente toda a Baseline Oficial: 28 capítulos cobrindo a estrutura de navegação, os 11 Dashboards, as 30 telas do sistema, a biblioteca de 24 itens de Componentes Visuais, o Design System Consolidado, os 30 fluxos oficiais (FL-001 a FL-030) como caminhos visuais, e um Protótipo Navegável Conceitual (sitemap completo + roteiro de demonstração). Por determinação do proprietário, o encerramento ocorreu ao final da Parte 6 (Capítulo 28) — os capítulos "Experiência do Usuário" e "Visualização do Sistema", originalmente previstos no roteiro inicial, não foram construídos, superados pela decisão de encerramento antecipado.

### Decisões tomadas
- D-018-05: encerramento oficial do TCOS-018 ao final da Parte 6 (Capítulo 28) — os capítulos "Experiência do Usuário" e "Visualização do Sistema" do roteiro original não foram construídos, por decisão explícita do proprietário, sem constituir lacuna ou pendência.
- D-018-06: as 3 divergências cosméticas catalogadas ao longo da fase (D-01 a D-03) permanecem registradas, não corrigidas, consolidadas no Relatório Consolidado de Padronização (dentro do próprio TCOS-018) — sujeitas a um único Change Request futuro, mediante aprovação explícita do proprietário.

### Alterações
- ALT-018-05: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (v1.0.0) congelado como documento oficial. Nenhum outro documento oficial foi alterado.

### Melhorias sugeridas (Backlog)
- Nenhuma nova. As 3 divergências cosméticas (D-01 a D-03) permanecem como candidatas a um único Change Request futuro de padronização de nomenclatura entre UX/UI Specification, Functional Specification e User Journeys — decisão exclusiva do proprietário, fora do escopo desta fase.

### Riscos encontrados
- Nenhum risco novo. Os 5 riscos já consolidados na Fase 016 permanecem, sem alteração.

### Pendências
- P-018-01 (aprovação parte a parte do Visual Blueprint) está **encerrada** — todas as 6 Partes e as 2 correções foram aprovadas pelo proprietário.
- Duas limitações informativas específicas desta fase permanecem registradas (Capítulo 27.10 do TCOS-018): FL-021 sem tela dedicada de configuração de Dashboard; FL-030 dependente de parâmetro de fidelização ainda não confirmado — nenhuma bloqueia a implementação do Frontend.
- Pendências herdadas: as mesmas 8 pendências substantivas consolidadas na Fase 016, sem nenhuma nova.

**Nova contagem oficial de Documentos Oficiais** (critério em vigor a partir desta fase): 22 Documentos Oficiais Congelados (TCOS-000 a TCOS-018) + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) + a Constituição Permanente (documento de governança, não contado como Fase) = **23 Documentos Oficiais + 1 Constituição**.

**Percentual de maturidade do projeto:** mantido em **97%** — esta fase valida visualmente a Baseline já completa, sem ampliar ou reduzir o escopo conceitual.

**Confirmação de auditoria (executada antes deste commit):** verificado programaticamente que a estrutura do `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` permanece íntegra — 28 capítulos sequenciais, subseções sequenciais em todos os capítulos que as possuem (24.1–24.20, 25.1–25.24, 26.1–26.5, 27.1–27.10, 28.1–28.5); 89 códigos F-XXX, 28 códigos RN-XXX, 3 códigos PF-XX e 30 códigos FL-XXX (cobertura de 30/30 fluxos oficiais) confirmados existentes/corretos; as 30 telas, 11 Dashboards e 27 módulos confirmados com representação visual completa; 14 inferências visuais, todas explicitamente identificadas. Confirmado via `git status`/`git diff` que, ao longo de toda a Fase 018, apenas o `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` e este `PROJECT_MEMORY.md` foram modificados — nenhum dos 21 documentos oficiais congelados anteriores nem a Constituição Permanente foram tocados.

---

*Este arquivo deve ser atualizado ao final de cada fase, adicionando uma nova seção "FASE NNN" sem remover o histórico das fases anteriores.*
