# THE CHARCOAL OS — VISUAL IDENTITY & DESIGN REFINEMENT

**Documento:** TCOS-019A
**Fase:** 019A — Visual Identity & Design Refinement (Fase 1 APROVADA — Fase 2 em construção)
**Natureza:** Documento exclusivamente conceitual de identidade e linguagem visual. NÃO constitui implementação, NÃO constitui código, NÃO constitui CSS, NÃO define tecnologia, framework ou biblioteca. NÃO altera arquitetura, regra de negócio, funcionalidade, fluxo, UX oficial, nomenclatura, módulo, Dashboard, componente existente ou qualquer documento oficial congelado.
**Baseline referenciada:** v1.0.0 (TCOS-000 a TCOS-018), sob a autoridade da Constituição Permanente do Projeto.
**Documentos-fonte desta fase:** Constituição Permanente; `THE_CHARCOAL_OS_UX_UI_SPECIFICATION.md` (TCOS-005); `THE_CHARCOAL_OS_FRONTEND_ARCHITECTURE.md` (TCOS-011); `THE_CHARCOAL_OS_VISUAL_BLUEPRINT.md` (TCOS-018).
**Status:** Em construção — Fase 1 (Identidade Visual Oficial) APROVADA — Fase 2 (Biblioteca Visual Oficial de Componentes) concluída — aguardando decisão do proprietário.

---

## EXECUTIVE MEMORY

Esta fase eleva a qualidade visual do THE CHARCOAL OS, definindo pela primeira vez os valores concretos (paleta, tipografia, espaçamento, elevação) para os tokens conceituais que o TCOS-018 deixou deliberadamente `[Pendente de confirmação visual]` — sem alterar nenhuma categoria semântica, nome, comportamento ou regra já oficial. Onde o TCOS-005 já nomeou uma categoria (ex.: "Brasa", "Roxo-IA"), esta fase apenas **instancia** essa categoria com um valor concreto; nunca renomeia, remove ou reatribui seu papel semântico.

**Auditoria Visual pré-fase (executada antes de qualquer definição):**
- Constituição Permanente: relida integralmente — nenhuma cláusula de governança impede a definição de identidade visual nesta fase; a Política de Change Request (Capítulo 15) permanece a única via de alteração de documento já congelado, não invocada aqui, pois nenhum documento congelado é alterado.
- UX/UI Specification (TCOS-005), Capítulo 5 (Design System): relido integralmente — confirma que nenhum valor hexadecimal, pixel além do grid de 8px, ou fonte tipográfica foi definido até este momento; as 7 categorias de cor (Brasa, Carvão, Cinza-claro, Verde-sucesso, Âmbar-atenção, Vermelho-crítico, Roxo-IA), os 5 estados de botão, os 4 estados de card e os 4 estados de indicador permanecem exatamente como já nomeados — esta fase não os redefine, apenas os instancia.
- Frontend Architecture (TCOS-011), Capítulo 11: relido — confirma o Design System como "congelado e não redefinido" na arquitetura de frontend, com uma única formalização adicional (Roxo-IA como atributo de estado obrigatório de conteúdo de IA) — mantida integralmente nesta fase.
- Visual Blueprint (TCOS-018): relido — nenhuma divergência entre o Blueprint e o mockup de alta fidelidade já aprovado (Dashboard CEO) foi encontrada; as 2 correções aplicadas ao mockup antes de sua apresentação (tabela restrita a Data/Cliente/Status; barra lateral com as 10 Áreas completas) já garantem essa aderência.
- **Nenhuma inconsistência documental, nenhuma divergência entre Blueprint e Mockup, nenhuma funcionalidade criada, nenhuma tela diferente do Blueprint foi encontrada.** A construção da Fase 1 está autorizada a prosseguir.

---

## 1. Papel deste Documento

O TCOS-019A é o documento que responde à pergunta: **qual é, concretamente, a aparência do THE CHARCOAL OS?** O TCOS-005 (UX/UI Specification) já havia nomeado as categorias semânticas de cor, os estados de componente e o grid-base; o TCOS-018 (Visual Blueprint) já havia mostrado exatamente onde cada uma dessas categorias aparece, tela por tela. Faltava o elo final: os valores concretos — a identidade visual completa e coesa que faz o sistema parecer **um único produto**, com personalidade própria, e não uma composição genérica de componentes.

## 2. Legenda e Convenções

- Toda categoria semântica de cor, estado ou componente usa exatamente o nome já oficial (TCOS-005, Seção 5.6–5.10) — este documento nunca renomeia, apenas instancia com valor concreto.
- **Token de identidade:** um valor concreto (cor, medida, curva de animação) atribuído a um conceito já nomeado — nunca um conceito novo.
- Todo valor definido aqui é **conceitual e visual**, nunca técnico: cores são descritas por papel e valor de referência (não por variável de CSS/SCSS); tipografia é descrita por característica (não por nome de arquivo de fonte ou licença); animação é descrita por sensação e curva (não por biblioteca ou implementação).

## 3. Personalidade Visual e Sensação Transmitida

O THE CHARCOAL OS deve parecer o oposto de dois extremos comuns em software de gestão: nunca a frieza burocrática de uma planilha, e nunca a leveza descompromissada de um aplicativo de consumo. A personalidade é a de um **instrumento de precisão operado por quem entende do ofício** — o mesmo cuidado de quem controla o ponto exato da brasa se reflete na forma como o sistema apresenta um número, um alerta ou uma decisão pendente.

As 10 sensações exigidas pelo proprietário se traduzem em decisões visuais concretas, não apenas em adjetivos:

| Sensação exigida | Tradução visual |
|---|---|
| Confiança | Cor usada com intenção, nunca decorativa; todo número crítico (KPI, alerta) recebe o mesmo tratamento tipográfico em qualquer tela — nunca varia sem motivo. |
| Robustez | Componentes com peso visual estável (bordas e sombras discretas, nunca frágeis ou "flutuantes" demais); nenhuma tela parece incompleta mesmo em Estado Vazio. |
| Organização | Grid rígido de 8px (já oficial, TCOS-005 §5.3) aplicado sem exceção; alinhamento vertical e horizontal previsível em toda tela. |
| Inteligência | Números sempre tabulares e alinhados; toda sugestão de IA visualmente distinta (Roxo-IA) e nunca misturada ao dado "de fato". |
| Simplicidade | Um único acento de cor por tela para ação primária; nunca mais de uma cor "gritando" ao mesmo tempo. |
| Alta tecnologia | Uso deliberado de profundidade sutil (elevação, Capítulo 9) para sinalizar camadas de informação, não decoração. |
| Sofisticação | Paleta neutra refinada (nunca cinza puro, nunca branco puro no canvas) — ver Capítulo 5. |
| Estabilidade | Nenhum componente muda de posição ou tamanho ao mudar de estado (loading/vazio/erro) — apenas seu conteúdo interno muda. |
| Velocidade | Microinterações curtas (Capítulo 22) — o sistema nunca faz o usuário esperar visualmente por uma confirmação que já aconteceu. |
| Precisão | Alinhamento numérico exato (tabular-nums), hierarquia sem ambiguidade entre o que é dado real e o que é meta/previsão. |

## 4. Linguagem de Design e Princípios de Interface

Cinco princípios, cada um derivado diretamente de um Princípio Fundamental já oficial (Framework, TCOS-000) ou de uma regra já estabelecida no TCOS-005/011:

