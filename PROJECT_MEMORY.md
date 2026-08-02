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

## FASE 019A — Visual Identity & Design Refinement (Progresso: Fase 1 aprovada)

**Status:** Em construção por fases — Fase 1 (Identidade Visual Oficial) APROVADA; Fase 2 (Biblioteca Visual Oficial de Componentes) em construção
**Data:** 2026-08-02

Autorizada pelo proprietário uma nova etapa, fora da implementação técnica, dedicada ao refinamento visual do THE CHARCOAL OS: `THE_CHARCOAL_OS_VISUAL_IDENTITY_AND_DESIGN_REFINEMENT.md` (TCOS-019A). A Fase 1 instanciou valores concretos (paleta, tipografia, espaçamento, elevação, raios de borda, contraste) para os tokens conceituais que o TCOS-018 havia deixado `[Pendente de confirmação visual]`, e definiu a linguagem visual de ícones, gráficos, cards, tabelas, botões, filtros, badges, alertas, estados, animações e microinterações — sem alterar nenhuma categoria semântica, componente, tela, arquitetura, regra de negócio ou documento oficial congelado já existente.

### Decisões tomadas
- D-019A-01: a paleta oficial do sistema é fundamentada em tons quentes (Brasa/Carvão), com o Roxo-IA mantido deliberadamente como a única cor fria — reforçando visualmente a distinção entre dado humano e sugestão de IA (PF-06).
- D-019A-02: tipografia definida por arquétipo (grotesca de baixo contraste) sem nomear fonte comercial específica, por ser decisão de licenciamento/tooling fora do escopo conceitual desta fase.
- D-019A-03: 3 raios de borda e 4 níveis de sombra/profundidade, criados nesta fase (conceitos novos, sem definição anterior), aplicados por categoria de componente, não por preferência pontual.

### Alterações
- ALT-019A-01: criado o documento `THE_CHARCOAL_OS_VISUAL_IDENTITY_AND_DESIGN_REFINEMENT.md`, em construção (Fase 1 de N aprovada). Nenhum documento oficial congelado foi alterado.

### Melhorias sugeridas (Backlog)
- Nenhuma nova.

### Riscos encontrados
- Nenhum risco novo.

### Pendências
- Validação técnica exata do contraste AA permanece pendente da escolha de tecnologia (M-011-02, já registrada na Fase 011).
- Fase 2 (Biblioteca Visual Oficial de Componentes) e fases subsequentes do TCOS-019A ainda pendentes.
- Pendências herdadas: as mesmas 8 pendências substantivas consolidadas na Fase 016, sem nenhuma nova.

**Confirmação de auditoria (executada antes deste registro):** confirmado que a Fase 1 instancia apenas valores concretos para categorias/conceitos já nomeados no TCOS-005/TCOS-011, sem renomear, remover ou alterar seu papel semântico; nenhuma tecnologia, código, CSS ou framework definido; confirmado via `git status` que apenas o `THE_CHARCOAL_OS_VISUAL_IDENTITY_AND_DESIGN_REFINEMENT.md` foi criado — nenhum dos 22 documentos oficiais congelados nem a Constituição Permanente foram alterados.

---

## FASE 019A — Visual Identity & Design Refinement (Progresso: Biblioteca Visual aprovada)

**Status:** Em construção por fases — Fase 1 (Identidade Visual Oficial) APROVADA; Fase 2 (Biblioteca Visual Oficial de Componentes) APROVADA; refinamento visual das 30 telas em início
**Data:** 2026-08-02

Aprovada pelo proprietário a Fase 2 do TCOS-019A: a Biblioteca Visual Oficial de Componentes, com 35 componentes documentados cobrindo integralmente as 24 categorias já catalogadas no TCOS-018 (Capítulo 25). A Biblioteca passa a ser a referência oficial obrigatória para todo refinamento visual futuro do THE CHARCOAL OS. Autorizado o início do refinamento visual das 30 telas, na ordem: os 11 Dashboards (CEO, Financeiro Pessoal, Financeiro Empresarial, Produção, Estoque, Engenharia de Custos, Eventos, CRM, Marketing, Metas, Inteligência Artificial), seguidos das 19 telas operacionais — uma tela por vez, cada uma com autoauditoria e aprovação do proprietário antes da próxima.

### Decisões tomadas
- D-019A-04: a Biblioteca Visual Oficial (35 componentes, 24/24 categorias do TCOS-018) é a referência obrigatória para todo refinamento visual futuro — nenhuma tela pode introduzir um componente fora dela sem nova especificação formal.
- D-019A-05: refinamento visual das 30 telas ocorre uma por vez, na ordem dos 11 Dashboards seguida das 19 telas operacionais, cada uma exigindo aprovação do proprietário antes da próxima.

### Alterações
- ALT-019A-02: `THE_CHARCOAL_OS_VISUAL_IDENTITY_AND_DESIGN_REFINEMENT.md` conclui a Fase 2 (Biblioteca Visual Oficial de Componentes), aprovada. Nenhum documento oficial congelado foi alterado.

### Melhorias sugeridas (Backlog)
- Nenhuma nova.

### Riscos encontrados
- Nenhum risco novo.

### Pendências
- Refinamento visual das 30 telas (11 Dashboards + 19 telas operacionais) ainda pendente, tela a tela.
- Pendências herdadas: as mesmas 8 pendências substantivas consolidadas na Fase 016, sem nenhuma nova.

**Confirmação de auditoria (executada antes deste registro):** confirmado que as 24 categorias de componente do TCOS-018 (Capítulo 25) têm especificação correspondente na Biblioteca Visual; nenhuma duplicidade; nenhuma funcionalidade, regra de negócio ou decisão arquitetural alterada; confirmado via `git status` que apenas o `THE_CHARCOAL_OS_VISUAL_IDENTITY_AND_DESIGN_REFINEMENT.md` foi modificado ao longo de toda a Fase 2 — nenhum dos 22 documentos oficiais congelados nem a Constituição Permanente foram tocados.

---

## AUDITORIA CORRETIVA DE ARQUITETURA — Achados Altos (Correção Documental)

**Status:** CONCLUÍDA E APROVADA PELO PROPRIETÁRIO (comando `CORRIGIR`, escopo fechado)
**Data:** 2026-08-02

Executada, a pedido do proprietário, uma Auditoria Arquitetural completa (arquitetura, escalabilidade, desacoplamento, manutenibilidade, reutilização, modularização, SOLID, Clean Architecture, riscos técnicos, gargalos futuros) sobre a documentação oficial de arquitetura (TCOS-002 a TCOS-017). Dos achados classificados como Alto, dois foram aprovados para correção documental mínima, sem qualquer alteração de arquitetura, módulo, Serviço, Fluxo, Funcionalidade ou Regra de Negócio.

### Decisões tomadas
- D-COR-01: a relação de colaboração mútua entre Produção (Módulo 10) e Estoque (Módulo 16), já registrada na Matriz de Dependências do TCOS-006 (Capítulo 4) e já resolvida operacionalmente no TCOS-017 (implementação em bloco único), estava descrita de forma factualmente incorreta no TCOS-009 (Capítulo 9), que afirmava "confirmar a ausência de dependência circular" — a frase foi corrigida para refletir corretamente o que o próprio TCOS-006 já registra.
- D-COR-02: a lista-resumo em prosa "Quem precisa obrigatoriamente de outro" do TCOS-006 (Capítulo 4) foi alinhada à sua própria tabela oficial, que já listava Estoque como dependente obrigatório de Produção — sem alterar a tabela, apenas complementando a prosa que a resume.
- D-COR-03: a declaração de fechamento da Fase 004 ("grafo acíclico, sem dependência circular") representava corretamente o estado do projeto naquele momento (antes da existência do conceito de Agregado e da Matriz de Dependências entre Módulos, ambos introduzidos apenas no TCOS-006/TCOS-007). Essa leitura foi posteriormente complementada pela decisão arquitetural formalizada no TCOS-006 (colaboração mútua Produção↔Estoque) e esclarecida operacionalmente no TCOS-017. O registro original da Fase 004 permanece intacto, sem edição — esta nota apenas o contextualiza.
- D-COR-04: o Serviço de Indicadores e Dashboards e o Serviço de Auditoria, por assinarem "todos os eventos do sistema, sem exceção" (TCOS-006, Capítulo 6), têm carga de processamento agregada por definição arquitetural — diferente dos demais 13 Serviços, cuja carga é independente entre si. Isso não é uma inconsistência documental (nenhum documento afirma o contrário de forma explícita), mas um risco de dimensionamento a ser observado quando houver definição tecnológica de infraestrutura. Nenhuma solução técnica (fila, particionamento, sharding) foi antecipada nesta fase.

### Alterações
- ALT-COR-01: `THE_CHARCOAL_OS_INTEGRATION_AND_API_CONTRACT.md` (TCOS-009), Capítulo 9 — última frase corrigida, substituindo a afirmação incorreta de "ausência de dependência circular" pelo reconhecimento da colaboração mútua Produção↔Estoque já documentada no TCOS-006 e resolvida no TCOS-017. Nenhuma outra linha do documento foi tocada.
- ALT-COR-02: `THE_CHARCOAL_OS_SYSTEM_ARCHITECTURE.md` (TCOS-006), Capítulo 4 — lista "Quem precisa obrigatoriamente de outro" complementada com "Estoque (Compras/Produção)", alinhando a prosa à tabela oficial já existente na mesma seção. Nenhuma outra linha do documento foi tocada.
- Nenhum outro documento oficial congelado foi alterado. O `THE_CHARCOAL_OS_IMPLEMENTATION_MASTER_PLAN.md` (TCOS-017) permanece integralmente intacto e válido — é, na verdade, a fonte da redação agora refletida no TCOS-009.

### Melhorias sugeridas (Backlog)
- Nenhuma nova.

### Riscos encontrados
- **R-COR-01 (Risco Técnico de Escalabilidade, registrado nesta fase, sem correção documental associada):** os Serviços Indicadores e Dashboards e Auditoria possuem carga de processamento agregada por definição arquitetural (assinam todos os eventos do sistema, sem exceção — TCOS-006, Capítulo 6), diferentemente dos demais 13 Serviços, cuja carga escala de forma independente (TCOS-006 Capítulo 9; TCOS-010 Capítulo 22). Nenhum documento oficial define hoje uma estratégia de processamento (não confundir com a estratégia de armazenamento/cache já definida no TCOS-008) para esse padrão de carga agregada. Este risco deverá receber atenção específica na primeira fase que definir a infraestrutura tecnológica do SaaS — sem antecipação de fila, particionamento, sharding ou qualquer outro mecanismo técnico nesta etapa.
- Os demais riscos já consolidados nas fases anteriores permanecem, sem alteração.

### Pendências
- R-COR-01 aguarda retomada na futura fase de definição de infraestrutura/tecnologia.
- Pendências herdadas: as mesmas 8 pendências substantivas consolidadas na Fase 016, sem nenhuma nova.

**Confirmação de auditoria (executada antes deste registro):** confirmado via `git diff` que apenas 1 frase do TCOS-009 (Capítulo 9) e 1 item da lista-resumo do TCOS-006 (Capítulo 4) foram alterados — nenhuma tabela, nenhuma outra frase, nenhum outro capítulo de nenhum dos dois documentos foi tocado; nenhuma Regra de Negócio (RN-XXX), Fluxo (FL-XXX) ou Funcionalidade (F-XXX) referencia as linhas alteradas; o TCOS-017 não foi modificado e permanece a fonte correta já refletida nas correções; a arquitetura conceitual (27 módulos, 15 Serviços, Event Bus) permanece exatamente a mesma — apenas a documentação passou a representar corretamente uma decisão arquitetural que já existia.

---

## FASE 020 — Product & SaaS Strategy (Camada de Produto, em construção)

**Status:** Em construção — v1.1.0 (revisão de mercado-alvo aplicada), aguardando aprovação final do proprietário
**Data:** 2026-08-02

