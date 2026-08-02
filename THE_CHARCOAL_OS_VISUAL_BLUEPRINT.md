# THE CHARCOAL OS — VISUAL BLUEPRINT

**Documento:** TCOS-018
**Fase:** 018 — Visual Blueprint (Validação Visual Pré-Implementação)
**Natureza:** Documento de representação visual do sistema. NÃO constitui implementação, NÃO constitui Frontend, NÃO constitui código. Sua finalidade exclusiva é permitir a validação da experiência do usuário antes de qualquer desenvolvimento técnico.
**Baseline referenciada:** v1.0.0 (TCOS-000 a TCOS-017), sob a autoridade da Constituição Permanente do Projeto.
**Referência visual canônica desta fase:** `THE_CHARCOAL_OS_UX_UI_SPECIFICATION.md` (TCOS-005) e `THE_CHARCOAL_OS_FRONTEND_ARCHITECTURE.md` (TCOS-011) — em caso de divergência de nomenclatura entre documentos oficiais, prevalecem estes dois, por determinação expressa do proprietário (comando `ALTERAR`, 2026-08-02).
**Status:** Documento em Construção — Parte 1 de 8 concluída — aguardando decisão do proprietário para prosseguir.

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

**Fim da Parte 1 de 8.**