1. **Um acento, uma vez por tela.** A cor Brasa é reservada para exatamente uma ação primária e para o item de navegação ativo — nunca usada como decoração repetida (evita a "poluição de cor" comum em dashboards genéricos).
2. **Hierarquia por peso, não por quantidade de cor.** Diferenciação de importância vem de peso tipográfico e tamanho (já oficial, TCOS-005 §5.4), não de aplicar cores diferentes a textos igualmente importantes.
3. **A cor sempre significa algo.** Nenhuma cor é usada apenas por estética — toda cor fora da paleta neutra corresponde a uma categoria semântica já oficial (status, criticidade, IA).
4. **Densidade com respiro.** O sistema mostra muito dado (Dashboards com 6 KPIs, tabelas extensas) sem parecer congestionado — resolvido por espaçamento consistente (Capítulo 7), nunca por reduzir a quantidade de informação real.
5. **Nada se move sem motivo.** Toda animação (Capítulo 21) comunica uma mudança de estado real — nunca decorativa (reforça PF-06, "IA nunca decide sozinha", e PF-04, "histórico obrigatório": o usuário sempre percebe visualmente que algo mudou e por quê).

## 5. Paleta Oficial

Instancia, pela primeira vez, valores concretos para as 7 categorias já nomeadas no TCOS-005 (§5.7) — nenhum nome, papel ou categoria é alterado.

| Categoria (já oficial) | Papel (já oficial) | Valor de referência definido nesta fase |
|---|---|---|
| Brasa | Ação primária, estado ativo/confirmado, destaque | `#E2542B` — laranja-avermelhado quente, a única cor "alta energia" do sistema |
| Carvão | Texto principal, alta ênfase, fundo do menu lateral | `#1B1917` — quase-preto de matiz quente (nunca neutro-frio) |
| Cinza-claro | Fundos neutros, estados inativos/desabilitados | Escala de 4 tons quentes, de `#F8F7F5` (fundo de tela) a `#DEDAD3` (bordas fortes) — nunca cinza-azulado |
| Verde-sucesso | Confirmações, Metas atingidas, "Disponível"/"Concluído" | `#1E9E6C` |
| Âmbar-atenção | Alertas não críticos, "Metas não atingidas", "Em manutenção" | `#C77C1F` |
| Vermelho-crítico | Alertas de alta prioridade, bloqueios, "Vencido"/"Cancelado" | `#D6472F` |
| Roxo-IA | Exclusivo para conteúdo gerado/sugerido por IA | `#7C5CFF` — deliberadamente a **única cor fria** de toda a paleta |

**Justificativa de identidade:** a decisão de fundamentar a paleta inteira em tons quentes (laranja-carvão, nunca azul) é a principal fonte de reconhecimento visual imediato do sistema — a esmagadora maioria dos produtos de gestão corporativa (incluindo várias das referências de qualidade citadas) usa azul ou roxo como cor dominante. Manter o Roxo-IA como a única exceção fria da paleta não é acidental: transforma a própria "quebra da regra de cor" em sinal — qualquer conteúdo em tom frio é, por definição, gerado por IA, nunca dado humano direto. Nenhum valor de cor aqui definido altera o papel semântico já oficial de nenhuma categoria — apenas atribui, pela primeira vez, um valor de referência a cada uma.

## 6. Tipografia e Pesos Tipográficos

Sem nomear uma família tipográfica comercial específica (decisão de licenciamento/tooling, fora do escopo conceitual desta fase) — define-se o **arquétipo tipográfico** que qualquer fonte escolhida futuramente deve seguir, reafirmando sem alteração a regra já oficial (TCOS-005 §5.4: fonte sans-serif única, peso variável).

- **Arquétipo:** grotesca contemporânea, de baixo contraste entre traços finos e grossos, terminais discretamente quadrados (não geométrica-circular, não humanista-caligráfica) — transmite precisão sem frieza excessiva.
- **Escala de peso:** Regular (400) para corpo de texto; Semibold (600) para títulos de card, cabeçalhos de seção e valores de KPI; Bold (700) reservado exclusivamente para alertas críticos (já oficial, TCOS-005 §5.4) — nunca usado por ênfase estética.
- **Números:** sempre com alinhamento tabular (todo dígito ocupa a mesma largura) — obrigatório em toda tabela, KPI e gráfico, para que colunas de números sempre alinhem verticalmente, reforçando a sensação de precisão (Capítulo 3).
- **Escala de tamanho:** proporção modesta entre níveis (na ordem de 1,25×), nunca saltos grandes — reforça "organização" e "estabilidade" (Capítulo 3) em vez de hierarquia agressiva.

## 7. Espaçamento e Grid

Reafirma, sem alteração, o grid de 8px já oficial (TCOS-005 §5.3) como a única unidade de espaçamento do sistema. Esta fase define a **aplicação consistente** dessa unidade:

- Espaçamento interno de componente (padding): múltiplos de 8, nunca valores intermediários.
- Espaçamento entre componentes irmãos (gap): múltiplos de 16 em telas densas (Dashboards, Listas), múltiplos de 24 em telas de leitura (Detalhe).
- Margem externa de seção: múltiplos de 32.
- Nenhum elemento visual jamais rompe o grid — inclusive elementos decorativos (ícones, avatares, badges) são dimensionados em múltiplos de 8 sempre que possível.

## 8. Raios de Borda

Conceito novo desta fase — não definido em nenhum documento anterior. Uma única escala de 3 valores, aplicada por categoria de componente, nunca por preferência pontual:

- **Raio pequeno** (elementos de ação: botões, badges, chips, campos de entrada) — cantos discretamente arredondados, transmitindo precisão sem rigidez.
- **Raio médio** (contêineres: cards, painéis, modais) — arredondamento mais perceptível, para diferenciar visualmente "container de conteúdo" de "elemento de ação".
- **Raio circular** (exclusivo para avatares, indicadores de estado pontuais e o ícone de IA) — a única forma totalmente circular do sistema, reforçando que representa uma "pessoa" ou uma "IA", nunca um dado ou uma ação.

## 9. Sombras e Profundidade

Conceito novo desta fase. A profundidade comunica **camada de informação**, nunca decoração:

- **Nível 0 (plano):** o próprio canvas da tela e a barra lateral — sem sombra, são a "base" de tudo.
- **Nível 1 (conteúdo):** cards, painéis, linhas de tabela em hover — sombra muito sutil, quase imperceptível, apenas suficiente para separar do fundo.
- **Nível 2 (sobreposição temporária):** Drawers, menus suspensos, tooltips — sombra mais perceptível, sinalizando que o elemento está temporariamente "acima" do fluxo normal da tela.
- **Nível 3 (interrupção):** Modais e confirmações de Operação Crítica (TCOS-018, item 25.19) — a sombra mais forte do sistema, reservada exclusivamente para o momento em que o sistema exige atenção total do usuário antes de prosseguir.

Esta escala de 4 níveis nunca se sobrepõe: um elemento de Nível 2 nunca aparece simultaneamente com um de Nível 3 sem que o de Nível 2 seja visualmente "esmaecido" ao fundo (reforça PF-06 e o padrão de confirmação explícita já oficial).

## 10. Hierarquia Visual

Reafirma e refina a hierarquia já oficial (TCOS-005 §5.2; TCOS-019A Capítulo 4, princípio 2): título de página → título de seção/card → corpo → legenda/metadado, cada nível distinguido por peso e tamanho tipográfico (Capítulo 6), nunca por cor. Números de KPI permanecem, como já oficial, o elemento de maior destaque tipográfico de qualquer tela — nesta fase, esse destaque é formalizado como o único caso em que um valor numérico pode usar tamanho de texto maior que um título de seção.

## 11. Padrões de Contraste

Conceito novo desta fase, respondendo à melhoria M-011-02 já registrada (Frontend Architecture, TCOS-011): todo par texto/fundo do sistema deve atingir, no mínimo, contraste equivalente ao padrão AA de acessibilidade — aplicável a texto sobre card, texto sobre barra lateral (Carvão) e texto sobre qualquer badge/pill de status. Esta fase registra o **requisito de contraste como princípio de identidade** (não apenas como regra técnica de acessibilidade) — um sistema "sofisticado e preciso" nunca sacrifica legibilidade por estética. A validação técnica exata do contraste permanece, como já registrado, pendente da escolha de tecnologia (M-011-02).

## 12. Linguagem de Ícones

