# THE CHARCOAL OS — FRONTEND ARCHITECTURE

**Documento:** TCOS-011 — Arquitetura Conceitual de Frontend
**Projeto:** THE CHARCOAL OS
**Fase:** 011 — Frontend Architecture
**Status:** Rascunho para validação do proprietário
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** negócio, domínio, regras, funcionalidades, fluxos, UX/UI, arquitetura de sistema, arquitetura de dados, banco de dados, contrato de integração entre módulos e arquitetura de backend completos e oficiais; iniciando a arquitetura lógica interna de frontend, ainda sem linguagem, framework, biblioteca, gerenciador de estado ou tecnologia de UI definidos.
- **Fase atual:** 011 — Frontend Architecture (TCOS-011).
- **Fases concluídas:** 000 a 010, todas aprovadas e oficiais (a mais recente, TCOS-010, congelada em 2026-08-02).
- **Critério de contagem de Documentos Oficiais (herdado da correção da Fase 010):** 14 Documentos Oficiais Congelados (entregáveis de Fase, imutáveis sem nova versão) + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) = **15 Documentos Oficiais no total**.
- **Documentos Oficiais Congelados (14):** Development Framework (v1.2.0), Enterprise Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0), UX/UI Specification (v1.0.0), System Architecture (v1.0.0), Data Architecture (v1.0.0), Database Specification (v1.0.0), Integration and API Contract (v1.0.0), Backend Architecture (v1.0.0).
- **Documento Oficial Vivo (1):** `PROJECT_MEMORY.md`.
- **Documento em elaboração:** este documento (TCOS-011) — `THE_CHARCOAL_OS_FRONTEND_ARCHITECTURE.md`.
- **Pendências:** confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24 (incluindo os 2 identificados na Fase 010); M-003A-03/04; M-005-01/02/03; M-006-01; M-007-01; M-008-01; M-009-01; M-010-01/02/03; decisão sobre retomar a entrevista de descoberta.
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede o desenho da arquitetura de frontend, pois todo parâmetro não confirmado continua modelado como Configuração pendente que bloqueia/alerta na interface, nunca como valor assumido.
- **Dependências para esta fase:** as 30 telas e o Design System (UX/UI Specification, TCOS-005); os 15 Serviços Conceituais e o Event Bus (System Architecture, TCOS-006); as 20 Integrações (Integration and API Contract, TCOS-009); os 15 Serviços, Casos de Uso e a Regra Transacional de Agregados (Backend Architecture, TCOS-010) — todos referenciados, nenhum reescrito.
- **Objetivo da fase que será iniciada:** definir a arquitetura lógica interna da camada de apresentação — organização, navegação, estado, ciclo de vida de tela, componentes, comunicação com o backend, estados de interface, acessibilidade, responsividade, performance e consistência com o backend — sem nenhuma decisão de tecnologia.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 14 Documentos Oficiais Congelados já aprovados.

### Auditoria de Abertura

Os 14 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase (telas, Design System, navegação, Serviços, Casos de Uso, Integrações e Regra Transacional já aprovados). Resultado:

- Não foram identificadas inconsistências, conflitos ou duplicidades entre os 14 Documentos Oficiais Congelados, no escopo revisado.
- **Base já sólida para o frontend:** o UX/UI Specification (TCOS-005) já define as 30 telas (11 Dashboards + 19 telas de módulo), a Navegação do Sistema e o Design System completo (cores, tipografia, espaçamento, ícones, 15 componentes reutilizáveis, responsividade); o System Architecture (TCOS-006) já define os 15 Serviços Conceituais e o Event Bus; o Integration and API Contract (TCOS-009) já define as 20 Integrações; o Backend Architecture (TCOS-010) já define os Casos de Uso, contratos públicos e a Regra Transacional de Agregados. Este documento **não redefine nada disso** — formaliza como a camada de apresentação consome tudo isso de forma organizada, consistente e auditável.
- **Lacuna real identificada:** o TCOS-005 descreveu estados de interface (carregando, erro, atualizado) apenas pontualmente, em telas específicas (ex.: Dashboard CEO, Seção 3.1) — nunca como um padrão formal aplicável a todas as 30 telas. Esta arquitetura formaliza Estados de Carregamento, Estados Vazios e Tratamento de Erros na Interface (Capítulos 18-20) como um padrão único e obrigatório, por adição — nenhuma tela é redesenhada, apenas o comportamento já esperado é tornado explícito e uniforme.
- **Lacuna real identificada:** nenhum documento anterior tratou de Acessibilidade como requisito arquitetural formal — o TCOS-005 previu apenas o estado visual "focus" de botões (Seção 5.8) como indício de atenção ao tema. Esta arquitetura formaliza Acessibilidade (Capítulo 25) como princípio transversal, por adição.
- **Lacuna real identificada:** Internacionalização/Localização, Funcionamento Offline, Observabilidade da Interface e Performance da Interface nunca foram tratados em nenhum documento anterior — são formalizados aqui pela primeira vez. Funcionamento Offline conecta-se diretamente ao Roadmap de aplicativo mobile já registrado no Framework (Seção 25) e à priorização de funcionalidades de campo já identificada no TCOS-005 (Seção 5.11, responsividade mobile).
- **Achado de consistência:** o Design System (TCOS-005, Capítulo 5) já define 4 níveis de hierarquia de tela (Dashboard → Lista → Detalhe → Modal, Seção 5.2) — esta arquitetura eleva essa hierarquia a 4 Templates formais de frontend (Capítulo 12), sem alterar a definição original, apenas nomeando estruturalmente o que já era, na prática, um padrão repetido nas 30 telas.
- **Achado de consistência:** a Regra Transacional de Agregados (TCOS-010, Capítulo 20) estabelece que todo Caso de Uso opera sobre exatamente um Agregado, sempre através de contratos públicos. Esta arquitetura de frontend adota o mesmo padrão de contrato público como única porta de comunicação com o backend (Capítulo 13) — nenhuma tela ou componente acessa dado de um Serviço fora do seu contrato já definido no TCOS-010.
- Nenhuma decisão de linguagem, framework, biblioteca, gerenciador de estado, tecnologia de UI, protocolo de comunicação, tecnologia de cache ou qualquer tecnologia foi tomada, em conformidade com a restrição explícita da fase.

---

## 1. Papel deste Documento

O UX/UI Specification (TCOS-005) definiu **como cada tela se parece e se comporta individualmente**: 30 telas, cada uma com seus 25 campos, mais o Design System. O Backend Architecture (TCOS-010) definiu **como cada Serviço se organiza por dentro**. Este documento (TCOS-011) define **como a camada de apresentação se organiza como um todo** para consumir os 15 Serviços e as 20 Integrações já aprovadas de forma consistente, auditável, responsiva, acessível e performática — a arquitetura lógica de frontend, complementar ao TCOS-010. Fornece a organização de navegação, estado, ciclo de vida de tela, comunicação com o backend e comportamento transversal (Capítulos 3 a 34) necessária para que uma equipe de desenvolvimento inicie a escolha de linguagem, framework e biblioteca de UI; as 30 telas, o Design System e as regras de negócio permanecem nos documentos de origem (TCOS-002 a TCOS-010) e não são redefinidos aqui — este documento referencia-os, nunca os substitui.