Instituída, a pedido do proprietário, a Camada de Produto do THE CHARCOAL OS: novo documento `THE_CHARCOAL_OS_PRODUCT_AND_SAAS_STRATEGY.md` (TCOS-020), com 30 seções cobrindo visão de produto, posicionamento, ICP, personas, JTBD, diferenciais competitivos, UVP, monetização, planos/empacotamento dos 27 módulos já existentes, estratégia de IA como diferencial comercial, roadmap comercial, escalabilidade, expansão internacional, onboarding, customer success, retenção, comunidade, feedback, evolução contínua, métricas SaaS, North Star Metric, KPIs, backlog estratégico, riscos de produto, SWOT, moat e plano direcional de 10 anos — operando exclusivamente acima da arquitetura já aprovada, sem alterar nenhum módulo, Serviço, tela, Fluxo, Funcionalidade, Regra de Negócio ou documento oficial congelado. O documento herda explicitamente o risco R-000-03 (domínio de negócio não confirmado, "o risco mais relevante do projeto" per TCOS-016) para todo o conteúdo de mercado/ICP/personas.

Nesta mesma fase, o proprietário instituiu também, de forma permanente e aplicável a todas as etapas futuras: (a) a ampliação do meu papel para incluir CPO, Product & Business Architect, SaaS Strategist, Growth Advisor, Customer Success Architect, UX Strategist e Software Quality Director; (b) o Protocolo Executivo de Desenvolvimento, com hierarquia de decisão (Constituição → Framework → Documentos Oficiais → Arquitetura → Regras de Negócio → TCOS-020 → demais documentos → prompt da tarefa) e Auditoria Executiva de 10 pontos (Estrutural, Componentes, Documental, Conteúdo, Consistência, Arquitetural, UX/UI, SaaS, Comercial, Estratégica); (c) o Protocolo de Orquestração Inteligente de Capacidades (Skills/Agent/Artifact/ferramentas usadas apenas quando trazem ganho objetivo, nunca conduzindo decisão arquitetural, sempre registradas em "Capacidades Utilizadas"); (d) o Protocolo de Priorização Estratégica (11 critérios de impacto, recomendação nunca automática).

### Decisões tomadas
- D-020-01: Camada de Produto opera estritamente acima da arquitetura oficial — nenhuma decisão de produto pode alterar módulo, Serviço, regra de negócio ou documento técnico já congelado; em qualquer conflito, arquitetura/regras de negócio prevalecem sobre recomendação comercial.
- D-020-02 (revisão v1.1.0): a **Austrália é estabelecida como mercado primário de validação** do THE CHARCOAL OS, com o **Brasil como mercado estratégico de expansão posterior** — substituindo a hipótese inicial (Brasil como mercado doméstico de lançamento), que era uma inferência estratégica não confirmada. Revisão limitada aos Capítulos 1–3 (Visão/Posicionamento/ICP), 13 (Roadmap Comercial) e 15 (Estratégia Internacional) do TCOS-020, com ajuste de consistência no Capítulo 30 (Plano de 10 Anos), que restatava diretamente a sequência do Capítulo 15.

### Alterações
- ALT-020-01: criado `THE_CHARCOAL_OS_PRODUCT_AND_SAAS_STRATEGY.md` (TCOS-020), em construção. Nenhum documento oficial congelado foi alterado.
- ALT-020-02: revisão v1.1.0 do TCOS-020 — mercado-alvo (Austrália/Brasil) — 6 trechos ajustados (Capítulos 1, 3, 13, 15, 30 + nota de revisão na Executive Memory), confirmados via `git diff` como as únicas alterações. Nenhum outro documento oficial foi tocado.

### Melhorias sugeridas (Backlog)
- Observação de auditoria (não incorporada ao TCOS-020 por estar fora do escopo autorizado desta revisão): a elevação da Austrália a mercado primário torna as pré-condições de localização de idioma (inglês) e moeda (AUD), e de adequação regulatória/tributária australiana, imediatamente relevantes — anteriormente essas pré-condições eram tratadas como diferidas a uma fase distante. Recomenda-se considerar, em revisão futura do Capítulo 27 (Riscos do Produto) do TCOS-020, o registro formal de um risco específico sobre isso — não registrado nesta fase por não constar no escopo autorizado pelo `CORRIGIR`.

### Riscos encontrados
- Nenhum risco novo de arquitetura. Riscos de produto já registrados no próprio TCOS-020 (RP-020-01 a RP-020-04) permanecem, com R-000-03 (herdado) como o de maior relevância sobre todo o conteúdo de mercado.

### Pendências
- Aprovação final do proprietário sobre o TCOS-020 (v1.1.0) ainda pendente.
- Pendências herdadas: as mesmas pendências substantivas já consolidadas, sem nenhuma nova de arquitetura.

**Confirmação de auditoria (executada antes deste registro):** confirmado via `git diff --stat` que, na revisão v1.1.0, apenas `THE_CHARCOAL_OS_PRODUCT_AND_SAAS_STRATEGY.md` foi modificado (10 inserções, 8 remoções, todas dentro dos Capítulos 1, 3, 13, 15, 30 e da Executive Memory); nenhum módulo, Serviço, Fluxo (FL-XXX), Funcionalidade (F-XXX) ou Regra de Negócio (RN-XXX) foi referenciado nas linhas alteradas; nenhum dos 24 documentos oficiais congelados nem a Constituição Permanente foram tocados.

---

## FASE 021 — Customer Experience & Lifecycle Strategy (Camada de Produto, Parte 2)

**Status:** Em construção — primeira apresentação, aguardando aprovação do proprietário
**Data:** 2026-08-02

Criado, a pedido do proprietário, o `THE_CHARCOAL_OS_CUSTOMER_EXPERIENCE_AND_LIFECYCLE_STRATEGY.md` (TCOS-021), segunda parte da Camada de Produto — complementa o TCOS-020 com o detalhamento operacional de Jornada do Cliente, Ciclo de Vida, Onboarding, Ativação, Trial, Conversão, Cobrança, Renovação, Cancelamento, Retenção, Expansão, Customer Success, Suporte e Feedback Contínuo. Toda a relação comercial de assinatura (trial/cobrança/renovação/cancelamento) foi formalmente definida como uma camada acima e fora dos 27 módulos de domínio, para nunca contaminar o Financeiro do próprio cliente (Módulos 02/03/27) com a receita de assinatura do fornecedor, e para não exigir nenhum módulo novo.

### Decisões tomadas
- D-021-01: a Camada de Assinatura/Cobrança do THE CHARCOAL OS como fornecedor é conceitualmente distinta e externa aos 27 módulos de domínio, que modelam exclusivamente o negócio do cliente — nenhuma implementação técnica de billing é definida nesta fase.
- D-021-02: o Ciclo de Vida do Cliente (6 estágios: Prospect, Trial, Onboarding, Ativo, Em risco, Encerrado) é modelado inteiramente como leitura comercial sobre dado e evento já existentes — nenhuma entidade nova do Domain Model.

### Alterações
- ALT-021-01: criado `THE_CHARCOAL_OS_CUSTOMER_EXPERIENCE_AND_LIFECYCLE_STRATEGY.md` (TCOS-021), em construção. Nenhum documento oficial congelado foi alterado. Confirmado via `git status` que apenas este arquivo foi criado.

### Melhorias sugeridas (Backlog)
- Nenhuma nova além das já registradas no TCOS-021 (Capítulo 18: RC-021-02, RC-021-03).

### Riscos encontrados
- **RC-021-01 (Erro, achado nesta fase, NÃO corrigido):** o TCOS-020, Capítulo 4 (Personas), cita incorretamente "5 Perfis... Proprietário, Administrativo, Operacional, Comercial, BI/Direção" como já formalizados no TCOS-012. A estrutura real e oficial (TCOS-012, Capítulos 8–9; TCOS-006, Capítulo 8) é de **10 Perfis por Área da Empresa** (Comercial/CRM, Produção, Compras/Suprimentos, Estoque/Logística, Eventos/Operações, Financeiro, Marketing, Pessoas/Mão de Obra, Administrativo/Documentos, BI/Direção Executiva) **mais o Administrador do Sistema transversal** — 11 papéis nomeados, nenhum deles "Proprietário" ou "Operacional". Severidade Média. O TCOS-021 já usa a estrutura correta em todo o seu conteúdo, para não propagar o erro. Correção do TCOS-020 Capítulo 4 pendente de autorização explícita do proprietário.
- RC-021-02 (Risco): ausência de definição técnica da Camada de Assinatura — sem estimativa de esforço até extensão futura do TCOS-017.
- RC-021-03 (Risco, herdado): retenção de dado pós-cancelamento depende da mesma decisão de Governança de Privacidade já pendente (TCOS-012, Capítulo 31).

### Pendências
- Aprovação do proprietário sobre o TCOS-021.
- Correção do TCOS-020 Capítulo 4 (RC-021-01) — aguardando autorização explícita.
- Pendências herdadas: as mesmas já consolidadas, sem nenhuma nova de arquitetura.

**Confirmação de auditoria (executada antes deste registro):** confirmado via `git status` que apenas `THE_CHARCOAL_OS_CUSTOMER_EXPERIENCE_AND_LIFECYCLE_STRATEGY.md` foi criado (arquivo novo, não modificação); nenhum dos 25 documentos oficiais existentes foi alterado; verificação programática confirmou 18 capítulos sequenciais (1–18) sem lacuna; toda a Matriz de Perfis e Módulos (Capítulo 17 do TCOS-021) foi conferida item a item contra a Matriz de Dependências do TCOS-006 (Capítulo 4) — nenhum módulo ou Perfil citado é inexistente.

---

## FASE 022 — SaaS Platform & Tenant Management Strategy (Camada de Produto, Parte 3)

**Status:** Em construção — primeira apresentação, aguardando aprovação do proprietário
**Data:** 2026-08-02

Criado, a pedido explícito do proprietário (com instrução de releitura direta dos documentos-fonte, sem uso de memória de conversa como fonte primária), o `THE_CHARCOAL_OS_SAAS_PLATFORM_AND_TENANT_MANAGEMENT_STRATEGY.md` (TCOS-022), terceira e última parte planejada da Camada de Produto — define a operação da Plataforma SaaS multi-tenant (Tenant/Organização, Workspace, Multiempresa/Multiusuário, Convites, Papéis Administrativos, Entitlements/Limites por Plano, Upgrade/Downgrade, Trial, Conversão, Suspensão/Reativação, Cancelamento, Ambiente de Demonstração, Feature Flags, Licenciamento, Governança da Plataforma, Escalabilidade para milhares de Tenants, Estratégias para Austrália e Brasil) inteiramente acima e fora dos 27 módulos, 15 Serviços, 11 Perfis de Segurança e 4 Ambientes de engenharia já oficiais — nenhum deles criado, alterado ou reinterpretado.

### Decisões tomadas
- D-022-01: "Tenant" é formalizado como o termo de plataforma/mercado para a "Organização" já reservada (TCOS-007 §7.6) — não uma entidade nova.
- D-022-02: "Entitlement" é formalizado como o termo técnico-comercial para o mecanismo já oficial "módulo habilitado por Organização" (TCOS-020, Capítulos 9–10) — não um conceito novo.
- D-022-03: "Ambiente de Demonstração" é formalizado como um Tenant especial com dado ilustrativo dentro do Ambiente de Produção já oficial (TCOS-014, Capítulo 5) — explicitamente NÃO um 5º Ambiente de engenharia, para não contradizer os 4 já oficiais (Development, Test, Staging, Production).
- D-022-04: "Papéis Administrativos da Organização" (Proprietário da Organização, Administrador da Assinatura) são formalizados como conceito de Plataforma, distinto e sem sobreposição com os 11 Perfis de Segurança já oficiais (TCOS-012) — para não reabrir nem agravar RC-021-01.
- D-022-05: "Suspensão/Reativação" são formalizados como uma dimensão de **acesso à Plataforma**, complementar e independente da dimensão de **relacionamento/sucesso** já definida no Ciclo de Vida do TCOS-021 (Capítulo 4) — as duas dimensões não se substituem.

### Alterações
- ALT-022-01: criado `THE_CHARCOAL_OS_SAAS_PLATFORM_AND_TENANT_MANAGEMENT_STRATEGY.md` (TCOS-022), em construção, 31 capítulos sequenciais confirmados programaticamente. Nenhum documento oficial congelado foi alterado. Confirmado via `git status` que apenas este arquivo foi criado.

### Melhorias sugeridas (Backlog)
- Nenhuma nova além das já registradas no próprio TCOS-022 (Capítulos 12, 16 — valores numéricos de Limite por Plano e duração de Trial, pendentes de dado de uso real).

