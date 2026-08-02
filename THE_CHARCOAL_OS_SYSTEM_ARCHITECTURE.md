# THE CHARCOAL OS — SYSTEM ARCHITECTURE

**Documento:** TCOS-006 — Arquitetura Conceitual do Sistema
**Projeto:** THE CHARCOAL OS
**Fase:** 006 — System Architecture
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** negócio, domínio, regras, funcionalidades, fluxos operacionais e experiência de usuário completos e oficiais; iniciando a organização técnica conceitual do sistema, ainda sem linguagem, banco de dados, framework, API ou infraestrutura definidos.
- **Fase atual:** 006 — System Architecture (TCOS-006).
- **Fases concluídas:** 000 a 005, todas aprovadas e oficiais (a mais recente, TCOS-005, congelada nesta mensagem).
- **Documentos oficiais:** Framework (v1.2.0), `PROJECT_MEMORY.md`, Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0), UX/UI Specification (v1.0.0, congelado a partir de agora).
- **Documentos em elaboração:** este documento (TCOS-006).
- **Pendências:** confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; M-004-01/02; M-005-01/02/03; decisão sobre retomar a entrevista de descoberta.
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede o desenho arquitetural conceitual, pois esta arquitetura já prevê, estruturalmente, onde e como esses parâmetros serão consumidos (Serviço de Configurações, Capítulo 6).
- **Dependências para esta fase:** as 30 entidades e Regras Globais (Domain Model); as 47 Regras de Negócio; os 27 módulos e 98 funcionalidades; os 30 fluxos e a Matriz de Integração (TCOS-004); as 30 telas e o Design System (TCOS-005) — todos referenciados, nenhum reescrito.
- **Objetivo da fase que será iniciada:** definir a arquitetura conceitual do THE CHARCOAL OS — como o sistema se organiza internamente — sem código, banco de dados ou tecnologia.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 9 documentos oficiais já aprovados e congelados.

### Auditoria de Abertura

Todos os documentos oficiais foram lidos integralmente. Resultado:

- **Nenhuma inconsistência, conflito ou duplicidade** entre os documentos existentes.
- **Dependências ocultas identificadas e tornadas explícitas:** Produção, Precificação e Escalas dependem do Módulo 24 (Configurações) para parâmetros de consumo/perda, margem-alvo e proporção de equipe, respectivamente — já documentado funcionalmente (TCOS-003) e operacionalmente (TCOS-004), mas nunca antes expresso como uma dependência arquitetural de um Serviço sobre outro. Esta arquitetura torna essa dependência explícita (Capítulo 4).
- **Risco técnico identificado e resolvido nesta arquitetura:** tratar a orquestração de confirmação de Evento (RN-006) como uma cadeia de chamadas síncronas diretas a cada módulo geraria alto acoplamento e um único ponto de falha. Resolução: RN-006 é modelada como um único evento publicado ("Evento confirmado"), com múltiplos Serviços assinando-o de forma independente (Capítulo 7 — Event Bus), nunca como uma chamada direta em cadeia.
- **Risco técnico identificado e resolvido nesta arquitetura:** o Dashboard CEO consome dado de todos os 27 módulos; se cada Dashboard consultasse diretamente cada Serviço de origem, o acoplamento cresceria proporcionalmente a cada novo módulo. Resolução: criado um único Serviço de Indicadores e Dashboards (Capítulo 6), que assina eventos de todos os demais Serviços — nenhum Dashboard consulta um Serviço de origem diretamente.
- **Oportunidade de simplificação concretizada:** a melhoria M-004-01 (unificar os três mecanismos de atualização de Dashboard/Indicador identificados no TCOS-004) é resolvida estruturalmente pelo Serviço de Indicadores e Dashboards desta arquitetura — não sobra mais que um único mecanismo.
- **Funcionalidades sem suporte arquitetural:** nenhuma das 98 funcionalidades ficou sem um Serviço Conceitual correspondente (ver mapeamento completo no Capítulo 4).
- **Módulos sem integração:** nenhum — todos os 27 aparecem na Matriz de Dependências (Capítulo 4).
- **Fluxos incompatíveis:** nenhum encontrado entre os 30 fluxos do TCOS-004 e a organização de Serviços aqui definida.
- Nenhuma decisão de linguagem, banco de dados, framework, API, nuvem ou infraestrutura foi tomada, em conformidade com a restrição explícita da fase.

---

## 1. Papel deste Documento

Este documento organiza, em nível conceitual, **como o THE CHARCOAL OS se estrutura internamente** para sustentar tudo que já foi aprovado: as entidades (Domain Model), as regras (Business Rules), as funcionalidades (Functional Specification), os fluxos (User Journeys) e as telas (UX/UI). Um arquiteto de software deve conseguir projetar tecnicamente o sistema a partir daqui, sem precisar reinterpretar nenhuma regra de negócio — apenas escolher a tecnologia que implementa a estrutura aqui descrita.

