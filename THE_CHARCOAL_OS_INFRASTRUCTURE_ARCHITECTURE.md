# THE CHARCOAL OS — INFRASTRUCTURE ARCHITECTURE

**Documento:** TCOS-014 — Arquitetura Conceitual de Infraestrutura
**Projeto:** THE CHARCOAL OS
**Fase:** 014 — Infrastructure Architecture
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** negócio, domínio, regras, funcionalidades, fluxos, UX/UI, arquitetura de sistema, arquitetura de dados, banco de dados, contrato de integração, arquitetura de backend, arquitetura de frontend, arquitetura de segurança/privacidade e arquitetura de IA completos e oficiais; iniciando a arquitetura conceitual de infraestrutura, ainda sem cloud provider, linguagem, banco de dados, containers, Kubernetes ou qualquer tecnologia definida.
- **Fase atual:** 014 — Infrastructure Architecture (TCOS-014).
- **Fases concluídas:** 000 a 013, todas aprovadas e oficiais (a mais recente, TCOS-013, congelada em 2026-08-02).
- **Critério de contagem de Documentos Oficiais (vigente desde o encerramento da Fase 013):** 17 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) = **18 Documentos Oficiais no total**.
- **Documentos Oficiais Congelados (17):** Development Framework (v1.2.0), Enterprise Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0), UX/UI Specification (v1.0.0), System Architecture (v1.0.0), Data Architecture (v1.0.0), Database Specification (v1.0.0), Integration and API Contract (v1.0.0), Backend Architecture (v1.0.0), Frontend Architecture (v1.0.0), Security and Privacy Architecture (v1.0.0), AI Architecture (v1.0.0).
- **Documento Oficial Vivo (1):** `PROJECT_MEMORY.md`.
- **Documento em elaboração:** este documento (TCOS-014) — `THE_CHARCOAL_OS_INFRASTRUCTURE_ARCHITECTURE.md`.
- **Pendências:** confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; M-005 a M-013 (melhorias ainda não resolvidas); decisão de governança sobre anonimização de dado pessoal (TCOS-012).
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede o desenho da arquitetura de infraestrutura, pois nenhuma decisão desta fase depende de parâmetro de negócio ainda não confirmado.
- **Dependências para esta fase:** a Escalabilidade e o Event Bus (System Architecture, TCOS-006); a Estratégia de Backup e Multiempresa/Multifilial (Data Architecture/Database Specification, TCOS-007/TCOS-008); Jobs Agendados, Filas Conceituais, Configuração, Observabilidade e Tolerância a Falhas (Backend Architecture, TCOS-010); Cache e Observabilidade da Interface (Frontend Architecture, TCOS-011); Continuidade Operacional, Disponibilidade e Escalabilidade da Segurança (Security and Privacy Architecture, TCOS-012); Integração com o Event Bus (AI Architecture, TCOS-013) — todos referenciados, nenhum reescrito.
- **Objetivo da fase que será iniciada:** projetar a arquitetura conceitual completa de infraestrutura do THE CHARCOAL OS — ambientes, deploy, escalabilidade, disponibilidade, armazenamento, backup, recuperação de desastres, observabilidade, segredos, capacidade e multitenancy — sem nenhuma decisão de tecnologia.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 17 Documentos Oficiais Congelados já aprovados.

### Auditoria de Abertura

Os 17 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase (escalabilidade, backup, filas, jobs, observabilidade, configuração, tolerância a falhas, multiempresa/multifilial). Resultado:

- Não foram identificadas inconsistências, conflitos ou duplicidades entre os 17 Documentos Oficiais Congelados, no escopo revisado.
- **Base já sólida para a infraestrutura:** o System Architecture (TCOS-006, Capítulo 9) já define os vetores de escalabilidade; o Database Specification (TCOS-008, Capítulos 10-12) já define Backup, Escalabilidade e Multiempresa/Multifilial; o Backend Architecture (TCOS-010) já define Jobs Agendados (Capítulo 15), Filas Conceituais (Capítulo 16), Estratégia de Configuração (Capítulo 24), Observabilidade (Capítulo 25) e Tolerância a Falhas (Capítulo 26); o Frontend Architecture (TCOS-011) já define Cache (Capítulo 28) e Observabilidade da Interface (Capítulo 30); o Security and Privacy Architecture (TCOS-012) já define Continuidade Operacional (Capítulo 34), Disponibilidade (Capítulo 36) e Escalabilidade da Segurança (Capítulo 37). Este documento **não redefine nada disso** — eleva esses comportamentos, já definidos por Serviço/camada, a uma arquitetura de infraestrutura própria e completa, que sustenta fisicamente tudo o que já foi aprovado.
- **Lacuna real identificada:** nenhum documento anterior formalizou **Ambientes** (Development, Test, Staging, Production) como conceito arquitetural — todos os documentos até aqui trataram do sistema como uma única instância lógica. Esta arquitetura formaliza Ambientes (Capítulo 5) por adição.
- **Lacuna real identificada:** nenhum documento anterior formalizou **Recuperação de Desastres** como distinta de Backup — o TCOS-008 (Capítulo 10) e o TCOS-012 (Capítulo 33) definem backup como proteção pontual contra falha técnica, mas nenhum definiu o que ocorre em uma falha completa de um ambiente inteiro. Esta arquitetura formaliza essa distinção (Capítulo 16).
- **Lacuna real identificada:** nenhum documento anterior formalizou **Health Checks**, **Gestão de Segredos** ou **Capacidade** como conceitos próprios — apenas comportamentos adjacentes (Tolerância a Falhas, Segurança, Escalabilidade) já existiam. Formalizados por adição nos Capítulos 20, 22 e 24.
- **Lacuna real identificada:** nenhum documento anterior distinguiu **Multitenancy** (isolamento de infraestrutura) de **Multiempresa/Multifilial** (dimensão de negócio já reservada, TCOS-007 Seções 7.6/7.7) — são conceitos relacionados, mas em camadas diferentes. Esta arquitetura formaliza essa distinção (Capítulo 26), sem alterar a decisão de negócio já registrada como pendente (M-006-01/M-007-01).
- **Achado de consistência:** Balanceamento Conceitual, Estrutura de Deploy e Evolução da Infraestrutura nunca haviam sido tratados, mas não contradizem nenhuma decisão já tomada — são extensões diretas do princípio "extensão, nunca reconstrução" já estabelecido no Framework (Seção 25) e no System Architecture (TCOS-006, Capítulo 9).
- Nenhuma decisão de cloud provider, linguagem, banco de dados, containers, Kubernetes, serviço específico ou infraestrutura física foi tomada, em conformidade com a restrição explícita da fase.