### Riscos encontrados
- Nenhum risco novo de arquitetura. R-COR-01 (herdado da Auditoria Corretiva de 2026-08-02) reafirmado com relevância ampliada: a carga agregada dos Serviços de Indicadores e Dashboards e de Auditoria cresce proporcionalmente ao número de Tenants operando no modelo compartilhado (TCOS-022, Capítulo 26) — sem antecipação de solução técnica.

### Pendências
- Aprovação do proprietário sobre o TCOS-022, e ainda sobre o TCOS-020 e o TCOS-021.
- Correção do TCOS-020 Capítulo 4 (RC-021-01) — permanece pendente, reafirmada nesta fase sem nova ação.
- M-006-01/M-007-01 (Multiempresa/Multifilial) e M-014-03 (escolha Tenant compartilhado/isolado) — agora também diretamente relevantes à Plataforma SaaS, sem decisão tomada nesta fase.
- Pendências herdadas: as mesmas já consolidadas, sem nenhuma nova de arquitetura.

**Confirmação de auditoria (executada antes deste registro):** confirmado via `git status` que apenas `THE_CHARCOAL_OS_SAAS_PLATFORM_AND_TENANT_MANAGEMENT_STRATEGY.md` foi criado (arquivo novo); nenhum dos 26 documentos oficiais existentes (25 anteriores + TCOS-021) foi alterado; verificação programática confirmou 31 capítulos sequenciais (1–31) sem lacuna; todos os documentos-fonte (TCOS-006, TCOS-007, TCOS-012, TCOS-014, TCOS-017, TCOS-020, TCOS-021) foram relidos diretamente nas seções citadas antes da redação, conforme instrução explícita do proprietário.

---

## FASE 023 — Product Analytics, Telemetry & Product Intelligence (Camada de Produto, Parte 4)

**Status:** APROVADA — TCOS-023 registrado como Baseline Oficial da Fase 023 (comando `APROVADO` do proprietário). Os 2 achados encontrados (RC-021-01 herdado; citação "Capítulo 15→14" da Constituição) permanecem registrados como backlog técnico/documental, não corrigidos, aguardando autorização específica futura. Com esta aprovação, a Camada de Produto (TCOS-020, TCOS-021, TCOS-022, TCOS-023) é considerada, pelo proprietário, com sua construção conceitual encerrada.
**Data:** 2026-08-02

Solicitado originalmente como "TCOS-024"; a Auditoria de Abertura confirmou, por busca em todo o repositório, que nenhum TCOS-023 havia sido criado — achado apresentado ao proprietário antes de qualquer escrita, que autorizou (`APROVADO`) a renumeração para **TCOS-023**, preservando a sequência cronológica sem lacuna. Criado o `THE_CHARCOAL_OS_PRODUCT_ANALYTICS_TELEMETRY_AND_PRODUCT_INTELLIGENCE.md` (TCOS-023), quarta e última parte planejada da Camada de Produto — define Product Intelligence, Analytics, Product Evolution, IA Aplicada ao Produto e Governança, com 45 capítulos, sem citar nenhuma tecnologia ou fornecedor, sem alterar nenhum documento oficial congelado.

### Decisões tomadas
- D-023-01: Product Intelligence opera como mais um assinante do Event Bus já oficial (TCOS-006, Capítulo 7) — nenhum mecanismo de captura paralelo, nenhuma arquitetura nova.
- D-023-02: Product Intelligence (valor entregue pelo produto) e Observabilidade Técnica (TCOS-014, Capítulos 17–20, saúde do sistema) são fronteiras explicitamente distintas, sem sobreposição.
- D-023-03: sinais de produto são formalmente divididos em Categoria A (derivados de eventos de negócio já existentes, disponíveis hoje sem nova instrumentação) e Categoria B (interação de interface — cliques, tempo de tela — que **não existe** em nenhum evento oficial hoje) — toda definição deste documento que depende de Categoria B está explicitamente marcada, nunca apresentada como já disponível.
- D-023-04: toda saída de IA aplicada a produto (Capítulos 34–38) é Sugestão, nunca Decisão, em conformidade estrita com o TCOS-013 (Capítulos 8, 27) — nenhuma exceção para o domínio de "insight de produto".

### Alterações
- ALT-023-01: criado `THE_CHARCOAL_OS_PRODUCT_ANALYTICS_TELEMETRY_AND_PRODUCT_INTELLIGENCE.md` (TCOS-023), em construção, 45 capítulos sequenciais confirmados programaticamente. Nenhum documento oficial congelado foi alterado. Confirmado via `git status` que apenas este arquivo foi criado.

### Melhorias sugeridas (Backlog)
- Endereçar, em fase futura de tecnologia (extensão do TCOS-011/TCOS-017), a instrumentação de sinais de Categoria B (interação de interface) — hoje inexistente em qualquer documento oficial.

### Riscos encontrados
- Nenhum risco novo de arquitetura. Nota de rastreabilidade: R-COR-01 (carga agregada de Indicadores/Auditoria) se aplicaria igualmente a um futuro Serviço de Product Intelligence, caso este também assine todos os eventos do sistema — mencionado no TCOS-023 (Capítulo 43), sem antecipação de solução técnica.
- **Achado (Erro, novo nesta fase, não corrigido):** a Política Oficial de Change Request é o Capítulo 14 da Constituição Permanente, não o Capítulo 15 — citação incorreta ("Capítulo 15") encontrada propagada em 3 documentos: TCOS-019A (Executive Memory, Fase 1, já aprovada), TCOS-020 (Executive Memory e Capítulo 20), TCOS-022 (Capítulo 25). Severidade Baixa (a política referenciada está correta, apenas o número do capítulo é impreciso). TCOS-023 já usa a citação correta em todo o seu conteúdo. Correção das 4 ocorrências nos 3 documentos pendente de autorização explícita do proprietário.

### Pendências
- Aprovação do proprietário sobre o TCOS-023, e ainda sobre o TCOS-020, TCOS-021 e TCOS-022.
- Correção do TCOS-020 Capítulo 4 (RC-021-01) — permanece pendente.
- Correção da citação "Capítulo 15 → Capítulo 14" em TCOS-019A, TCOS-020 e TCOS-022 (achado desta fase) — pendente de autorização.
- Pendências herdadas: as mesmas já consolidadas, sem nenhuma nova de arquitetura.

**Confirmação de auditoria (executada antes deste registro):** confirmado via `git status` que apenas `THE_CHARCOAL_OS_PRODUCT_ANALYTICS_TELEMETRY_AND_PRODUCT_INTELLIGENCE.md` foi criado (arquivo novo); nenhum dos 27 documentos oficiais existentes (26 anteriores + TCOS-022) foi alterado; verificação programática confirmou 45 capítulos sequenciais (1–45) sem lacuna; busca confirmou ausência de qualquer nome de fornecedor/ferramenta no documento; todos os documentos-fonte (Constituição, TCOS-006, TCOS-012, TCOS-013, TCOS-014, TCOS-020, TCOS-021, TCOS-022) foram relidos diretamente nas seções citadas antes da redação, conforme instrução explícita do proprietário.

---

## AUDITORIA GLOBAL DE CONTINUIDADE — Pós Fase 023 (Camada de Produto Completa)

**Status:** Executada a pedido do proprietário, encerrando o ciclo da Camada de Produto (TCOS-020 a TCOS-023)
**Data:** 2026-08-02

**Consistência entre TCOS-020, TCOS-021, TCOS-022, TCOS-023:** verificado programaticamente que os 4 documentos têm capítulos sequenciais sem lacuna (30, 18, 31 e 45 capítulos, respectivamente). Amostra de referências cruzadas entre os 4 documentos (TCOS-021 Cap. 4/7/8/9/11 citados por TCOS-022 e TCOS-023; TCOS-020 Cap. 22/23/24/30 citados por TCOS-021/022/023; TCOS-022 Cap. 3/4/13/18/26 citados por TCOS-023) conferida uma a uma contra os títulos reais dos capítulos — todas corretas, nenhuma referência quebrada encontrada.

**Integridade da sequência documental:** contagem oficial recalculada do zero, por arquivo: TCOS-000 a TCOS-016 (18 documentos numerados) + 2 artefatos da Fase 001B (Business Discovery Questionnaire, Discovery Interview Roadmap) = 20, já batendo com o registro histórico da Fase 016; + TCOS-017 (21) + TCOS-018 (22) + TCOS-019A (23) + TCOS-020 (24) + TCOS-021 (25) + TCOS-022 (26) + TCOS-023 (27) = **27 Documentos Oficiais**, exatamente o número já registrado no Quality Gate do próprio TCOS-023. Nenhuma lacuna, nenhuma duplicidade de número.

**Referências cruzadas:** nenhuma referência a "TCOS-024" remanescente fora dos 2 registros históricos intencionais (PROJECT_MEMORY e o próprio cabeçalho do TCOS-023, ambos explicando a renumeração).

**Aderência à Constituição Permanente:** confirmada. Nenhuma alteração de documento congelado sem Change Request; toda decisão seguiu a Hierarquia de Decisão já instituída. Achado já registrado (não novo): a citação "Capítulo 15" em vez de "Capítulo 14" (Política de Change Request) propagada em TCOS-019A/020/022 — reafirmado, não corrigido.

**Aderência ao Framework Oficial e ao Product & SaaS Strategy (TCOS-020):** confirmada — nenhum dos 4 documentos da Camada de Produto cria módulo, altera arquitetura ou contradiz o TCOS-020 v1.1.0 (mercado Austrália/Brasil já refletido consistentemente em TCOS-022 Capítulos 27–28 e citado corretamente em TCOS-023).

**Oportunidades reais identificadas, sem alterar arquitetura ou documento congelado (registradas como Backlog, não implementadas):**
- OE-CONT-01: os 2 achados de baixa severidade abertos (RC-021-01, citação Cap. 14/15) são de correção rápida e baixo risco — resolvê-los antes da próxima fase aumentaria a rastreabilidade percebida por um futuro investidor/auditor externo (Auditoria de Valuation, já um critério usado nesta Camada de Produto) a um custo muito baixo.
- OE-CONT-02: a Camada de Produto (TCOS-020–023) ainda não tem nenhuma representação visual — todo o conteúdo de Planos, Entitlements, Trial e Analytics existe apenas em texto. Uma vez retomada a construção das telas, valeria avaliar (mediante autorização futura) se alguma das 30 telas já previstas no TCOS-018 deveria refletir conceitos desta Camada (ex.: uma tela de "Administração da Assinatura", hoje não coberta pelas 30 telas de negócio do Blueprint) — registrado como oportunidade, não como pendência bloqueante.
- OE-CONT-03: o Backlog Estratégico do TCOS-020 (Capítulo 25) e o Backlog Técnico desta auditoria (achados RC-021-01, Cap.14/15) hoje vivem em documentos diferentes — consolidá-los em um único painel de rastreabilidade (dentro do próprio PROJECT_MEMORY) aumentaria a facilidade de acompanhamento, sem exigir nenhuma alteração de documento oficial.

### Recomendação de Próxima Fase

Avaliadas as opções sob os 7 critérios de prioridade do proprietário (valor para o cliente; receita recorrente; escalabilidade; diferenciação competitiva; facilidade de implementação futura; preparação para validação no mercado australiano; preparação para expansão internacional):

**Recomendação: retomar a construção visual das telas (Tela 05 em diante), começando pela resolução do Achado #1 já pendente da Tela 05 (Dashboard Estoque).** Justificativa: a Camada de Produto (TCOS-020–023) está agora conceitualmente completa e não gera valor adicional por si só sem um produto demonstrável; a validação no mercado australiano (critério 6, prioridade explícita do proprietário) depende de um produto visualmente navegável, não apenas de documentação estratégica; apenas 5 das 30 telas estão construídas. Retomar as telas atende diretamente aos critérios 1 (valor ao cliente), 3 (escalabilidade do padrão visual já estabelecido), 4 (diferenciação — identidade visual já é um Moat registrado no TCOS-020 Capítulo 29) e 6–7 (pré-requisito concreto para qualquer validação/expansão).