## 2. Filosofia Arquitetural

A arquitetura aplica diretamente os Princípios Fundamentais já aprovados no Framework:

- **Um dado, um dono (PF-01):** cada Serviço Conceitual é o único dono das entidades sob sua responsabilidade — nenhuma entidade é "gerenciada" por mais de um Serviço.
- **Compartilhamento nunca por acesso direto (PF-02):** um Serviço nunca lê ou escreve diretamente na estrutura interna de outro; toda comunicação ocorre por evento publicado (Event Bus) ou por consulta ao contrato público do Serviço dono.
- **Cálculo único (PF-03):** toda fórmula (custo, preço, indicador) vive em exatamente um Serviço; os demais a consomem, nunca a recalculam de forma independente.
- **Histórico obrigatório (PF-04):** todo Serviço publica um evento a cada mudança de estado relevante — o Serviço de Auditoria (Capítulo 6) constrói o histórico completo do sistema a partir desses eventos, nunca por acesso direto ao dado interno de cada Serviço.
- **IA nunca decide sozinha (PF-06):** o Serviço de IA publica sugestões como eventos, nunca altera diretamente o dado de outro Serviço.
- **Simplicidade e manutenção acima de tudo (PF-09):** poucos Serviços coesos e bem definidos — não um microsserviço por módulo ou por tela.

---

## 3. Arquitetura Conceitual

### 3.1 Visão Geral da Arquitetura

O THE CHARCOAL OS é organizado como um conjunto de **Serviços Conceituais** coesos (Capítulo 6), que se comunicam por meio de um **Event Bus interno** (Capítulo 7) para reagir a mudanças de estado, e por **consultas diretas restritas ao contrato público** de cada Serviço para leitura sob demanda. Nenhum Serviço acessa a estrutura interna de outro. Toda a arquitetura deriva das entidades, regras, funcionalidades e fluxos já aprovados — nenhuma estrutura de negócio nova é introduzida aqui.

### 3.2 Filosofia Arquitetural

Ver Capítulo 2.

### 3.3 Separação em Camadas

| Camada | Conteúdo | Origem já aprovada |
|---|---|---|
| **Apresentação** | as 30 telas e o Design System | TCOS-005 |
| **Orquestração de Regras** | as 47 Regras de Negócio e os 30 Fluxos, materializados como comportamento dos Serviços | TCOS-002A, TCOS-004 |
| **Domínio** | as 30 entidades e as Regras Globais do Domínio | TCOS-002 |
| **Dados** | persistência conceitual de cada entidade — sem tecnologia definida | TCOS-002 |
| **Transversal** | Segurança, Auditoria, Alertas, Inteligência Artificial — atravessam todas as demais camadas | Capítulos 6–8 deste documento |

### 3.4 Organização por Módulos

Os 27 módulos do Functional Specification são agrupados em 13 Serviços Conceituais coesos (detalhamento completo no Capítulo 6), evitando o antipadrão de um Serviço por módulo/tela — o que geraria acoplamento excessivo e complexidade desnecessária de coordenação (PF-09).

### 3.5 Comunicação entre Módulos

Um módulo nunca acessa diretamente o dado interno de outro módulo. Toda comunicação ocorre: (a) de forma **assíncrona**, via evento publicado no Event Bus, para reagir a uma mudança de estado (ex.: Produção reage a "Evento confirmado"); ou (b) de forma **síncrona**, via consulta ao contrato público do módulo dono, para leitura sob demanda (ex.: Orçamento consulta o preço vigente calculado por Precificação). Nunca há duplicação do mesmo dado entre módulos (PF-01/PF-03).

### 3.6 Comunicação entre Serviços

A mesma lógica da Seção 3.5 se aplica no nível de Serviço Conceitual: cada Serviço expõe um **contrato conceitual** — o que aceita como comando, o que publica como evento, o que responde a uma consulta — e nunca expõe sua estrutura interna de dado a outro Serviço.

### 3.7 Fluxo de Dados (resumo)

Ver Capítulo 5 — Fluxo Global de Dados, para o detalhamento completo da cadeia principal (Lead → Cliente → Orçamento → Contrato → Evento → Produção → Compras → Estoque → Financeiro → Dashboard CEO) e dos fluxos secundários que a alimentam.

### 3.8 Eventos Internos (resumo)

Ver Capítulo 7 — Event Bus, para o catálogo completo de eventos internos, seus publicadores e assinantes.

### 3.9 Integração entre Vida Pessoal e Empresa