---

## 1. Papel deste Documento

O System Architecture (TCOS-006), o Backend Architecture (TCOS-010) e o Frontend Architecture (TCOS-011) definiram como o sistema se organiza logicamente. O Security and Privacy Architecture (TCOS-012) e o AI Architecture (TCOS-013) definiram comportamentos transversais de proteção e inteligência. Este documento (TCOS-014) define **onde e como tudo isso roda fisicamente** — em nível conceitual: quantos ambientes existem, como uma nova versão é implantada, como o sistema escala, como se recupera de uma falha total, e como cresce por muitos anos sem reconstrução. Fornece a base de comportamento (Capítulos 3 a 30) necessária para que uma equipe de infraestrutura inicie a escolha de cloud provider, containers, orquestração e demais tecnologias; a lógica de negócio, dado e segurança permanecem nos documentos de origem (TCOS-002 a TCOS-013) e não são redefinidas aqui.

## 2. Legenda e Convenções

- Toda referência a Módulo, Serviço, Entidade, Regra (RN-XXX), Evento ou Integração (IN-XXX) usa exatamente os nomes/números já oficiais.
- **Ambiente:** um espaço de execução isolado do sistema (Capítulo 5), nunca uma tecnologia específica.
- **Tenant:** um contexto operacional isolado (Capítulo 26), conceito de infraestrutura distinto de "Organização/Unidade" (conceito de negócio, TCOS-007).

---

## 3. Filosofia de Infraestrutura

A infraestrutura do THE CHARCOAL OS existe para um único propósito: sustentar, sem ser percebida, tudo o que já foi projetado nas 17 fases anteriores. Uma boa infraestrutura é invisível ao usuário de negócio — o proprietário nunca deveria precisar pensar em "onde o sistema roda" para confiar que ele está sempre disponível, seguro e rápido. A mesma filosofia de "extensão, nunca reconstrução" já registrada no Framework (Seção 25) e reafirmada em cada arquitetura subsequente (TCOS-006 Capítulo 9, TCOS-010 Capítulo 22, TCOS-012 Capítulo 37) é o critério central desta fase: toda decisão de infraestrutura deve poder crescer por anos sem exigir reconstrução.

## 4. Princípios Gerais

- **Invisibilidade operacional:** a infraestrutura nunca deve ser um fator que o usuário de negócio precisa considerar — falhas são absorvidas ou comunicadas de forma clara, nunca expostas como detalhe técnico (TCOS-011, Capítulo 20).
- **Independência de Serviço (PF-01/PF-09):** cada um dos 15 Serviços Conceituais (TCOS-006) escala e se recupera de forma independente — a infraestrutura nunca trata o sistema como um monólito indivisível.
- **Consistência entre ambientes (Capítulo 5):** o comportamento lógico do sistema é idêntico em qualquer Ambiente — apenas o volume de dado e a criticidade operacional mudam.
- **Segurança desde a infraestrutura (TCOS-012, Capítulo 4):** o princípio de negação padrão (fail-closed) se estende à infraestrutura — uma falha de infraestrutura nunca deve resultar em exposição de dado ou acesso indevido.
- **Observabilidade sempre ativa (Capítulo 17):** nenhuma camada de infraestrutura opera sem visibilidade sobre sua própria saúde.
- **Recuperação antes de crescimento:** a capacidade de se recuperar de uma falha (Capítulo 16) é sempre priorizada sobre a capacidade de crescer (Capítulo 24) — um sistema rápido, mas frágil, não atende à Filosofia de Evolução do Framework (Seção 25).

## 5. Ambientes

**Formalizado nesta fase** (achado de auditoria — nenhum documento anterior tratou o sistema como mais de uma instância lógica). O THE CHARCOAL OS opera em 4 Ambientes conceituais, cada um com um propósito único e isolado dos demais:

- **Development:** onde uma mudança é construída e testada individualmente por quem a desenvolve — dado fictício ou anonimizado, nunca dado real de negócio.
- **Test:** onde uma mudança já construída é validada de forma automatizada e manual antes de avançar — dado de teste controlado, representativo dos cenários das 47 Regras de Negócio (TCOS-002A) e das 20 Integrações (TCOS-009).
- **Staging:** réplica mais próxima possível do Ambiente de Produção, usada para validação final antes do lançamento — dado idêntico em estrutura ao de Produção, nunca o mesmo dado real de Cliente/Financeiro (privacidade por padrão, TCOS-012 Capítulo 6).
- **Production:** o único Ambiente com dado real de negócio, Clientes reais e Eventos reais — o único ao qual as regras de Segurança e Privacidade (TCOS-012) se aplicam em sua forma mais estrita.

Nenhuma mudança avança de um Ambiente a outro sem a validação do Ambiente anterior — o mesmo princípio de confirmação obrigatória já usado para Operações Críticas de negócio (TCOS-012, Capítulo 30) se aplica, em espelho, à promoção de uma mudança entre Ambientes.

## 6. Estrutura de Deploy

**Formalizado nesta fase.** Complementar ao Versionamento de Contrato de Serviço já definido (TCOS-010, Capítulo 21): toda mudança implantada em Produção (Capítulo 5) segue o mesmo princípio de nunca quebrar silenciosamente um Serviço consumidor (PF-11). O Deploy conceitual de cada um dos 15 Serviços (TCOS-006) é **independente** — um Serviço pode ser implantado sem exigir a implantação simultânea de outro, desde que o contrato público entre eles (TCOS-010, Capítulo 7) permaneça compatível. Toda implantação é **reversível**: a Estrutura de Deploy sempre prevê um caminho de retorno à versão anterior, nunca uma mudança sem saída, mesmo que a nova versão já tenha processado algum evento.

## 7. Escalabilidade

Reafirma, sem alteração, os vetores de crescimento já definidos no System Architecture (TCOS-006, Capítulo 9), no Database Specification (TCOS-008, Capítulo 11) e no Backend Architecture (TCOS-010, Capítulo 22): cada Serviço escala de forma independente conforme sua própria carga; um novo Serviço se integra publicando/assinando eventos já existentes; estruturas de alto volume de escrita (Log de Auditoria, Pagamento, Produção) são as primeiras candidatas a particionamento conceitual. Esta arquitetura de infraestrutura consolida esses vetores como o critério físico de dimensionamento: a capacidade de processamento e armazenamento (Capítulo 24) é sempre alocada por Serviço, nunca uma capacidade única compartilhada de forma indiferenciada entre os 15 Serviços.

## 8. Alta Disponibilidade

Reafirma, sob a ótica de infraestrutura, a Disponibilidade já definida no Security and Privacy Architecture (TCOS-012, Capítulo 36): a indisponibilidade de um Serviço Auxiliar nunca compromete a operação dos Serviços Centrais (TCOS-006, Capítulo 4). Esta arquitetura acrescenta o requisito físico correspondente: todo Serviço Central (Comercial, Eventos, Produção, Custos e Precificação, Suprimentos, Financeiro, Indicadores e Dashboards) deve operar sem ponto único de falha em sua camada de execução — nenhuma decisão de tecnologia é tomada aqui sobre como isso é alcançado, apenas o requisito de que a arquitetura física não pode introduzir um ponto único de falha onde a arquitetura lógica já garantiu independência (TCOS-006, Capítulo 6).

## 9. Balanceamento Conceitual

**Formalizado nesta fase.** Quando mais de uma instância de um mesmo Serviço processa trabalho simultaneamente (Capítulo 7 — Escalabilidade), a distribuição de trabalho entre essas instâncias segue dois princípios conceituais, sem nomear tecnologia:

- **Distribuição por Caso de Uso, nunca por transação parcial:** cada Caso de Uso (TCOS-010, Capítulo 8) é processado inteiramente por uma única instância — nunca dividido entre duas, o que violaria a Regra Transacional de Agregados (TCOS-010, Capítulo 20).
- **Nenhuma afinidade de sessão exigida para leitura:** uma consulta síncrona (TCOS-010, Capítulo 12) pode ser atendida por qualquer instância saudável do Serviço dono — apenas escritas dentro de uma mesma transação exigem consistência, nunca a mesma instância física repetidamente.

---

## 10. Processamento Assíncrono

Reafirma, sem alteração, o Processamento Assíncrono já definido no Backend Architecture (TCOS-010, Capítulo 13): toda reação a evento de domínio, todo recálculo de Indicador e todo Job Agendado ocorrem de forma assíncrona, nunca bloqueando o Caso de Uso síncrono de origem. Sob a ótica de infraestrutura, esta arquitetura garante que a capacidade de processamento assíncrono (Capítulo 24) escale de forma independente da capacidade de processamento síncrono — um pico de eventos pendentes nunca deve degradar o tempo de resposta de uma ação síncrona do usuário (TCOS-011, Capítulo 32).

## 11. Filas