**Alternativa de menor prioridade, mas de baixo custo:** resolver os 2 achados administrativos abertos (RC-021-01 e citação Cap. 14/15) antes ou em paralelo às telas — não exige nova auditoria de abertura, apenas autorização pontual de correção já pré-analisada.

---

## CORREÇÃO — Botões e Modais Faltantes (TCOS-018, Capítulos 16–19; Telas 04 e 05)

**Status:** Correção executada dentro do escopo autorizado por `CORRIGIR`; aguardando confirmação final do proprietário antes de retomar a Tela 06
**Data:** 2026-08-02

Ao retomar a construção da Tela 06 (Dashboard Engenharia de Custos), a Auditoria de Abertura e a releitura direta da UX/UI Specification (§3.5 a §3.8) encontraram um achado real, não corrigido automaticamente: os Capítulos 16 (Produção), 17 (Estoque), 18 (Engenharia de Custos) e 19 (Eventos) do TCOS-018 omitiam integralmente os campos "Ações rápidas/Botões" e "Modais" exigidos por suas próprias fontes citadas — divergência do mesmo tipo já identificada e corrigida para o Capítulo 22 (Metas) durante a construção original do TCOS-018. O achado foi reportado ao proprietário antes de qualquer correção, que autorizou (`CORRIGIR`) o escopo mínimo abaixo.

### Decisões tomadas
- D-COR2-01: os campos "Ações rápidas" e "Modais" dos Capítulos 16–19 do TCOS-018 foram adicionados exatamente conforme definidos na UX/UI Specification (§3.5–§3.8), sem criar, remover ou reinterpretar nenhum requisito.
- D-COR2-02: as Telas 04 (Produção) e 05 (Estoque), já aprovadas, foram atualizadas para refletir os botões agora documentados — layout, grid, componentes, identidade visual, arquitetura, regras de negócio, fluxos, KPIs, nomenclaturas e comportamento já aprovado permaneceram integralmente preservados.
- D-COR2-03: identificado, durante a Auditoria de Regressão pré-edição, que o `.btn.primary` da Tela 04 estava escopado (corretamente) em Roxo-IA apenas para o botão "Aceitar" do widget de sugestão de IA — a correção usou um seletor mais específico (`.page-head .btn.primary`) para aplicar Brasa ao novo botão principal sem alterar em nada o componente de IA já aprovado.

### Alterações
- ALT-COR2-01: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018) — Capítulos 16, 17, 18 e 19, campos "Ações rápidas"/"Modal(is)" adicionados. Confirmado via `git diff` que apenas essas 4 seções foram tocadas (15 inserções, 1 remoção líquida) — nenhum outro capítulo do documento foi alterado.
- ALT-COR2-02: `mockup-dashboard-producao.html` (Tela 04, scratchpad, não versionado em Git) — adicionados botões "Planejar Produção", "Registrar Consumo Real", "Executar Produção" (primário, Brasa) no cabeçalho; nomes de Ficha Técnica na tabela convertidos em links (ação "Ver Ficha Técnica"). Nenhum outro elemento alterado.
- ALT-COR2-03: `mockup-dashboard-estoque.html` (Tela 05, scratchpad, não versionado em Git) — adicionados botões "Configurar Ponto de Reposição", "Registrar Descarte de Lote", "Realizar Inventário" (primário, Brasa) no cabeçalho. Nenhum outro elemento alterado; a correção do Achado #1 (borda/valor vermelho) permanece intacta.

### Melhorias sugeridas (Backlog)
- Nenhuma nova.

### Riscos encontrados
- Nenhum risco novo. Confirmado que a divergência encontrada não afeta nenhuma Regra de Negócio, Fluxo ou decisão arquitetural — apenas completude de representação visual já exigida pela documentação existente.

### Pendências
- Achados administrativos já registrados (RC-021-01; citação Cap. 14/15 da Constituição) permanecem pendentes, sem relação com esta correção.

**Confirmação de auditoria (executada antes e depois da correção):** Auditoria de Regressão pré-edição confirmou que "Botão" e "Modal" já são categorias oficiais da Biblioteca Visual (TCOS-018, Capítulo 25, itens 25.3/25.5, base UX/UI Spec §5.6/§5.8) e que os códigos F-020, F-034, F-053, F-054, F-056 citados existem exatamente com esse conteúdo na Functional Specification — nenhum componente ou funcionalidade nova foi criado. Auditoria Executiva Completa pós-correção confirmou, por re-renderização e inspeção visual das Telas 04 e 05, que nenhum componente pré-existente sofreu regressão (o botão "Aceitar" do widget de IA permanece Roxo-IA; o Card corrigido do Achado #1 na Tela 05 permanece sem a variante vermelha; grid, sidebar, KPIs, gráficos, tabelas e navegação permanecem idênticos). Confirmado via `git status`/`git diff` que apenas o `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` foi alterado entre os documentos oficiais — nenhum outro documento oficial congelado foi tocado.

---

## CORREÇÃO — Widget de IA, Alertas, Notificações e Estados Faltantes (TCOS-018, Capítulo 18)

**Status:** Correção documental executada dentro do escopo autorizado por `CORRIGIR`; Tela 06 ainda não construída, aguardando nova autorização
**Data:** 2026-08-02

Durante a Auditoria de Abertura para a Tela 06 (Dashboard Engenharia de Custos), a comparação linha por linha entre o TCOS-018 (Capítulo 18) e a UX/UI Specification (§3.7) — já reler diretamente, não por memória — encontrou 4 novas categorias ausentes, distintas das já corrigidas (Botões/Modais): Widget de IA (sugestão de preço, F-070), Alertas (RN-018/RN-019), Notificações e Estados da interface ("custo parcial"). O achado foi reportado antes de qualquer correção; o proprietário autorizou (`CORRIGIR`) o escopo mínimo abaixo, restrito exclusivamente ao Capítulo 18.

### Decisões tomadas
- D-COR3-01: os 4 elementos ausentes foram adicionados ao Capítulo 18 exatamente conforme literal da UX/UI Specification §3.7 (itens 16, 17, 23, e parágrafo de Integração com IA) — nenhuma reinterpretação.
- D-COR3-02: "links de drill-down" (item 19 da §3.7, "Fluxo de navegação") foi avaliado e **não adicionado como campo novo** — confirmado que nenhum capítulo de Dashboard do TCOS-018 (13 a 23) usa esse campo como seção própria, sendo a navegação já coberta pela estrutura de menu lateral (Capítulos 5 e 9 do próprio TCOS-018); portanto não é uma omissão real, apenas uma convenção editorial já consistente em todo o documento.
- D-COR3-03: o Widget de IA foi redigido espelhando exatamente o padrão já usado no Capítulo 16 ("sugestão de previsão de demanda por IA"), trocando apenas o código de Funcionalidade (F-070 em vez de F-069) e o conteúdo (sugestão de preço em vez de previsão de demanda) — nenhum padrão visual novo.

### Alterações
- ALT-COR3-01: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018) — Capítulo 18: adicionados "Widget especial" (após Gráfico), "Alertas", "Notificações" e "Estados da interface" (após Modal, antes de Comportamento esperado). Confirmado via `git diff` que apenas o Capítulo 18 foi tocado (8 inserções, 0 remoções) — Capítulos 16, 17 e 19 permanecem exatamente como corrigidos na etapa anterior, sem nenhuma alteração adicional.

### Melhorias sugeridas (Backlog)
- Avaliar, em fase futura, se os Capítulos 16, 17 e 19 do TCOS-018 também têm lacunas de Widget de IA/Alertas/Notificações/Estados frente às suas respectivas fontes (§3.5, §3.6, §3.8) — sinalizado, não verificado, para evitar repetir o ciclo achado-correção tela a tela.

### Riscos encontrados
- Nenhum risco novo. Confirmado que a correção não afeta nenhuma Regra de Negócio, Fluxo, Funcionalidade ou decisão arquitetural — apenas completude de representação visual já exigida pela UX/UI Specification.

### Pendências
- Construção da Tela 06 permanece pendente de nova autorização explícita do proprietário.
- Avaliação futura dos Capítulos 16, 17 e 19 (ver Backlog acima).
- Achados administrativos já registrados (RC-021-01; citação Cap. 14/15 da Constituição) permanecem pendentes, sem relação com esta correção.

**Confirmação de auditoria:** confirmado, antes da edição, que os 4 itens (Widget de IA/F-070, Alertas/RN-018/RN-019, Notificações, Estados) existem literalmente na UX/UI Specification §3.7. Confirmado, depois da edição, via `git diff`, que apenas o Capítulo 18 foi alterado; verificação programática confirmou os 28 capítulos do TCOS-018 permanecem sequenciais sem lacuna; busca confirmou que os códigos F-070, RN-018 e RN-019 citados existem exatamente como referenciados na Functional Specification e na Business Rules Specification, sem nenhuma alteração a esses documentos. Nenhum outro documento oficial congelado foi tocado.

---

## FASE — Tela 06 (Dashboard Engenharia de Custos) construída e apresentada

**Status:** Construída e apresentada, aguardando aprovação do proprietário
**Data:** 2026-08-02

Executada a Auditoria de Abertura final (nenhuma nova divergência objetiva encontrada entre TCOS-018 Capítulo 18, já corrigido, e a UX/UI Specification §3.7) e construído o mockup de alta fidelidade da Tela 06 — 6º Dashboard do sistema, reutilizando integralmente a Biblioteca Visual Oficial e os padrões já estabelecidos pelas Telas 01–05.

### Decisões tomadas
- D-T06-01: layout segue o precedente da Tela 04 (mesma Área "Produção" na barra lateral, mesmo padrão de cabeçalho/botões) — Cards de KPI, gráfico de barras (Custo previsto × real), Widget de IA (sugestão de preço, F-070), Tabela de Fichas Técnicas com Badge de status, botão "Ver Detalhamento de Custo do Evento".
- D-T06-02 (autocorreção antes da apresentação): inicialmente incluí um "Banner de alerta persistente" para os Alertas RN-018/RN-019 (mesmo componente visual do Dashboard CEO). Ao auditar a Biblioteca Visual (TCOS-018, Capítulo 25, item 9 da tabela mestra, e Capítulo 25.14 — Feedback Visual), confirmei que este componente é catalogado com "onde já aparece: Dashboard CEO (RN-047), Administração" — nenhum outro Dashboard o utiliza para outro Alerta até o momento. Diante da ambiguidade sobre se essa lista é exaustiva ou apenas descritiva, optei pela leitura mais conservadora (consistente com a regra "não criar novos padrões visuais" e com o histórico desta sessão de nunca expandir o uso de um componente sem precedente claro), removendo o banner antes da apresentação. Os Alertas RN-018/RN-019 permanecem documentados no TCOS-018 (Capítulo 18), mas sem representação visual nesta tela, até uma decisão explícita do proprietário sobre o padrão visual de Alertas não-RN-047.

### Alterações
- ALT-T06-01: criados `mockup-dashboard-engenharia-custos.html` e `shot6.js` (scratchpad, não versionados em Git); gerado `dashboard-engenharia-custos.png`. Nenhum documento oficial foi alterado nesta etapa.

### Melhorias sugeridas (Backlog)
- OE-T06-01: definir, em fase futura (Revisão Global de UX/UI ou extensão da Biblioteca Visual), um padrão visual oficial para Alertas específicos de Dashboard que não sejam RN-047 — hoje só existe o padrão restrito ao Dashboard CEO/Administração. Sem essa definição, todo Dashboard com "Alertas" documentados no TCOS-018 (ex.: Produção RN-029, Estoque RN-033/034, Engenharia de Custos RN-018/019, Eventos RN-006/007) ficará sem representação visual até essa decisão ser tomada.

### Riscos encontrados
- Nenhum risco novo de arquitetura.

### Pendências
- Aprovação do proprietário sobre a Tela 06.
- OE-T06-01 (ver Backlog acima) — decisão futura sobre padrão visual de Alertas não-RN-047.
- Pendências já registradas (RC-021-01; citação Cap. 14/15; avaliação futura dos Capítulos 16/17/19) permanecem, sem alteração.

