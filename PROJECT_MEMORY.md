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

*Este arquivo deve ser atualizado ao final de cada fase, adicionando uma nova seção "FASE NNN" sem remover o histórico das fases anteriores.*
