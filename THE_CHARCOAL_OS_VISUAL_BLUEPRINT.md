# THE CHARCOAL OS — VISUAL BLUEPRINT

**Documento:** TCOS-018
**Fase:** 018 — Visual Blueprint (Validação Visual Pré-Implementação)
**Natureza:** Documento de representação visual do sistema. NÃO constitui implementação, NÃO constitui Frontend, NÃO constitui código. Sua finalidade exclusiva é permitir a validação da experiência do usuário antes de qualquer desenvolvimento técnico.
**Baseline referenciada:** v1.0.0 (TCOS-000 a TCOS-017), sob a autoridade da Constituição Permanente do Projeto.
**Referência visual canônica desta fase:** `THE_CHARCOAL_OS_UX_UI_SPECIFICATION.md` (TCOS-005) e `THE_CHARCOAL_OS_FRONTEND_ARCHITECTURE.md` (TCOS-011) — em caso de divergência de nomenclatura entre documentos oficiais, prevalecem estes dois, por determinação expressa do proprietário (comando `ALTERAR`, 2026-08-02).
**Status:** Documento em Construção — Partes 1, 2 e 3 de 8 APROVADAS (Parte 3 = Capítulo 24, as 30 telas, em 3 sub-partes 3a/3b/3c, todas aprovadas) — Parte 4 de 8 em construção.

---

## EXECUTIVE MEMORY

Este documento é construído em partes, por determinação expressa do proprietário, seguindo a mesma metodologia disciplinada usada em todo o Framework: uma parte por vez, com salvamento imediato, Auditoria de Consistência e Resumo Executivo antes de cada nova parte.

**Pré-requisito cumprido:** antes de escrever qualquer conteúdo, foi executada uma Auditoria de Consistência completa sobre todos os documentos oficiais relevantes (UX/UI Specification, Frontend Architecture, Functional Specification, User Journeys and System Flows, Domain Model, Business Rules Specification, System Architecture, Data Architecture, Implementation Master Plan, Constituição Permanente, PROJECT_MEMORY.md, Executive Global Audit). O resultado foi apresentado ao proprietário, que determinou (comando `ALTERAR`): as divergências cosméticas identificadas não impedem a construção deste documento, não serão registradas como melhorias permanentes nesta fase, e serão apenas catalogadas para um único Relatório Consolidado de Padronização ao final da fase — que poderá, mediante aprovação futura do proprietário, originar um Change Request único.

**Divergências catalogadas até o momento (registro interno de acompanhamento, não uma melhoria permanente, não uma alteração documental):**

| # | Divergência | Documentos envolvidos | Tratamento nesta fase |
|---|---|---|---|
| D-01 | "Dashboard Metas" (UX/UI Spec, Frontend Architecture) vs. "Dashboard de Metas" (Functional Specification F-091, User Journeys) | TCOS-005, TCOS-011 vs. TCOS-003, TCOS-004 | Adotado "Dashboard Metas" (referência canônica desta fase) |
| D-02 | Contagem interna do UX/UI Specification: 14 componentes nomeados na Seção 5.6 vs. "15" citado no próprio Quality Gate e no Frontend Architecture | TCOS-005 (interno) | Sem efeito nesta fase — total final de 18 já validado pelo TCOS-016 |
| D-03 | "Dashboard Financeiro" não desambiguado (Pessoal vs. Empresarial) em várias passagens do User Journeys | TCOS-004 | Tratado nesta fase sempre como duas telas distintas (Dashboard Financeiro Pessoal e Dashboard Financeiro Empresarial), nunca como uma terceira tela |

Estas três divergências herdadas do TCOS-016 (M-016-01, M-016-02, referentes a contagens internas do System Architecture) permanecem registradas naquele documento, sem qualquer nova ação nesta fase.

**Metodologia de construção — Roteiro das 8 Partes (sujeito a ajuste, cada subdivisão adicional será explicitamente comunicada):**

| Parte | Conteúdo |
|---|---|
| 1 (esta) | Capítulos 1–11: Papel do Documento, Legenda, Visão Geral do Sistema, Arquitetura Visual, Mapa Geral de Navegação, Fluxo Principal do Usuário, Estrutura dos Menus, Barra Superior, Barra Lateral, Navegação Mobile, Navegação Desktop |
| 2 | Capítulos 12–23: Estrutura Visual dos Dashboards + os 11 Dashboards individuais |
| 3 | Capítulo 24: Blueprint completo das 30 telas já especificadas (poderá ser subdividida em até 3 sub-partes, dado o volume) |
| 4 | Capítulo 25: Componentes Visuais |
| 5 | Capítulo 26: Design System |
| 6 | Capítulo 27: Experiência do Usuário |
| 7 | Capítulo 28: Visualização do Sistema (detalhamento para prototipagem futura) — poderá ser subdividida |
| 8 | Resumo para o Proprietário, TCOS Quality Gate Executivo, Relatório Consolidado de Padronização |

**Registro de Aprovações por Parte:**

| Parte | Status | Observação |
|---|---|---|
| 1 | APROVADA (2026-08-02) | — |
| 2 | APROVADA (2026-08-02) | Inclui validação visual complementar dos 11 Dashboards (wireframe estrutural), aprovada pelo proprietário antes do início da Parte 3 |
| 3a | APROVADA (2026-08-02) | Cap. 24.1 (índice das 30 telas) + Cap. 24.2–24.8 (Leads, Clientes, Eventos, Orçamentos, Contratos, Produção, Receitas) |
| 3b | APROVADA (2026-08-02) | Cap. 24.9–24.14 (Fichas Técnicas, Precificação, Compras, Estoque, Lotes, Equipamentos) |
| 3c | APROVADA (2026-08-02) | Cap. 24.15–24.20 (Funcionários, Escalas, Bancos, Conciliação Bancária, Configurações, Administração) — Capítulo 24 concluído: 30/30 telas documentadas |

Nenhuma funcionalidade, regra de negócio, entidade, tela ou componente novo é criado neste documento — toda representação visual deriva exclusivamente do que já está oficialmente especificado. Onde a especificação existente descreve um layout em texto (ex.: "lista/kanban por estágio") sem atribuir formalmente um dos 4 Templates de Tela, este documento faz a inferência visual necessária e a identifica explicitamente como inferência, nunca como fato já decidido em outro documento.

---

## 1. Papel deste Documento

O THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md traduz em representação visual estruturada tudo o que já foi definido textualmente pela Functional Specification, UX/UI Specification, Frontend Architecture, User Journeys and System Flows e Domain Model. Seu papel é permitir que o proprietário **veja** o sistema — a navegação, os dashboards, as 30 telas, os componentes, o comportamento da interface — antes de autorizar a escrita da primeira linha de código.

Este documento não decide nada que já não tenha sido decidido. Ele não é uma nova camada de especificação funcional, nem substitui o Frontend Architecture (que trata de arquitetura técnica de apresentação) ou o UX/UI Specification (que trata de especificação de experiência). Ele é a camada de **visualização executiva** que conecta essas especificações a uma representação concreta e navegável em texto, servindo de insumo direto para uma eventual prototipagem visual (Figma ou ferramenta equivalente, ainda não decidida) numa fase futura, fora do escopo desta.

## 2. Legenda e Convenções

- Toda referência a Módulo, Tela, Serviço, Entidade, Regra (RN-XXX), Funcionalidade (F-XXX) ou Componente usa exatamente os nomes/números já oficiais, com prevalência de nomenclatura de UX/UI Specification e Frontend Architecture conforme determinado nesta fase (ver Executive Memory).
- **Tela:** uma das 30 unidades de navegação já catalogadas (11 Dashboards + 19 telas de módulo).
- **Template:** um dos 4 padrões estruturais já definidos pelo Frontend Architecture — Dashboard, Lista, Detalhe, Modal.
- **Componente:** um dos 18 componentes reutilizáveis já catalogados (15 herdados do UX/UI Specification + 3 novos do Frontend Architecture).
- **Área da Empresa:** um dos 10 agrupamentos de acesso já definidos (Enterprise Domain Discovery, Seção 5; reafirmado em System Architecture Cap. 8 e Security and Privacy Architecture) — usado neste documento apenas como critério de organização visual do menu, nunca como nova regra de negócio.
- **[Inferência visual]:** marcação explícita usada sempre que este documento precisa decidir um detalhe puramente visual (ex.: qual dos 4 Templates uma tela de módulo usa) que a especificação existente descreve em texto livre mas não atribui formalmente numa tabela — a inferência é sempre derivada do texto já oficial, nunca inventada.
- **[Pendente de confirmação visual]:** marcação usada para qualquer elemento que dependa de uma escolha ainda não feita fora do escopo documental (ex.: ferramenta de prototipagem, paleta em valores hexadecimais, fonte tipográfica) — nunca preenchido com um valor arbitrário.
- Cores, tipografia e demais valores de Design System são sempre referenciados pelo nome conceitual já oficial (ex.: "Brasa", "Carvão") — nenhum valor hexadecimal, nenhuma medida em pixels além da unidade de grid de 8px, e nenhum nome de fonte são definidos em nenhum documento oficial até o momento; este documento não inventa nenhum desses valores.