Reafirma o estilo já oficial (TCOS-005 §5.5: linha/outline, ícone de IA fixo). Esta fase acrescenta: traço de espessura única e consistente em todos os ícones do sistema (nunca ícones preenchidos misturados a ícones de linha); cantos com o mesmo raio pequeno já definido para botões (Capítulo 8), para que o ícone "combine" visualmente com os controles ao seu redor; o ícone de IA (já oficial, "uma pequena faísca") é o único ícone do sistema autorizado a usar a cor Roxo-IA — todos os demais ícones usam Carvão ou Cinza conforme o contexto, nunca cor semântica decorativa.

## 13. Linguagem dos Gráficos

Novo nesta fase, aplicável aos tipos de gráfico já usados no TCOS-018 (linha, barras, funil, calendário/timeline, feed cronológico, histograma): toda linha de gráfico usa a cor Brasa como traço principal, com preenchimento em gradiente sutil da mesma cor (opacidade decrescente) — nunca uma segunda cor de traço, exceto quando o gráfico compara duas séries semanticamente diferentes (ex.: planejado × real), caso em que a série "real" usa Brasa sólida e a série "planejado" usa Cinza-claro. Grades de fundo (linhas de referência) são sempre discretas, nunca competindo visualmente com o dado. Nenhum gráfico usa mais de 2 cores simultâneas, exceto o funil (Capítulo 20, Dashboard CRM) e o calendário, que usam a paleta semântica completa por serem, por natureza, uma composição de vários estados.

## 14. Linguagem dos Cards

Todo Card (KPI, progresso, contêiner de gráfico/tabela) segue a mesma anatomia visual: fundo neutro claro, borda de 1px na cor de borda mais sutil da escala (Capítulo 5), Nível 1 de sombra (Capítulo 9), raio médio (Capítulo 8). O rótulo do Card é sempre o elemento de menor ênfase visual dentro dele; o valor/conteúdo principal é sempre o de maior ênfase — nunca o inverso, reafirmando a hierarquia de KPI já oficial (TCOS-005 §5.4).

## 15. Linguagem das Tabelas

Cabeçalho de tabela sempre em texto pequeno, peso Semibold, cor secundária (nunca Carvão puro) e caixa alta discreta — para se diferenciar claramente do conteúdo das linhas. Linhas separadas por uma borda mais sutil que a borda de card (Capítulo 5), nunca por zebra-striping (alternância de cor de fundo), para manter a densidade visual "organizada" (Capítulo 3) sem ruído. Toda coluna numérica é alinhada à direita com números tabulares (Capítulo 6); toda coluna de texto é alinhada à esquerda.

## 16. Linguagem dos Botões

Reafirma os 3 tipos já oficiais (primário/secundário/terciário, TCOS-005 §5.6) com identidade concreta: o botão primário é a única aplicação de fundo sólido Brasa em toda a interface fora de badges de estado; o botão secundário usa apenas borda e texto Carvão, fundo neutro; o botão terciário é texto puro, sem borda nem fundo, reservado a ações de baixíssima prioridade (ex.: "Baixar PDF"). Os 5 estados já oficiais (normal, hover, focus, disabled, loading, TCOS-005 §5.8) recebem tratamento visual consistente em todos os tipos — hover sempre um leve escurecimento da própria cor do botão, nunca uma cor diferente.

## 17. Linguagem dos Filtros

O componente "Filtro combinável" (já oficial) usa sempre a mesma forma visual do campo de entrada (raio pequeno, Capítulo 8) com um ícone de seta discreto indicando que é expansível. Filtros ativos (com valor selecionado, diferente do padrão) recebem uma marcação visual sutil (borda em Brasa, nunca preenchimento) para que o usuário perceba, à distância, que a tela está sendo exibida com um recorte — nunca uma cor forte que compita com o dado principal da tela.

## 18. Linguagem dos Badges

O Badge de status (já oficial, uma cor por estado do ciclo de vida) usa sempre a mesma forma: pílula de raio circular, fundo em tom claro da cor semântica (nunca a cor sólida), texto na variante escura da mesma cor — nunca texto branco sobre cor sólida, para manter a leveza visual mesmo em telas com muitos badges simultâneos (ex.: tabela de Eventos com um badge por linha).

## 19. Linguagem dos Alertas

Reafirma os 3 componentes já oficiais (Alerta inline, Banner de alerta persistente, Notificação toast) com identidade visual distinta por nível de urgência: Alerta inline usa apenas texto colorido, sem fundo, por estar sempre próximo ao campo que o originou; Banner persistente usa fundo em tom claro da cor de criticidade com ícone de destaque, ocupando a largura total do contexto em que aparece; Toast usa fundo Carvão (não a cor semântica) com um pequeno indicador colorido lateral — para que notificações efêmeras nunca sejam confundidas visualmente com alertas persistentes que exigem ação.

## 20. Estados da Interface

Reafirma, com identidade visual concreta, os estados já formalizados (Frontend Architecture, TCOS-011, Capítulos 18–20): o Estado de Carregamento (Skeleton) usa sempre a mesma silhueta cinza-claro com uma animação sutil de "respiração" (Capítulo 21); o Estado Vazio usa uma ilustração de linha simples (nunca fotografia ou ilustração colorida, para permanecer consistente com a linguagem de ícones, Capítulo 12) mais texto explicativo; o Estado de Erro usa sempre o ícone de atenção já definido, nunca uma tela vermelha inteira — a cor crítica é reservada ao ícone e ao texto do motivo, nunca ao fundo completo da tela.

## 21. Animações Conceituais

Conceito novo desta fase — nenhuma tecnologia ou biblioteca definida, apenas sensação e curva:

- **Transições de tela:** dissolução suave e rápida (nunca deslizamento lateral longo), reforçando "velocidade" (Capítulo 3) sem desorientar o usuário.
- **Atualização automática de dado** (Dashboards, Frontend Architecture Capítulo 16): o valor numérico se atualiza com uma transição curta de contagem (nunca troca instantânea e brusca), sinalizando visualmente que algo mudou sem exigir que o usuário releia a tela inteira.
- **Skeleton de carregamento:** pulsação suave e lenta — nunca um piscar rápido, que transmitiria instabilidade, o oposto da identidade pretendida.
- **Abertura de Modal/Drawer:** entrada com leve elevação (sobe e ganha nitidez), reforçando a metáfora de profundidade já definida (Capítulo 9).

Toda animação é breve por princípio (Capítulo 4, item 5: "nada se move sem motivo") — a duração nunca compete com a velocidade percebida do sistema.

## 22. Microinterações Conceituais

- **Botão ao ser pressionado:** leve compressão visual, confirmando o toque/clique antes mesmo da resposta do backend chegar — nunca deixa o usuário em dúvida se a ação foi registrada.
- **Checkbox/seleção em tabela:** marcação com uma pequena confirmação visual instantânea (nunca uma troca abrupta sem transição).
- **Arraste em Kanban (Leads, Compras):** o card arrastado ganha elevação (Capítulo 9, Nível 2) durante o arraste, e "assenta" com uma pequena resposta visual ao soltar — comunicando fisicamente que a mudança de estágio foi aceita.
- **Aceitar/Recusar sugestão de IA:** a resposta do usuário (Componente de sugestão de IA) é seguida de uma transição de saída suave do card de sugestão — nunca um desaparecimento abrupto, para que o usuário perceba com clareza que sua decisão foi registrada (reforça PF-06 e a Auditoria Visual de Ações, TCOS-011 Capítulo 23).

---

**Fim da Fase 1 — Identidade Visual Oficial.**

## 23. Metodologia da Fase 2 — Biblioteca Visual Oficial de Componentes

