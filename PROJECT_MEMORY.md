# MEMÓRIA CUMULATIVA DO PROJETO — THE CHARCOAL OS

> Histórico obrigatório de consulta antes de qualquer nova fase, conforme
> Seção 17 do THE_CHARCOAL_OS_DEVELOPMENT_FRAMEWORK.md.

---

## FASE 000 — Governança do Projeto

**Status:** Aguardando validação do proprietário
**Data:** 2026-08-01

### Decisões tomadas
- D-000-01: Adotado o modelo de "Comitê Executivo multi-especialista" como postura de trabalho para todas as fases futuras. Motivo: garantir que decisões técnicas sejam avaliadas sob múltiplas perspectivas (arquitetura, dados, segurança, UX, negócio) antes de aprovação.
- D-000-02: Nenhum código, banco de dados, tela ou API será produzido antes da aprovação formal desta Fase 000. Motivo: instrução explícita do proprietário; evita retrabalho por ausência de regras estabelecidas.
- D-000-03: Adotado versionamento semântico (MAJOR.MINOR.PATCH) para o Framework, módulos e releases. Motivo: padrão amplamente utilizado por empresas de referência citadas (Microsoft, Apple, Google, Oracle, SAP), com rastreabilidade clara de impacto de mudanças.
- D-000-04: Toda fase exige auditoria de abertura e revisão de encerramento, com aprovação exclusiva do proprietário via comandos formais (`APROVADO`, `CORRIGIR`, `ALTERAR`, `REMOVER`, `CONTINUAR`). Motivo: instrução explícita do proprietário; garante controle final e rastreabilidade de todas as decisões relevantes.

### Alterações
- Nenhuma (fase inicial do projeto).

### Melhorias sugeridas (Backlog)
- M-000-01: Considerar, a partir da Fase 001, a criação de um repositório de artefatos vivos (Decision Log, Changelog, Registro de Riscos, Backlog de Melhorias, Mapa de Integrações, Glossário de Domínio) como arquivos versionados separados, em vez de seções soltas, para facilitar rastreamento incremental por fase.
- M-000-02: Avaliar, antes da Fase 001, se o projeto seguirá arquitetura modular monolítica ou modular distribuída (microsserviços) — decisão estrutural de alto impacto que deve ser tomada com registro formal de vantagens/desvantagens antes de qualquer definição de banco de dados.

### Riscos encontrados
- R-000-01: Ausência de repositório de código pré-existente (repositório vazio, sem commits). Impacto: nenhuma inconsistência herdada, mas também nenhuma referência arquitetural prévia — todas as convenções (nomenclatura, padrões de dados, estrutura de módulos) precisarão ser definidas do zero na primeira fase técnica. Status: aberto, a ser tratado na Fase 001.
- R-000-02: O framework define processos rigorosos de auditoria e aprovação; risco de a governança se tornar um gargalo se o proprietário não estiver disponível para validar cada fase tempestivamente. Mitigação proposta: manter fases com escopo objetivo e relatórios concisos para agilizar a validação. Status: aberto, monitorar.

### Pendências
- P-000-01: Aprovação formal do proprietário sobre este documento de governança (Fase 000).
- P-000-02: Definição do escopo da Fase 001 (provavelmente: arquitetura macro do sistema, escolha de stack tecnológica, modelo de dados conceitual) — não deve ser iniciada sem aprovação prévia desta fase.

### Funcionalidades aprovadas
- Nenhuma (fase de governança; nenhuma funcionalidade de produto foi proposta ou aprovada).

### Funcionalidades rejeitadas
- Nenhuma.

### Módulos existentes
- Nenhum (projeto ainda não possui módulos técnicos; apenas governança).

### Integrações
- Nenhuma.

---

*Este arquivo deve ser atualizado ao final de cada fase, adicionando uma nova seção "FASE NNN" sem remover o histórico das fases anteriores.*