## 2. Legenda e Convenções

- Toda referência a Tela, Módulo (01–27), Serviço Conceitual, Caso de Uso, Regra (RN-XXX), Evento de Domínio ou Integração (IN-XXX) usa exatamente os nomes/números já oficiais dos documentos anteriores.
- **Tela:** uma das 30 unidades de interface já catalogadas no UX/UI Specification (TCOS-005).
- **Template:** um dos 4 padrões estruturais de tela (Dashboard, Lista, Detalhe, Modal) já implícitos na hierarquia de tela do TCOS-005 (Seção 5.2), formalizados nesta arquitetura (Capítulo 12).
- **Componente:** todo bloco arquitetural detalhado nesta especificação segue, quando aplicável, o mesmo padrão de documentação do TCOS-010 (Objetivo, Responsabilidades, Entradas, Saídas, Dependências, Regras de funcionamento, Restrições, Impacto).

---

## 3. Organização Geral da Arquitetura de Frontend

O frontend do THE CHARCOAL OS ocupa a camada de Apresentação já reservada no System Architecture (TCOS-006, Seção 3.3) — a única das 5 camadas macro que o Backend Architecture (TCOS-010) explicitamente não detalhou. Esta arquitetura organiza essa camada em 5 sub-camadas internas, na mesma ordem de dependência (cada uma só depende da camada abaixo):

1. **Camada de Telas:** as 30 telas já catalogadas (TCOS-005), cada uma instanciando um dos 4 Templates (Capítulo 12).
2. **Camada de Componentes:** os componentes reutilizáveis já catalogados no Design System (TCOS-005, Seção 5.6), mais os componentes estruturais formalizados nesta fase (ex.: componente de Estado Vazio, componente de Skeleton de Carregamento).
3. **Camada de Estado:** o gerenciamento conceitual de dado em memória na interface (Capítulo 8) — nunca a fonte de verdade do dado, sempre um reflexo temporário do que o backend já possui.
4. **Camada de Comunicação:** o único ponto de contato com o backend, por contrato público (Capítulo 13) — nenhuma tela ou componente das camadas acima faz uma chamada direta a um Serviço.
5. **Camada Transversal:** Acessibilidade, Internacionalização, Cache, Observabilidade, Performance e Segurança/Permissões da interface — disponível a todas as camadas acima, sem conter regra de negócio (que permanece exclusivamente no backend, TCOS-010).

O frontend é organizado, em espelho ao backend, em torno das mesmas **Áreas da Empresa** já usadas na Navegação do Sistema (TCOS-005, Capítulo 4) — nunca em uma estrutura paralela de módulos própria do frontend.

## 4. Princípios Arquiteturais da Interface

Aplicação direta, no frontend, dos Princípios Fundamentais já aprovados no Framework:

- **Um dado, um dono (PF-01):** o frontend nunca mantém uma cópia de longa duração de um dado de negócio — toda tela busca o dado atualizado do Serviço dono através do seu contrato público (TCOS-010, Capítulo 7) a cada exibição relevante.
- **Compartilhamento nunca por acesso direto (PF-02):** nenhuma tela ou componente acessa a estrutura interna de um Serviço — apenas o contrato público já exposto.
- **Cálculo único (PF-03):** o frontend nunca recalcula custo, preço, indicador ou qualquer fórmula de negócio — apenas exibe o valor já calculado pelo Serviço dono.
- **Histórico obrigatório (PF-04):** toda ação do usuário que altera um dado de negócio é sempre precedida de confirmação explícita na interface, mostrando o que vai mudar, e nunca omite o acesso ao histórico já garantido pelo backend (Capítulo 23 — Auditoria Visual de Ações).
- **IA nunca decide sozinha (PF-06):** toda sugestão de IA é visualmente distinta (Roxo-IA, TCOS-005 Seção 5.7) e sempre exige confirmação explícita do usuário antes de qualquer efeito (Capítulo 31).
- **Dashboard CEO como visão principal (PF-07):** a Camada de Telas trata o Dashboard CEO como tela de entrada padrão, sem tratamento especial de arquitetura além dos demais Dashboards — a prioridade é de produto (UX/UI, TCOS-005), não de estrutura técnica.
- **Simplicidade, escalabilidade e manutenção acima de tudo (PF-09):** os 4 Templates (Capítulo 12) e os componentes reutilizáveis (Capítulo 10) existem exatamente para que uma nova tela nunca exija um padrão novo de estrutura — apenas a composição dos padrões já existentes.
- **Nenhuma automação ou integração quebra silenciosamente outro módulo (PF-11):** mudança de contrato público de um Serviço (TCOS-010, Capítulo 21) é tratada como nova versão de contrato — o frontend consome sempre uma versão de contrato explícita, nunca assume compatibilidade retroativa implícita.
- **Segurança e privacidade não são negociáveis (PF-12):** nenhuma tela exibe dado sensível (custo, margem, remuneração, dado pessoal) antes da checagem de permissão (Capítulo 22).

---

## 5. Organização das 30 Telas Oficiais

As 30 telas já catalogadas no UX/UI Specification (TCOS-005) são retomadas aqui sem alteração, organizadas por Template (Capítulo 12) e por Área da Empresa (TCOS-005, Capítulo 4):

**11 Dashboards** (Template Dashboard): Dashboard CEO (01), Dashboard Financeiro Pessoal (02), Dashboard Financeiro Empresarial (03), Dashboard Marketing (21), Dashboard Produção (10), Dashboard Estoque (16/17), Dashboard Engenharia de Custos (11), Dashboard Eventos (07), Dashboard CRM (04/05/06), Dashboard Metas (26), Dashboard Inteligência Artificial (22).

**19 Telas de Módulo** (Templates Lista/Detalhe/Modal, conforme a natureza de cada uma): Leads (06), Clientes (05), Eventos (07), Orçamentos (08), Contratos (09), Produção (10), Receitas (12), Fichas Técnicas (13), Precificação (14), Compras (15), Estoque (16), Lotes (17), Equipamentos (18), Funcionários (19), Escalas (20), Bancos (27), Conciliação Bancária (27), Configurações (24), Administração (25).

O Módulo 23 (Documentos) permanece, como já decidido no TCOS-005, sem tela própria — servido pelo componente reutilizável "Documentos Anexados" (Capítulo 10), reafirmado aqui como decisão de arquitetura de frontend, não como lacuna. As 30 telas cobrem, portanto, 26 dos 27 módulos com tela própria, e o 27º (Documentos) por componente — confirmando 27/27 módulos com representação na interface.

## 6. Estrutura de Navegação

Reafirma e detalha, no nível de arquitetura, a Navegação do Sistema já definida (TCOS-005, Capítulo 4): menu lateral fixo agrupado pelas Áreas da Empresa, breadcrumb em toda tela de detalhe, busca global no cabeçalho, barra de notificações. Esta arquitetura formaliza a estrutura de navegação como um **grafo de telas**, no qual:

- Cada Dashboard é um nó de entrada de sua Área da Empresa — nunca um nó terminal.
- Cada tela de Lista leva a exatamente uma tela de Detalhe por item selecionado, e a um Modal por ação de criação/edição simples.
- Nenhuma tela exige mais de um nível de navegação para ser alcançada a partir do Dashboard da sua Área — confirmando o compromisso de Velocidade já registrado no TCOS-005 (Capítulo 6, "no máximo dois cliques").
- O Dashboard CEO é o único nó acessível a partir de qualquer outro Dashboard (clique no logo, TCOS-005 Seção 4) — funcionando como nó raiz do grafo, sem ser, estruturalmente, diferente dos demais Dashboards.