**Confirmação de auditoria (Executiva Completa, Consistência, UX/UI, Regressão, Rastreabilidade):** confirmado que todos os componentes usados (Card de KPI, gráfico de barras, Badge/pill, Botão primário/secundário, Widget de sugestão de IA) já são oficiais na Biblioteca Visual, sem nenhum componente novo criado; confirmado que o conteúdo (KPIs, Tabela, Filtros, Ações rápidas, Widget) corresponde palavra por palavra ao TCOS-018 Capítulo 18 e à UX/UI Specification §3.7; confirmado, por inspeção direta do CSS, que grid, cores, tipografia, raios e sombras são idênticos aos já usados nas Telas 01–05, incluindo a correção de especificidade do botão primário (Brasa) sem alterar o widget de IA (Roxo-IA); confirmado que nenhum módulo, Serviço, regra de negócio ou documento oficial foi alterado nesta etapa — apenas o `PROJECT_MEMORY.md`.

**Aprovação:** a Tela 06 foi aprovada integralmente pelo proprietário (comando `APROVADO`), incluindo a decisão conservadora de remover o Banner de alerta persistente. 3 observações de melhoria futura, não bloqueantes, foram registradas por ele: (a) componente visual específico para Alertas Operacionais, distinto do padrão RN-047 — mesmo tema de OE-T06-01, já registrado; (b) avaliar hierarquia visual da tabela de Fichas Técnicas para maior volume de registros; (c) avaliar indicadores de tendência (↑ ↓ =) nos KPIs de custo/margem. Todas roteadas ao Backlog da Revisão Global de UX/UI, sem alterar a baseline aprovada.

---

## CORREÇÃO — Alertas, Notificações e Estados Faltantes (TCOS-018, Capítulo 19)

**Status:** Correção documental executada dentro do escopo autorizado por `CORRIGIR`; Tela 07 a ser construída na sequência
**Data:** 2026-08-02

Ao iniciar a Auditoria de Abertura da Tela 07 (Dashboard Eventos), a comparação linha por linha entre o TCOS-018 (Capítulo 19, já com Botões/Modais corrigidos) e a UX/UI Specification (§3.8) confirmou a suspeita já registrada no Backlog após a correção do Capítulo 18: o mesmo padrão de lacuna (Alertas/Notificações/Estados) também afetava o Capítulo 19 — sem Widget de IA, que a própria §3.8 confirma não se aplicar a este Dashboard. O achado foi reportado antes de qualquer correção; o proprietário autorizou (`CORRIGIR`) o escopo mínimo abaixo, restrito exclusivamente ao Capítulo 19.

### Decisões tomadas
- D-COR4-01: adicionados ao Capítulo 19 os campos Alertas (RN-006, margem mínima, RN-007), Notificações (Evento confirmado/concluído) e Estados da interface (5 estados do ciclo de vida do Evento com suas cores oficiais), exatamente conforme literal da UX/UI Specification §3.8 — nenhuma reinterpretação.
- D-COR4-02: os 5 Estados da interface agora documentados ("Prospectado" cinza, "Confirmado" Brasa, "Em execução" azul, "Concluído" verde, "Cancelado" vermelho riscado) são a base de cor obrigatória para o calendário da Tela 07 — sem essa definição, a cor do calendário teria sido inventada; a correção elimina esse risco antes da construção.

### Alterações
- ALT-COR4-01: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018) — Capítulo 19: adicionados "Alertas", "Notificações" e "Estados da interface" (após Modais, antes de Comportamento esperado). Confirmado via `git diff` que apenas o Capítulo 19 foi tocado (6 inserções, 0 remoções) — nenhum outro capítulo alterado; verificação programática confirmou os 28 capítulos permanecem sequenciais; RN-006 e RN-007 existem exatamente como citados na Business Rules Specification, sem alteração.

### Melhorias sugeridas (Backlog)
- Com a correção dos Capítulos 16, 17, 18 e 19, resta avaliar se os demais 7 Dashboards (13, 14, 15, 20, 21, 22, 23) têm as mesmas categorias já completas — indício forte de que sim, já que todos já incluíam Ações rápidas/Botões corretamente desde a auditoria original; não verificado exaustivamente para Alertas/Notificações/Estados nesta fase.

### Riscos encontrados
- Nenhum risco novo de arquitetura.

### Pendências
- Construção da Tela 07 prossegue imediatamente, conforme autorizado.
- Pendências já registradas (RC-021-01; citação Cap. 14/15; OE-T06-01) permanecem, sem alteração.

**Confirmação de auditoria:** confirmado, antes da edição, que os 3 itens autorizados existem literalmente na UX/UI Specification §3.8. Confirmado, depois da edição, via `git diff`, que apenas o Capítulo 19 foi alterado; nenhuma Regra de Negócio, Fluxo, Funcionalidade ou decisão arquitetural foi modificada; nenhum outro documento oficial congelado foi tocado.

---

## CORREÇÃO — Contradição TCOS-005 × TCOS-019A ("Em execução" azul → Âmbar-Atenção)

**Status:** CONCLUÍDA E APROVADA PELO PROPRIETÁRIO (comando `CORRIGIR`, escopo fechado, decisão de cor definida por ele)
**Data:** 2026-08-02

Ao aplicar os Estados da interface do Capítulo 19 (recém-corrigido) para construir o calendário da Tela 07, identifiquei uma contradição real entre a UX/UI Specification (TCOS-005 §3.8, item 23 — "Em execução" definido como "azul") e a Identidade Visual Oficial (TCOS-019A, Capítulo 5 — Paleta Oficial, já congelada), que reserva **qualquer tom frio exclusivamente para conteúdo de IA** (Roxo-IA como única exceção fria, "nunca azul" na paleta). O achado foi apresentado antes de qualquer correção; o proprietário decidiu oficialmente que "Em execução" passa a usar **Âmbar-Atenção**, e autorizou (`CORRIGIR`) a correção pontual do TCOS-005.

### Decisões tomadas
- D-COR5-01 (decisão oficial do proprietário): o estado "Em execução" do ciclo de vida do Evento é definido oficialmente como **Âmbar-Atenção** — nunca azul. Nenhuma cor nova foi criada; nenhuma categoria da Paleta Oficial (7 categorias) foi expandida.
- D-COR5-02: os 5 Estados da interface do Dashboard Eventos ficam definidos oficialmente como: Prospectado → Cinza-claro; Confirmado → Brasa; Em execução → Âmbar-Atenção; Concluído → Verde-sucesso; Cancelado → Vermelho-crítico (riscado).

### Alterações
- ALT-COR5-01: `THE_CHARCOAL_OS_UX_UI_SPECIFICATION.md` (TCOS-005), §3.8, item 23 — "Em execução (azul)" substituído por "Em execução (Âmbar-Atenção)". Confirmado via `git diff` que apenas essa linha foi alterada (1 inserção, 1 remoção) — nenhum outro trecho do documento tocado. TCOS-018 e TCOS-019A permanecem intocados, conforme exigido.

### Achado adicional, encontrado durante a Auditoria de Regressão, NÃO corrigido (fora do escopo autorizado)
- Busca por "azul" em todo o TCOS-005, executada como parte da Auditoria de Regressão, encontrou **1 ocorrência remanescente**: §3.15 Orçamentos (Módulo 08), item 23 — *"Estados da interface: cores por status (Rascunho cinza, **Enviado azul**, Aceito verde, Recusado vermelho, Expirado cinza-claro)."* Mesma contradição com o TCOS-019A ("nunca azul"), desta vez para o estado "Enviado" de Orçamento. Não corrigido — fora do escopo desta autorização, que era restrita a "não alterar qualquer outro trecho do TCOS-005". Nenhuma tela de Orçamentos foi construída ainda, então este achado não afeta nenhum mockup existente — registrado para correção quando a Tela de Orçamentos (fora da sequência dos 11 Dashboards, telas operacionais) for iniciada, ou antecipadamente, mediante autorização específica do proprietário.

### Riscos encontrados
- Nenhum risco novo de arquitetura. Risco de produto/design: outras seções do TCOS-005 não verificadas linha a linha para esta mesma contradição além da busca textual por "azul" já executada (que é exaustiva para a palavra exata, mas não cobre eventuais sinônimos ou referências indiretas a tons frios).

### Pendências
- Achado de §3.15 Orçamentos (Enviado, azul) — aguardando autorização específica para correção, quando a tela correspondente for iniciada.
- Construção da Tela 07 prossegue imediatamente, com os 5 Estados oficiais já definidos.
- Pendências já registradas (RC-021-01; citação Cap. 14/15; OE-T06-01) permanecem, sem alteração.

**Confirmação de auditoria (Regressão completa):** confirmado via `git diff` que apenas 1 linha do TCOS-005 foi alterada; confirmado via `git status` que TCOS-018 e TCOS-019A não foram tocados; confirmado que a Paleta Oficial (7 categorias) permanece exatamente a mesma, sem adição ou remoção de categoria; confirmado que a semântica de cores (tom frio exclusivo para IA) permanece consistente após a correção; busca por "azul" em todo o TCOS-005 confirmou exatamente 1 ocorrência remanescente (§3.15), registrada como achado novo, não corrigida.

---

## FASE — Tela 07 (Dashboard Eventos) construída e apresentada

**Status:** Construída e apresentada, aguardando aprovação do proprietário
**Data:** 2026-08-02

Construído o mockup de alta fidelidade da Tela 07 — 7º Dashboard do sistema — imediatamente após a correção da contradição TCOS-005×TCOS-019A, já usando oficialmente os 5 Estados definidos pelo proprietário (Prospectado/Cinza-claro, Confirmado/Brasa, Em execução/Âmbar-Atenção, Concluído/Verde-sucesso, Cancelado/Vermelho-crítico riscado).

### Decisões tomadas
- D-T07-01: layout segue o precedente das Telas 04–06 (mesmo padrão de cabeçalho/botões); Área "Eventos / Operações" da barra lateral, com único módulo (Eventos), renderizada expandida por consistência estrutural com as demais Áreas ativas, mesmo contendo apenas 1 item.
- D-T07-02: calendário e tabela reutilizam integralmente o componente Badge/pill já oficial, aplicando as 5 cores exatamente como recém-definidas — nenhuma cor nova, nenhum componente novo.
- D-T07-03: nomes de Evento na tabela convertidos em links (Brasa-dark), mesmo padrão já usado nas Telas 04/06, para representar a ação "Ver Orçamento/Contrato vinculado" (UX/UI §3.8) sem restruturar a tabela.

### Alterações
- ALT-T07-01: criados `mockup-dashboard-eventos.html` e `shot7.js` (scratchpad, não versionados em Git); gerado `dashboard-eventos.png`. Nenhum documento oficial foi alterado nesta etapa.

### Melhorias sugeridas (Backlog)
- Nenhuma nova além das já registradas (OE-T06-01, achado §3.15 Orçamentos).

### Riscos encontrados
- Nenhum risco novo.

### Pendências
- Aprovação do proprietário sobre a Tela 07.
- Achado §3.15 Orçamentos (Enviado, azul) e OE-T06-01 permanecem, sem alteração.

**Confirmação de auditoria (Executiva Completa, Consistência, UX/UI, Regressão, Rastreabilidade):** confirmado que todos os componentes (Card de KPI, calendário, Badge/pill, Botão primário/secundário, tabela) já são oficiais na Biblioteca Visual; confirmado que o conteúdo corresponde palavra por palavra ao TCOS-018 Capítulo 19 e à UX/UI Specification §3.8 (já corrigida); confirmado que as 5 cores de estado usadas são exatamente as 5 categorias já oficiais da Paleta (nenhuma cor inventada); confirmado, por inspeção visual, que "Confirmado" (Brasa) e "Cancelado" (Vermelho-crítico, riscado) permanecem distinguíveis apesar da proximidade tonal, graças ao riscado já exigido pela especificação; confirmado que grid, sidebar, topbar e paleta são idênticos às Telas 01–06; confirmado que nenhum módulo, Serviço, regra de negócio ou documento oficial foi alterado nesta etapa — apenas o `PROJECT_MEMORY.md`.

---

## CORREÇÃO — Ação Rápida, Alertas e Estados Faltantes (TCOS-018, Capítulo 20)

**Status:** CONCLUÍDA E APROVADA PELO PROPRIETÁRIO (comando `APROVADO`, escopo fechado)
**Data:** 2026-08-02