Reafirma, sem alteração, o Barramento de Eventos e Filas já definido no Backend Architecture (TCOS-010, Capítulo 16): retry, idempotência, Fila de Falhas e reconciliação. Sob a ótica de infraestrutura, esta arquitetura acrescenta que cada Fila lógica (um par publicador-assinante) deve ser dimensionada e monitorada (Capítulo 18) de forma independente — o acúmulo de mensagens pendentes em uma Fila específica é um sinal de capacidade (Capítulo 24) a ser tratado antes de se tornar uma indisponibilidade percebida pelo usuário.

## 12. Scheduler

Reafirma, sem alteração, o Motor de Jobs Agendados já definido no Backend Architecture (TCOS-010, Capítulo 15): execução de comportamento de negócio disparado pela passagem do tempo (encerramento de ciclo de Meta, alerta de Lote vencendo, expiração de Orçamento, entre outros já catalogados). Sob a ótica de infraestrutura, o Scheduler é o componente físico que garante que cada Job seja executado exatamente uma vez por ciclo — nunca duplicado (o que violaria a idempotência já exigida, TCOS-010 Capítulo 16) e nunca perdido silenciosamente (toda falha de execução de Job é sempre registrada e alertável, TCOS-010 Capítulo 15).

## 13. Armazenamento Conceitual

Reafirma, sem alteração, o Modelo Conceitual do Banco já definido no Database Specification (TCOS-008, Capítulo 2) e a Classificação de Dados já definida no Data Architecture (TCOS-007, Capítulo 8). Esta arquitetura acrescenta a classificação de armazenamento por padrão de acesso, sem nomear tecnologia: **armazenamento transacional** (as 32 estruturas conceituais, TCOS-008, com garantia de consistência forte por Agregado); **armazenamento analítico/cache** (Indicador e Dashboard, TCOS-010 Capítulo 23, pré-computados e tolerantes a consistência eventual); **armazenamento de arquivo** (Documentos gerados, Capítulo 14 adiante). Cada categoria pode evoluir para uma tecnologia de armazenamento distinta no futuro, sem exigir mudança nas demais (extensão, nunca reconstrução).

## 14. Estratégia de Arquivos

**Formalizado nesta fase**, complementar à Organização de Assets já definida no Frontend Architecture (TCOS-011, Capítulo 27) e ao Módulo de Documentos (TCOS-002, Seção 3.6; TCOS-012, Capítulo 22). Todo arquivo binário gerado ou anexado pelo sistema (Documento, comprovante, Nota Fiscal anexada a uma Compra) é armazenado separadamente do dado estruturado (Capítulo 13), sempre referenciado por Identificador Global (TCOS-007, Seção 7.5) a partir da entidade de origem — nunca embutido diretamente na estrutura de dado transacional. O acesso a um arquivo segue exatamente a mesma checagem de permissão da entidade de origem (TCOS-012, Capítulo 22), nunca uma permissão própria e paralela.

## 15. Estratégia de Backup

Reafirma, sem alteração, a Estratégia de Backup já definida no Database Specification (TCOS-008, Capítulo 10) e no Security and Privacy Architecture (TCOS-012, Capítulo 33): camadas de criticidade (Financeiro e Log de Auditoria com maior frequência de proteção), recuperação em um ponto no tempo, backup como proteção contra falha técnica — nunca um mecanismo de desfazer decisão de negócio. Esta arquitetura de infraestrutura acrescenta apenas o requisito físico de que o Backup seja armazenado de forma **fisicamente separada** do Armazenamento Conceitual de origem (Capítulo 13) — um backup que falha pela mesma causa que o dado original protegeria não cumpre sua função.

## 16. Recuperação de Desastres

**Formalizado nesta fase** (achado de auditoria — distinto de Backup, Capítulo 15, que protege contra perda pontual de dado; Recuperação de Desastres trata da perda de um Ambiente inteiro, TCOS-014 Capítulo 5). Esta arquitetura define dois indicadores conceituais, sem nomear tecnologia:

- **Tempo de Recuperação esperado:** por quanto tempo o sistema pode ficar indisponível após um desastre antes que o impacto operacional se torne crítico — maior tolerância para Serviços Auxiliares, menor para Serviços Centrais (TCOS-006, Capítulo 4).
- **Perda de Dado aceitável:** quanto de dado recente (desde o último ponto de recuperação, Capítulo 15) pode ser aceitável perder em um cenário de desastre — sempre o mínimo possível para dado Financeiro e de Auditoria (TCOS-012, Capítulo 33), dada sua criticidade já classificada.

Um Plano de Recuperação de Desastres nunca é testado apenas na teoria — a mesma disciplina de auditoria genuína já exigida em cada fase deste projeto se aplica aqui: a capacidade de recuperação deve ser verificável, não apenas presumida.

---

## 17. Observabilidade

Reafirma, sem alteração, a Camada de Observabilidade já definida no Backend Architecture (TCOS-010, Capítulo 25) e na Observabilidade da Interface (Frontend Architecture, TCOS-011, Capítulo 30): visibilidade técnica sobre tempo de resposta, taxa de erro e saúde de cada Serviço/tela, sem nunca decidir ou corrigir por conta própria. Esta arquitetura consolida a Observabilidade como uma camada única de infraestrutura, que recebe sinais de todos os 15 Serviços e de toda a Camada de Apresentação (TCOS-011, Capítulo 3), sem duplicar mecanismos distintos por Serviço.