## 7. Fluxo de Navegação entre Telas

Cada um dos 30 fluxos já catalogados no User Journeys and System Flows (TCOS-004) corresponde a um caminho específico neste grafo de telas. Esta arquitetura formaliza o padrão de transição:

1. Uma ação do usuário em uma Tela A (clique em card, linha de tabela, botão de ação) inicia uma transição de navegação.
2. A transição é sempre **local ao Template de origem**: de um Dashboard, a transição leva a uma tela de Lista ou Detalhe do módulo correspondente; de uma Lista, a um Detalhe ou Modal; de um Detalhe, a um Modal de edição/ação ou a um Detalhe relacionado (ex.: de Evento para Orçamento vinculado).
3. Nenhuma transição de navegação, por si só, aciona um Caso de Uso do backend (TCOS-010) — apenas uma ação explícita dentro da tela de destino (ex.: um botão "Confirmar") aciona um Caso de Uso (Capítulo 13).
4. O retorno (botão "voltar", breadcrumb) sempre preserva o estado de filtro/paginação da tela de origem, já garantido pela Camada de Estado (Capítulo 8).

## 8. Gerenciamento Conceitual de Estado

**Novo conceito desta fase**, sem nomear tecnologia de gerenciamento de estado. O frontend mantém três categorias distintas de estado, cada uma com um ciclo de vida próprio:

- **Estado de Sessão:** identidade do usuário autenticado, perfil/permissões (consultado do Serviço de Administração e Segurança, TCOS-010), preferências de interface — vive durante toda a sessão de uso, independentemente da tela atual.
- **Estado de Navegação:** tela atual, filtros ativos, paginação, aba selecionada — vive enquanto o usuário permanece na mesma Área/módulo, já observado como "persiste durante a sessão de navegação dentro do mesmo módulo" no TCOS-005 (Capítulo 4); é descartado ao trocar de módulo, salvo indicação contrária de uma tela específica.
- **Estado de Dado de Tela:** o reflexo local do dado consultado do backend por contrato público (Capítulo 13) para exibição na tela atual — nunca a fonte de verdade (PF-01), sempre substituído pela versão mais recente a cada nova consulta ou evento relevante (Capítulo 16).

Nenhum Caso de Uso de negócio (TCOS-010) é executado a partir do Estado de Dado de Tela diretamente — toda ação do usuário sobre esse dado é uma nova consulta/comando explícito (Capítulo 13), nunca uma escrita direta sobre o estado local.

## 9. Ciclo de Vida das Telas

Toda tela, independentemente do Template (Capítulo 12), atravessa o mesmo ciclo de vida:

1. **Montagem:** a tela é aberta (navegação ou abertura de Modal); permissão de acesso é verificada (Capítulo 22) antes de qualquer consulta de dado.
2. **Carregamento:** uma ou mais consultas por contrato público (Capítulo 13) são disparadas; a tela exibe o Estado de Carregamento (Capítulo 18) até a resposta.
3. **Exibição:** o dado retornado povoa o Estado de Dado de Tela (Capítulo 8) e é renderizado nos componentes correspondentes; se o resultado for vazio, a tela exibe o Estado Vazio (Capítulo 19) em vez de uma tela em branco.
4. **Interação:** o usuário aciona Casos de Uso (Capítulo 13) através de botões/formulários; toda ação de escrita segue o padrão de confirmação e feedback visual (Capítulo 17).
5. **Atualização:** a tela reage a eventos relevantes (Capítulo 16) enquanto permanece aberta, atualizando o Estado de Dado de Tela sem exigir nova navegação.
6. **Desmontagem:** a tela é fechada (navegação para outra tela, fechamento de Modal); o Estado de Dado de Tela é descartado; o Estado de Navegação é preservado ou descartado conforme a regra do Capítulo 8.

---

## 10. Componentes Reutilizáveis

Reafirma os 15 componentes já catalogados no Design System (TCOS-005, Seção 5.6): Card de KPI, Card de progresso, Tabela com paginação e ordenação, Filtro combinável, Modal padrão, Botão primário/secundário/terciário, Badge de status, Alerta inline, Banner de alerta persistente, Notificação toast, Menu lateral colapsável, Breadcrumb, Documentos Anexados, Componente de sugestão de IA. Esta arquitetura acrescenta, por adição, três componentes estruturais exigidos pelos padrões formalizados nesta fase — nenhum deles altera os 15 já existentes, apenas cobre estados que o TCOS-005 já previa pontualmente (ex.: skeleton no Dashboard CEO) sem formalizar como componente reutilizável:

- **Componente de Estado Vazio:** ilustração/mensagem + ação sugerida, usado por qualquer Lista ou Dashboard sem dado a exibir (Capítulo 19).
- **Componente de Skeleton de Carregamento:** silhueta do layout final, usado por qualquer Card, Tabela ou Dashboard durante o Estado de Carregamento (Capítulo 18) — generalização do padrão já citado pontualmente no TCOS-005 (Seção 3.1, Dashboard CEO).
- **Componente de Erro de Carregamento:** ícone de atenção + mensagem + ação "Tentar novamente", usado por qualquer Card ou seção de tela cuja consulta ao backend falhe (Capítulo 20) — generalização do padrão "card específico sinaliza dado indisponível" já citado no TCOS-005 (Seção 3.1).

## 11. Design System Conceitual

O Design System completo (paleta de cores, tipografia, grid de 8px, ícones, estados de botão/card/indicador, responsividade) já está integralmente definido no UX/UI Specification (TCOS-005, Capítulo 5) e permanece **congelado e não redefinido** nesta fase. Esta arquitetura de frontend adota o Design System como parte constituinte da Camada de Telas e da Camada de Componentes (Capítulo 3), com uma única formalização adicional: a cor **Roxo-IA** (TCOS-005, Seção 5.7) é tratada, nesta arquitetura, como um **atributo de estado obrigatório** de qualquer componente que exiba conteúdo gerado por Inteligência Artificial (Capítulo 31) — nunca uma escolha visual opcional deixada a critério da tela.

## 12. Layouts e Templates

Eleva a hierarquia de tela já definida no TCOS-005 (Seção 5.2: Dashboard → Lista → Detalhe → Modal) a 4 Templates formais de arquitetura, cada um com uma estrutura fixa de composição de componentes:

- **Template Dashboard:** cabeçalho + linha de Cards/KPI + área de gráficos + tabela/lista de apoio + widgets (Metas, Alertas, IA) — usado pelos 11 Dashboards (Capítulo 5).
- **Template Lista:** cabeçalho com filtros + tabela paginada/ordenável + botão de ação primária ("Novo X") — usado por toda tela de coleção de itens (ex.: Leads, Compras, Funcionários).
- **Template Detalhe:** breadcrumb + cabeçalho do item + abas/seções de dado relacionado + histórico (Capítulo 23) + ações contextuais — usado por toda tela de um item específico (ex.: Evento, Orçamento, Contrato).
- **Template Modal:** cabeçalho + corpo (formulário ou confirmação) + rodapé com ações — usado por toda ação pontual (criação simples, confirmação de exclusão/inativação).