Esta fase transforma a Identidade Visual Oficial (Fase 1) em uma biblioteca completa de componentes reutilizáveis, documentando cada um com 7 campos fixos: **Finalidade**, **Comportamento visual**, **Variações oficiais**, **Estados**, **Regras de utilização**, **Exemplo visual** (esboço textual — nenhuma imagem é gerada nesta fase, por determinação expressa do proprietário: "não atualizar nenhuma das 30 telas") e **Aderência ao TCOS-018**. Todo componente aqui documentado já existe, nomeado, no TCOS-018 (Capítulo 25) e/ou no TCOS-005 (§5.6); onde a lista de 26 itens desta fase inclui algo sem base oficial própria, isso é declarado explicitamente, nunca inventado. Os valores concretos (cor, raio, sombra, tipografia) aplicados a cada componente são os já definidos na Fase 1 — nenhum valor novo é criado aqui.

## 24. Sidebar

**Finalidade:** navegação estrutural principal do sistema, sempre visível em Desktop/Tablet (TCOS-018, Capítulo 9).
**Comportamento visual:** fundo Carvão sólido (Fase 1, Capítulo 5); 10 seções colapsáveis por Área da Empresa + rodapé fixo (Configurações/Administração); apenas a Área da tela atual expandida por padrão.
**Variações oficiais:** expandida (Desktop) e colapsada em ícones (Tablet) — TCOS-018, Capítulo 9.
**Estados:** item de navegação normal, item ativo (barra lateral esquerda em Brasa + fundo em leve wash de Brasa, já validado no mockup do Dashboard CEO), seção expandida/colapsada.
**Regras de utilização:** nunca é o único caminho para uma tela (Capítulo 5, TCOS-018); item ativo sempre visualmente único — nunca dois itens marcados como ativos simultaneamente.
**Exemplo visual:** faixa vertical escura de 248px, logotipo no topo, lista de seções com um item em destaque (fundo laranja-wash, barra lateral sólida) e as demais em texto neutro esmaecido.
**Aderência ao TCOS-018:** Capítulos 5 e 9; validado no mockup aprovado do Dashboard CEO (10 Áreas completas).

## 25. Header (Barra Superior)

**Finalidade:** acesso rápido e sempre visível, independentemente da Área navegada (TCOS-018, Capítulo 8).
**Comportamento visual:** fundo neutro claro (Nível 0, Fase 1 Capítulo 9), fixo no topo, altura constante em todas as telas.
**Variações oficiais:** completo (Desktop/Tablet) e simplificado — sem busca expandida, apenas ícone (Mobile, TCOS-018 Capítulo 8).
**Estados:** normal; com indicador de sugestão de IA pendente (ponto Roxo-IA); com notificação não lida (ponto Vermelho-crítico).
**Regras de utilização:** nunca compete visualmente com o conteúdo da tela — nenhum elemento do Header usa a cor Brasa, reservada à ação primária da página.
**Exemplo visual:** faixa branca fixa, busca à esquerda, ícones de IA/notificação/perfil à direita, sem borda inferior pesada (apenas linha de 1px na cor de borda sutil).
**Aderência ao TCOS-018:** Capítulo 8; validado no mockup aprovado do Dashboard CEO.

## 26. Breadcrumb

**Finalidade:** indicar o caminho de navegação em toda tela de Detalhe (TCOS-018, Capítulo 8; UX/UI Spec §4).
**Comportamento visual:** texto pequeno, cor secundária, separadores discretos (">"), cada nível clicável.
**Variações oficiais:** nenhuma — presente apenas em telas de Detalhe, ausente em Dashboards e Listas (Capítulo 11, TCOS-018).
**Estados:** normal; nível atual (último item) em Carvão de alta ênfase; níveis anteriores em cor secundária, clicáveis.
**Regras de utilização:** preserva sempre o estado de filtro/paginação da tela de origem ao ser clicado (Frontend Architecture, Capítulo 7).
**Exemplo visual:** "Eventos › Evento #123 › Orçamento", cada segmento separado por um ">" cinza discreto.
**Aderência ao TCOS-018:** Capítulos 5 e 8.

## 27. Barra de Busca

**Finalidade:** pesquisa global simultânea em Cliente, Evento, Orçamento e Contrato (UX/UI Spec, Capítulo 4).
**Comportamento visual:** campo com ícone de lupa, fundo neutro claro, raio pequeno (Fase 1, Capítulo 8), largura fixa no Header.
**Variações oficiais:** busca global (Header) e busca local (dentro de cada Lista, específica dos itens daquela tela) — UX/UI Spec, Capítulo 4.
**Estados:** normal (placeholder "Buscar..."); focus (borda em Brasa); com resultado ativo.
**Regras de utilização:** busca global nunca substitui os filtros locais de cada Lista — são mecanismos complementares, nunca redundantes.
**Exemplo visual:** campo retangular discreto no Header, ícone de lupa à esquerda, texto placeholder em cinza-claro.
**Aderência ao TCOS-018:** Capítulo 8; validado no mockup aprovado.

## 28. Perfil do Usuário

**Finalidade:** identificação do usuário autenticado e acesso a Configurações/Sair (TCOS-018, Capítulo 8).
**Comportamento visual:** avatar circular (Fase 1, Capítulo 8 — raio circular exclusivo de "pessoa"/IA) com iniciais, nome e Perfil/Área ao lado.
**Variações oficiais:** usuário com um Perfil (exibição direta) e usuário com mais de um Perfil vinculado (seletor de Perfil, TCOS-018 Capítulo 8).
**Estados:** normal; menu aberto (Drawer/dropdown, Capítulo 42).
**Regras de utilização:** avatar usa sempre a cor de fundo Brasa-wash com texto Brasa — nunca uma cor semântica de status, para não ser confundido com um Badge.
**Exemplo visual:** círculo pequeno com iniciais "MF" em laranja-claro, nome e cargo à esquerda dele.
**Aderência ao TCOS-018:** Capítulo 8; validado no mockup aprovado.

## 29. Área de Notificações

**Finalidade:** histórico de notificações e alertas críticos, acessível pelo sino do Header (UX/UI Spec, Capítulo 4).
**Comportamento visual:** ícone de sino com contagem de não lidas; ao clicar, abre um Drawer lateral (Capítulo 42).
**Variações oficiais:** painel de notificações (Drawer) e Banner de alerta persistente (quando crítico, exibido também na tela relevante, TCOS-018 Capítulo 25.14).
**Estados:** sem notificação (sino neutro); com notificação não lida (ponto Vermelho-crítico sobre o sino).
**Regras de utilização:** alerta crítico nunca aparece somente na Área de Notificações — sempre replicado como Banner persistente na tela relevante até ser tratado (já oficial, TCOS-018 Capítulo 8).
**Exemplo visual:** ícone de sino no Header com um pequeno ponto vermelho no canto superior direito.
**Aderência ao TCOS-018:** Capítulos 8 e 25.14; validado no mockup aprovado.

## 30. Cards KPI

**Finalidade:** exibir um valor numérico de alto destaque no topo de todo Dashboard (TCOS-018, Capítulo 12).
**Comportamento visual:** fundo branco, borda sutil, raio médio, sombra Nível 1 (Fase 1, Capítulos 8–9); número em tipografia Semibold/tabular (Fase 1, Capítulo 6), maior que qualquer outro texto do card.
**Variações oficiais:** com indicador de variação (seta + percentual, já validado no mockup) e sem indicador (quando não há comparação aplicável, ex.: "Módulo 27").
**Estados:** normal; carregando (Skeleton, Capítulo 48); erro (Capítulo 25.17, TCOS-018).
**Regras de utilização:** rótulo sempre em menor ênfase que o valor — nunca o inverso (Fase 1, Capítulo 14).
**Exemplo visual:** já demonstrado nos 6 Cards de KPI do mockup aprovado do Dashboard CEO.
**Aderência ao TCOS-018:** Capítulos 13–23 (todos os Dashboards); Capítulo 25.20.

## 31. Cards de Conteúdo

