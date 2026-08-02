# THE CHARCOAL OS — SECURITY AND PRIVACY ARCHITECTURE

**Documento:** TCOS-012 — Arquitetura Conceitual de Segurança e Privacidade
**Projeto:** THE CHARCOAL OS
**Fase:** 012 — Security and Privacy Architecture
**Status:** Oficial — Aprovado e Congelado pelo proprietário em 2026-08-02 (comando `APROVADO`)
**Versão:** 1.0.0

---

## EXECUTIVE MEMORY

- **Estado atual do projeto:** negócio, domínio, regras, funcionalidades, fluxos, UX/UI, arquitetura de sistema, arquitetura de dados, banco de dados, contrato de integração, arquitetura de backend e arquitetura de frontend completos e oficiais; iniciando a arquitetura conceitual de segurança e privacidade, ainda sem autenticação específica, criptografia específica, infraestrutura ou qualquer tecnologia definida.
- **Fase atual:** 012 — Security and Privacy Architecture (TCOS-012).
- **Fases concluídas:** 000 a 011, todas aprovadas e oficiais (a mais recente, TCOS-011, congelada em 2026-08-02).
- **Critério de contagem de Documentos Oficiais (vigente desde o encerramento da Fase 011):** 15 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`) = **16 Documentos Oficiais no total**.
- **Documentos Oficiais Congelados (15):** Development Framework (v1.2.0), Enterprise Domain Discovery (v1.0.0), Business Discovery Questionnaire (v1.0.0), Discovery Interview Roadmap (v1.0.0), Domain Model (v1.0.0), Business Rules Specification (v1.0.0), Functional Specification (v1.2.0), User Journeys and System Flows (v1.0.0), UX/UI Specification (v1.0.0), System Architecture (v1.0.0), Data Architecture (v1.0.0), Database Specification (v1.0.0), Integration and API Contract (v1.0.0), Backend Architecture (v1.0.0), Frontend Architecture (v1.0.0).
- **Documento Oficial Vivo (1):** `PROJECT_MEMORY.md`.
- **Documento em elaboração:** este documento (TCOS-012) — `THE_CHARCOAL_OS_SECURITY_AND_PRIVACY_ARCHITECTURE.md`.
- **Pendências:** confirmação do domínio de negócio (R-000-03); parâmetros do Módulo 24; M-003A-03/04; M-005-01/02/03; M-006-01; M-007-01; M-008-01; M-009-01; M-010-01/02/03; M-011-01/02/03; decisão sobre retomar a entrevista de descoberta.
- **Riscos ativos:** R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede o desenho da arquitetura de segurança, pois todo dado sensível não confirmado continua tratado por regra de visibilidade padrão (CG-05), nunca exposto por omissão.
- **Dependências para esta fase:** a Segurança Conceitual (System Architecture, TCOS-006, Capítulo 8); a Camada de Segurança/Autorização do backend (TCOS-010, Capítulo 27); as Permissões e Controle de Acesso na Interface (TCOS-011, Capítulo 22); os campos "Quem pode criar/alterar/excluir/visualizar" das 30 entidades (Domain Model, TCOS-002); CG-01, CG-05, CG-06, CG-07 e PF-04/PF-06/PF-11/PF-12 (Framework) — todos referenciados, nenhum reescrito.
- **Objetivo da fase que será iniciada:** definir o comportamento conceitual completo de segurança e privacidade do THE CHARCOAL OS — controle de acesso, perfis, permissões, isolamento de dados, auditoria, sessões, operações críticas, continuidade e disponibilidade — sem nenhuma decisão de tecnologia.
- **O que não pode ser alterado:** nenhum conteúdo de nenhum dos 15 Documentos Oficiais Congelados já aprovados.

### Auditoria de Abertura

Os 15 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase (segurança conceitual já definida, permissões por entidade, isolamento de dados, auditoria e histórico). Resultado:

- Não foram identificadas inconsistências, conflitos ou duplicidades entre os 15 Documentos Oficiais Congelados, no escopo revisado.
- **Base já sólida para a segurança:** o System Architecture (TCOS-006, Capítulo 8) já define Perfis, Permissões, Autenticação/Autorização conceituais, Auditoria, Histórico e Rastreabilidade; o Backend Architecture (TCOS-010, Capítulo 27) já detalha a Camada de Segurança/Autorização como primeiro passo de todo Caso de Uso; o Frontend Architecture (TCOS-011, Capítulo 22) já detalha a checagem de permissão na interface como complementar, nunca substituta, à do backend; o Domain Model (TCOS-002) já define, para cada uma das 30 entidades, quem pode criar/alterar/excluir/visualizar. Este documento **não redefine nada disso** — consolida, aprofunda e formaliza o comportamento de segurança e privacidade como uma arquitetura própria e completa.
- **Lacuna real identificada:** nenhum documento anterior formalizou o conceito de **Sessão** nem de **Expiração de Sessão** — o TCOS-006 previu apenas que "todo usuário tem sua identidade verificada antes de qualquer ação", sem definir por quanto tempo essa verificação permanece válida. Esta arquitetura formaliza Sessões e Expiração de Sessão (Capítulos 25-26) por adição.
- **Lacuna real identificada:** nenhum documento anterior formalizou **Herança de Permissões** — o campo "Quem pode visualizar" de várias entidades já concede à Direção uma visão consolidada (CG-06), mas nenhum documento declarou a regra geral de quando um perfil herda automaticamente o acesso de outro. Esta arquitetura formaliza essa regra (Capítulo 9) a partir do padrão já observável nos 30 registros do Domain Model — nenhuma permissão nova é concedida, apenas o padrão implícito é tornado explícito.
- **Lacuna real identificada:** nenhum documento anterior catalogou **Operações Críticas** como uma categoria formal — RN-006, RN-007 e diversas outras já exigem confirmação explícita individualmente, mas nunca foram reunidas sob um critério único de "o que torna uma operação crítica". Esta arquitetura formaliza esse catálogo (Capítulo 28).
- **Lacuna real identificada:** o Event Bus (TCOS-006, Capítulo 7) cataloga um único evento de segurança ("Permissão alterada") — esta arquitetura amplia, por adição, um catálogo de **Eventos de Segurança** (Capítulo 36), sem alterar o Event Bus já aprovado.
- **Lacuna real identificada:** nenhum documento anterior declarou o que acontece quando a própria checagem de autorização falha ou está indisponível — esta arquitetura formaliza o princípio de **negação padrão** (fail-closed, Capítulo 5): toda falha de checagem de permissão resulta em acesso negado, nunca concedido por omissão. Este é o achado de segurança mais relevante desta auditoria — nenhum dos 15 Documentos Oficiais Congelados o contradiz, mas nenhum o havia declarado explicitamente até agora.
- **Achado de consistência:** a separação entre Auditoria de negócio e Logs técnicos, já formalizada no Backend Architecture (TCOS-010, Capítulos 17-18), é adotada sem alteração como a distinção entre Capítulo 21 (Auditoria) e Capítulo 24 (Logs Conceituais) desta arquitetura.
- **Achado de consistência:** a Regra Transacional de Agregados (TCOS-010, Capítulo 20) já garante que nenhuma escrita ocorre fora de um Caso de Uso — esta arquitetura confirma que toda Operação Crítica (Capítulo 28) é, portanto, sempre rastreável a um único Caso de Uso e a uma única transação, nunca uma operação "solta".
- Nenhuma decisão de linguagem, framework, biblioteca, autenticação específica, criptografia específica, tecnologia ou infraestrutura foi tomada, em conformidade com a restrição explícita da fase.

---

## 1. Papel deste Documento

O System Architecture (TCOS-006) reservou a Segurança Conceitual como capítulo transversal. O Backend Architecture (TCOS-010) e o Frontend Architecture (TCOS-011) detalharam, cada um em seu lado, como a autorização é verificada. Este documento (TCOS-012) consolida e aprofunda **todo** o comportamento de segurança e privacidade do THE CHARCOAL OS em uma arquitetura própria e completa: quem pode fazer o quê, como isso é herdado, como é isolado por domínio de negócio, como é auditado, como sessões funcionam, o que é uma operação crítica, e como o sistema se comporta sob falha — sempre em nível conceitual. Fornece a base de comportamento (Capítulos 3 a 40) necessária para que uma equipe de desenvolvimento inicie a escolha de tecnologia de autenticação, autorização e criptografia; as entidades, regras e telas permanecem nos documentos de origem (TCOS-002 a TCOS-011) e não são redefinidas aqui.

## 2. Legenda e Convenções

- Toda referência a Módulo, Serviço, Entidade, Regra (RN-XXX), Evento, Tela ou Integração (IN-XXX) usa exatamente os nomes/números já oficiais.
- **Perfil:** um dos agrupamentos de acesso já definidos (10 Áreas da Empresa + Administrador do Sistema, TCOS-006 Capítulo 8).
- **Operação Crítica:** ação de negócio que, por seu impacto financeiro, irreversibilidade ou sensibilidade de dado, exige confirmação explícita e registro reforçado (Capítulo 28).
- Todo capítulo de "Segurança de [Domínio]" (12-20) segue o mesmo formato: Dados sensíveis do domínio, Quem acessa, Isolamento aplicado, Risco específico e Regra de mitigação.

---

## 3. Filosofia de Segurança

A segurança do THE CHARCOAL OS não é uma camada adicionada por cima do sistema — é uma consequência direta dos Princípios Fundamentais já aprovados no Framework (PF-01, PF-04, PF-06, PF-11, PF-12) e das Convenções Gerais do Domain Model (CG-01, CG-05, CG-06). Um sistema que já garante um dado único por dono (PF-01), histórico obrigatório (PF-04) e privacidade por padrão (PF-12) já nasce com metade da superfície de risco eliminada — esta arquitetura formaliza a outra metade: quem pode agir sobre esse dado, como essa ação é verificada, e como o sistema se comporta quando algo sai do esperado. A filosofia central é: **confiança nunca é assumida, é sempre verificada** — em cada Caso de Uso (TCOS-010), em cada tela (TCOS-011), sem exceção.

## 4. Princípios Gerais

- **Negação padrão (fail-closed):** toda checagem de permissão que não puder ser concluída com certeza resulta em acesso negado — nunca concedido por omissão, timeout ou indisponibilidade de um componente de segurança.
- **Menor privilégio:** todo perfil recebe apenas o acesso estritamente necessário à sua Área da Empresa (TCOS-006, Capítulo 8) — acesso mais amplo é sempre uma exceção explícita (ex.: Direção, Capítulo 9), nunca o padrão.
- **Defesa em profundidade:** a mesma permissão é verificada em mais de uma camada — na interface (TCOS-011, Capítulo 22, complementar) e, de forma obrigatória e definitiva, no Caso de Uso do backend (TCOS-010, Capítulo 27).
- **Privacidade por padrão (PF-12):** dado pessoal ou financeiro sensível nunca é exibido, exportado ou logado além do mínimo necessário à operação que o usuário está autorizado a executar.
- **Auditabilidade total (PF-04):** toda ação de segurança relevante (login, alteração de permissão, negação de acesso) é registrada com o mesmo rigor de qualquer outra mudança de estado de negócio.
- **Reversibilidade e transparência da IA (PF-06):** nenhuma ação de segurança é delegada à Inteligência Artificial — a IA sugere, nunca decide sobre controle de acesso, permissão ou autenticação.
- **Nenhuma quebra silenciosa (PF-11):** mudança em regra de permissão é tratada como mudança de contrato, nunca aplicada retroativamente sem registro.

## 5. Arquitetura de Segurança

A arquitetura de segurança do THE CHARCOAL OS é **centralizada na decisão, distribuída na aplicação**: a fonte única da regra de permissão é o Serviço de Administração e Segurança (TCOS-006/TCOS-010, item 14) — mas a aplicação dessa regra ocorre em cada um dos 15 Serviços, no primeiro passo de cada Caso de Uso (TCOS-010, Capítulo 8, passo 2), nunca centralizada em um único ponto de execução que, se falho, comprometeria o sistema inteiro. Esta arquitetura formaliza três camadas de verificação, cada uma independente da anterior (defesa em profundidade, Capítulo 4):

1. **Camada de Apresentação (TCOS-011, Capítulo 22):** primeira barreira, de experiência — oculta ou desabilita o que o usuário não pode fazer, mas nunca é a barreira definitiva.
2. **Camada de Aplicação (TCOS-010, Capítulo 27):** barreira obrigatória e definitiva — todo Caso de Uso verifica autorização antes de qualquer leitura ou escrita de domínio.
3. **Camada de Auditoria (Capítulo 21):** barreira de responsabilização — mesmo uma ação autorizada e executada corretamente é sempre rastreável a quem a realizou.

Nenhuma dessas três camadas substitui as outras duas; a ausência de qualquer uma delas é tratada, por esta arquitetura, como uma vulnerabilidade estrutural a ser corrigida antes de qualquer implementação técnica.

## 6. Arquitetura de Privacidade

Complementar à Arquitetura de Segurança (Capítulo 5): enquanto Segurança responde "quem pode agir", Privacidade responde "quem pode ver, e o quê exatamente". Aplica diretamente CG-05 (segurança por padrão) e PF-12:

- **Classificação de sensibilidade de dado:** todo dado do sistema pertence a uma de três categorias — **Público interno** (visível a qualquer perfil autenticado, ex.: nome de Produto), **Restrito por Área** (visível apenas às Áreas relacionadas, ex.: composição de Ficha Técnica), **Sensível** (custo, margem, remuneração, dado pessoal de Cliente/Funcionário — visível apenas a Financeiro/Direção ou ao próprio titular, CG-05).
- **Minimização:** toda tela, relatório ou exportação exibe apenas o dado sensível estritamente necessário à tarefa do perfil que o acessa — nunca um "modo administrador" que exponha tudo de uma vez sem justificativa de tarefa.
- **Separação Pessoa/Empresa:** reafirma o isolamento entre Financeiro Pessoal e Empresarial já definido (TCOS-006, Seção 3.9; RN-002/RN-005) como um requisito de privacidade, não apenas de organização contábil (Capítulo 11).
- **Direito ao próprio dado:** um Cliente ou Funcionário sempre pode visualizar o seu próprio dado (Orçamento, Contrato, Alocação), mesmo sem pertencer a nenhuma Área da Empresa — direito já implícito em vários campos "Quem pode visualizar" do Domain Model (ex.: Contrato, Seção 3.1) e agora formalizado como princípio geral de privacidade.

## 7. Controle de Acesso

O controle de acesso do THE CHARCOAL OS segue o modelo já implícito em todo o Domain Model (TCOS-002): controle baseado em **Perfil vinculado a Área da Empresa** (nunca por usuário individual como unidade primária de permissão). Formalização do fluxo de decisão, para toda tentativa de ação:

1. Identidade do usuário é verificada (Capítulo 25 — Sessão válida).
2. Perfil(is) do usuário são carregados do Serviço de Administração e Segurança.
3. A ação solicitada é comparada à Permissão exigida (Capítulo 8) para a entidade/funcionalidade envolvida.
4. Regras de Herança (Capítulo 9) são aplicadas, se o perfil não tiver a permissão direta.
5. Se, ao final, a permissão não for explicitamente confirmada, o acesso é **negado** (Capítulo 4 — negação padrão).

## 8. Papéis e Responsabilidades

Reafirma, sem alteração, os 10 Perfis por Área da Empresa já definidos (TCOS-006, Capítulo 8, espelhando o Domain Discovery, Seção 5): Comercial/CRM, Produção, Compras/Suprimentos, Estoque/Logística, Eventos/Operações, Financeiro, Marketing, Pessoas/Mão de Obra, Administrativo/Documentos, BI/Direção Executiva — mais o perfil transversal **Administrador do Sistema**. Cada Perfil é responsável, por padrão, por criar e alterar as entidades de que é dono (conforme os campos "Quem pode criar/alterar" já definidos entidade por entidade no Domain Model, TCOS-002) e por visualizar o que a Regra Global de cada entidade já concede. Nenhum Perfil pode excluir fisicamente uma entidade que já entrou em uso de negócio (CG-01) — a responsabilidade de "excluir" é sempre, na prática, a responsabilidade de inativar/cancelar/encerrar (Capítulo 29).

## 9. Perfis de Usuário

Cada Perfil (Capítulo 8) é atribuído a um usuário através do Serviço de Administração e Segurança (Módulo 25). Um usuário pode acumular mais de um Perfil (ex.: um proprietário que atua como Comercial e Direção simultaneamente) — nesse caso, suas permissões são a **união** dos Perfis atribuídos, nunca a interseção (o usuário nunca perde acesso por acumular papéis). O Perfil **BI/Direção Executiva** é o único com **Herança Consolidada** (Capítulo 9, adiante) — os demais 9 Perfis operacionais têm acesso estritamente escopado à sua própria Área, sem herança entre si (ex.: Compras não herda acesso de Estoque, mesmo colaborando na mesma cadeia de valor).

## 10. Permissões

Reafirma, sem redefinir, que toda Permissão do sistema deriva de duas fontes já oficiais, nunca inventadas nesta fase:

- O campo **"Quem pode criar/alterar/excluir/visualizar"** de cada uma das 30 entidades (Domain Model, TCOS-002, Seção 3).
- O campo **"Quem pode criar/alterar/excluir/visualizar"** de cada uma das 98 funcionalidades (Functional Specification, TCOS-003).

Toda Permissão é expressa em quatro tipos de ação — **Criar, Alterar, Visualizar, Encerrar** (substituindo "Excluir", CG-01) — nunca um tipo de ação técnica (ex.: "escrever no banco"). Uma Permissão é sempre concedida a um Perfil, nunca diretamente a um usuário individual (Capítulo 7).

## 11. Herança de Permissões

**Formalizado nesta fase** (achado de auditoria — o padrão já existia de forma implícita e consistente nos 30 registros do Domain Model, mas nunca fora declarado como regra geral). Duas formas de herança, e apenas duas:

- **Herança Consolidada (Direção/BI):** o Perfil BI/Direção Executiva herda **visualização** de toda entidade e Dashboard do sistema, mesmo sem ser o Perfil "dono" da entidade — já confirmado por CG-06 e por praticamente todo campo "Quem pode visualizar" do Domain Model ("consolidado à Direção"). Esta herança é **somente leitura** — a Direção não herda automaticamente permissão de Criar/Alterar sobre entidades de outra Área, salvo onde o Domain Model já concede explicitamente (ex.: Meta, Indicador — TCOS-002, Seções 3.6).
- **Herança Administrativa (Administrador do Sistema):** o Perfil Administrador do Sistema herda a capacidade de Criar/Alterar Perfis e Permissões de outros usuários (Módulo 25) — mas **não herda** visualização de dado de negócio sensível (custo, margem, remuneração, dado pessoal) apenas por ser administrador; esse acesso segue a mesma regra de CG-05 aplicável a qualquer outro Perfil.

Nenhuma outra forma de herança existe — um Perfil operacional nunca herda automaticamente o acesso de outro Perfil operacional, mesmo que colaborem na mesma cadeia de valor (Capítulo 9).

## 12. Isolamento entre Módulos

Reafirma, sob a ótica de segurança, o isolamento de dados já garantido estruturalmente pelo System Architecture (TCOS-006, "um dado, um dono") e pelo Backend Architecture (TCOS-010, Regra Transacional de Agregados, Capítulo 20): nenhum Serviço acessa a estrutura interna de outro, e essa mesma barreira arquitetural é, por construção, uma barreira de segurança — um Perfil autorizado a agir sobre o Serviço Comercial nunca obtém, por esse caminho, acesso à estrutura interna do Serviço Financeiro. O isolamento entre módulos é, portanto, garantido em duas camadas simultâneas: **arquitetural** (contratos públicos, TCOS-010 Capítulo 7) e **de permissão** (Capítulo 10) — a violação de qualquer uma delas, isoladamente, não compromete a outra.

## 13. Isolamento entre Dados Pessoais e Empresariais

Formaliza, como requisito de segurança e privacidade, o que o System Architecture (TCOS-006, Seção 3.9) já resolveu como decisão de modelagem: Financeiro Pessoal e Financeiro Empresarial são dois **contextos de dado** dentro do mesmo Serviço, isolados por categoria de lançamento (RN-002/RN-005), nunca por Serviço técnico separado. Esta arquitetura acrescenta a regra de segurança correspondente: nenhum Perfil que tenha acesso apenas a Financeiro Empresarial pode visualizar um lançamento categorizado como Retirada Pessoal, e vice-versa — a mesma tela (Dashboard Financeiro Pessoal/Empresarial, TCOS-005) nunca mistura os dois contextos em uma única consulta ao Serviço. O mesmo princípio de isolamento se estende a qualquer dado pessoal (Cliente, Funcionário) versus dado da operação empresarial: dado pessoal sensível (contato, remuneração) é sempre um sub-conjunto restrito dentro da entidade, nunca uma tabela ou tela genérica sem controle de campo.

---

## 14. Segurança Financeira

Dados sensíveis: saldo de Conta, valor de Pagamento/Despesa/Receita Financeira, dado bancário. Quem acessa: Financeiro, Direção (consolidado); Comercial visualiza apenas o status do próprio Contrato (TCOS-002, Seção 3.1). Isolamento aplicado: Pessoal/Empresarial (Capítulo 13); nenhuma Área fora de Financeiro/Direção acessa saldo de Conta ou detalhe de Pagamento. Risco específico: exposição de saldo consolidado ou dado bancário a Perfil sem necessidade de negócio; lançamento fraudulento sem origem identificável. Regra de mitigação: toda Despesa/Receita Financeira exige origem identificável (RN-045); toda alteração de Pagamento é por estorno + novo registro, nunca edição in-place (TCOS-007, Seção 4.4) — preservando rastreabilidade completa mesmo em caso de erro ou fraude.

## 15. Segurança da Engenharia de Custos

Dados sensíveis: custo de Ingrediente, custo total de Ficha Técnica, margem calculada. Quem acessa: Produção, Financeiro, Direção; Comercial visualiza apenas o preço resultante, não o detalhamento de custo (CG-05, TCOS-002 Seção 3.2 — Ficha Técnica), salvo decisão em contrário do proprietário. Isolamento aplicado: separação entre "preço" (visível a Comercial) e "custo"/"margem" (restrito a Produção/Financeiro/Direção). Risco específico: vazamento de margem para Comercial poderia influenciar negociação com Cliente de forma não autorizada pela Direção. Regra de mitigação: a Camada de Domínio do Serviço de Custos e Precificação (TCOS-010, item 4) nunca expõe o campo de custo/margem em uma consulta originada de um Caso de Uso do Serviço Comercial — apenas o preço final já calculado.

## 16. Segurança de Produção

Dados sensíveis: modo de preparo de Receita, rendimento e perda real de Produção. Quem acessa: Produção; Financeiro/Direção visualizam o custo resultante (Ficha Técnica), não necessariamente o modo de preparo (TCOS-002, Seção 3.2 — Receita). Isolamento aplicado: know-how de produção (Receita) restrito à própria Área, mesmo para Direção, salvo necessidade de auditoria formal. Risco específico: exposição de composição/modo de preparo (know-how do negócio) a Perfis externos à Produção. Regra de mitigação: nenhuma tela ou exportação de Ficha Técnica (TCOS-005, Seção 3.19) inclui o modo de preparo da Receita associada quando consultada por um Perfil fora de Produção.

## 17. Segurança do Estoque

Dados sensíveis: saldo real e localização de Estoque, rastreabilidade de Lote (potencialmente relevante a furto/perda). Quem acessa: Produção, Compras, Estoque/Logística; consolidado à Direção. Isolamento aplicado: nenhum Perfil fora de Suprimentos altera Estoque diretamente (PF-01, TCOS-006 Seção 3.16) — apenas consulta. Risco específico: ajuste manual de saldo sem rastreabilidade, mascarando perda ou desvio. Regra de mitigação: toda alteração de Estoque deriva de um evento de origem (Compra, Produção, venda) ou de um inventário formal explicitamente registrado (TCOS-002, Seção 3.3) — nunca uma edição livre de saldo sem evento e sem autor identificado (PF-04).

## 18. Segurança dos Eventos

Dados sensíveis: dado de Cliente associado ao Evento, escopo comercial, valor do Contrato. Quem acessa: Eventos/Operações, Comercial, Produção (escopo), Financeiro (valor); consolidado à Direção. Isolamento aplicado: nenhum recurso (Produção/Estoque/Equipamento/Alocação) é reservado antes de "Confirmado" (TCOS-002, Seção 3.7) — a segurança aqui é também operacional: impedir comprometimento de recursos por um Evento ainda não formalizado. Risco específico: confirmação indevida de Evento sem viabilidade operacional real (RN-006), gerando cascata de reservas de recurso incorreta. Regra de mitigação: a Operação Crítica "Confirmar Evento" (Capítulo 30) exige que a Regra de Negócio RN-006 bloqueie a confirmação antes de qualquer publicação de evento, nunca depois (TCOS-010, Capítulo 11).

## 19. Segurança dos Dashboards

Dados sensíveis: qualquer dado consolidado de outra Área, por definição (Dashboard CEO consome de todos os 27 módulos, TCOS-005 Seção 3.1). Quem acessa: conforme o público-alvo de cada Dashboard (TCOS-005); o Dashboard CEO é visível apenas à Direção. Isolamento aplicado: cada Dashboard aplica a mesma checagem de sensibilidade por campo (Capítulo 6), não apenas por tela inteira — um Dashboard consolidado nunca é uma forma de contornar a restrição de um dado individual. Risco específico: um Dashboard amplo (que já agrega múltiplas Áreas) se tornar um ponto único de vazamento de dado sensível de várias origens ao mesmo tempo. Regra de mitigação: o Serviço de Indicadores e Dashboards (TCOS-010, item 10) nunca compõe um Indicador exibível a um Perfil sem checar a sensibilidade do dado de origem daquele Indicador especificamente, mesmo quando o Dashboard como um todo é acessível a esse Perfil.

## 20. Segurança da IA

Dados sensíveis: qualquer dado de entrada usado pela IA para gerar sugestão (extrato bancário, dado de Produção, preço) e a própria sugestão gerada. Quem acessa: o Serviço de origem de cada sugestão (TCOS-010, Capítulo 28); o Dashboard de Inteligência Artificial (TCOS-005, Seção 3.11) é consultado pelos Perfis já autorizados ao dado subjacente. Isolamento aplicado: a IA nunca acumula, em um único ponto, dado de múltiplos Serviços além do estritamente necessário à sugestão que está gerando (PF-06) — nunca um "perfil consolidado" de dado cruzado sem finalidade declarada. Risco específico: uma sugestão de IA ser tratada como decisão já tomada, ou dado sensível vazar através do texto de uma sugestão exibida a um Perfil sem a permissão original sobre aquele dado. Regra de mitigação: toda sugestão de IA é exibida apenas ao Perfil que já teria acesso ao dado de origem por sua própria Permissão (Capítulo 10) — a IA nunca amplia o acesso a um dado que o Perfil não teria de outra forma; e nenhuma sugestão produz efeito sem confirmação humana explícita (RN-041, TCOS-011 Capítulo 31).

## 21. Segurança das Integrações

Dados sensíveis: qualquer dado trafegando entre Serviços através do Event Bus (TCOS-006, Capítulo 7), e qualquer dado externo entrando pelo Gateway de Integrações Futuras (TCOS-010, Capítulo 29). Quem acessa: apenas os Serviços assinantes já definidos de cada evento (Capítulo 12 — isolamento entre módulos). Isolamento aplicado: nenhuma Integração (TCOS-009) expõe a estrutura interna de um Serviço a outro além do que o evento já carrega (TCOS-010, Capítulo 14 — apenas o necessário para decidir a reação). Risco específico: uma futura integração externa (nova instituição bancária, nova fonte de dado) injetar dado malformado ou não confiável diretamente em um Serviço interno. Regra de mitigação: reafirma o Gateway de Integrações Futuras (TCOS-010, Capítulo 29) como fronteira obrigatória — todo dado externo é traduzido para um evento de domínio já catalogado antes de acionar qualquer Caso de Uso interno, nunca aceito em formato ou estrutura arbitrária.

## 22. Segurança dos Documentos

Dados sensíveis: conteúdo de Contrato, Compra e demais Documentos gerados, que podem conter dado pessoal ou financeiro de Cliente/Fornecedor. Quem acessa: a Área responsável pela entidade de origem; Administrativo/Documentos tem visão consolidada (TCOS-002, Seção 3.6). Isolamento aplicado: o Módulo 23 não possui tela própria (servido pelo componente "Documentos Anexados", TCOS-011 Capítulo 5) — a permissão de acesso a um Documento é sempre herdada da entidade de origem (Contrato, Compra), nunca uma permissão própria e paralela de "Documentos" que pudesse divergir da entidade que o originou. Risco específico: um Documento permanecer acessível a um Perfil que perdeu acesso à entidade de origem (ex.: Contrato encerrado e reatribuído). Regra de mitigação: a checagem de permissão de um Documento sempre consulta, em tempo de execução, a permissão vigente sobre a entidade de origem (Capítulo 10) — nunca uma permissão fixada no momento da geração do Documento.

---

## 23. Auditoria

Reafirma, sem alteração, o Serviço de Auditoria já definido (TCOS-006, Capítulo 6; TCOS-010, Capítulo 17): assina todos os eventos do Event Bus, sem exceção, e constrói um log de negócio imutável e apenas-para-inserção — quem fez o quê, quando, a partir de qual comando. Sob a ótica desta arquitetura de segurança, a Auditoria é a terceira camada de verificação já formalizada no Capítulo 5: mesmo uma ação corretamente autorizada permanece **responsabilizável** — a autorização decide se a ação pode ocorrer; a Auditoria garante que, tendo ocorrido, ela é para sempre atribuível a alguém.

## 24. Histórico Imutável

Reafirma, sem alteração, CG-01/PF-04 e a Estratégia de Soft Delete já definida (TCOS-007, Seção 7.2; TCOS-008, Capítulo 6): nenhuma entidade que já participou de um processo de negócio é fisicamente excluída — apenas transita para um estado terminal, preservando toda versão anterior. Sob a ótica de segurança, a imutabilidade do histórico é o que impede que uma ação mal-intencionada (alteração indevida, tentativa de "apagar rastros") produza efeito: mesmo que uma permissão seja indevidamente concedida e usada, a ação permanece registrada e nunca pode ser retroativamente removida do histórico.

## 25. Rastreabilidade

Reafirma, sem alteração, RN-039/RN-040 e a Estratégia de Identificação Global (TCOS-007, Seção 7.5): todo Identificador Global é único, estável e nunca reutilizado; todo valor exibido em qualquer Dashboard é rastreável, evento por evento, até a ação humana ou automática que o originou. Sob a ótica de segurança, a Rastreabilidade é o que permite reconstruir, a qualquer momento e para qualquer entidade, a cadeia completa de "quem viu o quê" e "quem alterou o quê" — pré-requisito de qualquer investigação de incidente de segurança ou privacidade, sem exigir uma estrutura de log paralela além da já existente (Log de Auditoria, TCOS-008 Seção 13.8).

## 26. Logs Conceituais

Reafirma, sem alteração, a distinção já formalizada no Backend Architecture (TCOS-010, Capítulo 18) entre Auditoria de negócio (Capítulo 23) e Logs técnicos: os Logs Conceituais registram comportamento técnico de execução (início/fim de Caso de Uso, falha de consulta, entrega de evento), nunca decisão de negócio. Sob a ótica de segurança, esta arquitetura acrescenta uma restrição própria: **os Logs Conceituais são, eles mesmos, um ativo protegido** — o acesso de leitura aos Logs é restrito à equipe técnica e à Administração e Segurança (Módulo 25), nunca exposto a um Perfil operacional comum, mesmo que o Log não contenha dado de negócio, pois padrões de acesso técnico (quem tentou o quê, quando) são, por si, uma informação sensível de segurança.

## 27. Sessões

**Formalizado nesta fase** (achado de auditoria — nenhum documento anterior definiu o conceito). Uma Sessão é o período em que a identidade de um usuário, já autenticada (TCOS-006, Capítulo 8), permanece válida para autorizar ações sem nova verificação de identidade completa. Toda Sessão:

- É criada no momento da autenticação bem-sucedida, carregando o(s) Perfil(is) do usuário (Capítulo 9).
- É a unidade que sustenta o Estado de Sessão já definido no frontend (TCOS-011, Capítulo 8) — mas sua validade real é sempre verificada no backend (Capítulo 5), nunca assumida apenas porque a interface ainda a exibe como ativa.
- É encerrada por ação explícita do usuário (logout), por Expiração (Capítulo 28), ou por revogação administrativa (ex.: desligamento de Funcionário, TCOS-002 Seção 3.5 — "Funcionário desligado" não pode manter Sessão ativa).

## 28. Expiração de Sessão

**Formalizado nesta fase.** Toda Sessão expira por dois motivos, e apenas dois — nenhum sistema de sessão "eterna":

- **Inatividade:** ausência de qualquer ação do usuário por um período definido (parâmetro de Configuração, Módulo 24 — sujeito às mesmas regras de parâmetro pendente já aplicadas a qualquer outro parâmetro de negócio, R-002A-01).
- **Duração máxima:** um limite absoluto de validade, independentemente de atividade contínua, forçando nova autenticação periódica mesmo para uso ininterrupto.

Ao expirar, a Sessão é imediatamente inválida para qualquer nova checagem de autorização (Capítulo 5) — nenhuma ação em andamento é concluída "silenciosamente" após a expiração; qualquer Caso de Uso em execução no momento da expiração segue a mesma regra de negação padrão (Capítulo 4). Uma Operação Crítica (Capítulo 30) pode exigir reautenticação mesmo dentro de uma Sessão ainda válida — reforço de segurança específico para ações de maior impacto, não uma contradição à validade geral da Sessão.

---

## 29. Confirmações Obrigatórias

Reafirma, como requisito de segurança, o padrão de confirmação explícita já espalhado por diversos documentos (TCOS-005, Capítulo 4 — "como exclui"; TCOS-011, Capítulo 17 — feedback visual): toda ação irreversível ou de alto impacto exige uma confirmação explícita e distinta do clique que a originou — nunca uma ação de duplo-efeito acidental (ex.: um único clique que já efetiva um Pagamento). A confirmação sempre exibe, de forma resumida, o que exatamente vai mudar (RN e entidade afetada), nunca um texto genérico "Tem certeza?" sem contexto.

## 30. Operações Críticas

**Catalogado nesta fase** (achado de auditoria — o requisito de confirmação já existia disperso por regra individual, nunca reunido sob um critério único). Uma ação é uma Operação Crítica quando atende a pelo menos um destes critérios: impacto financeiro direto e relevante; irreversibilidade (mesmo que soft-delete); alteração de permissão/perfil de outro usuário; exposição ou exportação de dado sensível (Capítulo 6); ou aceite de sugestão de Inteligência Artificial (Capítulo 20). Catálogo não exaustivo de Operações Críticas já identificadas nos documentos anteriores:

| Operação Crítica | Origem | Exigência adicional |
|---|---|---|
| Confirmar Evento | RN-006 | bloqueio prévio de viabilidade operacional |
| Cancelar Evento / Contrato | RN-007, RN-015 | confirmação com motivo obrigatório |
| Registrar Pagamento / Estorno | RN-044, RN-045 | confirmação explícita, nunca duplo-clique acidental |
| Alterar Perfil/Permissão de usuário | Módulo 25 | reautenticação (Capítulo 28), registro reforçado (Capítulo 36) |
| Aceitar sugestão de IA financeira/comercial | RN-041 a RN-043 | confirmação humana explícita, nunca automática |
| Inativar/Descontinuar entidade Mestre | CG-01 | confirmação com verificação de referência ativa (TCOS-007, Seção 7.4) |
| Exportar relatório com dado sensível | Capítulo 6 | checagem de sensibilidade por campo antes da exportação |
| Importar Extrato Bancário | IN-012 | validação de origem antes de qualquer Caso de Uso interno (Capítulo 21) |

## 31. Exclusão Lógica

Reafirma, sem alteração, CG-01 e a Estratégia de Soft Delete (TCOS-007, Seção 7.2): nenhuma entidade que já participou de um processo de negócio é fisicamente excluída — apenas um registro puramente transitório e nunca confirmado (ex.: Rascunho de Orçamento abandonado) é elegível a remoção física. Sob a ótica de segurança e privacidade, esta arquitetura acrescenta uma distinção: a Exclusão Lógica protege a **integridade do histórico de negócio** (Capítulo 24), mas não substitui uma eventual obrigação legal de anonimização de dado pessoal — cenário registrado como pendência de governança futura (TCOS-007, Seção 6, "Retenção"), não resolvido nesta fase por depender de decisão de negócio ainda não confirmada.

---

## 32. Recuperação de Dados

Reafirma, sem alteração, a Governança dos Dados já definida (TCOS-007, Seção 6 — "Recuperação"): como nenhuma exclusão física ocorre para dado que já entrou em uso de negócio, a "recuperação" de um registro é, na prática, a reversão do seu estado (ex.: reativar um Cliente) — sempre uma ação registrada e auditável (Capítulo 23), nunca uma restauração de backup para dado de negócio corrente. Sob a ótica de segurança, esta arquitetura reforça que a própria ação de reversão de estado é, ela mesma, uma Operação Crítica (Capítulo 30) sujeita às mesmas exigências de confirmação e auditoria.

## 33. Backup (Conceitual)

Reafirma, sem alteração, a Estratégia de Backup já definida (TCOS-008, Capítulo 10): camadas de criticidade (Financeiro e Log de Auditoria com a maior frequência de proteção), recuperação em um ponto no tempo, e backup como proteção contra falha técnica — nunca um mecanismo de desfazer decisão de negócio. Esta arquitetura acrescenta a exigência de segurança correspondente: o acesso a um backup restaurado segue exatamente as mesmas regras de Permissão (Capítulo 10) e Isolamento (Capítulos 12-13) do dado original — um backup nunca é um caminho alternativo para contornar uma restrição de acesso vigente no sistema em produção.

## 34. Continuidade Operacional

Formaliza, sob a ótica de segurança, o compromisso já implícito na Estratégia de Escalabilidade (TCOS-006, Capítulo 9; TCOS-010, Capítulo 22): a indisponibilidade de um Serviço Auxiliar nunca compromete a continuidade dos Serviços Centrais (TCOS-006, Capítulo 4). Esta arquitetura acrescenta que a continuidade da **segurança** segue a mesma prioridade — em qualquer cenário de degradação, a checagem de autorização (Capítulo 5) é o último mecanismo a ser sacrificado; um sistema pode, no limite, negar uma funcionalidade não crítica, mas nunca conceder acesso sem verificação para "manter tudo funcionando" (reforça a negação padrão, Capítulo 4).

## 35. Tratamento de Falhas

Reafirma, sob a ótica de segurança, a Camada de Tolerância a Falhas já definida no backend (TCOS-010, Capítulo 26): retry controlado, isolamento de falha de Serviço Auxiliar, degradação graciosa. Esta arquitetura acrescenta a regra específica de segurança: toda falha em um componente de segurança (checagem de permissão, validação de Sessão) é tratada exclusivamente pela categoria "Erro técnico" do Tratamento de Erros (TCOS-010, Capítulo 19) — nunca reclassificada como sucesso por retry automático sem nova verificação completa; um retry de autorização sempre reexecuta a checagem inteira, nunca assume o resultado de uma tentativa anterior incompleta.

## 36. Disponibilidade

Reafirma, sem alteração, a independência de escala de cada um dos 15 Serviços (TCOS-006, Capítulo 9; TCOS-010, Capítulo 22). Sob a ótica de segurança, a Disponibilidade do Serviço de Administração e Segurança (item 14) é tratada como **prioridade central**, ainda que classificado como Serviço Auxiliar na Matriz de Dependências (TCOS-006, Capítulo 4) — sua indisponibilidade não deve impedir a operação dos Serviços Centrais para leituras já autorizadas dentro de uma Sessão válida (Capítulo 27), mas impede, pela negação padrão (Capítulo 4), qualquer nova concessão de permissão até que a verificação volte a estar disponível.

## 37. Escalabilidade da Segurança

Reafirma, sem alteração, o critério de "extensão, nunca reconstrução" já estabelecido no Framework (Seção 25) e no System Architecture (TCOS-006, Capítulo 9). Um novo Perfil, uma nova Área da Empresa ou uma nova Operação Crítica se integram a este catálogo por adição — nunca exigindo redesenho das regras de Permissão (Capítulo 10) ou Herança (Capítulo 11) já vigentes. A dimensão Multiempresa/Multifilial (TCOS-007, Seções 7.6/7.7, M-006-01/M-007-01) é reservada, também aqui, como escopo adicional de isolamento (um Perfil poderá, no futuro, ser escopado por Unidade/Organização) — sem exigir uma segunda arquitetura de segurança paralela quando essa dimensão for implementada.

---

## 38. Eventos de Segurança

**Catálogo ampliado nesta fase** (achado de auditoria — o Event Bus, TCOS-006 Capítulo 7, cataloga apenas "Permissão alterada"). Estes eventos seguem exatamente o mesmo padrão publicar-assinar já aprovado (TCOS-006/TCOS-010) — nenhuma tecnologia de mensageria é definida, apenas o catálogo de negócio:

| Evento de Segurança | Publicado por | Assinado por | Efeito |
|---|---|---|---|
| Sessão iniciada | Administração e Segurança | Auditoria | registro de login |
| Sessão encerrada (logout/expiração) | Administração e Segurança | Auditoria | registro de encerramento |
| Tentativa de acesso negada | Serviço de origem da ação | Auditoria, Administração e Segurança | registro; alerta se repetida (Capítulo 30) |
| Permissão alterada *(já catalogado, TCOS-006)* | Administração e Segurança | Auditoria | registro de alteração de acesso |
| Operação Crítica confirmada | Serviço de origem | Auditoria | registro reforçado (autor, motivo, dado afetado) |
| Dado sensível exportado | Serviço de origem | Auditoria | registro de exportação (Capítulo 6) |

Todo Evento de Segurança é, sem exceção, assinado pelo Serviço de Auditoria (Capítulo 23) — nenhum evento desta categoria é opcionalmente auditado.

## 39. Matriz de Responsabilidades

Consolida, por Perfil, o padrão já existente entidade a entidade no Domain Model (TCOS-002, Seção 3) — nenhuma permissão nova é concedida aqui, apenas agregada por Perfil:

| Perfil | Cria/Altera (domínio próprio) | Visualiza consolidado | Não acessa (sem herança) |
|---|---|---|---|
| Comercial/CRM | Lead, Cliente, Orçamento, Contrato, Pacote | preço (não custo/margem) | custo/margem (Capítulo 15), remuneração |
| Produção | Produto, Ingrediente, Receita, Ficha Técnica, Produção | custo resultante | dado bancário, remuneração |
| Compras/Suprimentos | Fornecedor, Compra, Estoque, Lote | — | margem comercial, remuneração |
| Estoque/Logística | Estoque, Lote (movimentação) | — | dado financeiro, comercial |
| Eventos/Operações | Evento, Equipamento, Veículo | escopo do Evento | dado financeiro consolidado |
| Financeiro | Despesa, Receita Financeira, Pagamento, Banco, Conta | custo/margem, remuneração | modo de preparo (Receita) |
| Marketing | Campanha | retorno por Campanha | dado financeiro além de Contrato/retorno |
| Pessoas/Mão de Obra | Funcionário, Alocação | — | remuneração de outros Perfis (restrito a Financeiro/Direção) |
| Administrativo/Documentos | Documento (por herança da entidade de origem, Capítulo 22) | visão consolidada de Documentos | dado de origem além do já permitido pela entidade |
| BI/Direção Executiva | Meta, Indicador, Dashboard | **tudo** (Herança Consolidada, Capítulo 11) | — (única exceção à restrição por Área) |
| Administrador do Sistema | Perfil, Permissão (Módulo 25) | configuração do sistema | dado de negócio sensível (Capítulo 11) |

## 40. Fluxo Conceitual de Segurança

Consolida, em uma única sequência, os Capítulos 5 a 11:

1. Usuário se autentica → Sessão criada (Capítulo 27).
2. Perfil(is) carregado(s) do Serviço de Administração e Segurança (Capítulo 9).
3. Usuário navega a uma tela (TCOS-011) → interface aplica a primeira barreira de permissão (Capítulo 22 do TCOS-011).
4. Usuário aciona um Caso de Uso (TCOS-010, Capítulo 8) → backend verifica Sessão válida (Capítulo 28), depois Permissão direta ou herdada (Capítulos 10-11).
5. Se autorizado: Caso de Uso prossegue, dado é alterado dentro de uma única transação (TCOS-010, Capítulo 20), evento é publicado (Capítulo 38, se aplicável).
6. Se não autorizado, por qualquer motivo, incluindo falha de verificação: acesso **negado** (Capítulo 4) e evento "Tentativa de acesso negada" publicado.
7. Toda a sequência, com sucesso ou negação, é registrada pela Auditoria (Capítulo 23).

## 41. Fluxo Conceitual de Auditoria

Consolida, em uma única sequência, os Capítulos 23-26:

1. Um evento de domínio ou de segurança (Capítulo 38) é publicado por qualquer Serviço.
2. O Serviço de Auditoria assina o evento, sem exceção (TCOS-006, Capítulo 6).
3. Um registro imutável, apenas-para-inserção, é gravado: estrutura afetada, Identificador Global, tipo de evento, autor, data/hora, resumo (TCOS-008, Seção 13.8).
4. O registro fica disponível para consulta (nunca alteração) por: Auditoria Visual de Ações na interface (TCOS-011, Capítulo 23), investigação técnica via Observabilidade (TCOS-010, Capítulo 25; TCOS-011, Capítulo 30), ou reconciliação de eventos (TCOS-010, Capítulo 16).
5. Nenhum registro de Auditoria é jamais removido, mesmo que a entidade a que se refere seja posteriormente inativada, cancelada ou encerrada (Capítulo 24).

## 42. Regras Gerais de Segurança

Consolidação final, sem introduzir regra nova além do já formalizado nos capítulos anteriores:

1. Negação padrão sempre que uma verificação não puder ser concluída com certeza (Capítulo 4).
2. Permissão sempre por Perfil, nunca por usuário individual isolado (Capítulo 7).
3. Herança apenas nos dois padrões formalizados — Consolidada (Direção) e Administrativa (Administrador) — nunca implícita em outro caso (Capítulo 11).
4. Toda Operação Crítica exige confirmação explícita e registro reforçado (Capítulos 29-30).
5. Nenhuma exclusão física de dado que já participou de processo de negócio (Capítulo 31).
6. Toda ação relevante é auditável, permanente e nunca removível (Capítulos 23-24).
7. Dado sensível é minimizado por padrão e nunca exposto além da necessidade da tarefa (Capítulo 6).
8. A Inteligência Artificial nunca decide sobre segurança, permissão ou autenticação (Capítulo 4).
9. A checagem de permissão do backend é sempre definitiva; a da interface é sempre complementar (Capítulo 5).
10. Nenhuma mudança de regra de segurança quebra silenciosamente um comportamento já aprovado (PF-11) — toda mudança é uma nova versão explícita.

---

## RESUMO PARA O PROPRIETÁRIO

**O que foi construído:** a arquitetura conceitual completa de segurança e privacidade do THE CHARCOAL OS — quem pode fazer o quê (Perfis, Permissões, Herança), como o dado sensível é protegido (Privacidade, isolamento Pessoal/Empresarial, segurança por domínio de negócio), como toda ação fica registrada para sempre (Auditoria, Histórico Imutável, Rastreabilidade), como uma sessão de uso funciona e expira, o que torna uma operação "crítica" e exige confirmação reforçada, e como o sistema se comporta diante de falha (sempre negando acesso por segurança, nunca liberando por conveniência).

**Por que isso é importante:** até aqui, cada documento já continha pedaços de segurança (quem vê o quê em cada tela, quem decide o quê em cada regra) — mas nenhum os havia reunido em uma única arquitetura coerente. Isso importa especialmente porque o THE CHARCOAL OS mistura, no mesmo lugar, dinheiro pessoal e da empresa, dado de Cliente e Funcionário, e sugestões de Inteligência Artificial — exatamente os tipos de informação que exigem mais cuidado.

**Quais benefícios traz:** reduz o risco de um Perfil ver ou alterar algo que não deveria; garante que toda ação (mesmo autorizada) fique para sempre atribuível a alguém; e estabelece uma regra simples e poderosa — na dúvida, o sistema nega acesso, nunca concede.

**Como se conecta com os documentos anteriores:** nenhuma tela, entidade, regra, Serviço ou Integração foi redefinida — este documento reúne o que já estava certo (Segurança Conceitual do TCOS-006, permissões do TCOS-002, checagens do TCOS-010 e TCOS-011) e preenche, por adição, o que ainda faltava (sessões, herança de permissão, catálogo de operações críticas).

**Como prepara as próximas fases:** com backend (TCOS-010), frontend (TCOS-011) e agora segurança (TCOS-012) todos definidos em nível conceitual, o projeto está pronto para a etapa de decisão tecnológica real (linguagem, banco, autenticação, infraestrutura) sem que nenhuma dessas escolhas técnicas precise redefinir como o sistema se comporta.

---

## TCOS QUALITY GATE EXECUTIVO

Em conformidade com o Framework v1.2.0, os 15 Documentos Oficiais Congelados foram revisados quanto aos pontos relevantes a esta fase — resultado consolidado na Auditoria de Abertura e reafirmado aqui.

**1. Resumo Executivo da Fase**
Definida a arquitetura conceitual completa de segurança e privacidade do THE CHARCOAL OS: 40 tópicos obrigatórios cobertos (Capítulos 3-42), 11 Perfis consolidados em Matriz de Responsabilidades, 6 novos conceitos formalizados por adição (Herança de Permissões, Sessões, Expiração de Sessão, Operações Críticas, Eventos de Segurança, princípio de negação padrão), 9 capítulos de segurança por domínio de negócio, e 2 fluxos conceituais consolidados (Segurança e Auditoria). Nenhuma tecnologia foi definida; nenhum dos 15 Documentos Oficiais Congelados foi alterado.

**2. Estado Atual do Projeto**
Fases 000 a 011 encerradas e oficiais; Fase 012 em validação. Nenhum código, autenticação real, criptografia, infraestrutura ou desenvolvimento foi iniciado.

**3. Documentos Oficiais Existentes**
16 no total — 15 Documentos Oficiais Congelados + 1 Documento Oficial Vivo (`PROJECT_MEMORY.md`), mais este documento em rascunho (não contado como oficial até aprovação).

**4. Dependências**
Segurança Conceitual (TCOS-006, Capítulo 8); Camada de Segurança/Autorização do backend (TCOS-010, Capítulo 27); Permissões e Controle de Acesso na Interface (TCOS-011, Capítulo 22); campos de acesso das 30 entidades (TCOS-002); CG-01/05/06/07 e PF-04/06/11/12 (Framework) — todos referenciados, nenhum reescrito.

**5. Pendências Abertas**
Validação formal deste documento; parâmetros do Módulo 24 (incluindo o novo parâmetro de duração de Sessão/inatividade, identificado nesta fase); M-003A-03/04; M-005-01/02/03; M-006-01; M-007-01; M-008-01; M-009-01; M-010-01/02/03; M-011-01/02/03; confirmação do domínio de negócio (R-000-03); decisão de governança sobre anonimização de dado pessoal (Capítulo 31, nova pendência de negócio, não de arquitetura).

**6. Dúvidas Encontradas**
Nenhuma nova de negócio. Uma dúvida técnica foi levantada e já resolvida dentro desta própria fase: o que fazer quando a própria checagem de permissão falha — respondida pelo princípio de negação padrão (Capítulo 4).

**7. Riscos Ativos**
R-000-03/R-002-01, R-001-01/R-002-02, R-002A-01 — herdados; nenhum impede a arquitetura de segurança.

**8. Novos Riscos Encontrados**
Nenhum risco novo de negócio. Um risco de governança (não técnico) foi identificado: ausência de decisão sobre anonimização de dado pessoal para eventual exigência legal futura — registrado como pendência (item 5), não como risco de arquitetura, pois a Exclusão Lógica (Capítulo 31) já protege a integridade do histórico independentemente dessa decisão.

**9. Inconsistências Encontradas**
Nenhuma entre os 15 Documentos Oficiais Congelados, no escopo revisado.

**10. Conflitos entre Documentos**
Nenhum.

**11. Regras Duplicadas**
Nenhuma — todas as Regras de Negócio citadas (RN-002, RN-005, RN-006, RN-007, RN-015, RN-039 a RN-045) são citações do Business Rules Specification (TCOS-002A) já oficial, nunca reescritas ou duplicadas nesta arquitetura.

**12. Entidades Duplicadas**
Nenhuma — as 30 entidades permanecem exatamente as do Domain Model (TCOS-002); esta arquitetura apenas consolida seus campos de acesso já existentes em uma Matriz (Capítulo 39).

**13. Oportunidades de Simplificação**
Identificada e concretizada: reunir os campos de permissão, até então dispersos entidade por entidade no Domain Model, em uma única Matriz de Responsabilidades por Perfil (Capítulo 39) — reduz o esforço de consulta de "quem pode o quê" de 30 buscas individuais para uma única tabela.

**14. Melhorias Sugeridas**
- M-012-01 (nova): ao escolher a tecnologia de autenticação em fase técnica futura, avaliar mecanismos nativos de expiração de sessão e reautenticação para Operações Críticas antes de implementá-los de forma customizada.
- M-012-02 (nova): confirmar com o proprietário o parâmetro de duração de Sessão/inatividade (Capítulo 28) — hoje modelado como Configuração pendente, sem valor assumido.
- M-012-03 (nova): decisão de governança sobre anonimização de dado pessoal (Capítulo 31) permanece pendente — recomenda-se tratá-la antes de uma eventual exigência legal, não apenas reativamente.

**15. Impacto desta Fase nas Próximas**
Esta arquitetura de segurança é a referência obrigatória, junto ao TCOS-010 e TCOS-011, para qualquer fase técnica futura — nenhuma escolha de autenticação, criptografia ou infraestrutura deve introduzir um comportamento de acesso, herança, sessão ou auditoria incompatível com o que está aqui documentado, sem registrar formalmente o motivo.

**16. Quality Score: 9,5/10**
Justificativa técnica: cobertura completa dos 40 tópicos exigidos, com identificação e resolução — não apenas menção — de lacunas conceituais reais (Sessões, Expiração, Herança de Permissões, Operações Críticas, Eventos de Segurança, negação padrão), todas em conformidade com os 15 Documentos Oficiais Congelados, sem nenhuma contradição encontrada. Não é 10 porque 3 melhorias novas (M-012-01 a M-012-03) permanecem como refinamento pendente de decisões futuras (tecnologia de autenticação, parâmetro de sessão, governança de anonimização).

**17. Recomendação:** **APROVAR** — o documento cumpre integralmente o escopo solicitado, em nível conceitual, sem nenhuma decisão de tecnologia, e sem alterar nenhum documento anterior.

**18. Atualização do PROJECT_MEMORY.md:** ver commit correspondente — exclusivamente a seção da Fase 012.

**Estatísticas Finais**
- Quantidade total de páginas equivalentes: aproximadamente 24.
- Quantidade de entidades: 30 (referenciadas, 0 novas).
- Quantidade de regras: 47 no total do sistema; 12 citadas diretamente nesta arquitetura (0 novas, 0 alteradas).
- Quantidade de processos/fluxos conceituais: 2 (Fluxo Conceitual de Segurança, Fluxo Conceitual de Auditoria).
- Quantidade de eventos: 6 Eventos de Segurança catalogados (1 herdado do TCOS-006 + 5 novos).
- Quantidade de decisões registradas: 4 (D-012-01 a D-012-04, ver `PROJECT_MEMORY.md`).
- Quantidade de riscos ativos: 4 herdados; 0 novos de arquitetura.
- Quantidade de pendências: 11 (validação do documento + 10 herdadas/novas, incluindo 1 nova de governança).
- Quantidade de melhorias sugeridas: 3 novas (M-012-01 a M-012-03).
- Percentual estimado de maturidade do projeto: **91%** (subiu de 88% — a terceira e última arquitetura conceitual essencial antes do desenvolvimento [Backend, Frontend, Segurança] está completa e auditada; restam como não iniciadas: confirmação final do domínio de negócio via entrevista, escolha de tecnologia, e toda a fase de Desenvolvimento propriamente dita).

**Status desta fase:** APROVADA E CONGELADA pelo proprietário em 2026-08-02 (comando `APROVADO`). Este documento passa a integrar a documentação oficial do THE CHARCOAL OS como o 16º Documento Oficial Congelado; nenhuma alteração futura sem criação de nova versão formal. Nenhuma fase de Desenvolvimento, Código, Banco físico, APIs reais, Infraestrutura ou Deploy foi iniciada. A Fase 013 (AI Architecture) aguarda o Prompt Oficial do proprietário.

---

*Fim do documento — THE CHARCOAL OS SECURITY AND PRIVACY ARCHITECTURE v1.0.0 (Oficial)*