Ao auditar a Tela 08 (Dashboard CRM) antes da construção, a comparação linha por linha entre o TCOS-018 (Capítulo 20) e a UX/UI Specification (§3.9) encontrou duas categorias de achado: (1) a Ação rápida documentada ("Novo Lead") divergia da fonte, que define este Dashboard como **somente navegação** ("Ir para Leads"/"Ir para Clientes"), sem ação de criação própria — a própria §3.9 confirma "nenhum [modal] próprio — ações de criação ocorrem nas telas de Leads/Clientes"; (2) Alertas (Lead inativo, RN-011) e Estados da interface (normal/vazio) ausentes, mesmo padrão já visto nos Capítulos 18/19. Ambos reportados antes de qualquer correção; o proprietário autorizou (`APROVADO`, com escopo já definido no prompt de aprovação) a correção pontual abaixo.

### Decisões tomadas
- D-COR6-01: a Ação rápida do Capítulo 20 foi corrigida para "Ir para Leads"/"Ir para Clientes", eliminando a referência a uma ação de criação ("Novo Lead") que a própria fonte nega a este Dashboard.
- D-COR6-02: Alertas (RN-011) e Estados da interface (normal/vazio) adicionados exatamente conforme §3.9.

### Alterações
- ALT-COR6-01: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018), Capítulo 20 — Ação rápida corrigida; Alertas e Estados da interface adicionados. Confirmado via `git diff` que apenas o Capítulo 20 foi tocado (5 inserções, 1 remoção) — nenhum outro capítulo alterado; verificação programática confirmou os 28 capítulos permanecem sequenciais; RN-011 existe exatamente como citado.

### Achado adicional, encontrado durante esta auditoria, NÃO corrigido (fora do escopo desta autorização)
- O **Capítulo 19** (Dashboard Eventos), corrigido em etapa anterior a esta sessão, ainda contém o texto literal **"Em execução" (azul)** em seu campo "Estados da interface" — resíduo da correção original, aplicada *antes* da decisão do proprietário de substituir "azul" por "Âmbar-Atenção" no TCOS-005. Naquela ocasião, a autorização foi explícita em "não alterar TCOS-018", então o Capítulo 19 não foi atualizado. Resultado: o TCOS-018 Capítulo 19 está hoje **desatualizado frente ao TCOS-005 (já corrigido) e frente à própria Tela 07 (já aprovada e construída corretamente com Âmbar-Atenção)**. Não corrigido nesta fase — fora do escopo da autorização atual, que era restrita ao Capítulo 20. Recomenda-se `CORRIGIR` pontual do TCOS-018 Capítulo 19 para alinhar o texto à decisão já oficial.

### Riscos encontrados
- Nenhum risco novo de arquitetura.

### Pendências
- Correção pendente do TCOS-018 Capítulo 19 ("azul" → "Âmbar-Atenção") — aguardando autorização específica.
- Achado §3.15 Orçamentos (Enviado, azul), OE-T06-01 permanecem, sem alteração.
- Nova Auditoria de Abertura da Tela 08 a ser executada antes da construção, conforme instruído.

**Confirmação de auditoria:** confirmado, antes da edição, que os itens autorizados existem literalmente na UX/UI Specification §3.9. Confirmado, depois da edição, via `git diff`, que apenas o Capítulo 20 foi alterado; nenhuma Regra de Negócio, Fluxo, Funcionalidade ou decisão arquitetural foi modificada; nenhum outro documento oficial congelado foi tocado.

---

## FASE — Tela 08 (Dashboard CRM) construída e apresentada

**Status:** Construída e apresentada, aguardando aprovação do proprietário
**Data:** 2026-08-02

Reiniciada a Auditoria de Abertura da Tela 08 após a correção do Capítulo 20: releitura confirmou que o Capítulo 20 (já corrigido) corresponde integralmente à UX/UI Specification §3.9 — nenhum novo achado. Construído o mockup de alta fidelidade — 8º Dashboard do sistema, primeiro a usar o gráfico tipo "funil", já catalogado (TCOS-018 Cap. 25.20; TCOS-019A Cap. 13 — exceção autorizada, junto ao calendário, à regra de no máximo 2 cores por gráfico).

### Decisões tomadas
- D-T08-01: funil comercial (Lead → Qualificação → Conversão → Contrato) renderizado com opacidade decrescente de Brasa (100%/80%/60%/40%) — não a "paleta semântica completa" mencionada no TCOS-019A Cap. 13 como alternativa para o funil, pois os 4 estágios representam progressão sequencial de um único funil, não estados distintos de severidade (diferente do calendário, que usa a paleta semântica porque representa estados de ciclo de vida). **[Inferência visual]**, por não haver exemplo de funil já construído em nenhuma tela anterior para servir de precedente direto.
- D-T08-02 **[Inferência visual]**: rótulos de severidade da tabela "Leads que exigem atenção" ("Atenção"/"Inativo") e sua graduação de cor (Âmbar/Vermelho-crítico por tempo de inatividade) não são especificados literalmente pela UX/UI Specification (que só define o Alerta "Lead inativo há X dias", RN-011, sem texto de Badge nem limiar) — inferência necessária para renderizar a tabela, rastreável à RN-011.

### Alterações
- ALT-T08-01: criados `mockup-dashboard-crm.html` e `shot8.js` (scratchpad, não versionados em Git); gerado `dashboard-crm.png`. Nenhum documento oficial foi alterado nesta etapa.

### Melhorias sugeridas (Backlog)
- Nenhuma nova além das já registradas (correção pendente Cap. 19 "azul"; achado §3.15 Orçamentos; OE-T06-01).

### Riscos encontrados
- Nenhum risco novo.

### Pendências
- Aprovação do proprietário sobre a Tela 08.
- Correção pendente do TCOS-018 Capítulo 19 ("azul" → "Âmbar-Atenção"), achado §3.15 Orçamentos e OE-T06-01 permanecem, sem alteração.

**Confirmação de auditoria (Executiva Completa, Consistência, UX/UI, Regressão, Rastreabilidade):** confirmado que o funil e o gráfico de barras usam exclusivamente cores já oficiais (Brasa em opacidade decrescente, conforme autorizado pelo TCOS-019A para este tipo específico de gráfico); confirmado que o conteúdo (KPIs, Funil, Gráfico, Tabela, Ações rápidas, Filtros) corresponde ao TCOS-018 Capítulo 20 (já corrigido) e à UX/UI Specification §3.9; confirmado que a sidebar reflete exatamente o agrupamento oficial (Comercial/CRM: 04 CRM, 05 Clientes, 06 Leads, 08 Orçamentos); confirmado que grid, topbar e paleta são idênticos às Telas 01–07; confirmado que nenhum módulo, Serviço, regra de negócio ou documento oficial foi alterado nesta etapa — apenas o `PROJECT_MEMORY.md`.

**Aprovação:** a Tela 08 (Dashboard CRM) foi aprovada integralmente pelo proprietário (comando `APROVADO`) e passa a integrar oficialmente o conjunto de referências visuais aprovadas do THE CHARCOAL OS, ao lado das Telas 01–07.

---

## CORREÇÃO — Ações Rápidas, Modal, Widget, Notificações e Estados Faltantes (TCOS-018, Capítulo 21)

**Status:** CONCLUÍDA E APROVADA PELO PROPRIETÁRIO (comando `CORRIGIR`, escopo fechado)
**Data:** 2026-08-02

Ao iniciar a Auditoria de Abertura da Tela 09 (Dashboard Marketing), a comparação linha por linha entre o TCOS-018 (Capítulo 21) e a UX/UI Specification (§3.4) encontrou o achado mais extenso desta sequência: Ações rápidas incompletas (faltavam "Encerrar Campanha" e "Ver Leads desta Campanha"), Modal "Nova Campanha" ausente, Widget secundário de consolidação de Alertas de Leads inativos (RN-011) ausente, Notificações ausentes, Estados da interface ausentes. Reportado antes de qualquer correção; o proprietário autorizou (`CORRIGIR`) o escopo exato abaixo.

### Decisões tomadas
- D-COR7-01: Ações rápidas completadas com "Encerrar Campanha" e "Ver Leads desta Campanha", exatamente conforme §3.4.
- D-COR7-02: Modal "Nova Campanha" (nome, canal, período, objetivo, investimento) adicionado, exatamente conforme §3.4.
- D-COR7-03: Widget secundário de consolidação de Alertas de Leads inativos (RN-011) adicionado — explicitamente reutilizando o mesmo dado já exposto no Dashboard CRM (Capítulo 20), nunca recalculado ou duplicado com lógica divergente (PF-03), conforme já era a prática documentada no "Comportamento esperado" original deste mesmo capítulo.
- D-COR7-04: Notificações ("Campanha encerrada com sucesso") e Estados da interface (vazio/normal) adicionados, exatamente conforme §3.4.

### Alterações
- ALT-COR7-01: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018), Capítulo 21 — Ações rápidas completadas; Modal, Widget secundário, Notificações e Estados da interface adicionados. Confirmado via `git diff` que apenas o Capítulo 21 foi tocado (9 inserções, 1 remoção) — nenhum outro capítulo alterado; verificação programática confirmou os 28 capítulos permanecem sequenciais; RN-011 e F-065/066/067 existem exatamente como citados, sem alteração a esses documentos.

### Melhorias sugeridas (Backlog)
- Nenhuma nova além das já registradas (correção pendente Cap. 19 "azul"; achado §3.15 Orçamentos; OE-T06-01).

### Riscos encontrados
- Nenhum risco novo de arquitetura.

### Pendências
- Nova Auditoria de Abertura da Tela 09 a ser executada antes da construção, conforme protocolo.
- Correção pendente do TCOS-018 Capítulo 19 ("azul" → "Âmbar-Atenção"), achado §3.15 Orçamentos e OE-T06-01 permanecem, sem alteração.

**Confirmação de auditoria:** confirmado, antes da edição, que todos os itens autorizados existem literalmente na UX/UI Specification §3.4. Confirmado, depois da edição, via `git diff`, que apenas o Capítulo 21 foi alterado; validadas as referências cruzadas (RN-011, F-065, F-066, F-067) — todas íntegras e sem alteração em seus documentos de origem; nenhuma Regra de Negócio, Fluxo, Funcionalidade ou decisão arquitetural foi modificada; nenhum outro documento oficial congelado foi tocado.

---

## FASE — Tela 09 (Dashboard Marketing) construída e apresentada

**Status:** Construída e apresentada, aguardando aprovação do proprietário
**Data:** 2026-08-02

Reiniciada a Auditoria de Abertura da Tela 09: releitura linha por linha do TCOS-018 Capítulo 21 (já corrigido), UX/UI Specification §3.4, Functional Specification (F-065/066/067) e Business Rules (RN-011) confirmou cobertura completa — nenhuma nova divergência objetiva encontrada. Construído o mockup de alta fidelidade — 9º Dashboard do sistema.

### Decisões tomadas
- D-T09-01 **[Inferência visual]**: o "Widget secundário" de consolidação de Alertas de Leads inativos (RN-011), sem precedente visual em nenhum documento, foi renderizado como painel compacto em tom Âmbar-atenção — deliberadamente distinto do Banner de alerta persistente (reservado a RN-047) e do Widget de sugestão de IA (reservado a conteúdo de IA, Roxo-IA) — evitando expandir o uso de qualquer um dos dois componentes já escopados.
- D-T09-02 **[Inferência visual, simplificação assumida]**: a ação "Ver Leads desta Campanha" foi representada através do próprio nome da Campanha como link (mesmo padrão já usado nas Telas 04/06/07/08), em vez de um link textual separado — simplificação para manter a tabela consistente com o padrão de 1 link por linha já estabelecido, sem adicionar uma coluna de ação nova.
- D-T09-03: KPI-row com 4 Cards (não 3, como na maioria dos outros Dashboards) — grid ajustado para `repeat(4,1fr)`, mantendo o mesmo componente Card de KPI já oficial, sem alteração de estrutura.

### Alterações
- ALT-T09-01: criados `mockup-dashboard-marketing.html` e `shot9.js` (scratchpad, não versionados em Git); gerado `dashboard-marketing.png`. Nenhum documento oficial foi alterado nesta etapa.

### Autocorreções durante as auditorias finais
- Nenhuma necessária — a construção não apresentou nenhum problema de layout (ex.: quebra de botão) desta vez, diferente da Tela 06.

### Melhorias sugeridas (Backlog)
- Nenhuma nova além das já registradas (correção pendente Cap. 19 "azul"; achado §3.15 Orçamentos; OE-T06-01).