**Finalidade:** conter gráficos, tabelas ou widgets dentro de uma tela (contêiner genérico, Fase 1 Capítulo 14).
**Comportamento visual:** mesma anatomia dos Cards KPI (fundo, borda, raio, sombra), com cabeçalho de título + rótulo secundário (ex.: "Últimos 6 meses").
**Variações oficiais:** Card de progresso (Metas, TCOS-018 Capítulo 25.2) e Card genérico de painel (usado em gráficos/tabelas).
**Estados:** normal; carregando; vazio (Capítulo 46); erro.
**Regras de utilização:** nunca aninha outro Card de Conteúdo dentro de si — apenas Cards KPI podem aparecer lado a lado sem contêiner externo.
**Exemplo visual:** os painéis "Fluxo de Caixa" e "Margem por Evento" do mockup aprovado.
**Aderência ao TCOS-018:** Capítulo 25.2, 25.20.

## 32. Botões (todas as variações oficiais)

**Finalidade:** disparar ação de comando (TCOS-018, Capítulo 25.3).
**Comportamento visual:** conforme Fase 1, Capítulo 16 — primário (fundo Brasa sólido), secundário (borda Carvão), terciário (texto puro).
**Variações oficiais:** primário, secundário, terciário (§5.6, TCOS-005) — nenhuma quarta variação existe.
**Estados:** normal, hover, focus, disabled, loading (5 estados já oficiais, §5.8, TCOS-005).
**Regras de utilização:** apenas um botão primário visível por tela/seção (Fase 1, Capítulo 4, princípio 1); botão de Operação Crítica (TCOS-018, item 25.19) é sempre primário, nunca terciário.
**Exemplo visual:** já demonstrado no mockup aprovado — "Novo Evento" (primário), "Ver Financeiro" (secundário), "Ver Metas" (terciário/ghost).
**Aderência ao TCOS-018:** Capítulo 25.3; Fase 1 Capítulo 16.

## 33. Campos de Entrada

**Finalidade:** captura de dado textual/numérico em formulários e Modais (TCOS-018, Capítulo 25.4).
**Comportamento visual:** raio pequeno (Fase 1, Capítulo 8), borda sutil, rótulo acima do campo.
**Variações oficiais:** texto, numérico — nenhuma outra variação nomeada oficialmente (ver TCOS-018, Capítulo 25.4).
**Estados:** normal, focus (borda Brasa), disabled, erro (borda Vermelho-crítico + mensagem inline) — `[Inferência visual]` herdada do TCOS-018, que já extrapolou este modelo do padrão de Botões (§5.8).
**Regras de utilização:** validação de formato em tempo de digitação; validação de regra de negócio apenas na submissão (Frontend Architecture, Capítulo 21) — nunca simulada antecipadamente.
**Exemplo visual:** campo retangular de borda fina, rótulo pequeno acima ("Nome do Cliente"), texto de conteúdo em Carvão.
**Aderência ao TCOS-018:** Capítulo 25.4.

## 34. Selects

**Finalidade:** seleção de uma opção entre um conjunto fechado (ex.: tipo de Conta em Bancos, categoria de parâmetro em Configurações).
**Comportamento visual:** mesma anatomia visual de um Campo de Entrada (Capítulo 33), com um ícone de seta indicando expansibilidade.
**Variações oficiais:** **nenhuma** — o TCOS-018 (Capítulo 25.4) já registrou explicitamente que "Select" não é um componente nomeado em nenhum documento oficial; existe apenas implicitamente onde uma tela já lista opções fechadas.
**Estados:** normal, focus, disabled, aberto (lista de opções visível).
**Regras de utilização:** nunca usado para uma escolha com mais de ~8 opções sem busca interna — decisão de uso, não uma regra oficial (`[Inferência visual]`).
**Exemplo visual:** mesmo campo retangular dos Campos de Entrada, com uma seta "▾" à direita.
**Aderência ao TCOS-018:** Capítulo 25.4 (extensão explícita de uma lacuna já registrada, não um componente novo).

## 35. Filtros

**Finalidade:** refinar o conteúdo de uma Lista/Dashboard (TCOS-018, Capítulo 25.6).
**Comportamento visual:** conforme Fase 1, Capítulo 17 — mesma forma de Campo de Entrada, com marcação de "filtro ativo" em borda Brasa.
**Variações oficiais:** filtro lateral/superior combinável (Desktop) e painel deslizante (Drawer, Tablet/Mobile) — TCOS-018 Capítulo 25.6.
**Estados:** padrão (sem valor selecionado); ativo (valor diferente do padrão, borda Brasa).
**Regras de utilização:** todo filtro é combinável com outros da mesma tela (UX/UI Spec, Capítulo 4) — nunca um de cada vez.
**Exemplo visual:** o seletor de período "Agosto 2026" do mockup aprovado — campo com ícone de calendário e valor selecionado.
**Aderência ao TCOS-018:** Capítulos 25.6; validado no mockup aprovado.

## 36. Tabelas

**Finalidade:** exibir coleções de itens com paginação e ordenação (TCOS-018, Capítulo 25.5).
**Comportamento visual:** conforme Fase 1, Capítulo 15 — cabeçalho pequeno/Semibold, linhas separadas por borda sutil, sem zebra-striping, colunas numéricas alinhadas à direita com tabular-nums.
**Variações oficiais:** tabela completa (Desktop/Tablet) e lista de cartões (Mobile, TCOS-018 Capítulo 10).
**Estados:** normal, carregando (linhas em Skeleton), vazio (Capítulo 46), erro.
**Regras de utilização:** paginação e ordenação persistem durante a navegação no mesmo módulo (UX/UI Spec, Capítulo 4).
**Exemplo visual:** a tabela "Próximos Eventos confirmados" do mockup aprovado — 3 colunas (Data, Cliente, Status), sem linhas zebradas.
**Aderência ao TCOS-018:** Capítulo 25.5; validado no mockup aprovado.

## 37. Paginação

**Finalidade:** navegar entre páginas de uma Tabela extensa — parte constituinte do componente "Tabela com paginação e ordenação" (§5.6, TCOS-005), nunca um componente isolado.
**Comportamento visual:** controles numéricos discretos no rodapé da Tabela, página atual em destaque (Brasa).
**Variações oficiais:** nenhuma separada da Tabela — não há paginação fora do contexto de uma Tabela em nenhuma das 30 telas.
**Estados:** página normal; página atual (destaque); botão "anterior/próxima" desabilitado nas extremidades.
**Regras de utilização:** estado de página é preservado ao navegar para Detalhe e retornar via breadcrumb (Capítulo 26).
**Exemplo visual:** numeração discreta "1 2 3 ... 8" alinhada à direita do rodapé da Tabela, algarismo atual em Brasa.
**Aderência ao TCOS-018:** Capítulo 25.5 (parte constituinte do componente Tabela, não um item separado do catálogo de 18/24).

## 38. Badges

**Finalidade:** indicar o estado do ciclo de vida de uma entidade (TCOS-018, Capítulo 25.13).
**Comportamento visual:** conforme Fase 1, Capítulo 18 — pílula de raio circular, fundo em tom claro da cor semântica, texto na variante escura.
**Variações oficiais:** uma cor por estado do ciclo de vida — nunca mais de uma cor por Badge (§5.6, TCOS-005).
**Estados:** cada estado do ciclo de vida da entidade correspondente (ex.: Confirmado/verde, Aguardando pagamento/âmbar, Cancelado/vermelho).
**Regras de utilização:** cor sempre corresponde à categoria semântica já oficial (Verde-sucesso/Âmbar-atenção/Vermelho-crítico/Cinza-claro) — nunca uma cor arbitrária por tela.
**Exemplo visual:** "Confirmado" (verde) e "Aguardando pagamento" (âmbar) na tabela de Eventos do mockup aprovado.
**Aderência ao TCOS-018:** Capítulo 25.13; validado no mockup aprovado.

## 39. Tags