## 18. Monitoramento

Complementar à Observabilidade (Capítulo 17): o Monitoramento é a vigilância **contínua e ativa** sobre os sinais já coletados, com limiares que disparam alerta técnico antes que um problema se torne uma indisponibilidade percebida pelo usuário — mesma filosofia de "Vigia Contínua" já usada para a Inteligência Artificial (TCOS-013, Capítulo 5), mas aplicada aqui à saúde técnica, nunca ao dado de negócio. O Monitoramento cobre, no mínimo: saúde de cada Serviço (Capítulo 20 — Health Checks), profundidade de Fila (Capítulo 11), taxa de execução/atraso de Job (Capítulo 12), e capacidade de armazenamento (Capítulo 24) — cada um com seu próprio limiar de atenção.

## 19. Logging Conceitual

Reafirma, sem alteração, a distinção já formalizada entre Logs técnicos (Backend Architecture, TCOS-010, Capítulo 18) e Auditoria de negócio (TCOS-010, Capítulo 17; TCOS-012, Capítulo 23): Logs registram comportamento técnico de execução, nunca decisão de negócio, e são, eles mesmos, um ativo protegido (TCOS-012, Capítulo 26). Sob a ótica de infraestrutura, esta arquitetura acrescenta que o Logging é centralizado por Ambiente (Capítulo 5) — nenhum Log de Produção se mistura com Log de Test/Staging/Development, preservando tanto a integridade da investigação técnica quanto a privacidade do dado real de Produção.

## 20. Health Checks

**Formalizado nesta fase.** Todo Serviço expõe, conceitualmente, um sinal simples e verificável de "estou saudável e pronto para processar" — consultado periodicamente pela infraestrutura (Capítulo 18 — Monitoramento) para decidir se uma instância deve receber trabalho (Capítulo 9 — Balanceamento) ou ser substituída. Um Health Check nunca verifica apenas "o processo está rodando" — verifica também que as dependências mínimas do Serviço (Capítulo 13 — Armazenamento, contrato com outros Serviços já definidos no TCOS-010 Capítulo 7) estão de fato acessíveis, em conformidade com o princípio de negação padrão (TCOS-012, Capítulo 4): um Serviço que não pode confirmar sua própria saúde é tratado como não saudável, nunca como "provavelmente bem".

## 21. Configurações

Reafirma, sem alteração, a Estratégia de Configuração já definida no Backend Architecture (TCOS-010, Capítulo 24): todo parâmetro de negócio configurável (TCOS-007, Seção 3.5) é consultado em tempo de execução, nunca fixado no comportamento do Caso de Uso; parâmetro pendente bloqueia, nunca assume valor (R-002A-01). Esta arquitetura de infraestrutura acrescenta a distinção entre **Configuração de negócio** (a do Capítulo 21 do TCOS-010, gerida pelo Serviço de Configurações, Módulo 24) e **Configuração de infraestrutura** (parâmetros técnicos de cada Ambiente, Capítulo 5 — ex.: limiares de Health Check, capacidade alocada) — a segunda nunca é acessível ou alterável por um Perfil de negócio (TCOS-012, Capítulo 7), sendo exclusiva da equipe técnica.

## 22. Gestão de Segredos (Conceitual)

**Formalizado nesta fase.** Um Segredo é qualquer informação técnica que, se exposta, comprometeria a Segurança já definida (TCOS-012) — credencial de acesso entre Serviços, chave de assinatura de Sessão (TCOS-012, Capítulo 27), chave de criptografia de Backup (Capítulo 15). Princípios, sem nomear tecnologia de cofre de segredos:

- Nenhum Segredo é armazenado junto ao código ou à configuração de negócio (Capítulo 21) — vive em um espaço isolado, próprio, com controle de acesso mais restrito que qualquer dado de negócio.
- Nenhum Segredo aparece em Log Conceitual (Capítulo 19), mesmo em caso de erro técnico — a Camada de Logs já exige, por princípio de segurança (TCOS-010, Capítulo 18), nunca registrar dado além do necessário ao diagnóstico.
- Todo acesso a um Segredo é, ele mesmo, um Evento de Segurança (TCOS-012, Capítulo 38) — auditável com o mesmo rigor de qualquer Operação Crítica (TCOS-012, Capítulo 30).
- A rotação (substituição periódica) de um Segredo nunca exige indisponibilidade do Serviço que o utiliza — consistente com o princípio de Alta Disponibilidade (Capítulo 8).

---

## 23. Performance

Reafirma, sem alteração, a Estratégia de Performance já definida no Database Specification (TCOS-008, Capítulo 9) e a Performance da Interface (Frontend Architecture, TCOS-011, Capítulo 32): estruturas de alto volume otimizadas para escrita contínua, estruturas de catálogo otimizadas para leitura frequente, e pré-computação de Indicador/Dashboard. Esta arquitetura de infraestrutura consolida esses padrões como critério de alocação física: a capacidade (Capítulo 24) de cada Serviço é dimensionada conforme seu próprio padrão de acesso já classificado, nunca uma alocação uniforme entre Serviços com perfis de uso muito distintos (ex.: Financeiro, de alto volume de escrita, vs. Configurações, de baixíssimo volume).