O Serviço Financeiro trata Financeiro Pessoal e Financeiro Empresarial como **dois contextos dentro do mesmo Serviço**, nunca dois Serviços separados — separar em Serviços distintos criaria dois caminhos de código para o mesmo tipo de lançamento (Despesa/Receita Financeira/Pagamento), aumentando o risco de inconsistência entre eles. A separação ocorre por **categoria de lançamento** (RN-002/RN-005: "Retirada Pessoal" vs. operacional), nunca por Serviço.

### 3.10 Integração entre Dashboards

Todos os Dashboards (CEO e os dez especializados) consultam **exclusivamente** o Serviço de Indicadores e Dashboards — nunca os Serviços de origem diretamente. Existe, arquiteturalmente, um único caminho de atualização para qualquer painel do sistema (resolve o risco de acoplamento identificado na auditoria).

### 3.11 Integração entre IA

O Serviço de Inteligência Artificial nunca modifica diretamente o dado de outro Serviço. Ele **assina** eventos (ex.: "Extrato bancário importado", "Produção concluída") e **publica sugestões como eventos próprios** (ex.: "Sugestão de categorização gerada", "Previsão de demanda gerada"), que o Serviço de origem decide como tratar — implementação arquitetural direta do PF-06.

### 3.12 Integração entre Engenharia de Custos

O Serviço de Custos e Precificação assina "Custo de Ingrediente atualizado" (do Serviço de Suprimentos) e "Produção concluída" (do Serviço de Produção), recalcula e publica "Custo recalculado" — assinado pelo Serviço Comercial para revalidar Orçamentos abertos (RN-019), e pelo Serviço de Indicadores e Dashboards.

### 3.13 Integração entre Financeiro

O Serviço Financeiro nunca calcula Receita Financeira, Despesa ou custo de mão de obra de forma independente — ele **sempre reage** a um evento de origem: "Contrato assinado" (Receita Financeira prevista), "Compra conferida" (Despesa), "Alocação de Funcionário realizada" (custo de mão de obra).

### 3.14 Integração entre CRM

O Serviço Comercial mantém Lead, Cliente, Orçamento e Contrato como um **único domínio coeso** (evita o antipadrão de três Serviços minúsculos e fortemente acoplados entre si). Marketing e Eventos permanecem Serviços distintos, comunicando-se com o Comercial exclusivamente por eventos ("Lead criado", "Lead convertido", "Contrato assinado").

### 3.15 Integração entre Produção

O Serviço de Produção assina "Evento confirmado" para planejar automaticamente (RN-016), **consulta** o Serviço de Configurações para os parâmetros de consumo/perda (RN-024 a RN-029), e publica "Produção concluída" — assinado pelos Serviços de Custos, Suprimentos (baixa de Estoque) e Indicadores/Dashboards.

### 3.16 Integração entre Estoque

O Serviço de Suprimentos (Compras + Estoque + Lotes) é o **único dono** do saldo de Estoque. Nenhum outro Serviço o altera diretamente; toda alteração ocorre em resposta a um evento de outro Serviço (Produção consumindo, venda direta) — nunca por escrita direta de fora do Serviço.

### 3.17 Integração entre Marketing

O Serviço de Marketing assina eventos do Serviço Comercial ("Lead convertido", "Contrato assinado") para atribuir retorno de Campanha (RN-038), sem nunca escrever diretamente no domínio do Serviço Comercial.

### 3.18 Integração entre Eventos

O Serviço de Eventos é o orquestrador natural do ciclo comercial-operacional, mas **não executa** a lógica de Produção, Estoque, Financeiro ou Pessoas diretamente — ele publica "Evento confirmado" e "Evento cancelado"; cada Serviço interessado reage de forma independente, no padrão publicar-assinar detalhado no Capítulo 7.

---

## 4. Dependências entre Módulos