**Finalidade:** não há finalidade própria — **nenhum componente de "Tag" existe separadamente do Badge de status** em qualquer documento oficial (TCOS-018, Capítulo 25.13, já registrou esta ausência explicitamente).
**Comportamento visual:** idêntico ao Badge (Capítulo 38).
**Variações oficiais:** nenhuma — este item da lista da Fase 2 é tratado como sinônimo funcional do Badge, não como um segundo componente.
**Estados:** os mesmos do Badge.
**Regras de utilização:** onde uma tela futura precisar de um rótulo removível/múltiplo (diferente de estado de ciclo de vida), isso constituiria um componente novo, fora do escopo desta fase — não criado aqui.
**Exemplo visual:** ver Capítulo 38.
**Aderência ao TCOS-018:** Capítulo 25.13 (confirmação de ausência, não criação de componente).

## 40. Alertas

**Finalidade:** comunicar bloqueio, atenção ou criticidade ao usuário (TCOS-018, Capítulo 25.14).
**Comportamento visual:** conforme Fase 1, Capítulo 19 — Alerta inline (texto colorido, sem fundo), Banner persistente (fundo claro + ícone, largura total), Toast (fundo Carvão + indicador lateral colorido).
**Variações oficiais:** as 3 já oficiais — nenhuma quarta variação.
**Estados:** por severidade (Âmbar-atenção, Vermelho-crítico) e por tipo (inline/banner/toast).
**Regras de utilização:** alerta crítico de sistema (RN-047) é sempre Banner persistente, nunca apenas Toast (que é efêmero e poderia passar despercebido).
**Exemplo visual:** o Banner "2 alertas críticos aguardando tratamento" do mockup aprovado do Dashboard CEO.
**Aderência ao TCOS-018:** Capítulo 25.14; validado no mockup aprovado.

## 41. Modais

**Finalidade:** ação pontual — criação/edição simples ou confirmação (TCOS-018, Capítulo 25.7).
**Comportamento visual:** cabeçalho + corpo + rodapé com ações (§5.6, TCOS-005); sombra Nível 3 (Fase 1, Capítulo 9) — a mais forte do sistema, reservada a este momento de interrupção total.
**Variações oficiais:** Modal de formulário (criação/edição) e Modal de confirmação (ação irreversível, TCOS-018 Capítulo 25.19).
**Estados:** normal; com campo em erro (Capítulo 33); em processamento (botão de confirmação em estado loading, Capítulo 32).
**Regras de utilização:** rodapé sempre expõe a ação primária e uma ação de cancelamento — nunca apenas um botão de fechar.
**Exemplo visual:** um contêiner central sobreposto, fundo escurecido atrás dele (overlay), cabeçalho com título e botão de fechar, rodapé com "Cancelar" (secundário) e a ação primária (Brasa).
**Aderência ao TCOS-018:** Capítulo 25.7.

## 42. Drawers

**Finalidade:** painel deslizante temporário — notificações, filtro em Tablet/Mobile, expansão de Área na barra lateral (TCOS-018, Capítulo 25.8).
**Comportamento visual:** desliza a partir de uma borda da tela, sobrepõe o conteúdo (nunca o desloca), sombra Nível 2 (Fase 1, Capítulo 9).
**Variações oficiais:** painel de notificações (Capítulo 29), painel de filtro (Capítulo 35), expansão de barra lateral em Tablet (Capítulo 24) — os 3 usos já oficiais consolidados no TCOS-018.
**Estados:** fechado, abrindo (animação de entrada, Fase 1 Capítulo 21), aberto, fechando.
**Regras de utilização:** fecha ao clicar fora dele ou em ação explícita de fechar — nunca requer uma segunda confirmação para fechar (diferente do Modal).
**Exemplo visual:** painel estreito deslizando da borda direita, sobre um fundo levemente escurecido.
**Aderência ao TCOS-018:** Capítulo 25.8.

## 43. Gráficos

**Finalidade:** visualização de dado agregado em Dashboards (TCOS-018, Capítulo 25.20).
**Comportamento visual:** conforme Fase 1, Capítulo 13 — traço/preenchimento em Brasa, no máximo 2 cores por gráfico (exceto funil e calendário).
**Variações oficiais:** linha, barras, funil, calendário/timeline, feed cronológico, histograma — os 6 tipos já usados nas 30 telas (TCOS-018, Capítulo 24).
**Estados:** normal; carregando (Skeleton, Capítulo 48); vazio; erro.
**Regras de utilização:** nenhum gráfico recalcula um valor — sempre exibe o valor já entregue pelo Serviço dono (PF-03).
**Exemplo visual:** os gráficos "Fluxo de Caixa" (linha) e "Margem por Evento" (barras) do mockup aprovado.
**Aderência ao TCOS-018:** Capítulo 25.20; validado no mockup aprovado.

## 44. Widgets

**Finalidade:** blocos especiais de Dashboard além de Card/Gráfico/Tabela — sugestão de IA, alerta crítico, progresso de Meta (TCOS-018, Capítulo 12).
**Comportamento visual:** cada Widget herda a linguagem visual do seu tipo (Alerta = Capítulo 40; sugestão de IA = borda/ícone Roxo-IA; progresso de Meta = barra de progresso em Brasa sobre trilho neutro).
**Variações oficiais:** Card de progresso de Meta, Banner de alerta crítico, Componente de sugestão de IA — os 3 já usados nos 11 Dashboards.
**Estados:** conforme o tipo de Widget (ver Capítulos correspondentes).
**Regras de utilização:** um Dashboard nunca usa mais de um Widget do mesmo tipo simultaneamente sem separação visual clara.
**Exemplo visual:** o Widget "Metas do período" (3 barras de progresso) do mockup aprovado.
**Aderência ao TCOS-018:** Capítulo 25.20; validado no mockup aprovado.

## 45. Estados da Interface

**Finalidade:** comunicar visualmente o momento em que uma tela/componente se encontra — carregando, vazio, erro, sucesso (Frontend Architecture, Capítulos 17–20).
**Comportamento visual:** conforme Fase 1, Capítulo 20 — cada estado com identidade própria, nunca misturados (ex.: erro técnico nunca combinado com mensagem de regra de negócio).
**Variações oficiais:** carregando (Capítulo 47), vazio (Capítulo 46), erro, sucesso — os 4 já oficiais.
**Estados:** este é, ele próprio, o capítulo dos estados — não se aplica um nível adicional.
**Regras de utilização:** todo componente que consulta dado do backend (Card, Tabela, Gráfico) implementa os 4 estados de forma independente — nunca a tela inteira bloqueada por uma única consulta lenta.
**Exemplo visual:** ver Capítulos 46–48 (Empty States, Loading, Skeleton).
**Aderência ao TCOS-018:** Capítulos 25.15–25.18.

## 46. Empty States

**Finalidade:** substituir uma Lista/Tabela/Dashboard sem dado por uma mensagem construtiva, nunca uma área em branco (TCOS-018, Capítulo 25.16).
**Comportamento visual:** ilustração de linha simples (consistente com a linguagem de ícones, Fase 1 Capítulo 12) + texto explicativo + ação sugerida.
**Variações oficiais:** as 3 situações já oficiais — "ainda não há dado" (ação de criar o primeiro item), "filtro sem resultado" (ação de limpar filtro), "bloqueado por parâmetro pendente" (indica o parâmetro e o Perfil responsável).
**Estados:** cada uma das 3 variações é, ela própria, um estado distinto — nunca apresentadas com a mesma mensagem genérica.
**Regras de utilização:** nunca confundido visualmente com um erro técnico (Capítulo 40) — Empty State nunca usa a cor Vermelho-crítico.
**Exemplo visual:** ícone de linha simples ao centro de um Card/Tabela vazio, com texto "Nenhum Lead cadastrado ainda" e botão "Cadastrar o primeiro Lead".
**Aderência ao TCOS-018:** Capítulo 25.16.

## 47. Loading