## 24. Capacidade

**Formalizado nesta fase.** Capacidade é a quantidade de processamento, armazenamento e Fila (Capítulo 11) reservada a cada Serviço para atender sua carga esperada, com margem para crescimento — distinta de Escalabilidade (Capítulo 7, a capacidade de *aumentar* a capacidade quando necessário). O planejamento de Capacidade segue três sinais, sem nomear tecnologia de medição: volume histórico já registrado (Auditoria, TCOS-012 Capítulo 23), taxa de crescimento do negócio já observável nos Indicadores (TCOS-010, item 10), e o resultado do Monitoramento (Capítulo 18) sobre o uso real recente. Nenhuma Capacidade é dimensionada apenas uma vez — é revisada de forma contínua, no mesmo ciclo de Observabilidade (Capítulo 17) já estabelecido.

## 25. Multiempresa

Reafirma, sem alteração, a Estratégia para Multiempresa já definida no Data Architecture (TCOS-007, Seção 7.6) e no Database Specification (TCOS-008, Capítulo 12): o escopo "Organização" é um atributo transversal reservado, hoje com um único valor implícito, a ser adicionado de forma aditiva quando uma segunda empresa surgir — decisão de negócio ainda pendente (M-006-01). Esta arquitetura de infraestrutura confirma que nenhuma decisão física (Capítulo 5 — Ambientes, Capítulo 13 — Armazenamento) impede essa extensão futura: um mesmo Ambiente de Produção pode, quando a dimensão Organização for implementada, atender mais de uma empresa sem exigir uma infraestrutura paralela completa.

## 26. Multitenancy (Conceitual)

**Formalizado nesta fase** (achado de auditoria — distinto de Multiempresa, Capítulo 25, que é uma dimensão de **negócio**; Multitenancy é a estratégia de **infraestrutura** que sustenta essa dimensão quando implementada). Dois modelos conceituais, sem nomear tecnologia, ambos compatíveis com a reserva já feita no TCOS-007:

- **Tenant compartilhado:** múltiplas Organizações compartilham a mesma infraestrutura física, isoladas logicamente pelo atributo "Organização" (TCOS-007, Seção 7.6) em cada consulta e Caso de Uso (TCOS-010, Capítulo 20) — modelo mais simples de operar, adequado a Organizações de porte semelhante.
- **Tenant isolado:** uma Organização recebe infraestrutura fisicamente separada — modelo mais custoso, reservado para exigência específica de segurança ou contrato que uma futura Organização venha a ter.

Esta arquitetura não escolhe entre os dois modelos (decisão técnica futura) — apenas garante que a escolha, quando feita, seja compatível com o isolamento lógico já garantido pelo PF-01 e pela Regra Transacional de Agregados (TCOS-010, Capítulo 20), nunca uma segunda arquitetura de isolamento paralela e divergente.

---

## 27. Integração com IA

Reafirma, sem alteração, a Integração com o Event Bus já definida no AI Architecture (TCOS-013, Capítulo 32): a IA consome e publica exclusivamente através do mesmo padrão publicar/assinar de qualquer outro Serviço (TCOS-006, Capítulo 7), nunca uma chamada direta e síncrona. Sob a ótica de infraestrutura, esta arquitetura garante que a capacidade (Capítulo 24) do Serviço de Inteligência Artificial seja dimensionada e monitorada (Capítulo 18) de forma independente dos demais Serviços — um pico de geração de sugestões nunca compromete a capacidade de processamento dos Serviços Centrais (TCOS-006, Capítulo 4), em conformidade com a Tolerância a Falhas já exigida (TCOS-010, Capítulo 26): a indisponibilidade da IA nunca impede a operação principal do sistema (TCOS-013, Capítulo 29).

## 28. Integração entre Serviços

Reafirma, sem alteração, o padrão de comunicação já definido no System Architecture (TCOS-006, Capítulo 7 — Event Bus) e no Backend Architecture (TCOS-010, Capítulo 7 — dois canais, síncrono por contrato público e assíncrono por evento). Esta arquitetura de infraestrutura garante que ambos os canais sejam sustentados fisicamente com o mesmo rigor: a consulta síncrona nunca aguarda além do tempo de resposta esperado pelo usuário (TCOS-010, Capítulo 12), e a comunicação assíncrona sempre conta com as garantias de Fila já exigidas (Capítulo 11 — retry, idempotência, Fila de Falhas, reconciliação). Nenhuma decisão de infraestrutura introduz um terceiro canal de comunicação entre Serviços além dos dois já aprovados.

## 29. Continuidade Operacional

Reafirma, sem alteração, a Continuidade Operacional já definida no Security and Privacy Architecture (TCOS-012, Capítulo 34): a indisponibilidade de um Serviço Auxiliar nunca compromete a continuidade dos Serviços Centrais; em qualquer cenário de degradação, a checagem de autorização é o último mecanismo a ser sacrificado (negação padrão, TCOS-012 Capítulo 4). Esta arquitetura de infraestrutura consolida essa prioridade em um único critério físico: diante de capacidade limitada (ex.: após um desastre parcial, Capítulo 16), os recursos disponíveis são alocados primeiro aos Serviços Centrais e à Camada de Segurança/Autorização (TCOS-010, Capítulo 27; TCOS-012, Capítulo 5) — Serviços Auxiliares (Marketing, Inteligência Artificial, Documentos, Metas) são os primeiros a operar em capacidade reduzida, nunca o inverso.