## 3. Visão Geral do Sistema

O THE CHARCOAL OS é acessado como uma aplicação web responsiva única, com uma superfície de 27 módulos organizados em 10 Áreas da Empresa (mais o perfil transversal Administrador do Sistema), entregues visualmente através de 30 telas: 11 Dashboards (visão consolidada e indicadores por Área) e 19 telas de módulo (operação do dia a dia — Listas, Detalhes e Modais).

O ponto de entrada do sistema é sempre a tela de login. Após autenticação, o usuário é redirecionado automaticamente para o Dashboard mais relevante ao seu Perfil (ex.: um Perfil de Produção entra diretamente no Dashboard Produção; um Perfil com acesso executivo entra no Dashboard CEO) — comportamento já definido em UX/UI Specification, Capítulo 4, e apoiado pela Herança de Permissões já formalizada em Security and Privacy Architecture (TCOS-012).

A partir de qualquer Dashboard, o usuário acessa as telas de módulo da sua Área através do menu lateral fixo, nunca mais do que dois níveis de navegação de distância — compromisso já formalizado em UX/UI Specification, Capítulo 6, e Frontend Architecture, Capítulo 6. O Dashboard CEO funciona como nó raiz do grafo de navegação visual do sistema: é sempre alcançável a partir de qualquer outra tela através do clique no logotipo do cabeçalho.

O sistema opera hoje inteiramente em português brasileiro, com valores em Real (R$) e formato de data brasileiro — capacidade de multi-idioma e multi-moeda está reservada arquiteturalmente (Frontend Architecture, Capítulo 26) mas não implementada, permanecendo vinculada ao risco de negócio ainda não confirmado R-000-03 (domínio de negócio formalmente pendente de confirmação).

## 4. Arquitetura Visual

A Arquitetura Visual deste documento mapeia, sem alterar ou substituir, as 5 sub-camadas de apresentação já oficialmente definidas em Frontend Architecture (Capítulo 3). Nenhuma camada nova é criada; este capítulo apenas organiza a leitura visual do sistema em cinco níveis crescentes de concretude:

1. **Camada de Navegação** — o esqueleto fixo em toda tela: barra superior, barra lateral, breadcrumb, navegação mobile (Capítulos 7 a 11 deste documento).
2. **Camada de Tela** — as 30 telas, cada uma classificada em um dos 4 Templates (Dashboard, Lista, Detalhe, Modal) já definidos pelo Frontend Architecture, Capítulo 12 (Capítulos 12 a 24 deste documento).
3. **Camada de Componente** — os 18 componentes reutilizáveis já catalogados, que preenchem o conteúdo de cada Tela (Capítulo 25 deste documento).
4. **Camada de Estado Visual** — os estados que qualquer Tela ou Componente pode assumir: carregando (skeleton), vazio, erro, normal, destaque — já definidos em Frontend Architecture, Capítulos 17 a 20, e UX/UI Specification, Capítulo 5 (integrado ao Capítulo 26 — Design System, e ao Capítulo 27 — Experiência do Usuário, deste documento).
5. **Camada de Feedback** — alertas inline, banners persistentes, notificações toast, e o painel de notificações do cabeçalho — já definidos em UX/UI Specification, Capítulo 5.6, e Capítulo 4 (integrado aos Capítulos 8 e 27 deste documento).

Esta organização em cinco camadas é uma representação visual da mesma arquitetura já aprovada — não introduz nenhum conceito técnico novo, nenhuma tecnologia e nenhuma decisão de implementação.

## 5. Mapa Geral de Navegação

O grafo de navegação do THE CHARCOAL OS tem o Dashboard CEO como nó raiz. A partir dele, o menu lateral organiza os 27 módulos em 10 seções colapsáveis, uma por Área da Empresa, mais uma seção transversal para o Administrador do Sistema — estrutura de agrupamento já definida em UX/UI Specification, Capítulo 4 ("menu lateral fixo, com os 27 módulos agrupados pelas mesmas Áreas da Empresa já definidas").

**[Inferência visual]** — a especificação existente define as 10 Áreas e afirma que os módulos são agrupados por elas, mas não publica uma tabela explícita de "qual módulo pertence a qual Área" para fins de menu. Este documento infere esse agrupamento a partir das responsabilidades centrais e entidades-chave já registradas em Enterprise Domain Discovery, Seção 5, System Architecture, Capítulo 8, e Security and Privacy Architecture:

| Área da Empresa | Módulos agrupados no menu |
|---|---|
| BI / Direção Executiva | 01 Dashboard CEO, 22 Inteligência Artificial, 26 Metas |
| Comercial / CRM | 04 CRM, 05 Clientes, 06 Leads, 08 Orçamentos |
| Produção | 10 Produção, 11 Engenharia de Custos, 12 Receitas, 13 Fichas Técnicas, 14 Precificação |
| Compras / Suprimentos | 15 Compras |
| Estoque / Logística | 16 Estoque, 17 Lotes, 18 Equipamentos |
| Eventos / Operações | 07 Eventos |
| Financeiro | 02 Financeiro Pessoal, 03 Financeiro Empresarial, 27 Bancos |
| Marketing | 21 Marketing |
| Pessoas / Mão de Obra | 19 Funcionários, 20 Escalas |
| Administrativo / Documentos | 09 Contratos, 23 Documentos (via componente contextual, sem tela própria) |
| Administrador do Sistema (transversal) | 24 Configurações, 25 Administração do Sistema |

Este agrupamento é exclusivamente de organização visual do menu — não é uma nova regra de negócio nem uma redefinição de Perfil de acesso; a autorização real de cada módulo continua determinada exclusivamente pela Herança de Permissões já definida em Security and Privacy Architecture (TCOS-012).

A partir de cada seção do menu, o usuário alcança: o Dashboard da Área (quando existente) em um clique; a Lista de cada módulo da Área em um clique; o Detalhe de um item específico em dois cliques (Dashboard/Menu → Lista → Detalhe); um Modal de criação/edição rápida a partir de qualquer Lista ou Detalhe, sem navegação de página — nenhuma tela do sistema exige mais de dois níveis de navegação a partir do seu Dashboard de Área, compromisso já formalizado em Frontend Architecture, Capítulo 6.

## 6. Fluxo Principal do Usuário

O fluxo principal — aquele que qualquer novo usuário percorre nas primeiras interações — segue a sequência já formalizada em User Journeys and System Flows (TCOS-004) e reafirmada em UX/UI Specification:

1. **Login** — autenticação, verificação de sessão (Security and Privacy Architecture, Capítulo 25).
2. **Redirecionamento automático** ao Dashboard relevante ao Perfil do usuário.
3. **Leitura do Dashboard** — cards de KPI, gráficos e tabela de itens recentes/pendentes dão ao usuário uma visão imediata do estado da sua Área.
4. **Navegação para uma Lista** — a partir de um card, um item de tabela do Dashboard, ou do menu lateral, o usuário chega à Lista do módulo que precisa operar.
5. **Filtragem e busca** — dentro da Lista, o usuário refina por período, status ou categoria (filtros combináveis e persistentes durante a navegação no módulo, UX/UI Specification, Capítulo 4).
6. **Acesso ao Detalhe** — seleção de um item específico da Lista leva à tela de Detalhe, com abas internas quando aplicável (ex.: Evento).
7. **Ação de comando** — criação, alteração ou transição de estado (nunca "exclusão" literal — sempre Inativar/Cancelar/Encerrar/Descontinuar, UX/UI Specification, Capítulo 4), disparada a partir de um botão que aciona um Caso de Uso do backend (Frontend Architecture, Capítulo 7 — a navegação em si nunca aciona um Caso de Uso).
8. **Feedback imediato** — confirmação visual (toast, atualização de badge de status, atualização do Dashboard de origem) do resultado da ação.
9. **Retorno** — via breadcrumb, botão "voltar" ou clique no logotipo (retorno ao Dashboard CEO), preservando filtros e paginação já aplicados.

Este fluxo se repete, com variações específicas por módulo, em todas as 19 telas de módulo — as variações específicas de cada uma são detalhadas no Capítulo 24 (Blueprint completo das 30 telas).

## 7. Estrutura dos Menus

O menu principal do sistema é a barra lateral (Capítulo 9), organizada em 10 seções colapsáveis por Área da Empresa mais a seção transversal do Administrador do Sistema (ver mapa completo no Capítulo 5). Cada seção, quando expandida, lista os módulos daquela Área como itens de navegação — um item de menu por módulo com tela própria (26 módulos), mais o caso especial do Módulo 23 (Documentos), que não recebe item de menu próprio por decisão de design já registrada (UX/UI Specification e Frontend Architecture): é acessado apenas contextualmente, dentro de Contratos, Compras, Clientes e Fornecedores, através do componente reutilizável "Documentos Anexados".

Complementarmente ao menu lateral, dois outros níveis de menu existem no sistema:
- **Menu do cabeçalho (barra superior):** acesso rápido e sempre visível, independentemente da Área em que o usuário está navegando (Capítulo 8).
- **Menus contextuais dentro de Detalhe:** abas internas (ex.: Evento com abas de Equipe, Equipamento, Financeiro do Evento) — não são itens de navegação global, mas subdivisões visuais dentro de uma única tela de Detalhe.