**Finalidade:** indicar que uma ação do usuário está em processamento (Frontend Architecture, Capítulo 18) — distinto do carregamento de dado em tela (Capítulo 48, Skeleton).
**Comportamento visual:** conforme Fase 1, Capítulo 21 — o próprio Botão assume o estado "loading" (spinner substitui o texto), nunca um bloqueio de tela inteira.
**Variações oficiais:** loading de botão (ação de formulário) — a única variação já oficial (§5.8, TCOS-005).
**Estados:** este é, ele próprio, um dos 5 estados oficiais do Botão (Capítulo 32).
**Regras de utilização:** nunca combinado com um spinner de tela inteira — uma ação de usuário nunca bloqueia o restante da interface.
**Exemplo visual:** o botão "Novo Evento" com um pequeno spinner circular substituindo o texto, mesma cor Brasa, levemente esmaecido.
**Aderência ao TCOS-018:** Capítulo 25.3 (Botões, estado loading).

## 48. Skeleton

**Finalidade:** indicar que um dado de tela ainda está sendo consultado do backend (Frontend Architecture, Capítulo 18; TCOS-018 Capítulo 25.15).
**Comportamento visual:** conforme Fase 1, Capítulo 21 — silhueta cinza-claro no exato formato do conteúdo final, com pulsação suave e lenta (nunca piscar rápido).
**Variações oficiais:** Skeleton de Card, de linha de Tabela, de Gráfico — a mesma lógica aplicada à silhueta de cada componente.
**Estados:** este é, ele próprio, o Estado de Carregamento de qualquer componente (não possui sub-estados).
**Regras de utilização:** aparece apenas no espaço exato que o dado ocupará quando chegar — nunca uma tela em branco, nunca um spinner genérico cobrindo a tela inteira.
**Exemplo visual:** um card com retângulos cinza-claro arredondados no lugar do rótulo e do valor, em leve pulsação.
**Aderência ao TCOS-018:** Capítulo 25.15.

## 49. Tooltips

**Finalidade:** explicar uma restrição ou fornecer contexto adicional sem ocupar espaço permanente na tela (Frontend Architecture, Capítulo 22: "ação desabilitada com indicação visual, tooltip explicando a restrição").
**Comportamento visual:** balão pequeno, fundo Carvão sólido, texto branco, aparece ao passar o cursor/foco sobre o elemento.
**Variações oficiais:** nenhuma variação além do uso já citado (explicação de ação desabilitada por permissão) — o TCOS-011 não cataloga outros usos de Tooltip.
**Estados:** oculto (padrão); visível (hover/focus).
**Regras de utilização:** usado exclusivamente para informação de apoio, nunca para conteúdo essencial à tarefa — se a informação for indispensável, deve estar visível permanentemente na tela, não atrás de um Tooltip.
**Exemplo visual:** um pequeno balão escuro acima de um botão desabilitado, com o texto "Acesso restrito a Financeiro/Direção".
**Aderência ao TCOS-018:** Frontend Architecture, Capítulo 22 (base oficial única).

## 50. Menus de Contexto

**Finalidade:** **nenhuma base oficial encontrada.** Nenhum documento oficial (UX/UI Specification, Frontend Architecture, Visual Blueprint) descreve um menu de contexto (menu suspenso ao clique secundário ou ícone "⋮") em nenhuma das 30 telas.
**Comportamento visual:** não especificado — não definido nesta fase, por ausência de base oficial.
**Variações oficiais:** nenhuma.
**Estados:** não aplicável.
**Regras de utilização:** onde uma ação múltipla por linha de Tabela for necessária no futuro, as 30 telas já especificadas resolvem isso com botões de ação diretos (ex.: "Ver Ficha Técnica", "Editar") — nunca um menu de contexto oculto. A introdução de um Menu de Contexto real exigiria uma nova especificação funcional/UX, fora do escopo desta fase.
**Exemplo visual:** não gerado — ausência de base oficial impede qualquer representação sem inventar comportamento.
**Aderência ao TCOS-018:** nenhuma — item registrado como não especificado, por transparência, não como omissão a corrigir.

## 51. Abas e Accordions

**Finalidade:** organizar conteúdo relacionado dentro de uma mesma tela sem exigir navegação separada (Abas); organizar categorias de navegação de forma compacta e colapsável (Accordion).
**Comportamento visual:** Abas horizontais no topo do painel de Detalhe, aba ativa com sublinhado em Brasa (Fase 1, Capítulo 5); Accordion vertical, exclusivo da barra lateral (Capítulo 24), expande/colapsa ao clicar no cabeçalho da seção.
**Variações oficiais:** Abas — Clientes (Histórico, Eventos, Documentos, Financeiro), Eventos (Resumo, Orçamento, Contrato, Produção, Equipe, Equipamentos, Financeiro), Financeiro Empresarial (Despesas, Receitas, Pagamentos), Administração (Usuários, Log, Alertas, Saúde). Accordion — exclusivo das 10 Áreas da Empresa na barra lateral (Capítulo 24).
**Estados:** aba ativa/inativa; seção de Accordion expandida/colapsada.
**Regras de utilização:** apenas uma aba ativa por vez, dentro do Template Detalhe (Frontend Architecture, Capítulo 12); apenas a Área da tela atual permanece expandida por padrão na barra lateral (já oficial, TCOS-018 Capítulo 9).
**Exemplo visual:** no topo da tela de Eventos, abas "Resumo | Orçamento | Contrato | Produção | Equipe | Equipamentos | Financeiro", a aba ativa com sublinhado em Brasa e peso Semibold.
**Aderência ao TCOS-018:** Capítulo 25.9; Frontend Architecture, Capítulo 12 (Template Detalhe).

## 52. Calendários

**Finalidade:** representar visualmente a distribuição de itens (Escala, Evento, Produção) ao longo de datas de calendário — distinto de um Gráfico (Capítulo 43), que representa série temporal contínua, não datas específicas.
**Comportamento visual:** grade de células por dia; cor da célula corresponde ao Badge de status (Fase 1, Capítulo 18) do item daquele dia.
**Variações oficiais:** calendário de Escalas por Evento/Produção (Escalas), calendário colorido por status (Eventos), calendário/timeline de Produções planejadas (Produção) — os 3 já usados nas 30 telas.
**Estados:** dia vazio (sem item); dia com item (célula colorida pelo status); dia atual (borda de destaque).
**Regras de utilização:** uma célula nunca combina mais de uma cor simultânea — múltiplos itens no mesmo dia são exibidos como contagem numérica, nunca como sobreposição de cores (`[Inferência visual]`, já registrada no TCOS-018 §25.11, quanto à unificação de estilo entre os 3 usos).
**Exemplo visual:** grade de 7 colunas (dias da semana), células com pequenos indicadores coloridos por Evento/Produção/Escala programada naquele dia.
**Aderência ao TCOS-018:** Capítulo 25.11.

## 53. Upload de Arquivos / Documentos Anexados

**Finalidade:** anexar ou consultar documento vinculado a uma entidade, ou importar um arquivo externo (extrato bancário).
**Comportamento visual:** área de seleção de arquivo com borda tracejada (Fase 1, Capítulo 8 — raio pequeno) no estado padrão; lista de documentos já anexados abaixo, cada um com ícone por tipo de arquivo (Fase 1, Capítulo 12).
**Variações oficiais:** as 2 únicas já oficiais — componente "Documentos Anexados" (Contratos, Compras, Clientes) e a ação "Importar Extrato" (Conciliação Bancária, F-068/FL-023).
**Estados:** vazio (nenhum documento anexado); com documentos; enviando (Loading, Capítulo 47); erro de envio (Capítulo 40).
**Regras de utilização:** não existe um componente de upload genérico reutilizável fora desses 2 contextos já oficiais — qualquer novo uso exigiria nova especificação funcional, fora do escopo desta fase (`[Inferência visual]`, já registrada no TCOS-018 §25.12).
**Exemplo visual:** área tracejada com ícone de clipe e texto "Arraste um arquivo ou clique para selecionar", lista de anexos abaixo com nome do arquivo e data de envio.
**Aderência ao TCOS-018:** Capítulo 25.12.