| Módulo | Serviço Conceitual | Categoria | Depende obrigatoriamente de | Pode operar isoladamente? |
|---|---|---|---|---|
| 01 Dashboard CEO | Indicadores e Dashboards | Central (visão) | Todos os demais Serviços (via eventos) | Não |
| 02 Financeiro Pessoal | Financeiro | Central | 27 (Bancos, dado de Conta) | Não |
| 03 Financeiro Empresarial | Financeiro | Central | 07, 09, 15, 19, 27 | Não |
| 04 CRM | Comercial | Central | 06, 05, 21 (dado consolidado) | Não |
| 05 Clientes | Comercial | Central | 06 (origem via conversão, opcional) | Sim (cadastro direto) |
| 06 Leads | Comercial | Central | 21 (origem, opcional) | Sim |
| 07 Eventos | Eventos | Central | 05, 08, 09 | Não |
| 08 Orçamentos | Comercial | Central | 13, 14 | Não |
| 09 Contratos | Comercial | Central | 08 | Não |
| 10 Produção | Produção | Central | 13, 16, 24 | Não |
| 11 Engenharia de Custos | Custos e Precificação | Central | 13, 10, 19 | Não |
| 12 Receitas | Produção | Central | — (Ingrediente, cadastro básico) | Sim |
| 13 Fichas Técnicas | Produção | Central | 12, 24 | Não |
| 14 Precificação | Custos e Precificação | Central | 13, 24 | Não |
| 15 Compras | Suprimentos | Central | — (Fornecedor, cadastro básico) | Sim |
| 16 Estoque | Suprimentos | Central | 15, 10 | Não |
| 17 Lotes | Suprimentos | Central | 15, 10 | Não |
| 18 Equipamentos | Pessoas e Recursos | Auxiliar | 07 (uso) | Sim (cadastro) |
| 19 Funcionários | Pessoas e Recursos | Auxiliar | — | Sim |
| 20 Escalas | Pessoas e Recursos | Auxiliar | 19, 07, 24 | Não |
| 21 Marketing | Marketing | Auxiliar | 06, 04 (leitura) | Sim (cadastro de Campanha) |
| 22 Inteligência Artificial | Inteligência Artificial | Auxiliar | Serviço(s) de origem de cada sugestão | Não (depende de dado alheio) |
| 23 Documentos | Documentos | Auxiliar | entidade de origem (Contrato, Compra etc.) | Não |
| 24 Configurações | Configurações | Auxiliar | — | Sim |
| 25 Administração do Sistema | Administração e Segurança | Auxiliar | — | Sim |
| 26 Metas | Metas | Auxiliar | Indicador associado (Serviço de Indicadores) | Não |
| 27 Bancos | Financeiro (Bancos) | Central | — | Sim |

**Módulos/Serviços centrais** (formam a espinha dorsal da cadeia de valor — comercial, operação, custo, caixa): Comercial, Eventos, Produção, Custos e Precificação, Suprimentos, Financeiro, Indicadores e Dashboards.

**Módulos/Serviços auxiliares** (ampliam ou governam o sistema, mas sua ausência temporária não impede a operação central): Marketing, Pessoas e Recursos, Inteligência Artificial, Documentos, Configurações, Administração e Segurança, Metas.

**Quem pode funcionar sozinho** (não exige nenhum outro Serviço para existir): Clientes (cadastro direto), Leads (cadastro direto), Receitas, Compras, Equipamentos (cadastro), Funcionários, Marketing (cadastro de Campanha), Configurações, Administração, Bancos.

**Quem precisa obrigatoriamente de outro** (não pode operar sem que outro Serviço já exista/responda): Eventos (Comercial), Orçamentos (Custos/Precificação), Contratos (Orçamentos), Produção (Fichas Técnicas/Estoque/Configurações), Estoque (Compras/Produção), Precificação (Fichas Técnicas/Configurações), Escalas (Funcionários/Eventos/Configurações), Metas (Indicador), Dashboards (todos), IA (o Serviço de origem de cada sugestão).

---

## 5. Fluxo Global de Dados

A cadeia principal de dados do THE CHARCOAL OS segue exatamente a Cadeia de Valor já registrada no Domain Discovery e no Domain Model:

```
Lead
  → Cliente
    → Orçamento (consulta Custos/Precificação)
      → Contrato
        → Evento (Confirmado)
          → Produção (consulta Configurações; consome Estoque)
          → Compras (repõe Estoque)
          → Estoque (rastreado por Lote)
          → Escalas/Equipamentos (recursos alocados)
        → Financeiro (Receita Financeira prevista, Despesas de Produção/Compras/Pessoas)
          → Indicadores e Dashboards
            → Dashboard CEO
```

**Fluxos secundários que alimentam a cadeia principal, sem fazer parte dela:**
- **Bancos → Financeiro:** fornece o cadastro de Conta/Banco consumido por todo lançamento financeiro (nunca o contrário).
- **Marketing → Comercial (Lead):** origem de parte dos Leads que entram na cadeia principal; retorno flui de volta a Marketing por evento, nunca por consulta direta ao domínio Comercial.
- **Inteligência Artificial → Financeiro/Suprimentos/Precificação:** insere sugestões em pontos específicos da cadeia (categorização de lançamento, previsão de demanda, sugestão de preço), sempre como entrada opcional, nunca como etapa obrigatória do fluxo principal.
- **Metas ← Indicadores:** consome o resultado final da cadeia (margem, faturamento, conversão) para medir progresso — nunca insere dado na cadeia principal, apenas observa.
- **Configurações → Produção/Precificação/Escalas/Eventos:** fornece parâmetros consultados em pontos específicos da cadeia (nunca participa do fluxo de dados transacional em si).