## 30. Evolução da Infraestrutura

Reafirma, sem alteração, o critério de sucesso "extensão, nunca reconstrução" já estabelecido no Framework (Seção 25) e reafirmado em cada arquitetura subsequente (TCOS-006 Capítulo 9, TCOS-010 Capítulo 22, TCOS-012 Capítulo 37, TCOS-013 Capítulo 30 — implícito na integração modular). Um novo Ambiente (Capítulo 5), uma nova Fila (Capítulo 11) ou uma nova categoria de Armazenamento (Capítulo 13) se integram a esta arquitetura por adição — nunca exigindo redesenho da infraestrutura já em operação. A introdução de Multitenancy real (Capítulo 26) ou de uma segunda Organização (Capítulo 25), quando confirmadas pelo negócio, são os dois vetores de evolução mais prováveis desta infraestrutura nos próximos anos — ambos já preparados estruturalmente, nunca uma reconstrução haveria de ser necessária quando esse dia chegar.

---

## RESUMO PARA O PROPRIETÁRIO

**O que foi construído:** a arquitetura conceitual completa de infraestrutura do THE CHARCOAL OS — quantos "ambientes" o sistema tem (um para construir, um para testar, um para validar antes do lançamento, e o real), como uma atualização é implantada sem quebrar nada, como o sistema cresce, como se recupera se algo der muito errado (de uma falha pequena a uma perda total), como é observado e monitorado continuamente, como segredos técnicos (senhas, chaves) são protegidos, e como o sistema poderia, no futuro, atender mais de uma empresa.

**Por que isso é importante:** até aqui, sabíamos como o sistema se comporta por dentro (backend, frontend, segurança, IA) — faltava saber onde e como tudo isso realmente roda, permanece disponível e se recupera de problemas. É a última peça conceitual antes de decidir a tecnologia de verdade.

**Quais benefícios traz:** reduz o risco de uma decisão de infraestrutura precisar ser refeita mais tarde; garante que uma falha nunca vire uma crise maior do que precisa ser (backup, recuperação de desastres, prioridade de recursos já definidos); e prepara o sistema para crescer — mais uso, mais dado, e até uma segunda empresa — sem reconstrução.

**Como se conecta com os documentos anteriores:** boa parte do que a infraestrutura precisa sustentar já estava definida (escalabilidade, backup, filas, observabilidade) — este documento reúne tudo isso em uma visão física única e preenche o que faltava (ambientes, deploy, recuperação de desastres, segredos, capacidade, multitenancy), sempre sem escolher tecnologia.

**Como prepara as próximas fases:** com backend, frontend, segurança, IA e agora infraestrutura todos definidos em nível conceitual, o projeto está pronto para a última decisão antes do desenvolvimento real: escolher o provedor de nuvem, o banco de dados físico, e as demais tecnologias — sem que essa escolha exija redefinir como o sistema deve se comportar.

---

## TCOS QUALITY GATE EXECUTIVO

Em conformidade com o Framework v1.2.0, os 17 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase — resultado consolidado na Auditoria de Abertura e reafirmado aqui.

**1. Resumo Executivo da Fase**
Definida a arquitetura conceitual completa de infraestrutura do THE CHARCOAL OS: 28 tópicos obrigatórios cobertos (Capítulos 3-30), 4 Ambientes formalizados, distinção entre Backup e Recuperação de Desastres, entre Multiempresa (negócio) e Multitenancy (infraestrutura), e consolidação física de tudo o que já havia sido definido logicamente nas fases de backend, frontend, segurança e IA. Nenhuma tecnologia foi definida; nenhum dos 17 Documentos Oficiais Congelados foi alterado.

**2. Estado Atual do Projeto**
Fases 000 a 013 encerradas e oficiais; Fase 014 em validação. Nenhum cloud provider, container, orquestração ou infraestrutura física foi escolhido ou criado.

