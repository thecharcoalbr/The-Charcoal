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

**Status:** NÃO INICIADA — aguardando Prompt Oficial do proprietário (ver D-000-09)
**Data de redefinição:** 2026-08-01

Conforme D-000-09, esta fase substitui a proposta original de "Arquitetura Macro e Stack Tecnológica" como próxima fase do projeto. Seu objetivo será compreender profundamente o funcionamento real do negócio antes de qualquer decisão técnica. Nenhuma atividade desta fase pode ser iniciada antes do recebimento do Prompt Oficial e da execução do processo de auditoria de abertura de fase (Seção 17 do Framework).

---

*Este arquivo deve ser atualizado ao final de cada fase, adicionando uma nova seção "FASE NNN" sem remover o histórico das fases anteriores.*