Nenhum menu deste sistema é de profundidade maior que dois níveis (Área → Módulo), reforçando o compromisso de navegação enxuta já estabelecido no Capítulo 5.

## 8. Barra Superior

A barra superior (cabeçalho) é fixa em todas as telas do sistema, em qualquer resolução, e contém, da esquerda para a direita, conforme já especificado em UX/UI Specification, Capítulo 4, e Frontend Architecture, Capítulo 6:

- **Logotipo do THE CHARCOAL OS** — clicável, retorna sempre ao Dashboard CEO, atuando como o nó raiz do grafo de navegação visual (Capítulo 5).
- **Breadcrumb** — visível em toda tela de Detalhe, mostrando o caminho de navegação (ex.: Eventos > Evento #123 > Orçamento), permitindo retorno direto a qualquer nível anterior sem perder o estado de filtros/paginação.
- **Barra de busca global** — pesquisa simultânea em Cliente, Evento, Orçamento e Contrato (UX/UI Specification, Capítulo 4); distinta da busca local, específica de cada tela, que pesquisa apenas os itens daquela Lista.
- **Sino de notificações** — com contagem de não lidas; ao ser clicado, desliza um painel lateral com o histórico de notificações; alertas críticos (RN-047) aparecem adicionalmente como banner persistente na tela relevante até serem tratados, não apenas na notificação do cabeçalho.
- **Indicador de sugestão de IA pendente** — ícone Roxo-IA (cor exclusiva de conteúdo gerado por IA em todo o sistema), visível sempre que existir sugestão pendente de aceite/recusa em qualquer módulo, levando ao Dashboard de Inteligência Artificial (Capítulo 23).
- **Identificação do usuário e Perfil ativo** — nome do usuário e, quando aplicável, seletor de Perfil (para usuários com mais de um Perfil vinculado), seguido do acesso a Configurações da conta e Sair.

Em Navegação Mobile (Capítulo 10), a barra superior é simplificada — mantém logotipo, sino de notificações e identificação do usuário; a busca global move-se para um ícone dedicado, dado o espaço horizontal reduzido.

## 9. Barra Lateral

A barra lateral é o menu principal fixo do sistema em Desktop e Tablet (em Mobile, é substituída pela navegação inferior — Capítulo 10). Contém as 10 seções colapsáveis por Área da Empresa mais a seção do Administrador do Sistema, na ordem definida no Capítulo 5, com os seguintes comportamentos visuais já especificados:

- **Estado expandido (padrão em Desktop):** cada seção mostra o nome da Área e, quando expandida, a lista de módulos daquela Área como itens de navegação individuais; a Área correspondente à tela atualmente aberta permanece expandida por padrão.
- **Estado colapsado (padrão em Tablet, Frontend Architecture, Capítulo 24):** a barra lateral reduz-se a uma coluna estreita de ícones, um por Área da Empresa, sem os nomes dos módulos visíveis — a expansão de uma Área ocorre ao clicar seu ícone, sobrepondo temporariamente o conteúdo principal.
- **Indicador de item ativo:** o módulo/tela atualmente aberto é destacado visualmente na barra lateral (cor Brasa, conforme convenção de estado ativo do Design System) para orientação constante do usuário.
- **Rodapé da barra lateral:** acesso fixo, sempre visível independentemente do scroll do menu, para Configurações (Módulo 24) e Administração do Sistema (Módulo 25) — reforçando que esses dois módulos são transversais e não pertencem a nenhuma das 10 Áreas de negócio.

A barra lateral nunca é o único caminho de navegação para uma tela — toda tela alcançável pela barra lateral também é alcançável a partir do Dashboard correspondente, preservando o compromisso de no máximo dois cliques (Capítulo 5).

## 10. Navegação Mobile

Em resolução mobile, a navegação estrutural muda de barra lateral para uma barra de navegação inferior fixa, já especificada em UX/UI Specification, Capítulo 5.11, e Frontend Architecture, Capítulo 24, com os seguintes destinos priorizados:

- **Dashboard CEO** (ou o Dashboard relevante ao Perfil do usuário) — item inicial.
- **Eventos** — priorizado por ser a operação de campo mais frequente para Perfis operacionais.
- **Financeiro** — acesso rápido a Financeiro Pessoal ou Empresarial, conforme Perfil.
- **Notificações** — mesmo painel acessível pelo sino do cabeçalho, promovido a item de navegação principal dado o espaço reduzido do cabeçalho mobile.
- **Mais** — item que expande o acesso às demais Áreas e módulos, replicando em lista vertical simples a mesma estrutura de 10 Áreas da barra lateral desktop.

Em Mobile, todo grid de conteúdo colapsa para coluna única, cards empilham verticalmente, e tabelas transformam-se em listas de cards (um card por linha, com os campos mais relevantes visíveis e os demais acessíveis ao expandir o card) — comportamento já especificado em Frontend Architecture, Capítulo 24. Funções priorizadas para uso em campo — como confirmação de Escala (Módulo 20) e consulta do "Evento do dia" — recebem posicionamento de destaque nas primeiras dobras de tela, conforme já determinado nessa mesma especificação.

O Funcionamento Offline (Frontend Architecture, Capítulo 29) aplica-se prioritariamente ao contexto mobile: dados já carregados (ex.: Evento do dia, Escala do Funcionário) permanecem visíveis em modo somente leitura com indicação explícita de "pode estar desatualizado"; ações de escrita feitas offline ficam visualmente marcadas como "pendente de envio" até confirmação do backend — nunca reportadas como concluídas antecipadamente.

## 11. Navegação Desktop

Em resolução desktop, a navegação estrutural completa descrita nos Capítulos 8 e 9 está sempre visível simultaneamente: barra superior fixa no topo, barra lateral expandida fixa à esquerda, área de conteúdo principal ocupando o espaço remanescente com grids de 2 a 4 colunas conforme a densidade de informação de cada tela (Design System, Capítulo 26).

Em Desktop, o breadcrumb do cabeçalho é sempre visível em telas de Detalhe (nunca ocultado por espaço, ao contrário do que pode ocorrer em Tablet/Mobile), e os painéis de filtro lateral das Listas (Componente "Filtro lateral/superior combinável") são exibidos como coluna fixa lateral, em vez de um painel deslizante sobreposto — diferença de comportamento puramente responsiva, sem qualquer diferença de funcionalidade em relação a Tablet ou Mobile.

Multitarefa visual (múltiplas informações simultâneas — ex.: Dashboard com 4 a 6 cards de KPI, um gráfico e uma tabela, todos visíveis sem rolagem em telas grandes) é a principal vantagem funcional da navegação Desktop sobre Mobile, já reconhecida implicitamente pela priorização de campos por resolução em Frontend Architecture, Capítulo 24.

---

## 12. Estrutura Visual dos Dashboards

Os 11 Dashboards do THE CHARCOAL OS compartilham a mesma anatomia visual — instâncias do Template Dashboard (Frontend Architecture, Capítulo 12) — construída a partir dos 25 campos já especificados individualmente em UX/UI Specification, Capítulos 3.1 a 3.11. Nenhum Dashboard foge a este padrão comum:

1. **Cabeçalho de contexto** — nome do Dashboard e, quando aplicável, seletor de período (ex.: mês corrente, últimos 30 dias) que filtra todos os cards e gráficos simultaneamente.
2. **Linha de Cards de KPI** (Componente "Card de KPI") — de 3 a 6 cards no topo da tela, primeira leitura visual ao abrir o Dashboard, cada um com valor numérico em destaque e rótulo curto.
3. **Área de visualização gráfica** — um ou mais gráficos (linha, barra, funil, calendário/timeline ou feed cronológico, conforme o Dashboard), sempre abaixo da linha de KPIs.
4. **Tabela ou lista de itens relevantes/pendentes** (Componente "Tabela com paginação e ordenação") — os itens que exigem atenção mais imediata do Perfil daquela Área.
5. **Ações rápidas** — botões primários específicos do módulo, permitindo iniciar a ação mais comum daquela Área sem navegar até a Lista correspondente.
6. **Widgets especiais**, quando aplicável a um Dashboard específico: sugestão de IA (Componente de sugestão de IA, cor Roxo-IA), alerta crítico (Banner de alerta persistente, RN-047), indicador de Meta (Card de progresso, consumo apenas leitura do Módulo 26).

Cada card, gráfico ou tabela assume seus próprios Estados de Carregamento (Skeleton) e Estado Vazio de forma independente (Frontend Architecture, Capítulos 18–19) — um Dashboard nunca fica bloqueado como um todo enquanto uma única fonte de dado ainda carrega; cada bloco aparece assim que seu próprio dado estiver disponível.

Distribuição em grid: Desktop 2 a 4 colunas (Capítulo 11 deste documento), Tablet 1 a 2 colunas, Mobile coluna única com cards empilhados (Capítulo 10 deste documento).

**[Inferência visual]** — a ordem espacial exata de cada bloco (ex.: gráfico à esquerda ou à direita da tabela) não é prescrita por nenhum documento oficial; este documento não fixa esse detalhe, deixando-o como uma decisão de prototipagem visual futura, fora do escopo desta fase — apenas a presença e o conteúdo de cada bloco são especificados aqui, nunca sua posição relativa exata em pixels.

## 13. Dashboard CEO

**Objetivo:** visão executiva consolidada do negócio — tela de entrada padrão do sistema para Perfis com acesso executivo (UX/UI Specification, §3.1; Functional Specification, Módulo 01, F-001/F-002).

**Cards de KPI (4 a 6):** Faturamento do período, Margem média, Eventos confirmados, Eventos concluídos, Retiradas pessoais do período (dado consumido do Módulo 02), Saldo consolidado (dado consumido do Módulo 27).

**Gráficos:** gráfico de linha de Fluxo de Caixa (F-008); gráfico de barras de margem por Evento (F-009).

**Tabela:** próximos Eventos confirmados, com data, Cliente e status do ciclo de vida (Badge de status).

**Widgets especiais:** Card de progresso de Metas (consumo apenas leitura do Módulo 26); Banner de alerta persistente para Alertas Críticos (RN-047).

**Ações rápidas:** "Novo Evento", "Ver Financeiro", "Ver Metas".

**Filtros:** seletor de período no cabeçalho, aplicado a todos os cards e gráficos.

**Comportamento esperado:** atualização reativa a eventos relevantes de qualquer módulo consumido (User Journeys, FL-027 — "Atualização Automática do Dashboard CEO"), sem exigir recarregamento manual da tela.

## 14. Dashboard Financeiro Pessoal

**Objetivo:** controle das retiradas pessoais dos sócios, isolado do Financeiro Empresarial por privacidade e por organização contábil (UX/UI Specification, §3.2; Functional Specification, Módulo 02, F-003/F-004; Security and Privacy Architecture, Capítulo 13 — Isolamento entre Dados Pessoais e Empresariais).

**Cards de KPI:** Total retirado no período; Retirada média mensal.

**Gráfico:** gráfico de linha do histórico de retiradas ao longo do tempo.

**Tabela:** histórico de retiradas, com data, valor e sócio responsável.

**Ações rápidas:** "Registrar Retirada".

**Filtros:** seletor de período; filtro por sócio (quando houver mais de um vinculado ao Perfil).

**Comportamento esperado:** dado exibido nunca é somado ou comparado ao Dashboard Financeiro Empresarial na mesma tela — a separação visual reforça o isolamento já exigido por regra de negócio (RN-002/RN-005).

## 15. Dashboard Financeiro Empresarial

**Objetivo:** visão consolidada das finanças da empresa — contas a pagar/receber, fluxo de caixa, fechamento de período (UX/UI Specification, §3.3; Functional Specification, Módulo 03, F-005–F-010).

**Cards de KPI:** Saldo consolidado; Total a pagar; Total a receber; Margem média.

**Gráfico:** gráfico de linha de Fluxo de Caixa (F-008) — mesma visualização conceitual do Dashboard CEO, com maior nível de detalhe.

**Tabela:** com abas internas — Despesas (F-005), Receitas Financeiras (F-006), Pagamentos (F-007).

**Ações rápidas:** "Fechar Período" (F-010) — Operação Crítica (Security and Privacy Architecture, Capítulo 30), exige confirmação explícita antes de execução.

**Filtros:** seletor de período; filtro por categoria de Despesa/Receita dentro de cada aba.

**Comportamento esperado:** "Fechar Período" é sempre precedido de tela de confirmação mostrando o resumo do que será encerrado, nunca uma ação de um único clique sem revisão (padrão de Operação Crítica, Security and Privacy Architecture, Capítulo 30).

## 16. Dashboard Produção

**Objetivo:** acompanhamento das Produções planejadas e em execução, com desvio de rendimento e perda (UX/UI Specification, §3.5; Functional Specification, Módulo 10, F-032–F-035).

**Cards de KPI:** Produções planejadas hoje; Desvio médio de rendimento; Desvio médio de perda.

**Visualização:** calendário/timeline das Produções planejadas.

**Gráfico:** gráfico de barras planejado x real (F-035).

**Widget especial:** sugestão de previsão de demanda por IA (Componente de sugestão de IA, F-069) — sempre rotulada como "sugestão", nunca como decisão automática (PF-06).

**Tabela:** Fichas Técnicas associadas às Produções do período, com data de última recalculação.

**Filtros:** seletor de período; filtro por status de Produção.

**Comportamento esperado:** todo valor de desvio (rendimento/perda) é somente leitura, calculado pelo Serviço dono — o Dashboard nunca recalcula esse valor na interface (PF-03, Camada de Componente, Capítulo 4 deste documento).

## 17. Dashboard Estoque

**Objetivo:** posição consolidada de Estoque e Lotes, incluindo alertas de reposição e validade (UX/UI Specification, §3.6; Functional Specification, Módulo 16, F-052–F-054, e Módulo 17, F-055/F-056).

**Cards de KPI:** Itens abaixo do ponto de reposição; Lotes próximos do vencimento; Giro médio.

**Gráfico:** gráfico de barras de saldo por categoria de Ingrediente/Produto.

**Tabela:** posição de estoque (F-052), com Badge de status para itens críticos; aba de Lotes (F-055), com destaque visual (cor Amarelo/Âmbar-atenção ou Vermelho-crítico, conforme severidade) para Lotes próximos do vencimento.

**Ações rápidas:** acesso direto à tela de Lotes (Capítulo 24 deste documento) a partir do card de Lotes próximos do vencimento.

**Filtros:** seletor de categoria; filtro por proximidade de vencimento.

**Comportamento esperado:** o destaque de vencimento segue a mesma paleta de severidade usada em todo o sistema (Design System, Capítulo 26 deste documento) — nunca uma cor exclusiva desse Dashboard.

## 18. Dashboard Engenharia de Custos

**Objetivo:** acompanhamento do custo real de Eventos frente ao previsto pelas Fichas Técnicas (UX/UI Specification, §3.7; Functional Specification, Módulo 11, F-036–F-038).

**Cards de KPI:** Custo real médio por Evento; Desvio médio de custo; Margem média.

**Gráfico:** gráfico de barras custo previsto vs. real (F-038).

**Tabela:** Fichas Técnicas com data de recalculação, custo unitário e Badge de status de atualização.

**Filtros:** seletor de período; filtro por Produto/Receita.

**Comportamento esperado:** todo valor de custo exibido é somente leitura, oriundo exclusivamente do Serviço dono de Engenharia de Custos — o Dashboard nunca exibe um valor de custo recalculado localmente (PF-03).

## 19. Dashboard Eventos

**Objetivo:** acompanhamento do ciclo de vida dos Eventos confirmados e em execução (UX/UI Specification, §3.8; Functional Specification, Módulo 07, F-020–F-024).

**Cards de KPI:** Eventos confirmados no período; Eventos em execução; Margem média prevista.

**Visualização:** calendário colorido por status do ciclo de vida do Evento (Badge de status).

**Tabela:** lista de Eventos por estágio do ciclo de vida, com data, Cliente e responsável.

**Filtros:** seletor de período; filtro por estágio do ciclo de vida.

**Comportamento esperado:** ao contrário dos demais Dashboards, este não possui uma funcionalidade de indicador dedicada (F-XXX) além do próprio ciclo de vida do Módulo 07 — os dados exibidos são consumidos através do Serviço de Indicadores (Frontend Architecture, Capítulo 15), reafirmando que o Dashboard nunca duplica lógica de cálculo já existente em outro Serviço.

## 20. Dashboard CRM

**Objetivo:** acompanhamento da captação e conversão de Leads em Clientes (UX/UI Specification, §3.9; Functional Specification, Módulo 04, F-011/F-012).

**Cards de KPI:** Novos Leads; Taxa de conversão; Clientes fidelizados.

**Visualização:** funil visual dedicado (Lead → Qualificação → Conversão → Contrato).

**Gráfico:** gráfico de barras de retorno por Campanha (F-012).

**Tabela:** Leads que exigem atenção (RN-011), com Badge de status e tempo desde o último contato.

**Ações rápidas:** "Novo Lead", acesso direto à tela de Leads (Capítulo 24 deste documento).

**Filtros:** seletor de período; filtro por estágio do funil.

**Comportamento esperado:** o funil visual reflete exatamente os mesmos estágios já definidos no ciclo de vida de Lead (Domain Model) — nenhum estágio novo é introduzido nesta representação visual.

## 21. Dashboard Marketing

**Objetivo:** acompanhamento de Campanhas e geração de demanda (UX/UI Specification, §3.4; Functional Specification, Módulo 21, F-065–F-067).

**Cards de KPI:** Leads gerados; Taxa de conversão; Custo por Lead; Retorno consolidado.

**Gráfico:** gráfico de barras de retorno por Campanha (F-066).

**Tabela:** Campanhas ativas e encerradas (F-065/F-067), com Badge de status.

**Ações rápidas:** "Nova Campanha".

**Filtros:** seletor de período; filtro por canal de Campanha.

**Comportamento esperado:** os indicadores de retorno por Campanha aqui exibidos são os mesmos consumidos pelo Dashboard CRM (Capítulo 20) — nenhum valor é calculado duas vezes com lógica divergente (PF-03), apenas apresentado sob um recorte de leitura diferente (visão de Marketing vs. visão de CRM).

## 22. Dashboard Metas

**Objetivo:** acompanhamento do progresso das Metas ativas da empresa (UX/UI Specification, §3.10, nome canônico adotado nesta fase — ver Executive Memory, divergência D-01; Functional Specification, Módulo 26, F-084–F-091, especificamente F-091 "Visualizar Dashboard de Metas").

**Cards:** um Card de progresso por Meta ativa, mostrando percentual alcançado frente ao alvo.

**Gráfico:** gráfico de linha de histórico de progresso.

**Tabela:** histórico completo de Metas (F-089), incluindo Metas já encerradas (atingidas ou não).

**Filtros:** seletor de período; filtro por Área da Empresa responsável pela Meta.

**Comportamento esperado:** este é o único Dashboard cujo conteúdo é também consumido, em versão reduzida (apenas leitura), como widget dentro de outros Dashboards (ex.: Dashboard CEO, Capítulo 13) — o dado de origem é sempre o mesmo Serviço dono, nunca duplicado com cálculo próprio.

## 23. Dashboard Inteligência Artificial

**Objetivo:** centralizar as sugestões geradas por IA em todos os módulos, permitindo acompanhamento e configuração (UX/UI Specification, §3.11; Functional Specification, Módulo 22, F-068–F-071).

**Cards de KPI:** Sugestões pendentes; Taxa de aceite; Previsões ativas.

**Visualização:** feed cronológico de sugestões, cada uma com origem (módulo), tipo (Classificação/Previsão/Recomendação/Monitoramento, AI Architecture, Capítulo 6) e Componente de sugestão de IA (botões Aceitar/Recusar).

**Gráfico:** gráfico de taxa de aceite ao longo do tempo.

**Ações rápidas:** "Configurar Automação" (F-071).

**Filtros:** filtro por módulo de origem; filtro por tipo de Agente Inteligente.

**Comportamento esperado:** toda sugestão listada aqui é a mesma sugestão que aparece contextualmente no módulo de origem (ex.: uma sugestão de previsão de demanda também aparece no Dashboard Produção, Capítulo 16) — este Dashboard nunca gera uma sugestão própria, apenas centraliza a visualização e o histórico de aceite/recusa já registrado pelo Serviço de IA (AI Architecture, TCOS-013). Nenhuma sugestão tem efeito sobre o sistema sem confirmação explícita do usuário (PF-06).

---

## 24. Blueprint Completo das 30 Telas já Especificadas

**Nota metodológica:** dado o volume (30 telas, 14 aspectos visuais cada), este Capítulo foi construído em 3 sub-partes, conforme sinalizado no roteiro da Executive Memory: **3a** (índice das 30 telas + Leads, Clientes, Eventos, Orçamentos, Contratos, Produção, Receitas), **3b** (Fichas Técnicas, Precificação, Compras, Estoque, Lotes, Equipamentos) e **3c** (Funcionários, Escalas, Bancos, Conciliação Bancária, Configurações, Administração) — esta última concluindo o Capítulo 24.

### 24.1 Índice Completo das 30 Telas

Os 11 Dashboards já foram integralmente detalhados nos Capítulos 13–23 (Parte 2, aprovada) — não são repetidos aqui, apenas referenciados. Este capítulo completa o quadro com as 19 telas de módulo, classificadas por Template (Frontend Architecture, Capítulo 12) a partir do "Layout geral" já descrito em cada perfil oficial (UX/UI Specification, §3.12–3.30) — toda classificação de Template é uma **[Inferência visual]**, pois a especificação existente não publica essa atribuição em tabela própria (ver Auditoria de Consistência, Capítulo 2).

| # | Tela | Módulo | Template (inferência visual) | Sub-parte |
|---|---|---|---|---|
| 1–11 | (os 11 Dashboards) | — | Dashboard | Capítulos 13–23 |
| 12 | Leads | 06 | Lista (variante Kanban) | 3a |
| 13 | Clientes | 05 | Lista + Detalhe (abas) | 3a |
| 14 | Eventos | 07 | Detalhe (abas) | 3a |
| 15 | Orçamentos | 08 | Lista + Detalhe (editor) | 3a |
| 16 | Contratos | 09 | Lista + Detalhe (visualizador) | 3a |
| 17 | Produção | 10 | Lista + Modal (execução) | 3a |
| 18 | Receitas | 12 | Lista + Detalhe (editor) | 3a |
| 19 | Fichas Técnicas | 13 | Lista + Detalhe | 3b |
| 20 | Precificação | 14 | Lista + Detalhe | 3b |
| 21 | Compras | 15 | Lista + Detalhe | 3b |
| 22 | Estoque | 16 | Lista | 3b |
| 23 | Lotes | 17 | Lista | 3b |
| 24 | Equipamentos | 18 | Lista + Detalhe | 3b |
| 25 | Funcionários | 19 | Lista + Detalhe | 3c |
| 26 | Escalas | 20 | Lista (calendário) | 3c |
| 27 | Bancos | 27 | Lista + Detalhe | 3c |
| 28 | Conciliação Bancária | 27 | Lista (pareamento) | 3c |
| 29 | Configurações | 24 | Lista + formulário inline | 3c |
| 30 | Administração | 25 | Lista + Detalhe | 3c |

### 24.2 Leads

**Objetivo:** gerenciar o ciclo de vida do Lead, da captação à conversão/perda (Módulo 06).

**Layout / Template:** Lista em variante Kanban por estágio (Novo, Em qualificação, Convertido, Perdido), com alternativa em tabela.

**Distribuição dos componentes:** kanban de colunas por estágio no corpo principal; card de contagem por estágio no topo de cada coluna; painel de detalhe do Lead ao selecionar um card.

**Cards:** contagem por estágio (topo do kanban); total de Leads ativos (cabeçalho da tela).

**Tabelas:** lista alternativa ao kanban, colunas Nome, Origem, Estágio, Data.

**Gráficos:** nenhum nesta tela — consolidados no Dashboard CRM (Capítulo 20).

**Filtros:** por origem/Campanha; por estágio; por período; busca por nome/contato.

**Menus:** menu lateral (Comercial/CRM → Leads).

**Botões:** "Novo Lead" (F-016), "Qualificar" (F-017), "Converter" (F-018), "Marcar como Perdido" (F-019).

**Atalhos:** arrastar card entre colunas do kanban para mudar de estágio.

**Estados da interface:** vazio; normal; "correspondência ambígua" (modal de confirmação na conversão).

**Mensagens:** confirmação de "Lead convertido com sucesso".

**Alertas:** badge de "Lead inativo há X dias" no card (RN-011).

**Validações visuais:** cadastro sem meio de contato é bloqueado, com mensagem explicativa.

**Comportamento esperado:** conversão navega automaticamente para a tela de Clientes (Capítulo 24.3); atribuição de origem e sugestão de perda por inatividade ocorrem automaticamente (RN-008/RN-011), sempre visíveis, nunca silenciosas.

### 24.3 Clientes

**Objetivo:** manter o cadastro único e o histórico de relacionamento com cada Cliente (Módulo 05).

**Layout / Template:** Lista de Clientes + Detalhe com abas (Histórico, Eventos, Documentos, Financeiro).

**Distribuição dos componentes:** tabela de Clientes à esquerda/topo; painel de Detalhe com abas ao selecionar um Cliente.

**Cards (no Detalhe):** total de Eventos, valor total histórico, status de fidelização.

**Tabelas:** lista de Clientes (nome, tipo, status, último Evento); linha do tempo de Eventos/Orçamentos/Contratos na aba Histórico (F-014).

**Gráficos:** nenhum nesta tela.

**Filtros:** por status (ativo/inativo); por fidelização; por tipo (PF/PJ); busca por nome/contato.

**Menus:** menu lateral (Clientes); abas internas no painel de Detalhe.

**Botões:** "Novo Cliente" (F-013), "Inativar" (F-015), "Novo Orçamento para este Cliente" (a partir do Detalhe).

**Atalhos:** ação rápida de novo Orçamento direto do painel de Detalhe.

**Estados da interface:** ativo; inativo (visualmente esmaecido, permanece acessível — nunca "excluído").

**Mensagens:** badge visual de "Cliente fidelizado" (RN-010, automático).

**Alertas:** possível duplicidade no cadastro (RN-009).

**Validações visuais:** tentativa de criar Orçamento para Cliente inativo sugere reativação antes de prosseguir.

**Comportamento esperado:** dados de contato visíveis a Comercial/CRM; dados financeiros restritos a Financeiro/Direção (Security and Privacy Architecture, Capítulo 6 — Arquitetura de Privacidade, Classificação de sensibilidade de dado); marcação de fidelização nunca manual.

### 24.4 Eventos

**Objetivo:** gerenciar o ciclo de vida operacional de um Evento específico — tela de gestão/detalhe, complementar ao Dashboard Eventos (Módulo 07).

**Layout / Template:** Detalhe com abas — Resumo, Orçamento, Contrato, Produção, Equipe/Escala, Equipamentos, Financeiro.

**Distribuição dos componentes:** cabeçalho com Badge de status do ciclo de vida; abas internas; linha do tempo do ciclo de vida.

**Cards:** margem prevista; número de convidados; dias até o Evento.

**Tabelas:** itens do Orçamento (aba Orçamento); lista de Produções (aba Produção); lista de Alocações (aba Equipe).

**Gráficos:** nenhum nesta tela — consolidados no Dashboard Eventos (Capítulo 19).

**Filtros:** não aplicável — tela de Detalhe de um único Evento.

**Menus:** abas internas (Resumo, Orçamento, Contrato, Produção, Equipe, Equipamentos, Financeiro).

**Botões:** "Confirmar Evento" (F-021), "Ajustar Planejamento" (F-022), "Concluir Evento" (F-023), "Cancelar Evento" (F-024).

**Atalhos:** "Ver Orçamento completo", "Ver Contrato", direto de cada aba relacionada.

**Estados da interface:** um estado visual (cor + ações disponíveis) por estágio do ciclo de vida, de Prospectado a Cancelado.

**Mensagens:** confirmação com resumo da orquestração completa disparada ao confirmar o Evento.

**Alertas:** inviabilidade operacional (RN-006); margem abaixo do mínimo; conflito de Equipamento/Escala.

**Validações visuais:** confirmação bloqueada com explicação exata do recurso insuficiente, nunca um erro genérico.

**Comportamento esperado:** confirmação de Evento aciona orquestração automática completa (RN-006) envolvendo Módulos 08, 09, 10, 15, 16, 18, 19, 20 e 03; cada aba é visível apenas conforme a Área do usuário (Security and Privacy Architecture, Capítulo 7 — Controle de Acesso).

### 24.5 Orçamentos

**Objetivo:** montar, enviar e acompanhar propostas comerciais (Módulo 08).

**Layout / Template:** Lista de Orçamentos + Detalhe/editor de proposta.

**Distribuição dos componentes:** tabela de Orçamentos; editor de itens (uma linha por Produto/Pacote) com resumo de valor/margem.

**Cards:** valor total; margem calculada (visível apenas a quem tem permissão).

**Tabelas:** lista de Orçamentos (Cliente, valor, status, validade); itens do Orçamento no editor.

**Gráficos:** nenhum nesta tela.

**Filtros:** por status (Rascunho, Enviado, Aceito, Recusado, Expirado); por Cliente; por período; busca por Cliente/Evento.

**Menus:** menu lateral (Orçamentos).

**Botões:** "Novo Orçamento" (F-025), "Enviar" (F-026), "Nova Versão" (F-027), "Registrar Aceite/Recusa" (F-028).

**Atalhos:** "Duplicar Orçamento" para Evento semelhante.

**Estados da interface:** Badge de status por cor — Rascunho (cinza), Enviado (azul/Brasa conforme convenção de ativo), Aceito (verde), Recusado (vermelho), Expirado (cinza-claro).

**Mensagens:** Orçamento aceito dispara geração automática de Contrato, com aviso visível ao usuário.

**Alertas:** margem abaixo do mínimo (RN-023, bloqueio com fluxo de aprovação); Produto sem Ficha Técnica vigente (RN-021).

**Validações visuais:** tentativa de enviar Orçamento sem itens é bloqueada.

**Comportamento esperado:** cálculo de preço e expiração automática (RN-012/013/022) sempre executados pelo Serviço dono, nunca recalculados na interface (PF-03); aceite navega automaticamente para a tela de Contratos (Capítulo 24.6).

### 24.6 Contratos

**Objetivo:** formalizar e acompanhar o compromisso contratual (Módulo 09).

**Layout / Template:** Lista de Contratos + Detalhe com visualizador de documento e histórico de aditivos.

**Distribuição dos componentes:** tabela de Contratos; visualizador de PDF/documento; linha de histórico de aditivos.

**Cards:** valor total; status; data de assinatura.

**Tabelas:** lista de Contratos; histórico de aditivos.

**Gráficos:** nenhum nesta tela.

**Filtros:** por status; por Cliente; por período; busca por Cliente/Evento.

**Menus:** menu lateral (Contratos).

**Botões:** "Assinar" (F-030), "Registrar Aditivo" (F-031), "Baixar PDF", "Ver Evento vinculado".

**Atalhos:** acesso direto ao Evento vinculado a partir do Contrato.

**Estados da interface:** Rascunho, Assinado, Em execução, Concluído, Cancelado.

**Mensagens:** Contrato assinado dispara confirmação de Evento, visível ao usuário.

**Alertas:** dados obrigatórios ausentes (RN-014); impacto de aditivo em recursos já reservados (RN-015).

**Validações visuais:** tentativa de editar Contrato assinado diretamente é bloqueada, com redirecionamento explícito para "Registrar Aditivo".

**Comportamento esperado:** minuta gerada automaticamente a partir do Orçamento aceito (RN-014); assinatura gera Receita Financeira prevista automaticamente, consumida pelo Dashboard Financeiro Empresarial (Capítulo 15).

### 24.7 Produção *(tela operacional)*

**Objetivo:** executar e registrar a Produção do dia a dia — complementar ao Dashboard Produção (Módulo 10).

**Layout / Template:** Lista de Produções planejadas + Modal de execução.

**Distribuição dos componentes:** tabela de Produções por status; formulário de execução (consumo/rendimento real) em Modal.

**Cards:** Produções pendentes hoje; Produções concluídas hoje.

**Tabelas:** lista de Produções por status.

**Gráficos:** nenhum nesta tela — consolidados no Dashboard Produção (Capítulo 16).

**Filtros:** por Evento; por Ficha Técnica; por status; por data; busca por nome de Produto/Receita.

**Menus:** menu lateral (Produção).

**Botões:** "Iniciar Execução" (F-033), "Registrar Consumo/Rendimento" (F-034), "Ver Ficha Técnica".

**Atalhos:** acesso direto à Ficha Técnica a partir de uma Produção listada.

**Estados da interface:** Planejada, Em execução, Concluída, Cancelada.

**Mensagens:** confirmação de "Produção concluída".

**Alertas:** Estoque insuficiente (RN-032); rendimento insuficiente (RN-029, alta prioridade).

**Validações visuais:** tentativa de concluir sem registrar consumo real é bloqueada.

**Comportamento esperado:** conclusão da execução dispara baixa automática de Estoque e geração de Lote (RN-032) — sempre visível ao usuário no resumo de conclusão, nunca uma alteração silenciosa de saldo.

### 24.8 Receitas

**Objetivo:** padronizar e versionar o "como fazer" de cada item (Módulo 12).

**Layout / Template:** Lista de Receitas + Detalhe/editor (ingredientes, quantidades, modo de preparo).

**Distribuição dos componentes:** tabela de Receitas; editor com lista de Ingredientes.

**Cards:** total de Receitas ativas; em desenvolvimento.

**Tabelas:** lista de Receitas com estado e versão atual.

**Gráficos:** nenhum nesta tela.

**Filtros:** por estado (Em desenvolvimento, Aprovada, Em revisão, Descontinuada); busca por nome de Receita/Ingrediente.

**Menus:** menu lateral (Receitas).

**Botões:** "Nova Receita" (F-039), "Aprovar" (F-040), "Revisar/Nova Versão" (F-041).

**Atalhos:** "Criar Ficha Técnica a partir desta Receita".

**Estados da interface:** Em desenvolvimento, Aprovada, Em revisão, Descontinuada.

**Mensagens:** aviso à equipe de Produção quando uma nova versão é publicada.

**Alertas:** tentativa de aprovar Receita sem Ficha Técnica associada.

**Validações visuais:** edição de Receita Aprovada sempre gera nova versão automaticamente — nunca sobrescreve a versão vigente.

**Comportamento esperado:** aprovação leva à criação da Ficha Técnica associada (Capítulo 24.9, a seguir); nova versão se propaga automaticamente à Ficha Técnica já existente (RN-020), sempre com aviso visível, nunca silenciosamente.

### 24.9 Fichas Técnicas

**Objetivo:** ser a fonte única de custo de produção de cada item (Módulo 13).

**Layout / Template:** Lista de Fichas Técnicas + Detalhe/editor de composição e custo.

**Distribuição dos componentes:** tabela de Fichas Técnicas; editor com lista de Ingredientes/quantidades/custo; histórico de versões.

**Cards:** custo total vigente; rendimento.

**Tabelas:** lista de Fichas Técnicas; histórico de versões (F-044).

**Gráficos:** evolução de custo ao longo das versões (mini-gráfico de linha).

**Filtros:** por Produto; por estado (Vigente, Substituída, Descontinuada); busca por nome de Produto/Receita.

**Menus:** menu lateral (Fichas Técnicas).

**Botões:** "Nova Ficha Técnica" (F-042), "Recalcular" (F-043, normalmente automático).

**Atalhos:** "Ver impacto em Orçamentos abertos" após um recálculo.

**Estados da interface:** Rascunho, Vigente, Substituída, Descontinuada.

**Mensagens:** aviso de "Ficha Técnica recalculada automaticamente".

**Alertas:** impacto de recálculo em Orçamentos abertos (RN-019).

**Validações visuais:** duas Fichas Técnicas Vigentes para o mesmo item não são permitidas simultaneamente — bloqueio explícito na tentativa.

**Comportamento esperado:** recálculo automático disparado por atualização de custo de Ingrediente (RN-019) é sempre visível ao usuário — nunca um valor de custo silenciosamente atualizado sem notificação; valores de custo aqui exibidos alimentam diretamente o Dashboard Engenharia de Custos (Capítulo 18).

### 24.10 Precificação

**Objetivo:** garantir que todo preço tenha lastro em custo e margem definida (Módulo 14).

**Layout / Template:** Lista de Produtos/Pacotes com preço calculado + painel de margem-alvo.

**Distribuição dos componentes:** tabela de Produtos/Pacotes com custo/preço/margem; painel de configuração de margem-alvo.

**Cards:** margem média; número de exceções aprovadas no período.

**Tabelas:** lista de Produtos/Pacotes com custo, margem e preço.

**Gráficos:** distribuição de margem por Produto (histograma simples).

**Filtros:** por categoria de Produto; por faixa de margem; busca por nome de Produto/Pacote.

**Menus:** menu lateral (Precificação).

**Botões:** "Definir Margem-Alvo" (F-045/F-077, atalho para Configurações), "Recalcular Preço" (F-046), "Aprovar Exceção de Margem" (F-047).

**Atalhos:** atalho direto de "Definir Margem-Alvo" para a tela de Configurações (Capítulo 24.19, sub-parte 3c).

**Estados da interface:** normal; "margem-alvo não definida" (bloqueio com link direto para Configurações).

**Mensagens:** aviso de "preço recalculado" após mudança de custo.

**Alertas:** margem abaixo do mínimo (RN-023); preço fora da faixa esperada.

**Validações visuais:** preço nunca é editável diretamente — sempre calculado a partir de custo e margem; qualquer tentativa de edição direta é bloqueada.

**Comportamento esperado:** cálculo automático de preço a partir do custo vigente (RN-022) sempre pelo Serviço dono (PF-03); aprovação de exceção de margem exige justificativa obrigatória em Modal — nunca uma aprovação de um único clique.

### 24.11 Compras

**Objetivo:** garantir o abastecimento junto a Fornecedores (Módulo 15).

**Layout / Template:** Lista em variante Kanban por status (Solicitada → Cotação → Pedido → Recebida → Conferida) + Detalhe de Fornecedores.

**Distribuição dos componentes:** kanban/lista por status no corpo principal; tabela de Fornecedores com histórico (F-051).

**Cards:** Compras pendentes de conferência; valor total do período.

**Tabelas:** lista de Compras; lista de Fornecedores com histórico.

**Gráficos:** gasto por Fornecedor (barras).

**Filtros:** por Fornecedor; por status; por período; busca por nome de Fornecedor/Ingrediente.

**Menus:** menu lateral (Compras).

**Botões:** "Ver Lista de Compras Sugerida" (F-048), "Cotar/Emitir Pedido" (F-049), "Receber e Conferir" (F-050).

**Atalhos:** "Registrar divergência" direto da tela de conferência.

**Estados da interface:** cor por status do ciclo — Solicitada, Cotação, Pedido, Recebida, Conferida.

**Mensagens:** "Compra conferida — Estoque atualizado".

**Alertas:** item sem Fornecedor definido; prazo incompatível com data do Evento; divergência na conferência (RN-031).

**Validações visuais:** conferência com divergência exige decisão explícita do usuário antes de prosseguir — nunca um avanço automático silencioso.

**Comportamento esperado:** lista de Compras sugerida é gerada automaticamente a partir da Produção planejada (RN-030); conferência aprovada gera automaticamente Estoque/Lote/Despesa, sempre visível no resumo da ação, nunca uma alteração de saldo sem rastro visual.

### 24.12 Estoque *(tela operacional)*

**Objetivo:** operar o controle diário de saldo de Ingredientes/Produtos — complementar ao Dashboard Estoque (Módulo 16).

**Layout / Template:** Lista com painel de detalhe lateral (histórico de movimentações do item selecionado) — não uma tela de Detalhe navegável separada.

**Distribuição dos componentes:** tabela detalhada por item; painel de detalhe lateral com histórico de movimentações.

**Cards:** itens críticos (abaixo do ponto de reposição).

**Tabelas:** movimentações por item (entrada/saída, origem, Lote).

**Gráficos:** histórico de saldo do item (linha).

**Filtros:** por item; por localização; por tipo de movimentação; busca por nome de item.

**Menus:** menu lateral (Estoque).

**Botões:** "Realizar Inventário" (F-053), "Configurar Ponto de Reposição" (F-054).

**Atalhos:** "Ver Lotes deste item" (Capítulo 24.13, a seguir).

**Estados da interface:** normal; crítico (cor Vermelho-crítico).

**Mensagens:** "inventário concluído".

**Alertas:** saldo insuficiente; abaixo do ponto de reposição.

**Validações visuais:** ajuste de inventário sem justificativa é bloqueado.

**Comportamento esperado:** atualização automática de saldo (RN-032) sempre visível na tabela de movimentações — nenhum ajuste de saldo ocorre sem um registro de movimentação correspondente; destaque crítico usa a mesma paleta de severidade de todo o sistema (Capítulo 26, a construir).

### 24.13 Lotes

**Objetivo:** garantir rastreabilidade de origem e validade (Módulo 17).

**Layout / Template:** Lista com destaque visual por proximidade de vencimento + painel de detalhe (origem, consumo, validade).

**Distribuição dos componentes:** tabela de Lotes; painel de detalhe do Lote selecionado.

**Cards:** Lotes vencendo em 7 dias; Lotes vencidos não descartados.

**Tabelas:** lista de Lotes (item, quantidade, origem, validade, estado).

**Gráficos:** nenhum nesta tela.

**Filtros:** por item; por validade; por estado; busca por item ou número de Lote.

**Menus:** menu lateral (Lotes).

**Botões:** "Registrar Descarte" (F-056).

**Atalhos:** "Ver Compra/Produção de origem" (F-055).

**Estados da interface:** Ativo, Em consumo, Vencido (Vermelho-crítico), Descartado, Esgotado.

**Mensagens:** "descarte registrado".

**Alertas:** validade próxima; tentativa de uso de Lote vencido é bloqueada.

**Validações visuais:** descarte sem motivo obrigatório é bloqueado.

**Comportamento esperado:** priorização automática "primeiro que vence, primeiro que sai" (RN-034) é uma regra de consumo do backend — a tela apenas exibe a ordem já determinada, nunca decide por conta própria qual Lote usar.

### 24.14 Equipamentos *(inclui Veículos)*

**Objetivo:** controlar disponibilidade e alocação de bens físicos reutilizáveis (Módulo 18).

**Layout / Template:** Lista/calendário de alocação por item + Detalhe do item.

**Distribuição dos componentes:** tabela de itens; calendário de alocação; painel de detalhe.

**Cards:** itens disponíveis; itens em manutenção.

**Tabelas:** lista de Equipamentos/Veículos com estado e próxima alocação.

**Gráficos:** nenhum nesta tela.

**Filtros:** por tipo; por estado; por período de alocação; busca por nome/identificação do item.

**Menus:** menu lateral (Equipamentos).

**Botões:** "Cadastrar" (F-057), "Alocar" (F-058), "Registrar Manutenção/Baixa" (F-059).

**Atalhos:** "Ver Evento" a partir de uma alocação (Capítulo 24.4).

**Estados da interface:** Disponível (Verde-sucesso), Alocado (Brasa), Em manutenção (Âmbar-atenção), Baixado (Cinza-claro).

**Mensagens:** "manutenção concluída — item disponível novamente".

**Alertas:** conflito de alocação, com sugestão de alternativa (RN-035, bloqueante).

**Validações visuais:** tentativa de alocar item em manutenção é bloqueada.

**Comportamento esperado:** bloqueio automático de conflito de sobreposição de alocação — o usuário nunca consegue confirmar uma alocação conflitante, mesmo que tente forçar a ação.

### 24.15 Funcionários

**Objetivo:** manter o cadastro e o custo de mão de obra da equipe (Módulo 19).

**Layout / Template:** Lista de Funcionários + Detalhe (painel com histórico de Alocações).

**Distribuição dos componentes:** tabela de Funcionários; painel de detalhe com histórico de Alocações.

**Cards:** total de Funcionários ativos; fixos vs. freelancers.

**Tabelas:** lista de Funcionários; histórico de Alocações no painel de detalhe.

**Gráficos:** nenhum nesta tela.

**Filtros:** por tipo de vínculo; por função; por status; busca por nome.

**Menus:** menu lateral (Funcionários).

**Botões:** "Cadastrar" (F-060), "Desligar" (F-062).

**Atalhos:** "Ver Escala" (Capítulo 24.16, a seguir).

**Estados da interface:** Ativo, Afastado, Inativo/Desligado.

**Mensagens:** nenhuma notificação própria além das gerais do sistema.

**Alertas:** Alocação sem valor definido (RN-036).

**Validações visuais:** desligamento de Funcionário com Alocação futura pendente exige confirmação explícita, nunca um desligamento silencioso.

**Comportamento esperado:** consolidação automática de custo a partir de Alocações Realizadas (F-061) é sempre somente leitura na interface; dados de remuneração restritos a Financeiro/Direção (CG-05), nunca visíveis a Pessoas/Mão de Obra por padrão.

### 24.16 Escalas

**Objetivo:** planejar quem trabalha em cada Evento/Produção (Módulo 20).

**Layout / Template:** Lista em formato de calendário de Escalas por Evento/Produção.

**Distribuição dos componentes:** calendário; lista de Alocações por Evento.

**Cards:** Escalas pendentes de confirmação; Eventos sem escala definida.

**Tabelas:** lista de Alocações por Evento (Funcionário, função, horário, status).

**Gráficos:** nenhum nesta tela.

**Filtros:** por Evento; por Funcionário; por período; busca por nome de Funcionário/Evento.

**Menus:** menu lateral (Escalas).

**Botões:** "Confirmar/Ajustar Escala" (F-064).

**Atalhos:** "Substituir Funcionário" em caso de indisponibilidade.

**Estados da interface:** "parâmetro não definido" (bloqueio com link direto para Configurações, Capítulo 24.19, a seguir), Planejada, Confirmada, Realizada, Cancelada.

**Mensagens:** "escala confirmada — Funcionários notificados".

**Alertas:** escala não confirmada a X dias do Evento (RN-037); sobreposição de horário (bloqueio).

**Validações visuais:** sobreposição de horário do mesmo Funcionário é sempre bloqueada, nunca permitida com aviso apenas informativo.

**Comportamento esperado:** escala é gerada automaticamente na confirmação do Evento (mesma orquestração de RN-006, Capítulo 24.4) e sugerida por RN-037 — toda sugestão permanece editável pelo usuário antes da confirmação, nunca é aplicada como fato consumado sem revisão.

### 24.17 Bancos

**Objetivo:** centralizar o cadastro de Banco, Conta e Cartão (Módulo 27).

**Layout / Template:** Lista de Bancos/Contas + Detalhe (saldo e histórico).

**Distribuição dos componentes:** tabela de Contas agrupadas por Banco; painel de detalhe.

**Cards:** saldo consolidado total; saldo por tipo de Conta (pessoal/empresarial/investimento).

**Tabelas:** lista de Contas/Cartões; movimentações no painel de detalhe.

**Gráficos:** distribuição de saldo por Banco (pizza ou barras).

**Filtros:** por Banco; por tipo de Conta; por status; busca por nome do Banco/Conta.

**Menus:** menu lateral (Bancos).

**Botões:** "Cadastrar Banco" (F-092), "Cadastrar Conta/Cartão" (F-093/F-094), "Encerrar" (F-095).

**Atalhos:** "Ver Histórico de Movimentações" (F-097), "Ir para Conciliação" (Capítulo 24.18, a seguir).

**Estados da interface:** Ativa, Encerrada.

**Mensagens:** "Conta/Cartão cadastrado com sucesso".

**Alertas:** resumo herdado de RN-043/RN-044 (detalhados na Conciliação Bancária).

**Validações visuais:** Conta encerrada não aceita novo Pagamento — bloqueio explícito na tentativa.

**Comportamento esperado:** este módulo não executa nenhuma ação automática própria — apenas fornece o dado de referência (Contas/Cartões) consumido pelas automações do Financeiro Pessoal (Capítulo 14) e Empresarial (Capítulo 15); acesso restrito a Financeiro/Direção.

### 24.18 Conciliação Bancária

**Objetivo:** garantir que todo Pagamento registrado corresponda a um lançamento real (Módulo 27 — sub-tela financeira).

**Layout / Template:** Lista em duas colunas paralelas — Pagamentos registrados (esquerda) vs. lançamentos do extrato (direita) — com sugestões de correspondência ao centro.

**Distribuição dos componentes:** duas listas paralelas; indicadores visuais de correspondência (linha conectando os dois lados quando batem).

**Cards:** total conciliado; total pendente; divergências abertas.

**Tabelas:** Pagamentos e lançamentos do extrato, lado a lado.

**Gráficos:** nenhum nesta tela.

**Filtros:** por Conta; por período; por status (conciliado/pendente/divergente); busca por valor/data.

**Menus:** menu lateral (Bancos → Conciliação).

**Botões:** "Importar Extrato" (F-068/FL-023), "Conciliar Selecionados", "Marcar Divergência".

**Atalhos:** aceitar sugestão de correspondência com um clique.

**Estados da interface:** conciliado (Verde-sucesso), pendente (Cinza-claro), divergente (Âmbar-atenção).

**Mensagens:** "extrato importado com sucesso"; "conciliação concluída".

**Alertas:** Conta com pendência de conciliação há mais de um período definido (RN-044); possível duplicidade; possível lançamento pessoal (RN-005).

**Validações visuais:** divergência nunca é corrigida automaticamente — exige decisão humana registrada, nunca uma resolução silenciosa.

**Comportamento esperado:** sugestão de categorização e conciliação vem da IA (RN-043, cor Roxo-IA, PF-06) mas nenhuma conciliação é efetivada sem confirmação explícita em caso de ambiguidade — a IA nunca decide sozinha, mesmo em uma tela de alto volume operacional.

### 24.19 Configurações

**Objetivo:** ser o local único onde todo parâmetro de negócio pendente é definido (Módulo 24).

**Layout / Template:** Lista de categorias de parâmetro + formulário inline por categoria (não um Modal, dado o volume de campos).

**Distribuição dos componentes:** menu de categorias à esquerda (Consumo, Perdas/Rendimento, Precificação, Escalas, Cancelamento); formulário à direita; indicador de "parâmetros pendentes".

**Cards:** quantidade de parâmetros definidos vs. pendentes.

**Tabelas:** lista de parâmetros por categoria, com valor atual e data da última alteração.

**Gráficos:** nenhum nesta tela.

**Filtros:** por categoria; por status (definido/pendente); busca por nome do parâmetro.

**Menus:** menu lateral de categorias (interno à própria tela).

**Botões:** "Definir Parâmetro de Consumo" (F-075), "Definir Perdas/Rendimento" (F-076), "Definir Margem-Alvo" (F-077), "Definir Proporção de Escala" (F-078), "Definir Política de Cancelamento" (F-079).

**Atalhos:** "Ir para onde este parâmetro é usado" (ex.: da margem-alvo direto para Precificação, Capítulo 24.10).

**Estados da interface:** "Definido" (Verde-sucesso), "Pendente" (Âmbar-atenção, com badge de contagem no menu).

**Mensagens:** "parâmetro salvo com sucesso", sempre acompanhado do aviso de impacto (ex.: "afeta X Orçamentos abertos").

**Alertas:** destaque visual persistente para parâmetro crítico ainda não definido, até ser resolvido.

**Validações visuais:** valores fora de faixas plausíveis (ex.: percentual de perda negativo) são bloqueados.

**Comportamento esperado:** este é o único módulo do sistema 100% de definição humana — nenhuma ação automática, nenhuma suposição de valor, consistente com o mandato de nunca inventar parâmetro de negócio não confirmado (Constituição Permanente); telas bloqueadas por parâmetro ausente (Produção, Precificação, Escalas, Eventos) sempre linkam diretamente para cá.

### 24.20 Administração

**Objetivo:** governar acesso, integridade e auditabilidade técnica do sistema (Módulo 25).

**Layout / Template:** Lista + Detalhe, organizados em abas internas (Usuários e Permissões, Log de Auditoria, Central de Alertas, Saúde do Sistema).

**Distribuição dos componentes:** tabela de usuários; visualizador de log; central de alertas consolidada; painel de saúde.

**Cards:** usuários ativos; alertas pendentes; parâmetros de Configurações não definidos.

**Tabelas:** usuários e suas Áreas de Empresa vinculadas (F-080); log de auditoria filtrável (F-081); lista de alertas (F-082).

**Gráficos:** nenhum nesta tela.

**Filtros:** por usuário; por área; por período; por tipo de alerta; busca por nome de usuário ou entidade auditada.

**Menus:** abas internas (Usuários e Permissões, Log de Auditoria, Central de Alertas, Saúde do Sistema).

**Botões:** "Adicionar Usuário", "Editar Permissões", "Marcar Alerta como Tratado".

**Atalhos:** "Ver detalhe da alteração" a partir de uma linha do log.

**Estados da interface:** normal; "alerta crítico pendente" (badge Vermelho-crítico no menu principal).

**Mensagens:** "usuário criado/editado com sucesso".

**Alertas:** central consolidada de todos os alertas do sistema (RN-047, mesma origem do banner do Dashboard CEO, Capítulo 13).

**Validações visuais:** tentativa de remover a única permissão de Administrador do Sistema é bloqueada — trava de segurança, sem exceção.

**Comportamento esperado:** acessível apenas pelo menu lateral, nunca como destino de drill-down de outra tela — reforça seu caráter de módulo de governança transversal, não operacional; nenhuma ação automática própria, é o ponto de controle manual do sistema.

---

**Fim da Parte 3 (sub-parte 3c de 3) — Capítulo 24 concluído.**