### Riscos encontrados
- Nenhum risco novo.

### Pendências
- Aprovação do proprietário sobre a Tela 09.
- Correção pendente do TCOS-018 Capítulo 19 ("azul" → "Âmbar-Atenção"), achado §3.15 Orçamentos e OE-T06-01 permanecem, sem alteração.

**Confirmação de auditoria (Executiva Completa, Consistência, UX/UI, Regressão, Rastreabilidade):** confirmado que todos os componentes (Card de KPI, gráfico de barras, Badge/pill, Botão primário/secundário, painel de widget) já são oficiais ou são aplicações mínimas e rastreáveis de padrões já oficiais; confirmado que o conteúdo (KPIs, Gráfico, Widget, Tabela, Ações rápidas, Filtros) corresponde ao TCOS-018 Capítulo 21 (já corrigido) e à UX/UI Specification §3.4; confirmado que a sidebar reflete o agrupamento oficial (Marketing: Módulo 21, único); confirmado que grid, topbar e paleta são idênticos às Telas 01–08; confirmado que nenhum módulo, Serviço, regra de negócio ou documento oficial foi alterado nesta etapa — apenas o `PROJECT_MEMORY.md`.

---

## FASE — Auditoria de UX/UI de Excelência da Tela 09 (Dashboard Marketing) — Aprovada

**Status:** CONCLUÍDA E APROVADA PELO PROPRIETÁRIO (comando `APROVADO`)
**Data:** 2026-08-02

Executada, a pedido do proprietário, uma Auditoria de UX/UI de Excelência sobre a Tela 09 já concluída, buscando oportunidades reais de melhoria de percepção de qualidade, sem alterar nenhuma regra de negócio, documento oficial ou funcionalidade já aprovada. A auditoria cobriu UX, UI, Produto SaaS, Consistência, Acessibilidade, Escalabilidade Visual, Microinterações, Navegação, Produtividade e Valor Percebido, evitando repetir observações genéricas já registradas no backlog padrão da Revisão Global de UX/UI.

### Resultado da auditoria
Recomendação final: **APROVAR COM MELHORIAS RECOMENDADAS**.

Pontuação (0–10): UX 8.0 · UI 8.5 · Produto 8.0 · Consistência 9.0 · Escalabilidade Visual 8.5 · Qualidade Enterprise 8.0 · Prontidão mercado brasileiro 9.0 · Prontidão mercado australiano 4.0 (localização de moeda/idioma ainda não endereçada — decisão técnica futura, TCOS-017/TCOS-022 Cap. 27, corretamente fora de escopo visual nesta fase).

### Backlog Oficial de UX/UI — Tela 09 (Dashboard Marketing)

Prioridade **Médio**:
1. OE-T09-01 — Widget de Leads Inativos sem ação direta (nenhum link/botão para agir sobre o lead a partir do próprio widget).
2. OE-T09-02 — Desequilíbrio de altura entre os painéis do row2 (gráfico de barras x widget de leads inativos).
3. OE-T09-03 — Gráfico de barras (canais de aquisição) sem rótulos de valor.

Prioridade **Baixo**:
4. OE-T09-04 — Ausência de diferenciação de urgência (graduação de cor) no Widget de Leads Inativos — **mesmo risco já identificado e revertido no Achado #1 da Tela 05; não implementar sem nova autorização explícita.**
5. OE-T09-05 — Redundância do rótulo "Marketing" repetido (área expandida + único item de submenu) na sidebar.

Observação estratégica (sem ação recomendada nesta fase):
6. OE-T09-06 — Localização de moeda/idioma para o mercado australiano ainda pendente (score 4.0/10); tratamento é decisão técnica futura, fora do escopo desta auditoria visual.

### Determinações do proprietário (comando `APROVADO`)
- Todas as oportunidades acima são registradas exclusivamente como Backlog Oficial de UX/UI, preservando a prioridade Médio → Baixo, **sem implementação nesta fase**.
- Nenhuma melhoria será aplicada isoladamente, para evitar inconsistência entre as telas já aprovadas e congeladas.
- Estas oportunidades serão consolidadas, junto ao backlog acumulado das Telas 04–09, para uma futura **Revisão Global de UX/UI**, a ser executada somente após a conclusão de 100% das 30 telas oficiais.
- Princípio reafirmado: primeiro concluir integralmente a arquitetura visual; somente depois executar um ciclo único de refinamento premium, simultâneo, em todas as telas.
- **Nenhuma alteração visual foi aplicada nesta etapa** — nem ao `mockup-dashboard-marketing.html`, nem a qualquer outro mockup, nem a qualquer documento oficial (TCOS-018, TCOS-005 ou qualquer outro).
- A Tela 09 (Dashboard Marketing) permanece oficialmente **aprovada e congelada** como referência visual desta fase, ao lado das Telas 01–08.

### Alterações
- Nenhuma. Apenas este registro em `PROJECT_MEMORY.md`.

### Riscos encontrados
- Nenhum risco novo de arquitetura, regra de negócio ou documento oficial.

### Pendências
- Backlog Oficial de UX/UI da Tela 09 (itens OE-T09-01 a OE-T09-05) e a observação estratégica OE-T09-06 aguardam a futura Revisão Global de UX/UI (pós-Tela 30).
- Correção pendente do TCOS-018 Capítulo 19 ("azul" → "Âmbar-Atenção"), achado §3.15 Orçamentos (UX/UI Specification) e OE-T06-01 permanecem, sem alteração.
- Início imediato do protocolo oficial da Tela 10 (Dashboard Metas).

**Confirmação de auditoria:** confirmado que nenhum arquivo de mockup, TCOS-018, TCOS-005 ou qualquer outro documento oficial foi alterado nesta etapa — apenas `PROJECT_MEMORY.md`; confirmado que a Tela 09 permanece aprovada e congelada; confirmado que todas as 6 oportunidades identificadas foram registradas com prioridade preservada e nenhuma foi implementada.

---

## CORREÇÃO — Notificações e Estados da Interface Faltantes (TCOS-018, Capítulo 22)

**Status:** CONCLUÍDA E APROVADA PELO PROPRIETÁRIO (comando `CORRIGIR`, escopo fechado)
**Data:** 2026-08-02

Ao iniciar a Auditoria de Abertura da Tela 10 (Dashboard Metas), a comparação linha por linha entre o TCOS-018 (Capítulo 22) e a UX/UI Specification (§3.10) encontrou o mesmo padrão sistêmico de lacuna já corrigido nos Capítulos 16–21: os campos "Notificações" (item 17) e "Estados da interface" (item 23) da UX/UI Specification não estavam presentes no Capítulo 22. Reportado como Achado formal antes de qualquer correção; o proprietário autorizou (`CORRIGIR`) o escopo exato abaixo.

### Decisões tomadas
- D-COR8-01: campo "Notificações" adicionado ao Capítulo 22, copiado literalmente da UX/UI Specification §3.10, item 17 ("Meta atingida — celebração visual"; "Meta não atingida — neutro, sem 'gamificação negativa'").
- D-COR8-02: campo "Estados da interface" adicionado ao Capítulo 22, copiado literalmente da UX/UI Specification §3.10, item 23 (Ativa → Brasa; Atingida → Verde-Sucesso; Não atingida → Âmbar-Atenção, nunca Vermelho-Crítico — estado não punitivo; Encerrada → Cinza).
- D-COR8-03: confirmado, conforme instrução explícita do proprietário, que nenhum "Widget de IA" foi adicionado — nenhuma das fontes oficiais (TCOS-018 original ou UX/UI Specification §3.10) prevê widget de IA para este Dashboard.

### Alterações
- ALT-COR8-01: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018), Capítulo 22 — campos "Notificações" e "Estados da interface" adicionados. Confirmado via `git diff` que apenas o Capítulo 22 foi tocado (4 inserções, 0 remoções) — nenhum outro capítulo alterado; verificação programática confirmou os 28 capítulos permanecem sequenciais; RN-046 e F-084–F-091 existem exatamente como já citados, sem alteração a esses documentos ou a qualquer outro campo já existente no Capítulo 22 (Objetivo, Cards, Gráfico, Tabela, Ações rápidas, Modais, Alertas, Filtros, Comportamento esperado).

### Melhorias sugeridas (Backlog)
- Nenhuma nova além das já registradas (correção pendente Cap. 19 "azul"; achado §3.15 Orçamentos; OE-T06-01; Backlog Oficial de UX/UI da Tela 09, itens OE-T09-01 a OE-T09-06).

### Riscos encontrados
- Nenhum risco novo de arquitetura, regra de negócio ou documento oficial.

### Pendências
- Nova Auditoria de Abertura da Tela 10 a ser executada antes da construção, conforme protocolo.
- Correção pendente do TCOS-018 Capítulo 19 ("azul" → "Âmbar-Atenção"), achado §3.15 Orçamentos e OE-T06-01 permanecem, sem alteração.

**Confirmação de auditoria:** confirmado, antes da edição, que o working tree estava limpo e os 28 capítulos íntegros/sequenciais. Confirmado, depois da edição, via `git diff`, que apenas o Capítulo 22 foi alterado (4 inserções); confirmado que RN-046 e as referências F-084–F-091 permanecem íntegras em seus documentos de origem; confirmado que nenhum outro campo do Capítulo 22 (KPIs/Cards, Gráfico, Tabela, Filtros, Alertas, Ações rápidas, Modais) foi modificado; confirmado que nenhuma Regra de Negócio, Fluxo, Funcionalidade ou decisão arquitetural foi alterada; confirmado que nenhum outro documento oficial congelado foi tocado.

---

## CORREÇÃO — Divergência no campo "Filtros" (TCOS-018, Capítulo 22)

**Status:** CONCLUÍDA E APROVADA PELO PROPRIETÁRIO (comando `CORRIGIR`, escopo fechado)
**Data:** 2026-08-02

Ao reiniciar a Auditoria de Abertura da Tela 10 após a correção anterior (Notificações/Estados da interface), a releitura linha por linha do campo "Filtros" do Capítulo 22 contra a UX/UI Specification §3.10 encontrou uma nova divergência, independente da anterior: o TCOS-018 citava "Área da Empresa" como dimensão de filtro (não especificada na fonte oficial) e omitia "Indicador" (explicitamente especificado). Reportado como Achado formal antes de qualquer correção; o proprietário autorizou (`CORRIGIR`) o escopo exato abaixo.

### Decisões tomadas
- D-COR9-01: campo "Filtros" do Capítulo 22 corrigido — "Área da Empresa" substituído por "Indicador", copiado literalmente da UX/UI Specification §3.10, item 5–15 ("filtro por período/responsável/Indicador; pesquisa por nome de Meta"). Filtros "período", "responsável" e "busca por nome de Meta" mantidos inalterados.

### Alterações
- ALT-COR9-01: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018), Capítulo 22, campo "Filtros" — substituição pontual de uma dimensão de filtro. Confirmado via `git diff` que apenas essa linha foi alterada (1 inserção, 1 remoção) — nenhum outro campo do Capítulo 22 (Objetivo, Cards, Gráfico, Tabela, Ações rápidas, Modais, Alertas, Notificações, Estados da interface, Comportamento esperado) foi tocado; nenhum outro capítulo alterado; verificação programática confirmou os 28 capítulos permanecem sequenciais; nenhum identificador oficial (RN-046, F-084–F-091) foi modificado.

### Melhorias sugeridas (Backlog)
- Nenhuma nova além das já registradas (correção pendente Cap. 19 "azul"; achado §3.15 Orçamentos; OE-T06-01; Backlog Oficial de UX/UI da Tela 09, itens OE-T09-01 a OE-T09-06).

### Riscos encontrados
- Nenhum risco novo de arquitetura, regra de negócio ou documento oficial.

### Pendências
- Nova Auditoria de Abertura da Tela 10 a ser executada (novamente) antes da construção, conforme protocolo.
- Correção pendente do TCOS-018 Capítulo 19 ("azul" → "Âmbar-Atenção"), achado §3.15 Orçamentos e OE-T06-01 permanecem, sem alteração.