## 54. Timeline

**Finalidade:** exibir a sequência cronológica de mudanças de estado de uma entidade.
**Comportamento visual:** linha vertical com marcadores por evento de mudança, cada um com data, autor ("Sistema" quando automático) e descrição da mudança, ordem cronológica decrescente (mais recente no topo) — conteúdo mínimo já oficial (Frontend Architecture, Capítulo 23).
**Variações oficiais:** linha do tempo do ciclo de vida do Evento (cabeçalho de Eventos, UX/UI Spec §3.14) e a aba "Ver histórico" de toda entidade com histórico obrigatório (ex.: Clientes).
**Estados:** marcador normal; marcador de mudança automática (ícone diferenciado indicando "Sistema"); vazio (entidade recém-criada, sem histórico).
**Regras de utilização:** nunca omite o autor da mudança — toda entrada mostra "usuário" ou "Sistema", nunca em branco (Frontend Architecture, Capítulo 23); consome o Log de Auditoria apenas por consulta, nunca por escrita própria.
**Exemplo visual:** linha vertical fina em cinza, pontos coloridos por tipo de mudança, texto "05/08 · Sistema · Contrato assinado, Evento confirmado".
**Aderência ao TCOS-018:** Capítulo 25.22; Frontend Architecture, Capítulo 23.

## 55. Kanban

**Finalidade:** representar um item avançando por estágios de um ciclo de vida, com transição por arraste entre colunas.
**Comportamento visual:** colunas verticais, uma por estágio; Cards de Conteúdo (Capítulo 31) dentro de cada coluna; contagem no topo de cada coluna.
**Variações oficiais:** as 2 únicas já oficiais — Leads (Novo, Em qualificação, Convertido, Perdido) e Compras (Solicitada, Cotação, Pedido, Recebida, Conferida), cada um com tabela alternativa equivalente já especificada.
**Estados:** coluna vazia; coluna com cards; card sendo arrastado (elevação Nível 2, Fase 1 Capítulo 9; microinteração de arraste, Fase 1 Capítulo 22).
**Regras de utilização:** mover um card entre colunas é sempre equivalente à mesma transição de estágio já disponível na tabela alternativa da mesma tela — nunca uma segunda regra de transição divergente (já oficial, TCOS-018 §25.23).
**Exemplo visual:** 4 colunas lado a lado com título e contagem no topo, cards exibindo nome do Lead e badge de origem/Campanha.
**Aderência ao TCOS-018:** Capítulo 25.23.

## 56. Painéis e Visualizadores Especializados

**Finalidade:** agrupamento de padrões de exibição específicos de uma única tela cada, sem componente único genérico por trás deles.
**Comportamento visual:** variável por tipo — editor de composição é uma Tabela (Capítulo 36) com células editáveis e totalizador; visualizador de documento é um quadro de exibição de PDF; visualizador de log é uma lista cronológica filtrável (Filtros, Capítulo 35); indicador de correspondência é uma marcação visual conectando duas linhas pareadas.
**Variações oficiais:** as 5 já citadas no TCOS-018 §25.24 — editor de composição (Orçamentos, Receitas, Fichas Técnicas), visualizador de documento/PDF (Contratos), visualizador de log (Administração), painel de saúde do sistema (Administração), indicador de correspondência (Conciliação Bancária).
**Estados:** cada um herda os estados do componente-base que estende — Tabela (editor, log) ou vazio/erro (visualizador de documento).
**Regras de utilização:** o painel de saúde do sistema permanece sem conteúdo visual específico definido, por ausência de base oficial além de sua citação como uma das 4 abas de Administração — esta fase não preenche essa lacuna, apenas a reconhece (já registrado, TCOS-018 §25.24).
**Exemplo visual:** o editor de itens do Orçamento (linha por Produto/Pacote com totalizador ao final) e o visualizador de PDF de um Contrato assinado, com botão "Baixar PDF" ao lado.
**Aderência ao TCOS-018:** Capítulo 25.24.

## 57. Estados de Sucesso

**Finalidade:** confirmar visualmente que uma ação do usuário foi concluída com êxito (Frontend Architecture, Capítulo 17).
**Comportamento visual:** conforme Fase 1, Capítulo 20 — nunca uma tela inteira em verde; a confirmação é sempre um Toast (Capítulo 40) ou uma mudança de estado do próprio componente (ex.: Badge de status atualizado).
**Variações oficiais:** as 2 formas já oficiais — Toast de sucesso e mudança de estado in-place do componente afetado (Frontend Architecture, Capítulo 17).
**Estados:** este é, ele próprio, um dos 4 Estados da Interface (Capítulo 45) — não possui sub-estados adicionais.
**Regras de utilização:** nunca acompanhado de um redirecionamento inesperado sem explicação (já oficial, Frontend Architecture Capítulo 17).
**Exemplo visual:** toast breve "Orçamento enviado com sucesso" no canto da tela, com um pequeno indicador em Verde-sucesso.
**Aderência ao TCOS-018:** Capítulo 25.18; Frontend Architecture, Capítulo 17.

## 58. Estados de Operações Críticas

**Finalidade:** garantir que as 8 Operações Críticas já catalogadas (Security and Privacy Architecture, Capítulo 30) recebam tratamento visual distinto de qualquer ação comum do sistema.
**Comportamento visual:** conforme Fase 1, Capítulo 9 (sombra Nível 3, a mais forte do sistema) — Modal (Capítulo 41) ou tela de confirmação com o resumo exato do que será alterado; botão primário de confirmação nunca pré-selecionado por teclado (Fase 1, Capítulo 25.19 do TCOS-018).
**Variações oficiais:** as 8 já catalogadas — Confirmar Evento; Cancelar Evento/Contrato; Registrar Pagamento/Estorno; Alterar Perfil/Permissão de usuário; Aceitar sugestão de IA financeira/comercial; Inativar/Descontinuar entidade Mestre; Exportar relatório com dado sensível; Importar Extrato Bancário.
**Estados:** pendente de confirmação (Modal aberto); confirmado (fecha com Estado de Sucesso, Capítulo 57); cancelado pelo usuário (fecha sem efeito, nenhum Caso de Uso acionado).
**Regras de utilização:** nenhuma Operação Crítica é executada em um único clique, sem exceção — reafirma, sem alteração, Security and Privacy Architecture, Capítulo 30.
**Exemplo visual:** o Modal "Fechar Período" do Dashboard Financeiro Empresarial, com o resumo do que será encerrado e os botões "Cancelar" / "Confirmar Fechamento".
**Aderência ao TCOS-018:** Capítulo 25.19; Security and Privacy Architecture, Capítulo 30.

## 59. Confirmação de Cobertura da Biblioteca

Complementada a Biblioteca Visual Oficial com os 6 componentes integralmente ausentes (Abas e Accordions, Calendários, Upload de Arquivos/Documentos Anexados, Timeline, Kanban, Painéis e Visualizadores Especializados) e o aprofundamento dos 2 componentes com tratamento insuficiente (Estados de Sucesso, Estados de Operações Críticas), totalizando **34 componentes documentados** (26 da Fase 2 original + 8 desta complementação), cada um com os mesmos 7 campos obrigatórios. Cruzando integralmente contra o inventário do TCOS-018 (Capítulo 25.1–25.24, as 30 telas dos Capítulos 12–24): **100% dos componentes usados nas 30 telas possuem agora especificação correspondente na Biblioteca Visual Oficial.** Nenhum componente, estado, variação, comportamento ou funcionalidade foi criado sem ancoragem direta em TCOS-005, TCOS-011, TCOS-018, Security and Privacy Architecture (Capítulo 30, para Operações Críticas) ou na Fase 1 deste próprio documento.

---

**Fim da Fase 2 — Biblioteca Visual Oficial de Componentes.**