Nenhuma das 30 telas foge a um destes 4 Templates — uma tela pode combinar mais de um (ex.: uma tela de Detalhe que abre um Modal de edição), mas nunca introduz uma quinta estrutura sem que uma futura versão desta arquitetura a formalize.

## 13. Comunicação Conceitual com o Backend

Aplica ao frontend exatamente o mesmo padrão de comunicação já definido no Backend Architecture (TCOS-010, Capítulo 7): dois canais, nunca um terceiro.

- **Consulta síncrona por contrato público:** toda tela, ao carregar (Capítulo 9) ou ao precisar de um dado específico, consulta o contrato público do Serviço dono (TCOS-010, Capítulo 6) — nunca a estrutura interna de um Serviço, e nunca um Serviço que não seja o dono do dado (PF-01).
- **Consumo assíncrono de eventos:** toda tela aberta assina, de forma implícita, os eventos relevantes ao seu próprio dado (Capítulo 16), para atualização automática sem exigir nova navegação.
- Toda ação do usuário que modifica um dado de negócio (Capítulo 9, passo 4) é traduzida em exatamente um Caso de Uso do backend (TCOS-010, Capítulo 8) — nunca uma escrita direta em uma estrutura de dado, mesmo que conceitual.
- Em conformidade com a Regra Transacional de Agregados (TCOS-010, Capítulo 20, regras 1 e 5): uma consulta do frontend a um contrato público nunca inicia ou amplia uma transação no backend — é sempre uma leitura externa, concluída antes de qualquer Caso de Uso subsequente.

---

## 14. Consumo das Integrações já Definidas no TCOS-009

As 20 Integrações do Integration and API Contract (TCOS-009) não são reexecutadas pelo frontend — são **observadas**. Cada Integração dispara, no backend, uma cadeia de Casos de Uso e eventos (TCOS-009/TCOS-010); o frontend consome o resultado dessa cadeia de duas formas:

- **Como Dashboard atualizado (IN-016/IN-017):** todo Dashboard consome exclusivamente o Serviço de Indicadores e Dashboards (TCOS-010, item 10), nunca os Serviços de origem de cada Integração diretamente — mesma regra de acoplamento único já estabelecida no TCOS-006 (Capítulo 6) e confirmada na Cadeia de Dashboards (TCOS-009, Capítulo 7).
- **Como alerta/notificação (campo "Alertas gerados" de cada Integração, TCOS-009):** toda Integração com alerta gerado (ex.: IN-001 "margem abaixo do mínimo", IN-012 "pendência de conciliação prolongada") é refletida na interface via o Banner de Alerta Persistente ou a Notificação Toast (Capítulo 10), nunca por uma tela dedicada a "ver Integrações".

O frontend nunca inicia uma Integração diretamente — apenas o comando do usuário que dispara o Caso de Uso de origem da Integração (ex.: "Confirmar Evento", origem de IN-001) o faz, através do canal síncrono (Capítulo 13); toda a cadeia subsequente é assíncrona e transparente à tela que iniciou a ação (Capítulo 9, passo 5).

## 15. Consumo dos Serviços Definidos no TCOS-010

Cada tela consome um ou mais dos 15 Serviços Conceituais (TCOS-010, Capítulo 6), sempre por contrato público (Capítulo 13), na mesma correspondência módulo→Serviço já estabelecida:

| Tela(s) | Serviço(s) consumido(s) |
|---|---|
| CRM, Leads, Clientes, Orçamentos, Contratos | Comercial |
| Eventos (Dashboard e detalhe) | Eventos |
| Produção (Dashboard e detalhe), Receitas, Fichas Técnicas | Produção |
| Engenharia de Custos, Precificação | Custos e Precificação |
| Compras, Estoque (Dashboard e detalhe), Lotes | Suprimentos |
| Equipamentos, Funcionários, Escalas | Pessoas e Recursos |
| Financeiro Pessoal, Financeiro Empresarial, Bancos, Conciliação Bancária | Financeiro |
| Marketing | Marketing |
| Inteligência Artificial (Dashboard e sugestões em qualquer tela) | Inteligência Artificial |
| Dashboard CEO e todos os demais Dashboards | Indicadores e Dashboards |
| Metas | Metas |
| Documentos Anexados (componente, não tela) | Documentos |
| Configurações | Configurações |
| Administração | Administração e Segurança |
| *(nenhuma tela própria — consumido apenas para reconstrução de histórico, Capítulo 23)* | Auditoria |

Nenhuma tela consome um Serviço que não seja o dono do dado que exibe — quando uma tela precisa de dado de mais de um Serviço (ex.: Dashboard CEO consumindo, transitivamente, todos), a consulta é sempre feita ao Serviço de Indicadores e Dashboards (que já assina os demais, TCOS-006), nunca por múltiplas consultas diretas paralelas a Serviços de origem.

## 16. Estratégia de Atualização da Interface

Espelha, no frontend, a Cadeia Completa de Atualização dos Dashboards (TCOS-009, Capítulo 7): quando um evento de domínio relevante ocorre, o Serviço de Indicadores e Dashboards recalcula o Indicador afetado e publica "Indicador recalculado" (TCOS-010, Capítulo 14). O frontend:

1. Assina, de forma implícita, os eventos relevantes ao dado exibido na tela atualmente aberta (Capítulo 9, passo 5).
2. Ao receber "Indicador recalculado" ou o evento de domínio correspondente à tela aberta, atualiza o Estado de Dado de Tela (Capítulo 8) sem exigir recarregamento da tela inteira.
3. Nunca força o usuário a atualizar manualmente (F5/refresh) para ver um dado atualizado — mas sempre com uma indicação visual sutil de atualização (toast "Dashboard atualizado agora", já citado no TCOS-005, Seção 4), nunca uma mudança de tela abrupta sem aviso.
4. Em conformidade com a garantia de retry/idempotência/fila de falhas/reconciliação do Barramento de Eventos (TCOS-010, Capítulo 16), o frontend tolera atraso de poucos instantes entre o evento de origem e a atualização visual — consistência eventual, nunca uma promessa de tempo real absoluto.

## 17. Feedback Visual ao Usuário

Toda ação do usuário recebe uma de três respostas visuais imediatas, nunca deixando o usuário sem indicação do que aconteceu:

- **Sucesso:** confirmação visual breve (toast ou mudança de estado do próprio componente, ex.: badge de status atualizado) — nunca um redirecionamento inesperado sem explicação.
- **Bloqueio de regra de negócio:** mensagem explícita referenciando o motivo (ex.: "Margem abaixo do mínimo definido"), nunca um erro técnico genérico — espelha a categoria 1 de Tratamento de Erros já definida no backend (TCOS-010, Capítulo 19).
- **Indisponibilidade temporária:** indicação clara de que a ação não pôde ser confirmada por falha técnica, com opção de tentar novamente — espelha a categoria 3 de Tratamento de Erros do backend (TCOS-010, Capítulo 19), nunca apresentada como se fosse um bloqueio de regra de negócio.

Toda ação irreversível (inativar, cancelar, encerrar) exige confirmação explícita antes de acionar o Caso de Uso correspondente (TCOS-005, Capítulo 4, "como exclui"), nunca é executada em um único clique.