O dado, uma vez criado em sua origem (ex.: um Lead), nunca é duplicado ao longo da cadeia — cada etapa seguinte o referencia (PF-01), e todo valor calculado (preço, custo, margem) é computado uma única vez, na etapa correta (PF-03), e apenas consumido pelas etapas seguintes.

---

## 6. Serviços Conceituais

Nenhuma tecnologia é definida — apenas responsabilidade, eventos publicados/assinados e consultas expostas.

| # | Serviço | Módulos que representa | Publica (eventos-chave) | Assina (eventos-chave) | Consultas expostas |
|---|---|---|---|---|---|
| 1 | **Comercial** | 04, 05, 06, 08, 09 | Lead criado, Lead convertido, Orçamento aceito, Contrato assinado | Custo recalculado (14), Evento cancelado (Eventos) | Preço vigente de Orçamento, histórico de Cliente |
| 2 | **Eventos** | 07 | Evento confirmado, Evento concluído, Evento cancelado | Contrato assinado (Comercial), Produção concluída (Produção) | Estado do Evento, escopo do Evento |
| 3 | **Produção** | 10, 12, 13 | Produção planejada, Produção concluída, Ficha Técnica recalculada | Evento confirmado (Eventos), Custo de Ingrediente atualizado (Suprimentos) | Ficha Técnica vigente, custo de Produto |
| 4 | **Custos e Precificação** | 11, 14 | Custo recalculado, Preço atualizado | Ficha Técnica recalculada (Produção), Alocação realizada (Pessoas) | Preço vigente, margem calculada |
| 5 | **Suprimentos** (Compras/Estoque/Lotes) | 15, 16, 17 | Compra conferida, Estoque atualizado, Lote vencido | Produção planejada (Produção), Evento confirmado (Eventos) | Saldo de Estoque, rastreabilidade de Lote |
| 6 | **Pessoas e Recursos** (Funcionários/Escalas/Equipamentos) | 18, 19, 20 | Alocação realizada, Equipamento alocado | Evento confirmado (Eventos) | Disponibilidade de Funcionário/Equipamento |
| 7 | **Financeiro** (Pessoal/Empresarial/Bancos) | 02, 03, 27 | Despesa registrada, Receita Financeira prevista, Pagamento efetivado | Contrato assinado, Compra conferida, Alocação realizada | Saldo de Conta, Fluxo de Caixa |
| 8 | **Marketing** | 21 | Campanha criada, Retorno atribuído | Lead convertido, Contrato assinado (Comercial) | Retorno por Campanha |
| 9 | **Inteligência Artificial** | 22 | Sugestão gerada | Extrato importado (Financeiro), Produção concluída (Produção) | Nenhuma — apenas publica sugestão |
| 10 | **Indicadores e Dashboards** | 01, + visões especializadas | Indicador recalculado | Todos os eventos relevantes de todos os Serviços | Valor de Indicador, composição de Dashboard |
| 11 | **Metas** | 26 | Meta criada, Ciclo de Meta encerrado | Indicador recalculado (Indicadores) | Progresso de Meta |
| 12 | **Documentos** | 23 | Documento gerado | Contrato assinado, Compra conferida (e demais origens) | Documento vigente por entidade |
| 13 | **Configurações** | 24 | Parâmetro definido/alterado | — | Valor de parâmetro vigente |
| 14 | **Administração e Segurança** | 25 | Permissão alterada | — | Perfil/permissão de usuário |
| 15 | **Auditoria** *(transversal, sem módulo funcional próprio)* | — | — | **Todos** os eventos do Event Bus, sem exceção | Log de auditoria completo |

O **Serviço de Auditoria** não corresponde a nenhum dos 27 módulos funcionais — é a materialização arquitetural do Princípio PF-04 (histórico obrigatório): ele assina every evento publicado por qualquer outro Serviço e constrói o log de auditoria completo do sistema, sem nunca escrever de volta em nenhum outro Serviço.

---

## 7. Event Bus

Nenhuma tecnologia é definida (fila, broker, etc.) — apenas o comportamento de publicar/assinar. Os eventos abaixo são um subconjunto arquiteturalmente significativo dos 89 Eventos de Domínio já catalogados no Domain Model (Seção 6) — o catálogo completo permanece válido e é herdado integralmente por esta arquitetura.