**Confirmação de auditoria:** confirmado, antes da edição, que o working tree estava limpo e os 28 capítulos íntegros/sequenciais. Confirmado, depois da edição, via `git diff`, que apenas a linha do campo "Filtros" do Capítulo 22 foi alterada; confirmado que nenhum outro campo, capítulo ou documento oficial foi modificado; confirmado que RN-046 e F-084–F-091 permanecem íntegros em seus documentos de origem.

---

## FASE — Tela 10 (Dashboard Metas) construída e apresentada

**Status:** Construída e apresentada, aguardando aprovação do proprietário
**Data:** 2026-08-02

Reiniciada a Auditoria de Abertura da Tela 10 após as duas correções do Capítulo 22 (Notificações/Estados da interface; Filtros). A releitura linha por linha do TCOS-018 Capítulo 22 (já corrigido) contra a UX/UI Specification §3.10, a Functional Specification (F-084–F-091, com destaque para F-089 que confirmou literalmente "filtro por período/responsável/Indicador") e a Business Rules Specification (RN-046) confirmou cobertura completa — nenhuma nova divergência objetiva encontrada. Construído o mockup de alta fidelidade — 10º Dashboard do sistema, primeiro da Área "BI / Direção Executiva" a ser construído (grupo de 3 módulos: Dashboard CEO, Inteligência Artificial, Metas — todos exibidos expandidos, sem submenu colapsado, já que esta Área contém múltiplos módulos e já estava assim na Tela 01, congelada).

### Decisões tomadas
- D-T10-01 **[Inferência visual]**: o Alerta "atraso no progresso" (RN-046) foi renderizado como uma pequena etiqueta Âmbar-Atenção separada, ao lado das ações do Card ("⚠ Atraso no progresso"), deliberadamente distinta e não sobreposta ao pill de Estado ("Ativa") — evitando criar um 5º "estado" não catalogado nos 4 Estados oficiais (Ativa/Atingida/Não atingida/Encerrada).
- D-T10-02: a ação "Duplicar" (F-087) foi posicionada exclusivamente nas linhas de Metas já encerradas da tabela de histórico (Atingida/Não atingida/Encerrada), não nos Cards de Metas ativas — rastreável à Jornada FL-019 (TCOS-018, linha 1435), que mostra "Duplicar para novo ciclo" ocorrendo após o registro da Justificativa de encerramento, nunca durante o ciclo ainda ativo.
- D-T10-03: "Editar" (F-085) e "Encerrar Antecipadamente" (F-086) posicionados nos Cards de Metas ativas — únicas ações que fazem sentido sobre uma Meta ainda em curso.

### Alterações
- ALT-T10-01: criados `mockup-dashboard-metas.html` e `shot10.js` (scratchpad, não versionados em Git); gerado `dashboard-metas.png`. Nenhum documento oficial foi alterado nesta etapa.

### Autocorreções durante as auditorias finais (antes da apresentação)
- AC-T10-01: a Auditoria Executiva Completa encontrou que o gráfico de histórico de ciclos havia sido inicialmente desenhado como gráfico de barras, divergindo do texto literal do TCOS-018 Capítulo 22 ("gráfico de linha de histórico de progresso"). Corrigido para um gráfico de linha com 2 séries (Atingida em Verde-Sucesso; Não atingida em Âmbar-Atenção, tracejada para diferenciação sem depender só da cor) antes de qualquer apresentação — autocorreção sobre mockup ainda não aprovado, sem tocar em documento oficial.
- AC-T10-02: a Auditoria de Consistência com a Tela 01 (Dashboard CEO, já aprovada e congelada) — obrigatória, dado que o Capítulo 22 declara que o dado de origem de uma Meta "é sempre o mesmo Serviço dono, nunca duplicado com cálculo próprio" — encontrou que o widget "Metas do período" da Tela 01 já exibia "Faturamento do mês" em 72%, enquanto o rascunho da Tela 10 usava 91% para a mesma Meta. Corrigido para 72% (R$ 180.000 / R$ 250.000), alinhando os dois números da mesma entidade nas duas telas. As demais Metas ("Novos Clientes no trimestre" 45%; "Redução de perda de Produção" 100%) já estavam consistentes com a Tela 01 desde o rascunho inicial.

### Melhorias sugeridas (Backlog)
- Nenhuma nova além das já registradas (correção pendente Cap. 19 "azul"; achado §3.15 Orçamentos; OE-T06-01; Backlog Oficial de UX/UI da Tela 09, itens OE-T09-01 a OE-T09-06).

### Riscos encontrados
- Nenhum risco novo.

### Pendências
- Aprovação do proprietário sobre a Tela 10.
- Correção pendente do TCOS-018 Capítulo 19 ("azul" → "Âmbar-Atenção"), achado §3.15 Orçamentos e OE-T06-01 permanecem, sem alteração.

**Confirmação de auditoria (Executiva Completa, Consistência, UX/UI, Produto SaaS, Regressão, Rastreabilidade):** confirmado que todos os componentes (Card de progresso — já oficial, UX/UI Spec §5.6, catalogado para uso em Dashboard Metas e como widget no Dashboard CEO; gráfico de linha; tabela; pill de Estado; botão primário) já são oficiais ou aplicações mínimas e rastreáveis de padrões já oficiais; confirmado que o conteúdo (Cards, Gráfico, Tabela, Ações rápidas, Filtros, Alertas, Estados) corresponde integralmente ao TCOS-018 Capítulo 22 (já corrigido nas 2 rodadas) e à UX/UI Specification §3.10; confirmado que os 4 Estados da interface usam exatamente as cores oficiais determinadas (Ativa=Brasa, Atingida=Verde-Sucesso, Não atingida=Âmbar-Atenção — nunca Vermelho-Crítico —, Encerrada=Cinza); confirmado que a sidebar reflete o agrupamento oficial (BI/Direção Executiva: Dashboard CEO, Inteligência Artificial, Metas — mesmo padrão expandido já usado na Tela 01); confirmado que grid, topbar e paleta são idênticos às Telas 01–09; confirmado que os dados de "Faturamento do mês", "Novos Clientes no trimestre" e "Redução de perda de Produção" são idênticos aos já exibidos no widget da Tela 01 (mesma origem, nunca duplicado com cálculo divergente); confirmado que nenhum módulo, Serviço, regra de negócio ou documento oficial foi alterado nesta etapa — apenas o `PROJECT_MEMORY.md`.

---

## APROVAÇÃO — Tela 10 (Dashboard Metas) — Conclusão oficial

**Status:** APROVADA E CONGELADA PELO PROPRIETÁRIO (comando `APROVADO`)
**Data:** 2026-08-02

O proprietário aprovou integralmente a Tela 10 (Dashboard Metas) como baseline oficial, encerrando esta etapa.

### Alterações
- Nenhuma alteração de conteúdo. Apenas este registro de aprovação em `PROJECT_MEMORY.md`.

### Confirmação de auditoria de consistência pós-aprovação
- Confirmado que o mockup `mockup-dashboard-metas.html`/`dashboard-metas.png` (scratchpad, não versionado em Git) corresponde integralmente ao TCOS-018 Capítulo 22 (já corrigido nas 2 rodadas desta fase) e à UX/UI Specification §3.10.
- Confirmado que os dados compartilhados com a Tela 01 (Dashboard CEO) — Faturamento do mês (72%), Novos Clientes no trimestre (45%), Redução de perda de Produção (100%) — permanecem idênticos entre as duas telas, sem duplicação de cálculo.
- Confirmado, via `git status`, que nenhum documento oficial além do `PROJECT_MEMORY.md` foi alterado nesta etapa de aprovação.
- Confirmado que a Tela 10 passa a integrar oficialmente o conjunto de referências visuais aprovadas do THE CHARCOAL OS, ao lado das Telas 01–09.

### Pendências
- Correção pendente do TCOS-018 Capítulo 19 ("azul" → "Âmbar-Atenção"), achado §3.15 Orçamentos (UX/UI Specification) e OE-T06-01 permanecem, sem alteração.
- Backlog Oficial de UX/UI da Tela 09 (OE-T09-01 a OE-T09-06) permanece aguardando a futura Revisão Global de UX/UI.
- Início imediato do protocolo oficial da Tela 11 (Dashboard Inteligência Artificial).

**Aprovação:** a Tela 10 (Dashboard Metas) foi aprovada integralmente pelo proprietário (comando `APROVADO`) e passa a integrar oficialmente o conjunto de referências visuais aprovadas do THE CHARCOAL OS, ao lado das Telas 01–09.

---

## CORREÇÃO — Alertas, Notificações, Modais, Estados da Interface e Filtros Incompletos (TCOS-018, Capítulo 23)

**Status:** CONCLUÍDA E APROVADA PELO PROPRIETÁRIO (comando `CORRIGIR`, escopo fechado)
**Data:** 2026-08-02

Ao iniciar a Auditoria de Abertura da Tela 11 (Dashboard Inteligência Artificial), a comparação linha por linha entre o TCOS-018 (Capítulo 23) e a UX/UI Specification (§3.11) encontrou o achado mais extenso desta sequência de correções: campos "Alertas", "Notificações", "Modais" e "Estados da interface" totalmente ausentes, e campo "Filtros" incompleto (faltavam as dimensões "status" e "pesquisa por período"). Reportado como Achado formal antes de qualquer correção; o proprietário autorizou (`CORRIGIR`) o escopo exato abaixo.

### Decisões tomadas
- D-COR10-01: campo "Modais" adicionado — "Configurar Nível de Automação" (por tipo de sugestão: sempre confirmar vs. automático se reversível), copiado literalmente da UX/UI Specification §3.11, item 18.
- D-COR10-02: campo "Alertas" adicionado — baixa confiança de previsão por histórico insuficiente (RN-042), copiado literalmente do item 16.
- D-COR10-03: campo "Notificações" adicionado — nova sugestão de alta relevância disponível, copiado literalmente do item 17.
- D-COR10-04: campo "Filtros" completado — de "filtro por módulo de origem; filtro por tipo de Agente Inteligente" para "filtro por módulo de origem; filtro por tipo; filtro por status; pesquisa por período", alinhado literalmente ao item 5–15.
- D-COR10-05: campo "Estados da interface" adicionado — "Pendente" (Brasa), "Aceita" (Verde-Sucesso), "Recusada" (Cinza, com motivo visível), copiado literalmente do item 23.

### Alterações
- ALT-COR10-01: `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018), Capítulo 23 — campos "Modais", "Alertas", "Notificações", "Estados da interface" adicionados; campo "Filtros" completado. Confirmado via `git diff` que apenas o Capítulo 23 foi tocado (1 linha removida, 5 campos inseridos) — nenhum outro capítulo alterado; verificação programática confirmou os 28 capítulos permanecem sequenciais; RN-041/042/043 e F-068–F-071 existem exatamente como já citados, sem alteração a esses documentos ou a qualquer outro campo já existente no Capítulo 23 (Objetivo, Cards de KPI, Visualização, Gráfico, Ações rápidas, Comportamento esperado).

### Melhorias sugeridas (Backlog)
- Nenhuma nova além das já registradas (correção pendente Cap. 19 "azul"; achado §3.15 Orçamentos; OE-T06-01; Backlog Oficial de UX/UI da Tela 09, itens OE-T09-01 a OE-T09-06).

### Riscos encontrados
- Nenhum risco novo de arquitetura, regra de negócio ou documento oficial.

### Pendências
- Nova Auditoria de Abertura da Tela 11 a ser executada antes da construção, conforme protocolo.
- Correção pendente do TCOS-018 Capítulo 19 ("azul" → "Âmbar-Atenção"), achado §3.15 Orçamentos e OE-T06-01 permanecem, sem alteração.

**Confirmação de auditoria:** confirmado, antes da edição, que o working tree estava limpo e os 28 capítulos íntegros/sequenciais. Confirmado, depois da edição, via `git diff`, que apenas o Capítulo 23 foi alterado; confirmado que RN-041/042/043 e as referências F-068–F-071 permanecem íntegras em seus documentos de origem; confirmado que nenhum outro campo do Capítulo 23 foi modificado; confirmado que nenhuma Regra de Negócio, Fluxo, Funcionalidade ou decisão arquitetural foi alterada; confirmado que nenhum outro documento oficial congelado foi tocado.

---

*Este arquivo deve ser atualizado ao final de cada fase, adicionando uma nova seção "FASE NNN" sem remover o histórico das fases anteriores.*