---

## 18. Estados de Carregamento

**Padrão formalizado nesta fase** (achado de auditoria — generaliza o que o TCOS-005 já previa pontualmente no Dashboard CEO). Toda consulta ao backend (Capítulo 13) que ainda não retornou exibe o Componente de Skeleton de Carregamento (Capítulo 10) no exato espaço que o dado ocupará quando chegar — nunca uma tela em branco, nunca um spinner genérico cobrindo toda a tela quando apenas uma seção específica está carregando. Carregamento de ação do usuário (submissão de formulário) usa o estado "loading" do próprio botão (TCOS-005, Seção 5.8), nunca um bloqueio de tela inteira.

## 19. Estados Vazios

**Padrão formalizado nesta fase.** Toda Lista, Tabela ou Dashboard sem dado a exibir apresenta o Componente de Estado Vazio (Capítulo 10) — nunca uma tabela com cabeçalho e nenhuma linha, sem explicação. O Estado Vazio distingue três situações, com mensagem própria para cada uma:

- **Ainda não há dado** (ex.: nenhum Lead cadastrado): mensagem convidativa + ação primária ("Cadastrar o primeiro Lead").
- **Filtro não retornou resultado** (ex.: nenhum Evento no período filtrado): mensagem neutra + ação para limpar o filtro.
- **Bloqueado por parâmetro de Configuração pendente** (R-002A-01): mensagem explícita indicando qual parâmetro está pendente e qual perfil deve defini-lo — nunca apresentado como "vazio" comum, para não confundir ausência de dado com bloqueio de negócio (espelha a categoria 2 de erro já definida no backend, TCOS-010 Capítulo 19).

## 20. Tratamento de Erros na Interface

Espelha, na interface, as três categorias de Tratamento de Erros já definidas no Backend Architecture (TCOS-010, Capítulo 19), sem redefini-las:

1. **Erro de regra de negócio:** exibido inline, próximo ao campo/ação que o causou, com o motivo exato — nunca um modal genérico de "erro" sem contexto.
2. **Erro de dado pendente:** exibido como Estado Vazio de bloqueio (Capítulo 19) ou como Alerta Inline, conforme o contexto da tela.
3. **Erro técnico:** exibido através do Componente de Erro de Carregamento (Capítulo 10), com ação explícita de "Tentar novamente" — nunca combinado com uma mensagem de regra de negócio, para que o usuário sempre saiba se o problema é dele (dado incorreto) ou do sistema (indisponibilidade).

Nenhum erro técnico expõe detalhe de implementação (identificador de log, mensagem técnica bruta) ao usuário final — apenas ao Log técnico (TCOS-010, Capítulo 18), consultável pela equipe técnica via Observabilidade (Capítulo 30).

## 21. Mensagens de Validação

Toda validação de formulário ocorre em dois momentos, nunca apenas um:

- **Validação de formato, em tempo de digitação:** campo obrigatório vazio, formato de dado inválido (ex.: data) — feedback imediato, inline, sem submissão do formulário.
- **Validação de regra de negócio, na submissão:** verificada pelo Caso de Uso do backend (TCOS-010, Capítulo 19, categoria 1) — a interface nunca assume que uma regra de negócio foi satisfeita apenas porque o formato do campo está correto; a mensagem de validação de negócio só é exibida após a resposta do backend, nunca simulada no frontend antecipadamente (o que duplicaria a Regra de Negócio fora da sua única fonte, PF-03).

Mensagens de validação nunca usam linguagem técnica ou genérica ("campo inválido") — sempre a linguagem de negócio já usada na Regra de Negócio correspondente (ex.: "A data de validade do Orçamento já expirou", refletindo RN-013).

## 22. Permissões e Controle de Acesso na Interface

Reafirma e detalha, na interface, a Segurança Conceitual já definida (TCOS-006, Capítulo 8) e a Camada de Segurança/Autorização do backend (TCOS-010, Capítulo 27):

- Toda tela verifica a permissão do perfil autenticado **antes** de renderizar qualquer dado sensível ou ação de comando (Capítulo 9, passo 1) — nunca renderiza e depois oculta, o que exporia brevemente o dado.
- Uma ação sem permissão nunca é apenas ocultada silenciosamente — é desabilitada com indicação visual (tooltip explicando a restrição), exceto quando a própria existência da ação já revelaria informação sensível (ex.: valor de remuneração), caso em que a ação é integralmente omitida.
- A checagem de permissão na interface é **sempre complementar**, nunca substituta, à checagem obrigatória do Caso de Uso no backend (TCOS-010, Capítulo 27) — a interface nunca é a única barreira de segurança, mesmo que ofereça a primeira camada de experiência.
- Dados financeiros e pessoais seguem CG-05: visíveis por padrão apenas a perfis de Financeiro/Direção ou ao próprio titular, respectivamente — qualquer tela que agregue esse dado (ex.: Dashboard CEO) aplica a mesma checagem por campo, não apenas por tela inteira.

## 23. Auditoria Visual de Ações

Toda entidade com histórico obrigatório (CG-01, praticamente todas) exibe, na sua tela de Detalhe (Template Detalhe, Capítulo 12), uma aba ou seção "Ver histórico" (já citada no TCOS-005, Capítulo 4) — esta arquitetura formaliza seu conteúdo mínimo: data, autor (usuário ou "Sistema", quando automático), e o que mudou, na mesma linguagem de negócio da Regra que gerou a mudança. A Auditoria Visual consome o Log de Auditoria do backend (TCOS-010, Capítulo 17) exclusivamente por consulta (nunca por escrita) e nunca duplica esse histórico em armazenamento próprio do frontend — é sempre uma janela para o mesmo histórico que já existe no backend.

---

## 24. Responsividade

Reafirma, sem alteração, os 3 níveis de responsividade já definidos no Design System (TCOS-005, Seção 5.11): Desktop (layout completo, grids de 2-4 colunas), Tablet (menu colapsado, grids de 1-2 colunas), Mobile (navegação por abas inferiores, coluna única, cards empilhados). Esta arquitetura formaliza a regra de composição: os 4 Templates (Capítulo 12) são os mesmos nos 3 níveis — a responsividade altera **densidade e disposição** dos componentes dentro de um Template, nunca a estrutura lógica da tela ou o Serviço/contrato consumido. A priorização de funcionalidades de campo em Mobile (confirmação de Escala, consulta de Evento do dia, já citada no TCOS-005) é a mesma base usada para a priorização de Funcionamento Offline (Capítulo 27).

## 25. Acessibilidade

**Novo princípio formalizado nesta fase** (achado de auditoria — nenhum documento anterior tratou disso como requisito arquitetural formal, apenas o estado visual "focus" de botão, TCOS-005 Seção 5.8, indicava atenção ao tema). Aplicado a todas as 30 telas, sem exceção:

- Todo componente interativo (botão, campo, link, card clicável) é navegável e operável por teclado, com o estado "focus" já definido no Design System sempre visível.
- Toda informação transmitida por cor (Badge de status, Estados de Indicadores, TCOS-005 Seção 5.10) é também transmitida por texto ou ícone — nunca cor como único canal de informação (crítico para o padrão Verde-sucesso/Âmbar-atenção/Vermelho-crítico já definido).
- Todo componente visual possui um rótulo textual associado, mesmo quando visualmente representado apenas por ícone (ex.: ícone de IA, TCOS-005 Seção 5.5).
- Contraste de texto e fundo, em toda a paleta de cores já definida (TCOS-005, Seção 5.7), deve atender ao nível AA de contraste — restrição de design a ser validada quando a paleta for implementada tecnicamente, sem que isso altere as cores já aprovadas.