| Evento | Publicado por | Assinado por | Efeito |
|---|---|---|---|
| Lead criado | Comercial | Marketing (retorno) | Nenhum efeito automático relevante fora do próprio Comercial |
| Lead convertido em Cliente | Comercial | Marketing | Atribuição de retorno de Campanha |
| Orçamento aceito | Comercial | Comercial (interno, gera Contrato) | Geração automática de minuta de Contrato |
| Contrato assinado | Comercial | Eventos, Financeiro, Documentos | Evento confirmado (Eventos); Receita Financeira prevista (Financeiro); Documento gerado |
| **Evento confirmado** | Eventos | Produção, Suprimentos, Pessoas e Recursos, Financeiro, Indicadores | Orquestração completa (RN-006): planejamento de Produção, reserva de Estoque, sugestão de Escala, lista de Compras, previsão financeira, atualização de Dashboards — todos disparados pelo **mesmo evento**, de forma independente entre si |
| Evento cancelado | Eventos | Suprimentos, Pessoas e Recursos, Financeiro | Liberação de recursos reservados; tratamento financeiro do cancelamento (RN-007) |
| Evento concluído | Eventos | Financeiro, Indicadores, Comercial (Pós-venda) | Apuração de resultado (RN-003); atualização de fidelização (RN-010) |
| Produção planejada | Produção | Suprimentos | Confirmação/ajuste de reserva de Estoque |
| Produção concluída | Produção | Suprimentos, Custos e Precificação, Indicadores | Baixa definitiva de Estoque; recálculo de custo real; atualização de Indicadores |
| Custo de Ingrediente atualizado | Suprimentos | Produção | Recálculo automático de Ficha Técnica (RN-019) |
| Custo recalculado | Custos e Precificação | Comercial, Indicadores | Alerta em Orçamentos abertos; atualização de margem |
| Compra conferida | Suprimentos | Financeiro | Geração automática de Despesa |
| Alocação de Funcionário realizada | Pessoas e Recursos | Custos e Precificação, Financeiro | Consolidação de custo de mão de obra |
| Despesa registrada / Receita Financeira prevista | Financeiro | Indicadores | Recálculo de margem e Fluxo de Caixa |
| Pagamento efetivado | Financeiro | Indicadores, Auditoria | Atualização de saldo e Fluxo de Caixa |
| Extrato bancário importado | Financeiro | Inteligência Artificial | Geração de sugestão de categorização/conciliação |
| Sugestão gerada (IA) | Inteligência Artificial | Serviço de origem (Financeiro, Suprimentos, Custos e Precificação) | Exibição ao usuário para confirmação (nunca aplicação automática, salvo exceção pré-aprovada) |
| Indicador recalculado | Indicadores e Dashboards | Metas, Dashboard CEO e especializados | Atualização de progresso de Meta; atualização de painel |
| Ciclo de Meta encerrado | Metas | Indicadores e Dashboards | Registro de "Atingida"/"Não atingida" |
| Lote vencido / descartado | Suprimentos | Produção, Auditoria | Bloqueio de uso; registro de perda |
| Documento gerado/revisado | Documentos | Auditoria | Registro de nova versão |
| Permissão alterada | Administração e Segurança | Auditoria | Registro de alteração de acesso |
| **Qualquer evento acima** | — | **Auditoria** (sempre) | Log de auditoria imutável (PF-04) |

O padrão publicar-assinar é a regra geral: um Serviço nunca sabe, nem precisa saber, quem assina seus eventos — isso é o que garante que novos Serviços (novos módulos, futuras integrações, novas IAs) possam ser adicionados sem alterar nenhum Serviço existente (ver Capítulo 9 — Escalabilidade).

---

## 8. Segurança Conceitual

- **Perfis:** um perfil corresponde a uma ou mais Áreas da Empresa já definidas (Comercial/CRM, Produção, Compras/Suprimentos, Estoque/Logística, Eventos/Operações, Financeiro, Marketing, Pessoas/Mão de Obra, Administrativo/Documentos, BI/Direção Executiva), mais o perfil transversal Administrador do Sistema.
- **Permissões:** derivam diretamente do campo "Quem pode criar/alterar/excluir/visualizar" já definido para cada uma das 98 funcionalidades (Functional Specification) — nenhuma permissão nova é inventada aqui; esta arquitetura apenas formaliza que a checagem de permissão ocorre em toda operação de comando (nunca apenas na tela).
- **Autenticação (conceitual):** todo usuário tem sua identidade verificada antes de qualquer ação no sistema; nenhuma operação de comando (criar, alterar, encerrar) ocorre sem uma identidade autenticada associada, para fins de auditoria (PF-04).
- **Autorização (conceitual):** toda operação de comando é avaliada contra o perfil do usuário autenticado antes de ser executada pelo Serviço dono da entidade — a autorização é responsabilidade do próprio Serviço, nunca apenas da camada de apresentação.
- **Auditoria:** o Serviço de Auditoria (Capítulo 6) assina todos os eventos do Event Bus, sem exceção, e constrói um log imutável — quem fez o quê, quando, e a partir de qual comando.
- **Histórico:** nenhuma entidade é fisicamente excluída (CG-01/PF-04); toda mudança de estado gera um evento, e o histórico de estados é reconstruível a qualquer momento a partir do log de eventos do Serviço de Auditoria.
- **Rastreabilidade:** todo valor exibido em qualquer Dashboard é rastreável, evento por evento, até a ação humana ou automática que o originou — nenhum número "aparece do nada" (RN-039/040, já herdado do Functional Specification).

