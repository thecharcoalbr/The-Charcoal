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

**Status:** Rascunho entregue — aguardando validação do proprietário (`THE_CHARCOAL_OS_ENTERPRISE_DOMAIN_DISCOVERY.md` v1.0.0)
**Data:** 2026-08-01

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

---

*Este arquivo deve ser atualizado ao final de cada fase, adicionando uma nova seção "FASE NNN" sem remover o histórico das fases anteriores.*