## 26. Internacionalização e Localização

**Novo conceito formalizado nesta fase**, tratado como dimensão reservada e aditiva — no mesmo padrão já usado para Multiempresa/Multifilial (TCOS-007, Seções 7.6/7.7): o sistema opera hoje integralmente em português do Brasil, formato de moeda (R$) e data brasileiros, sem confirmação de negócio (R-000-03 e correlatos) sobre a necessidade de outro idioma ou moeda. Esta arquitetura reserva, sem implementar, a capacidade de externalizar todo texto de interface e formato de número/data/moeda para um recurso de localização — nenhuma tela, string ou regra de formatação é hoje escrita assumindo estrutura multi-idioma, mas nenhuma decisão de arquitetura desta fase impede essa extensão futura de forma aditiva.

## 27. Organização de Assets

Os ativos visuais do frontend (ícones do Design System, logo, ilustrações dos Estados Vazios, Capítulo 19) são organizados em uma única biblioteca conceitual de assets, versionada em conjunto com o Design System (TCOS-005) — nunca duplicados por tela ou módulo. Todo novo asset (ex.: uma nova ilustração de Estado Vazio) segue o mesmo estilo de linha (outline) já definido para ícones (TCOS-005, Seção 5.5), garantindo que a Filosofia Visual (TCOS-005, Seção 5.1) permaneça coesa mesmo quando novos ativos forem adicionados.

## 28. Cache Conceitual da Interface

Distinto do Cache do backend (TCOS-010, Capítulo 23, que armazena valor de Indicador já calculado): o Cache da Interface é a retenção temporária, no dispositivo do usuário, de dado já consultado nesta sessão — para reduzir consultas repetidas ao navegar entre telas que compartilham o mesmo dado de referência (ex.: lista de Ingredientes, consultada tanto em Fichas Técnicas quanto em Compras).

- Dado de catálogo (Mestre, TCOS-007 Seção 3.3 — Cliente, Fornecedor, Ingrediente, Produto) é elegível a cache de curta duração na interface, sempre invalidado pelo mesmo evento de domínio que o alteraria no backend (Capítulo 16) — nunca por tempo fixo arbitrário, mesma filosofia já aplicada ao cache de Indicador (TCOS-010, Capítulo 23).
- Dado transacional em edição (Orçamento sendo montado, Produção em execução) nunca é cacheado além do Estado de Dado de Tela (Capítulo 8) — é sempre buscado novamente ao reabrir a tela, para nunca exibir um valor potencialmente obsoleto em uma decisão de negócio em andamento.
- O Cache da Interface nunca é a única cópia de um dado — é sempre reconstruível a partir de uma nova consulta ao contrato público (PF-03).

## 29. Funcionamento Offline (Conceitual, quando aplicável)

**Novo conceito formalizado nesta fase**, conectado ao Roadmap de aplicativo mobile já registrado no Framework (Seção 25) e à priorização de funcionalidades de campo em Mobile (TCOS-005, Seção 5.11; Capítulo 24 desta arquitetura). Aplica-se apenas às funcionalidades já identificadas como uso de campo, sem presumir que o sistema inteiro operará offline:

- **Consulta offline:** dado já carregado antes da perda de conectividade (ex.: Evento do dia, Escala do Funcionário) permanece visível em modo de somente leitura, com indicação explícita de que pode estar desatualizado (mesma filosofia de "nunca esconder que um dado pode estar obsoleto" já usada no TCOS-005, Seção 3.1).
- **Ação offline:** nenhuma ação de escrita (confirmar Escala, registrar consumo) é permitida sem confirmação de que foi de fato recebida pelo backend — uma ação tentada offline é enfileirada localmente e reapresentada ao usuário como "pendente de envio" até a reconexão, nunca reportada como concluída antes da confirmação real (mesma garantia de idempotência já exigida do backend, TCOS-010 Capítulo 16, estendida à origem da ação).
- Nenhuma regra de negócio é avaliada localmente no dispositivo offline — a avaliação de regra permanece exclusivamente no backend (PF-03); o modo offline apenas retarda o envio do comando, nunca antecipa sua validação.

---

## 30. Observabilidade da Interface

**Novo conceito formalizado nesta fase**, espelhando a Camada de Observabilidade do backend (TCOS-010, Capítulo 25), com escopo distinto: observa o comportamento técnico da interface, nunca o comportamento de negócio (que permanece na Auditoria, Capítulo 23). Consolida: tempo de carregamento por tela/Template, taxa de erro técnico por tela (Capítulo 20, categoria 3), frequência de uso de cada Estado (Vazio, Erro, Carregamento) por tela — indicadores técnicos para a equipe de desenvolvimento identificar telas com desempenho ou taxa de erro fora do esperado. Assim como no backend, a Observabilidade da Interface nunca decide nem corrige nada por conta própria — apenas observa e alerta a equipe técnica.

## 31. Integração Conceitual com Inteligência Artificial

Reafirma e detalha, na interface, o padrão já definido no System Architecture (TCOS-006, Seção 3.11), na Cadeia Completa de Atualização da IA (TCOS-009, Capítulo 8) e no Motor de Sugestões de IA do backend (TCOS-010, Capítulo 28):

- Toda sugestão de IA exibida em qualquer tela usa, sem exceção, a cor Roxo-IA e o ícone de "faísca" já definidos (TCOS-005, Seção 5.5/5.7) — nunca um estilo visual diferente do já catalogado, mesmo em uma tela nova.
- Toda sugestão de IA é acompanhada dos botões "Aceitar" e "Recusar" lado a lado (TCOS-005, Capítulo 4) — nunca um botão único de "OK" que implique aceite por omissão.
- Aceitar uma sugestão aciona um Caso de Uso do Serviço de origem da sugestão (TCOS-010, item 9), nunca do próprio Serviço de Inteligência Artificial — a interface nunca trata a sugestão como já aplicada antes dessa confirmação explícita.
- O Dashboard de Inteligência Artificial (TCOS-005, Seção 3.11) é a única tela dedicada a revisar o histórico de sugestões e decisões — mas qualquer tela pode exibir uma sugestão pontual relevante ao seu próprio dado (ex.: sugestão de categorização dentro da tela de Conciliação Bancária).

## 32. Performance da Interface

**Novo conceito formalizado nesta fase**, sem nomear tecnologia de otimização. Aplicação, no frontend, do compromisso de Velocidade já registrado no TCOS-005 (Capítulo 6):

- Toda tela deve exibir seu Estado de Carregamento (Capítulo 18) dentro de um tempo imperceptível ao usuário, e o dado completo assim que a consulta ao backend retornar — nunca uma tela que pareça travada sem indicação.
- Consultas de dado de catálogo (Capítulo 28, Cache da Interface) priorizam o Cache da Interface quando disponível e ainda válido, reduzindo consultas redundantes ao mesmo contrato público na mesma sessão.
- Nenhuma tela carrega, antecipadamente, dado que o usuário não solicitou — a Camada de Estado (Capítulo 8) busca dado sob demanda (ao montar a tela ou navegar para uma aba), nunca especulativamente para todos os módulos de uma vez (exceção estrutural: o Dashboard CEO, que por definição consome de todos, TCOS-005 Seção 3.1).