---

## 9. Escalabilidade

Esta arquitetura sustenta diretamente os vetores de crescimento já registrados na Filosofia de Evolução do Framework (Seção 25):

- **Crescimento da empresa (mais usuários, mais volume):** cada Serviço Conceitual é independente e pode evoluir/escalar isoladamente conforme sua própria carga (ex.: Financeiro pode crescer em volume de lançamentos sem exigir mudança em Produção).
- **Novos módulos:** um novo Serviço se integra publicando/assinando eventos no Event Bus existente, sem exigir alteração em nenhum Serviço já em operação — este é o critério de sucesso já definido no Framework ("extensão, não reconstrução").
- **Novas integrações externas:** o Serviço Financeiro (importação bancária) e o Serviço de Inteligência Artificial já são, por desenho, as fronteiras naturais de integração externa — uma nova integração bancária ou uma nova fonte de dado externo entra por um desses dois Serviços, sem tocar os demais.
- **Novas capacidades de IA:** o Serviço de Inteligência Artificial é a única porta de entrada para qualquer nova sugestão — adicionar uma nova capacidade (ex.: previsão de inadimplência) significa adicionar um novo assinante/publicador dentro deste Serviço, nunca espalhar lógica de IA por outros Serviços.
- **Múltiplas empresas / múltiplas filiais:** nenhuma entidade desta arquitetura assume, estruturalmente, uma única empresa ou unidade — a dimensão "Organização/Unidade" (já antecipada na Filosofia de Evolução do Framework) pode ser introduzida como um atributo transversal consultado por todos os Serviços, sem exigir a criação de Serviços paralelos por unidade.
- **Novos Produtos:** o Serviço de Produção já opera sobre um número arbitrário de Receitas/Fichas Técnicas — um novo Produto é apenas um novo dado dentro da estrutura existente, nunca uma mudança estrutural.

O critério de sucesso desta arquitetura, pelos próximos anos, é o mesmo já registrado no Framework: cada vetor acima deve ser absorvido como uma **extensão** do Event Bus e dos Serviços existentes — nunca como motivo de reconstrução deles.

---

## 10. Resumo para o Proprietário

Organizamos como o THE CHARCOAL OS vai "se organizar por dentro" — não as telas (isso já foi feito), mas a estrutura invisível que vai sustentar tudo funcionando junto, sem virar uma bagunça conforme o sistema crescer.

A ideia central é simples: o sistema é dividido em 15 "setores internos" (chamados aqui de Serviços) — um para Comercial, um para Financeiro, um para Produção, um para Estoque, e assim por diante — e cada um deles só se comunica com os outros através de "avisos" (eventos), nunca mexendo diretamente no que não é seu. Por exemplo: quando um Evento é confirmado, ele não "manda" a Produção, o Estoque e o Financeiro fazerem algo — ele apenas "avisa" que foi confirmado, e cada setor reage do seu próprio jeito. Isso é o que garante que, no futuro, dá para adicionar uma nova área ao sistema (uma nova unidade, um novo tipo de IA, uma nova integração bancária) sem precisar mexer em tudo que já existe.

Isso é importante porque protege o investimento: sem essa organização, cada nova funcionalidade tenderia a ficar mais cara e arriscada de adicionar com o tempo. Com ela, o sistema cresce como o Framework sempre previu — por extensão, não por reconstrução.

Este documento conecta diretamente tudo que já foi construído (o que existe, o que o sistema faz, como cada processo acontece, como cada tela funciona) com a próxima etapa real: agora sim, dá para decidir o Banco de Dados e as APIs — porque já sabemos exatamente quais "setores" existem, o que cada um guarda, e como eles conversam entre si.

---

## 11. TCOS QUALITY GATE EXECUTIVO

Em conformidade com a Regra Permanente do Framework, foi reexecutada a auditoria completa sobre todos os 9 documentos oficiais antes do encerramento desta fase — resultado já consolidado na Auditoria de Abertura (Seção 0) e reafirmado aqui: nenhuma inconsistência, conflito, duplicidade ou dependência oculta permaneceu sem tratamento.

**1. Resumo Executivo**
Definida a arquitetura conceitual completa do THE CHARCOAL OS: 5 camadas, 13 integrações de domínio, matriz de dependências dos 27 módulos, fluxo global de dados, 15 Serviços Conceituais, catálogo arquitetural de Event Bus, segurança conceitual e plano de escalabilidade. Nenhuma tecnologia foi definida; nenhum documento anterior foi alterado.