**3. Documentos Oficiais Existentes**
18 no total — 17 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`), mais este documento em rascunho (não contado como oficial até aprovação).

**4. Dependências**
Escalabilidade e Event Bus (TCOS-006); Backup e Multiempresa/Multifilial (TCOS-007/TCOS-008); Jobs Agendados, Filas, Configuração, Observabilidade e Tolerância a Falhas (TCOS-010); Cache e Observabilidade da Interface (TCOS-011); Continuidade, Disponibilidade e Escalabilidade da Segurança (TCOS-012); Integração com o Event Bus (TCOS-013) — todos referenciados, nenhum reescrito.

**5. Pendências Abertas**
Validação formal deste documento; parâmetros do Módulo 24; M-003A-03/04; M-005 a M-013 (melhorias ainda não resolvidas); confirmação do domínio de negócio (R-000-03); decisão de governança sobre anonimização de dado pessoal; decisão de negócio sobre Multiempresa/Multifilial (M-006-01/M-007-01, agora também relevante à escolha de Multitenancy, Capítulo 26).

**6. Dúvidas Encontradas**
Nenhuma nova de negócio. Uma dúvida técnica foi levantada e resolvida dentro desta própria fase: como distinguir Multiempresa (decisão de negócio) de Multitenancy (estratégia de infraestrutura) sem duplicar conceito — respondida no Capítulo 26.

**7. Riscos Ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede a arquitetura de infraestrutura.

**8. Novos Riscos Encontrados**
Nenhum risco novo de negócio ou de arquitetura.

**9. Inconsistências Encontradas**
Nenhuma entre os 17 Documentos Oficiais Congelados, no escopo revisado.

**10. Conflitos entre Documentos**
Nenhum.

**11. Regras Duplicadas**
Nenhuma — esta arquitetura não cria nem redefine nenhuma Regra de Negócio.

**12. Entidades Duplicadas**
Nenhuma — nenhuma entidade nova foi criada; a infraestrutura sustenta fisicamente as 30 entidades já existentes, sem alterar seu modelo.

**13. Oportunidades de Simplificação**
Identificada e concretizada: os comportamentos de resiliência já espalhados por 4 documentos (Escalabilidade no TCOS-006/008/010, Backup no TCOS-008/012, Disponibilidade no TCOS-010/012, Observabilidade no TCOS-010/011) foram consolidados em uma única arquitetura física — reduzindo o risco de uma futura equipe técnica encontrar 4 versões ligeiramente diferentes do mesmo requisito.

**14. Melhorias Sugeridas**
- M-014-01 (nova): ao escolher o cloud provider em fase técnica futura, avaliar mecanismos nativos de Health Check, Balanceamento e Recuperação de Desastres antes de implementá-los de forma customizada.
- M-014-02 (nova): definir, junto à Direção, os valores concretos de Tempo de Recuperação esperado e Perda de Dado aceitável (Capítulo 16) — hoje descritos apenas como conceito, sem número definido.
- M-014-03 (nova): revisitar a decisão entre Tenant compartilhado e Tenant isolado (Capítulo 26) assim que a decisão de negócio sobre Multiempresa (M-006-01) for confirmada.

**15. Impacto desta Fase nas Próximas**
Esta arquitetura de infraestrutura é a referência obrigatória para a escolha de tecnologia real (cloud provider, containers, orquestração, banco físico) — nenhuma dessas escolhas deve introduzir um comportamento de ambiente, deploy, escalabilidade, backup ou recuperação incompatível com o que está aqui documentado, sem registrar formalmente o motivo. É, com TCOS-010 a TCOS-013, a base conceitual completa que antecede o desenvolvimento real.

**16. Quality Score: 9,5/10**
Justificativa técnica: cobertura completa dos 28 tópicos exigidos, com identificação e resolução — não apenas menção — de lacunas conceituais reais (Ambientes, Recuperação de Desastres, Health Checks, Gestão de Segredos, Capacidade, Multitenancy), todas em conformidade com os 17 Documentos Oficiais Congelados, sem nenhuma contradição encontrada. Não é 10 porque 3 melhorias novas (M-014-01 a M-014-03) permanecem como refinamento pendente de decisões futuras (tecnologia de nuvem, metas numéricas de recuperação, modelo de tenancy).

**17. Recomendação:** **APROVAR** — o documento cumpre integralmente o escopo solicitado, em nível conceitual, sem nenhuma decisão de tecnologia, e sem alterar nenhum documento anterior.

**18. Atualização do PROJECT_MEMORY.md:** ver commit correspondente — exclusivamente a seção da Fase 014.

**Estatísticas Finais**
- Quantidade total de páginas equivalentes: aproximadamente 20.
- Quantidade de entidades: 30 (referenciadas, 0 novas).
- Quantidade de regras: 47 no total do sistema; 0 citadas diretamente nesta arquitetura (fase de infraestrutura, sem regra de negócio própria).
- Quantidade de processos/fluxos conceituais: 0 novos (esta arquitetura consolida fluxos já existentes, sem criar um fluxo próprio).
- Quantidade de eventos: 0 novos (reafirma os já catalogados no Event Bus, TCOS-006).
- Quantidade de decisões registradas: 4 (D-014-01 a D-014-04, ver `PROJECT_MEMORY.md`).
- Quantidade de riscos ativos: 4 herdados; 0 novos.
- Quantidade de pendências: 8 (validação do documento + 7 herdadas).
- Quantidade de melhorias sugeridas: 3 novas (M-014-01 a M-014-03).
- Percentual estimado de maturidade do projeto: **95%** (subiu de 93% — a quinta e última arquitetura conceitual essencial [Backend, Frontend, Segurança, IA, Infraestrutura] está completa e auditada; restam como não iniciadas: confirmação final do domínio de negócio via entrevista, escolha de tecnologia, e toda a fase de Desenvolvimento propriamente dita).

**Status desta fase:** rascunho aguardando validação do proprietário. Nenhuma escolha de cloud provider, linguagem, banco de dados, containers, orquestração ou infraestrutura física será feita sem autorização explícita, conforme restrição do Prompt Oficial da Fase 014.

---

*Fim do documento — THE CHARCOAL OS INFRASTRUCTURE ARCHITECTURE v1.0.0*