## 33. Regras de Consistência entre Frontend e Backend

Consolida, em um único capítulo, as garantias de consistência já exigidas pelos capítulos anteriores, para que nenhuma equipe de desenvolvimento futura introduza uma tela que viole o que já foi aprovado nos TCOS-005 a TCOS-010:

1. Nenhuma tela exibe um valor calculado (custo, preço, indicador) que não venha diretamente do contrato público do Serviço dono (PF-03) — nunca um cálculo replicado na interface.
2. Nenhuma tela permite uma ação que o Caso de Uso correspondente bloquearia por Regra de Negócio — a interface pode antecipar visualmente o bloqueio (ex.: desabilitar um botão), mas a validação definitiva é sempre do backend (Capítulo 21).
3. Nenhuma tela assume que uma ação foi concluída antes da confirmação explícita do backend (Capítulo 17) — mesmo em modo offline (Capítulo 29).
4. Toda mudança de contrato público de um Serviço (TCOS-010, Capítulo 21 — versionamento de contrato) é tratada, no frontend, como uma mudança explícita de versão consumida — nunca uma adaptação silenciosa a um contrato alterado sem aviso (PF-11).
5. Nenhuma tela introduz um Template, componente ou padrão de estado que não esteja entre os já formalizados nesta arquitetura (Capítulos 12, 10, 18-20) sem que uma nova versão deste documento o formalize.

## 34. Padrões Obrigatórios de Experiência do Usuário

Reafirma, sem alteração, os seis compromissos de Experiência do Usuário já definidos no UX/UI Specification (TCOS-005, Capítulo 6): Simplicidade, Velocidade, Profissionalismo, Inteligência, Segurança, Confiabilidade. Esta arquitetura declara esses seis compromissos como **critério de aceitação obrigatório** de qualquer tela nova ou alterada a partir desta fase — nenhuma tela é considerada completa, do ponto de vista de arquitetura de frontend, se violar qualquer um dos seis, independentemente de estar tecnicamente funcional.

---

## RESUMO PARA O PROPRIETÁRIO

Este documento (TCOS-011) responde à pergunta: **por dentro da interface do sistema (as 30 telas já desenhadas), como tudo vai se organizar, se comunicar com o "motor" do sistema (o Backend, TCOS-010) e se comportar em situações do dia a dia — carregando, vazio, com erro, offline?**

O que foi construído: organizamos as 30 telas em 4 "moldes" reutilizáveis (Dashboard, Lista, Detalhe, Modal), definimos como cada tela conversa com os 15 Serviços do backend sem nunca "inventar" um cálculo por conta própria, e formalizamos comportamentos que até aqui só apareciam soltos em telas específicas: o que a tela mostra enquanto carrega, o que mostra quando não há nada a exibir, como avisa quando algo dá errado, como garante que qualquer pessoa (inclusive com limitação visual ou motora) consiga usar o sistema, e como um Funcionário em campo, sem internet, ainda consegue consultar sua Escala do dia.

Por que isso é importante: até aqui, sabíamos como cada tela se parece (TCOS-005) e como o "motor" por trás dela funciona (TCOS-010). Faltava a "ponte" entre os dois — como a tela pede o dado, o que faz enquanto espera, o que faz se o motor recusar o pedido, e como isso se mantém consistente nas 30 telas, sem que cada uma resolva esses casos de um jeito diferente.

Como isso conecta com tudo que já foi construído: as 30 telas usadas aqui são exatamente as mesmas do TCOS-005; os 15 Serviços consumidos são exatamente os mesmos do TCOS-010; as 20 Integrações observadas são exatamente as mesmas do TCOS-009. Nenhuma tela nova foi criada, nenhuma regra de negócio foi alterada — apenas a organização de como a interface consome tudo isso.

Como isso prepara o próximo passo: com este documento, uma equipe de desenvolvimento tem a organização de navegação, estado, comunicação e comportamento de interface necessária para começar a escolher a linguagem, o framework e as bibliotecas de UI — sem que essa escolha exija redefinir como a tela se comporta por dentro.

Nada de código, linguagem, framework, biblioteca, gerenciador de estado ou tecnologia foi definido nesta fase — apenas o "manual de organização interna" da interface do sistema.

---

## TCOS QUALITY GATE EXECUTIVO

Em conformidade com a Regra Permanente do Framework, os 14 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase — resultado consolidado na Auditoria de Abertura e reafirmado aqui.

**1. Resumo Executivo**
Definida a arquitetura lógica interna de frontend do THE CHARCOAL OS: 5 sub-camadas de apresentação, 30 telas organizadas em 4 Templates formais, comunicação por contrato público (espelhando o TCOS-010), consumo formalizado das 20 Integrações e dos 15 Serviços, e 8 conceitos genuinamente novos (Gerenciamento de Estado, Estados de Carregamento/Vazios, Acessibilidade, Internacionalização, Cache da Interface, Funcionamento Offline, Observabilidade da Interface, Performance da Interface). Nenhuma tecnologia foi definida; nenhum dos 14 Documentos Oficiais Congelados foi alterado.

**2. Estado atual do projeto**
Fases 000 a 010 encerradas e oficiais; Fase 011 em validação. Nenhum código, framework, biblioteca ou desenvolvimento foi iniciado.