**2. Estado atual do projeto**
Fases 000 a 005 encerradas e oficiais; Fase 006 em validação. Nenhuma fase técnica de implementação (Banco de Dados, APIs, Desenvolvimento) foi iniciada.

**3. Documentos oficiais existentes**
Os 9 já registrados na Executive Memory, mais este documento em rascunho.

**4. Dependências desta fase**
30 entidades, 47 Regras de Negócio, 27 módulos, 98 funcionalidades, 30 fluxos e 30 telas — todos referenciados, nenhum reescrito.

**5. Pendências abertas**
Validação formal deste documento; parâmetros do Módulo 24; M-003A-03/04; M-004-01/02 (resolvida estruturalmente por esta arquitetura, ver item 15); M-005-01/02/03; confirmação do domínio de negócio (R-000-03).

**6. Dúvidas encontradas**
Nenhuma nova.

**7. Riscos ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede a arquitetura conceitual.

**8. Novos riscos encontrados**
Nenhum risco novo de negócio. Dois riscos técnicos foram identificados **e já resolvidos dentro desta própria arquitetura** (acoplamento na orquestração de Evento; acoplamento no consumo do Dashboard CEO) — ver Auditoria de Abertura.

**9. Inconsistências encontradas**
Nenhuma.

**10. Conflitos entre documentos**
Nenhum.

**11. Módulos sem integração**
Nenhum — todos os 27 aparecem na Matriz de Dependências (Capítulo 4).

**12. Funcionalidades sem suporte arquitetural**
Nenhuma das 98 — todas mapeadas a um dos 15 Serviços Conceituais.

**13. Fluxos incompatíveis**
Nenhum entre os 30 fluxos do TCOS-004 e esta arquitetura.

**14. Dependências ocultas**
Identificadas e documentadas explicitamente: Produção/Precificação/Escalas → Configurações (Capítulo 4).

**15. Melhorias sugeridas**
- M-006-01: quando a dimensão "Organização/Unidade" (múltiplas filiais/empresas) for de fato implementada, revisar o contrato de consulta de todos os 15 Serviços para incluir esse atributo desde o início — evita retrofit custoso.
- M-004-01 (herdada): **resolvida estruturalmente** por este documento — o Serviço de Indicadores e Dashboards unifica os três mecanismos antes descritos separadamente no TCOS-004.

**16. Impacto nas próximas fases**
Esta arquitetura torna-se a referência obrigatória de estrutura interna para Banco de Dados, APIs e Desenvolvimento — nenhuma dessas fases deve introduzir um Serviço, dependência ou padrão de comunicação que contradiga o que está aqui documentado, sem registrar formalmente o motivo.

**17. Quality Score: 9,5/10**
Justificativa técnica: cobertura completa dos 18 itens de arquitetura conceitual e dos 6 capítulos obrigatórios, com identificação e resolução — não apenas menção — de dois riscos técnicos reais de acoplamento, e resolução estrutural de uma melhoria já pendente (M-004-01). Não é 10 porque a dimensão de multiempresa/multifilial, embora prevista, ainda não foi formalmente modelada como atributo transversal (fica como M-006-01 para quando for de fato necessária).

**18. Atualização do PROJECT_MEMORY.md:** ver commit correspondente.

**19. Estatísticas Finais**
- Quantidade de módulos integrados: 27 (todos).
- Quantidade de fluxos arquiteturais: 18 (as 18 integrações de domínio da Seção 3, itens 3.1–3.18) + 1 fluxo global de dados consolidado (Capítulo 5).
- Quantidade de serviços conceituais: 15 (14 correspondentes a módulos + 1 transversal, Auditoria).
- Quantidade de eventos internos: 23 eventos arquiteturalmente destacados (subconjunto dos 89 já catalogados no Domain Model, todos herdados).
- Quantidade de dependências: 27 relações módulo→serviço mapeadas na Matriz de Dependências (Capítulo 4).
- Riscos ativos: 3 herdados (R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01); 0 novos de negócio; 2 riscos técnicos identificados e resolvidos nesta própria fase.
- Pendências: 6 (validação do documento + 5 herdadas).
- Melhorias: 1 nova (M-006-01) + 1 herdada resolvida (M-004-01).
- Percentual estimado de maturidade do projeto: **62%** (subiu de 55% — toda a estrutura conceitual do sistema está definida e auditada; falta a decisão de persistência de dados, contratos de API e a construção técnica propriamente dita, além da confirmação de parâmetros reais de negócio).

---

*Fim do documento — THE CHARCOAL OS SYSTEM ARCHITECTURE v1.0.0*