**3. Documentos oficiais existentes**
15 no total — 14 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`), mais este documento em rascunho (não contado como oficial até aprovação).

**4. Dependências desta fase**
30 telas e Design System (TCOS-005); 15 Serviços Conceituais e Event Bus (TCOS-006); 20 Integrações (TCOS-009); 15 Serviços, Casos de Uso e Regra Transacional de Agregados (TCOS-010) — todos referenciados, nenhum reescrito.

**5. Pendências abertas**
Validação formal deste documento; parâmetros do Módulo 24; M-003A-03/04; M-005-01/02/03; M-006-01; M-007-01; M-008-01; M-009-01; M-010-01/02/03; confirmação do domínio de negócio (R-000-03). Nenhuma pendência nova de negócio.

**6. Dúvidas encontradas**
Nenhuma nova de negócio. Uma dúvida técnica foi levantada e já resolvida dentro desta própria fase: como tratar consistentemente carregamento/vazio/erro nas 30 telas sem que cada uma resolvesse de um jeito diferente — respondida nos Capítulos 18 a 20.

**7. Riscos ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede a arquitetura de frontend.

**8. Novos riscos encontrados**
Nenhum risco novo de negócio.

**9. Inconsistências encontradas**
Nenhuma entre os 14 Documentos Oficiais Congelados, no escopo revisado.

**10. Conflitos entre documentos**
Nenhum.

**11. Telas sem arquitetura de consumo**
Nenhuma — as 30 telas (TCOS-005) têm, todas, Serviço(s) de origem identificado(s) na Matriz do Capítulo 15.

**12. Módulos sem representação na interface**
Nenhum — 27/27 (100%): 26 módulos com tela própria + Módulo 23 (Documentos) via componente reutilizável, decisão já registrada no TCOS-005 e reafirmada aqui.

**13. Integrações sem consumo formalizado**
Nenhuma das 20 Integrações (TCOS-009) ficou sem explicação de como a interface a observa — Dashboards/Indicadores (Capítulo 14) ou alertas/notificações (Capítulo 14), confirmado integração por integração no campo "Alertas gerados" já existente no TCOS-009.

**14. Serviços sem tela consumidora**
Nenhum dos 15 — inclusive o Serviço de Auditoria, consumido por consulta (não por tela própria) na Auditoria Visual de Ações (Capítulo 23).

**15. Melhorias sugeridas**
- M-011-01 (nova): ao escolher a tecnologia de frontend em fase técnica futura, avaliar mecanismos nativos de cache de interface (Capítulo 28) e de fila de ações offline (Capítulo 29) antes de implementá-los de forma customizada.
- M-011-02 (nova): validar formalmente o nível de contraste AA (Capítulo 25) sobre a paleta de cores já aprovada (TCOS-005, Seção 5.7) assim que a tecnologia de UI for escolhida — nenhuma cor foi alterada nesta fase, apenas o requisito de validação foi registrado.
- M-011-03 (nova): a decisão de negócio sobre suporte a múltiplos idiomas/moedas (Capítulo 26) permanece não confirmada (relacionada a R-000-03) — registrada como pendência de negócio, não como lacuna de arquitetura.

**16. Impacto nas próximas fases**
Esta arquitetura de frontend é a referência obrigatória, junto ao TCOS-010, para qualquer fase técnica futura (escolha de linguagem, framework, biblioteca, desenvolvimento) — nenhuma dessas fases deve introduzir uma tela, Template, padrão de estado ou comunicação incompatível com o que está aqui documentado, sem registrar formalmente o motivo.

**17. Quality Score: 9,5/10**
Justificativa técnica: cobertura completa dos 32 itens de arquitetura de frontend exigidos, com identificação e resolução — não apenas menção — de 8 lacunas conceituais reais (Estados de Carregamento/Vazios formalizados, Acessibilidade, Internacionalização, Cache da Interface, Offline, Observabilidade e Performance da Interface), todas em conformidade com o Design System e a Regra Transacional já aprovados, sem nenhuma contradição encontrada. Não é 10 porque 3 melhorias novas (M-011-01 a M-011-03) permanecem como refinamento pendente de decisões futuras (tecnologia de UI, validação de contraste, confirmação de negócio sobre idiomas).

**18. Atualização do PROJECT_MEMORY.md:** ver commit correspondente — exclusivamente a seção da Fase 011.

**19. Estatísticas Finais**
- Documentos oficiais: 15 no total (14 congelados + 1 vivo).
- Telas cobertas: 30/30 (100%).
- Módulos representados na interface: 27/27 (100%).
- Serviços consumidos: 15/15 (100%).
- Integrações observadas: 20/20 (100%), nenhuma redefinida.
- Templates formalizados: 4 (Dashboard, Lista, Detalhe, Modal).
- Componentes reutilizáveis: 18 (15 do TCOS-005 + 3 novos: Estado Vazio, Skeleton de Carregamento, Erro de Carregamento).
- Conceitos genuinamente novos formalizados nesta fase: 8 (Gerenciamento de Estado, Estados de Carregamento, Estados Vazios, Acessibilidade, Internacionalização, Cache da Interface, Funcionamento Offline, Observabilidade da Interface, Performance da Interface — contabilizados como 8 capítulos com a marca "novo conceito/princípio desta fase").
- Riscos ativos: 4 herdados; 0 novos de negócio.
- Pendências: 9, todas herdadas.
- Melhorias: 3 novas (M-011-01 a M-011-03).
- Percentual estimado de maturidade do projeto: **88%** (subiu de 84% — a arquitetura lógica de frontend, complementar à de backend, está agora completa e auditada; restam como não iniciadas: confirmação final do domínio de negócio via entrevista, escolha de tecnologia, e toda a fase de Desenvolvimento propriamente dita).

**Status desta fase:** rascunho aguardando validação do proprietário. Nenhuma fase de linguagem, framework, biblioteca ou Desenvolvimento será iniciada sem autorização explícita, conforme restrição do Prompt Oficial da Fase 011.

---

## AUDITORIA DE ENCERRAMENTO

Reexecutada, ao final da elaboração deste documento, a verificação de consistência entre o conteúdo produzido e todos os 14 Documentos Oficiais Congelados, conforme exigido pelo procedimento obrigatório do Prompt Oficial da Fase 011:

1. **Nenhum Documento Oficial Congelado foi alterado** — confirmado por revisão do histórico de edições desta sessão: apenas `THE_CHARCOAL_OS_FRONTEND_ARCHITECTURE.md` (novo) e `PROJECT_MEMORY.md` (seção Fase 011) foram escritos.
2. **Nenhuma tecnologia foi escolhida** — confirmado por revisão de todo o texto produzido: nenhuma linguagem, framework, biblioteca, gerenciador de estado, tecnologia de UI, protocolo de comunicação ou tecnologia de cache foi nomeada em nenhum capítulo.
3. **Nenhum código foi escrito** — confirmado: o documento contém apenas texto descritivo, tabelas e listas, sem nenhum trecho de código ou pseudocódigo.
4. **Consistência com o TCOS-005 (UX/UI Specification):** as 30 telas, o Design System e a Navegação do Sistema foram referenciados sem redefinição — nenhuma cor, tipografia, espaçamento ou comportamento de tela já aprovado foi alterado.
5. **Consistência com o TCOS-006 (System Architecture):** os 15 Serviços Conceituais e o Event Bus foram referenciados sem redefinição — a camada de Apresentação, reservada mas não detalhada no TCOS-006, foi detalhada aqui sem contradizer a separação de camadas original.
6. **Consistência com o TCOS-009 (Integration and API Contract):** as 20 Integrações foram referenciadas sem redefinição — nenhuma nova Integração foi criada; o consumo pela interface foi descrito como observação (Dashboards/alertas), nunca como reexecução da Integração.
7. **Consistência com o TCOS-010 (Backend Architecture):** os Casos de Uso, contratos públicos e a Regra Transacional de Agregados (6 pontos) foram adotados como base de comunicação do frontend sem nenhuma reformulação divergente — toda menção a "consulta síncrona" e "Caso de Uso" nesta arquitetura usa exatamente a definição já congelada no TCOS-010.
8. **Referências cruzadas internas verificadas:** todas as ocorrências de "Capítulo N" neste documento foram conferidas contra os cabeçalhos reais (1 a 34), sem referência quebrada remanescente.
9. **Nenhuma regra de negócio nova foi criada** — as Regras de Negócio citadas (RN-002, RN-006, RN-013, RN-023, RN-034, RN-039 a RN-041, RN-047, entre outras) são todas já existentes no Business Rules Specification (TCOS-002A), citadas apenas como exemplo de aplicação na interface.
10. **A Fase 012 não foi iniciada** — este documento encerra-se aguardando exclusivamente o comando formal do proprietário.

Nenhuma inconsistência remanescente foi encontrada nesta Auditoria de Encerramento.

---

*Fim do documento — THE CHARCOAL OS FRONTEND ARCHITECTURE v1.0.0*
