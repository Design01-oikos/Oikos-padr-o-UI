---
description: Padrão de interface para aplicativos internos da Oikos Wealth Management (v1) — tema Grafite, tokens de cor, tipografia Aeonik, marca, ícones, estrutura de tela, componentes de sistema (barra, palco, ferramentas, grade, tabela, formulário, estado), gráficos, escrita e comportamento. Inclui o kit de duplicação (CSS base e esqueleto de tela). Derivado do Padrão de Slide v3.5.1, das pranchas de UI do Oikos Studio e do código do Oikos Studio.
---

# Padrão de UI — Aplicativos internos Oikos | v1

> ## ⚠️ ATENÇÃO — leia antes de usar este documento
>
> **1. Siga apenas o que o usuário pediu.** O pedido define o escopo. Este
> documento diz *como* fazer o que foi pedido dentro da marca. Ele não é
> autorização para fazer mais do que isso.
>
> **2. Siga a interface do aplicativo que já existe.** Telas, layout,
> navegação, componentes, fluxos, textos e comportamento atuais ficam como
> estão. Não se reorganiza, não se "moderniza" e não se aproxima dos exemplos
> deste documento por iniciativa própria.
>
> **3. Não crie nada novo sem ser pedido.** Isso inclui tela, seção,
> componente, botão, ferramenta, atalho, campo, estado, aviso, animação, tema,
> ícone e texto. Também não se troca um componente existente por outro "mais
> adequado".
>
> **4. Na dúvida, pergunte.** Se o pedido não deixa claro se algo deve ser
> criado ou alterado, pergunte ao usuário antes. Não decida sozinho.
>
> **5. Este documento não cria pendências.** Diferenças entre o app e o padrão
> não são tarefas implícitas. Se notar alguma relevante, **mencione ao
> usuário** e deixe que ele decida se quer a mudança. Não aplique por conta
> própria.
>
> Os exemplos, pranchas e apêndices servem para consulta quando algo **foi
> pedido**. Nunca são lista de coisas a implementar.

Documento único para **qualquer aplicativo interno da casa**: editor de peças,
painel de carteira, ferramenta de análise, cadastro, consolidação, back-office.
São telas **sistemáticas**, usadas o dia inteiro por quem já conhece a operação:
muita lista, tabela, campo, número e estado.

O objetivo é que **qualquer app novo, ou já existente, carregue a marca sem
perder a forma que ele já tem**:

1. **Tokens fechados.** Cor, tamanho, raio e espaço saem do Apêndice A. Nada se
   inventa por tela.
2. **Regras de forma, não de layout.** O documento diz *como* cada peça se
   parece e se comporta. *Onde* ela fica e *quais* peças a tela tem é decisão
   do app (§0).
3. **Componentes com receita** (§10). Componente novo entra aqui antes de entrar
   no código (§17).

---

## 0. Regra × exemplo — leia antes de tudo

**Este documento não é um molde para copiar.** As pranchas, os diagramas de
tela, as medidas de anatomia e os Apêndices A e B são **exemplos de como as
regras se aplicam**, não a tela que todo app deve ter.

### 0.1 A ordem de prioridade

```
1º  O que o usuário já tem em mãos
    app existente, tela em uso, layout aprovado, fluxo que a equipe já conhece,
    arquivo, rascunho, pedido descrito. Isso é a base. Não se descarta nem se
    redesenha para "ficar igual ao exemplo".

2º  O que o Claude gerar a partir do pedido
    só quando o usuário pede algo novo e não há nada em mãos. A estrutura
    nasce do que foi pedido (quais dados, quais ações, qual fluxo), e só
    daquilo. Não nasce de copiar a prancha nem ganha peças extras.

3º  Os exemplos deste documento
    consultados para resolver dúvida de forma ("como fica uma aba?", "qual o
    raio de um campo?"), nunca como planta a reproduzir.
```

**Em qualquer dos três casos, a camada de marca se aplica por cima.** Um app
existente não muda de layout para entrar no padrão: muda de cor, fonte, forma,
ícone e escrita.

### 0.2 O que é obrigatório e o que é exemplo

| Obrigatório em todo app | Exemplo (adaptar ou ignorar) |
|---|---|
| Aeonik, só 300/400/500 (§5) | o layout editor + grade (§8.1, §8.2) |
| Paleta e papéis de cor, inclusive os degraus do verde (§4) | quais regiões a tela tem e onde ficam |
| Onshore verde / offshore azul; positivo e negativo por sinal (§4.4) | larguras, alturas e margens das regiões (§2.1, §8.3) |
| Contraste AA, com texto sobre verde em `#1B2023` (§4.5) | quantas ferramentas, seções ou colunas existem |
| Forma pelo papel: reto · raio 4 · pílula (§9.1) | os textos de exemplo (`Recentes`, `Arquivos`, `Ver todos`) |
| Casinha e disco da marca sem redesenho; nada de logo horizontal (§6) | ter ou não ter barra superior, barra de ferramentas, gaveta, botão flutuante |
| | quais ações existem (`+ Novo`, `Importar`, `Exportar`, `Buscar`…) |
| Ícones só da biblioteca (§7) | o Apêndice B inteiro |
| Nenhuma foto ou ilustração (§6.4) | o tema: Grafite ou Papel, conforme o app (§4.2–4.3) |
| Profundidade sem sombra decorativa (§9.3) | |
| Regras de tabela, número e data (§10.11, §12) | |
| Escrita (§13), teclado e confirmação destrutiva (§14) | |

**Na dúvida entre seguir o exemplo e preservar o que já existe, preserva-se o
que existe** e aplica-se a regra de marca a ele.

### 0.3 Na prática

- **App existente:** manter estrutura, navegação, fluxo e componentes. Mexer
  só no que o usuário pediu. Se o pedido for aplicar o padrão, trocam-se fonte,
  tokens de cor, raios, ícones e textos dos componentes **que já existem**,
  sem mudar lugar nem função e sem acrescentar nada.
- **App novo com rascunho ou referência do usuário:** o rascunho manda na
  estrutura. O documento manda na aparência.
- **App novo sem referência:** construir só o que foi pedido. As anatomias de
  §8 servem de inspiração, não de lista de peças a incluir.
- **Peça que o documento não cobre:** só se o usuário pedir. Aí se cria com os
  tokens e as regras de forma (§17), sem forçar a peça a parecer com uma das
  pranchas.

**De onde vem cada regra:**

| Marca | Origem |
|---|---|
| **[3.5.1]** | `PADRAO-SLIDE-OIKOS_v3.5.1.md`: regra de marca, vale igual na tela |
| **[prancha]** | as duas pranchas de UI do Oikos Studio (editor e grade de arquivos, 2382×1110): a **estética** do app |
| **[studio]** | `oikos-studio/static/app.css`: o que já está implementado |
| **[v1]** | decisão deste documento (interação, contraste, densidade) |
| ⚖️ | divergência resolvida, com a decisão ao lado |
| ⚠️ | em aberto, depende de design ou jurídico |

**As pranchas são referência de estética, não molde.** Delas se tiram a paleta,
as proporções, a forma de cada peça e a hierarquia. Não se copiam o layout de
uma tela específica, os textos de exemplo, os glifos genéricos de UI desenhados
nelas nem os pontos em que reprovam contraste (anotados com ⚖️). Ver §0.

**Precedência.** Marca segue o **3.5.1** sem exceção. Estética do chassi segue a
**prancha**. Comportamento e acessibilidade seguem este documento. **Saída para
cliente** (PDF, slide, e-mail) segue o 3.5.1, e a interface nunca vai para o
cliente como está.

---

## 1. A estética em sete princípios

1. **Grafite, não preto.** O app vive em quatro degraus de cinza-grafite
   (`#1B2023` → `#242C2F` → `#3F4649` → `#5A6063`). A profundidade é feita por
   degrau de cinza, nunca por sombra.
2. **O conteúdo é a peça clara.** O chassi é escuro para que o documento, a
   tabela ou o slide, que são claros, sejam o único ponto de luz da tela.
3. **Um tamanho de texto no chassi; a hierarquia vem da tinta.** Barra,
   ferramentas, botões, campos e listas usam o mesmo corpo. O que distingue principal de
   apoio é a tinta: branco, branco-gelo, cinza.
4. **O verde é a voz da interface, em degraus.** Cada degrau da escala verde
   tem um papel fixo (marca, seleção, ação, ligado). Fora desses papéis, nada é
   verde no chassi.
5. **Três formas, cada uma com significado.** Pílula = ferramenta flutuante.
   Retângulo de raio 4 = controle de formulário. Canto reto = estrutura (card,
   rótulo de seção, dado).
6. **Nenhuma imagem.** Sem fotografia, ilustração ou avatar com foto. A casinha,
   os ícones da biblioteca e o próprio dado são os únicos recursos gráficos.
7. **Previsível acima de criativo.** O mesmo controle tem a mesma aparência e
   o mesmo comportamento em todos os apps, mesmo quando cada app o coloca num
   lugar diferente.

---

## 2. Kit de duplicação — levar a marca para um app

```
1. Copiar o Apêndice A para  static/oikos-ui.css      (tokens + base + componentes)
2. Servir Branding/ em  /branding/                    (fonte e ícones — §3)
3. Gerar static/icons.svg a partir de Branding/ÍCONES (§7.3)
4. Estrutura da tela:
     app existente      → manter a que já existe e aplicar as classes/tokens
     rascunho do usuário → montar a partir dele
     nada em mãos       → desenhar a partir do pedido; o Apêndice B é só
                          um exemplo opcional de partida
5. Rodar o checklist de §18 antes de liberar
```

**O que se duplica entre apps é a camada de marca** (tokens, fonte, formas,
ícones, escrita), **não a tela.** Dois apps Oikos podem ter estruturas
completamente diferentes e ser reconhecidos como da mesma casa.

- **`oikos-ui.css` não se edita por app.** O CSS do app vai em `app.css` e
  **só consome** variáveis.
- **Nenhum hex, `font-size` ou `border-radius` literal em `app.css`.** Uma busca
  por `#[0-9A-Fa-f]{3,6}` em `app.css` tem que voltar vazia.
- **Na barra, só `OIKOS`** ao lado do disco (§6.2). O nome do app vai no
  título da aba do navegador: `<Tela> | Oikos <Nome>`.
- **Armazenamento local:** chaves `oikos:<app>:<recurso>:v1`.

### 2.1 Escala: prancha × tela

As pranchas foram desenhadas em **2382×1110**. **Os valores deste documento e do
Apêndice A são de tela (CSS)**, obtidos multiplicando a prancha por **0,8** e
arredondando para a grade de 4px. Isso permite conferir qualquer medida contra
o desenho.

| Elemento | Prancha | Tela (CSS) |
|---|---|---|
| Barra superior | 75 | **60** |
| Disco da marca | 27 | **22** |
| `OIKOS` na barra | 27 | **16** (reduzido — §6.2) |
| Texto do chassi | 20 | **16** |
| Ferramenta (pílula) | 42 alt. | **36** |
| Campo / botão de formulário | 47–48 alt. | **40** |
| Card da grade | 413 × 215 | **330 × 172** |
| Gap da grade | 22 | **16** |
| Margem lateral da grade | 114 | **96** |
| Raio de controle | 4,5 | **4** |

⚖️ **Escala fixa.** O Oikos Studio encolhe a interface inteira com uma variável
`--k` conforme a largura da janela. **Apps novos não fazem isso**: as medidas
são fixas e quem amplia é o zoom do navegador. Assim a tela aguenta 200% de
zoom e é igual em toda máquina. [v1]

---

## 3. Assets oficiais — pasta `Branding/`

**Fonte, símbolo e ícones vêm sempre daqui. Nunca redesenhar, nunca buscar fora,
nunca usar biblioteca de terceiros.**

| Pasta | Conteúdo | Uso no app |
|---|---|---|
| `Branding/FONTE/Aeonik-Full-Family-Desktop/` | Aeonik `.otf` + EULA | só Light, Regular e Medium (§5) |
| `Branding/LOGO/` | `Simbolo_Oikos.pdf` (casinha) · `LogoBranca_Oikos.svg` (lettering vertical) | casinha e lettering (§6) |
| `Branding/ÍCONES/` | 73 `.svg` em `viewBox 0 0 72 72` + 4 `.png` | toda iconografia (§7) |

**A marca tem dois elementos e nenhum outro:** a **casinha** e o **lettering
vertical `O I K O S`**. **Não existe logo horizontal.** O `OIKOS` escrito ao
lado do disco (§6.2) é rótulo de produto, não logotipo.

---

## 4. Cor

### 4.1 Tema Grafite (padrão)

Medido nas pranchas, com o texto de apoio ajustado para contraste:

| Token | HEX | Papel | Origem |
|---|---|---|---|
| `--ok-bar` | `#1B2023` | barra superior, header de tabela (**tinta oficial**) | prancha · 3.5.1 |
| `--ok-stage` | `#242C2F` | palco: o fundo onde o conteúdo vive | prancha |
| `--ok-surface` | `#3F4649` | card, ferramenta, gaveta, popover | prancha |
| `--ok-raised` | `#5A6063` | campo, rótulo de seção inativo | prancha |
| `--ok-line` | `#686D71` | contorno de campo, divisória do chassi | prancha |
| `--ok-hover` | `#4B5356` | hover de peça `--ok-surface` | studio |
| `--ok-ink` | `#FDFDFD` | texto principal | prancha |
| `--ok-ink-2` | `#ECECEC` | texto de campo, valor secundário | prancha |
| `--ok-mut` | `#C9CBCC` | apoio: metadado, rótulo, placeholder, botão secundário | ⚖️ v1 |
| `--ok-icon` | `#919398` | ícone em repouso | prancha |

⚖️ **Apoio em `#C9CBCC`, não em `#767A7E`.** As pranchas usam `#767A7E` para
metadado, placeholder e botão secundário. Ele dá **2,2:1** sobre `#3F4649` e
1,5:1 sobre `#5A6063`, ou seja, ilegível. O `#C9CBCC` mantém a mesma posição
na hierarquia (abaixo do branco e do gelo) e passa no contraste. [v1]

### 4.2 Os degraus do verde na interface

**Cada degrau tem um papel, e só ele.** É o que torna os apps reconhecíveis
entre si:

| Degrau | HEX | Papel na interface | Texto sobre ele |
|---|---|---|---|
| green-200 | `#B7E583` | **disco da marca** (§6.2) | casinha `#1B2023` |
| green-300 | `#A5DD7D` | **rótulo da seção atual** (faixa sólida) | `#1B2023` |
| green-300 a 45% | `rgba(165,221,125,.45)` | **item selecionado** (linha de lista, índice ativo) | `#FDFDFD` |
| green-400 | `#92D476` | **ação primária** (botão `Salvar`, `Confirmar`) | `#1B2023` |
| green-500 | `#6EC26A` | **ligado / ativo** (ferramenta ligada, moldura do item em foco, foco) | `#1B2023` |

⚖️ **Texto sobre verde é sempre `#1B2023`.** A prancha escreve branco sobre
verde-500: **2,2:1**, reprova. Tinta oficial sobre verde dá 7,5:1. [v1]

⚖️ **O verde de interface não entra na área de dado.** Dentro de tabela,
gráfico e lista de ativos, verde significa **onshore** [3.5.1]. Uma linha
selecionada tingida de verde leria como "Brasil". Regra: **dentro da área de
dado, a seleção é neutra** (fundo `--ok-raised` no Grafite, `#ECECEC` no Papel).
O verde de interface fica no chassi: barra, ferramentas, botões, menus e listas de
arquivos. [v1]

### 4.3 Tema Papel (variante clara)

Para telas cujo conteúdo **é** a tabela ou o formulário longo (cadastro,
conciliação, relatório lido por horas), o palco pode ser claro. **A barra
continua `#1B2023` e os papéis do verde não mudam.**

| Token | Grafite | Papel |
|---|---|---|
| `--ok-bar` | `#1B2023` | `#1B2023` |
| `--ok-stage` | `#242C2F` | `#FDFDFD` |
| `--ok-surface` | `#3F4649` | `#F4F4F4` |
| `--ok-raised` | `#5A6063` | `#ECECEC` |
| `--ok-line` | `#686D71` | `#D7D8D5` |
| `--ok-hover` | `#4B5356` | `#ECECEC` |
| `--ok-ink` | `#FDFDFD` | `#1B2023` |
| `--ok-ink-2` | `#ECECEC` | `#3F4649` |
| `--ok-mut` | `#C9CBCC` | `#686D71` |
| `--ok-icon` | `#919398` | `#686D71` |

Um app escolhe **um** tema por tela inteira. Nunca misture regiões escuras e
claras do chassi na mesma tela (o conteúdo claro no palco, como slide ou
documento, não conta).

### 4.4 Cor de dado — igual ao slide [3.5.1 §7]

| Token | HEX | Papel |
|---|---|---|
| `--ok-onshore` | `#A5DD7D` | série, chip, realce onshore |
| `--ok-offshore` | `#B7CDFF` | série, chip, realce offshore |
| `--ok-ref` | `#A7A8A8` | benchmark, série de referência |
| `--ok-neg` | `#EE4E3B` no Grafite · `#B22B20` no Papel | negativo, erro, crítico |
| `--ok-warn` | `#FFE500` no Grafite · `#D9C300` no Papel | atenção |

| | 900 | 800 | 700 | 600 | 500 | 400 | 300 | 200 | 100 | 50 |
|---|---|---|---|---|---|---|---|---|---|---|
| **Verde** | `#008D44` | `#259F51` | `#49B05D` | `#5CB964` | `#6EC26A` | `#92D476` | `#A5DD7D` | `#B7E583` | `#DBF68F` | `#E6F9B4` |
| **Azul** | `#182662` | `#213282` | `#273A98` | `#384BA4` | `#495BAF` | `#586BBB` | `#677AC6` | `#8FA4E3` | `#B7CDFF` | `#D6E2FF` |
| **Vermelho** | `#B22B20` | — | ⚠️ | — | `#EE4E3B` | — | ⚠️ | `#FFA19C` | ⚠️ | — |
| **Amarelo** | `#D9C300` | — | — | — | `#FFE500` | — | `#FFEB5F` | `#FDEF85` | `#FDF4AF` | `#FEF9D2` |

- **Onshore nunca em azul; offshore nunca em verde.** Exceção: gráfico sem
  contexto de localidade (ranking de fundos) pode misturar as escalas. [3.5.1]
- ⚖️ **Positivo não é verde, informação não é azul.** Positivo = tinta normal +
  sinal `+`. Negativo = `--ok-neg` + sinal `−`. Informação = cinza. Verde e
  azul já são jurisdição. [v1]
- ⚠️ `red-700`, `red-300` e `red-100` estão cadastrados com HEX de verde. **Não
  usar.** [3.5.1 §7.2]
- **No Grafite, as séries usam os tons 100–400.** Os 700–900 somem sobre
  `#242C2F`. **No Papel, valem as regras do slide.**

### 4.5 Contraste — o que pode ser texto

Meta **WCAG 2.2 AA**: 4,5:1 para texto normal, 3:1 para texto ≥ 24px, ícone e
borda de controle. Valores calculados, não medidos.

| Tinta | `#242C2F` palco | `#3F4649` card | `#5A6063` campo | Uso |
|---|---|---|---|---|
| `#FDFDFD` | 14,2 ✅ | 9,6 ✅ | 6,4 ✅ | principal |
| `#ECECEC` | 12,0 ✅ | 8,1 ✅ | 5,4 ✅ | campo, secundário |
| `#C9CBCC` | 8,6 ✅ | 5,8 ✅ | 3,9 ⚠️ | apoio; no campo, só placeholder |
| `#919398` | 4,6 ✅ | 3,1 ✅ | — | ícone, nunca texto pequeno sobre card |
| `#767A7E` | 3,3 ❌ | 2,2 ❌ | 1,5 ❌ | **não usar como texto** |
| `#1B2023` sobre verde 300/400/500 | — | — | — | 10,4 / 9,3 / 7,5 ✅ |

---

## 5. Tipografia

### 5.1 Fonte: sempre Aeonik

**Aeonik em todo elemento**: barra, ferramenta, campo, botão, célula,
tooltip, eixo de gráfico, mensagem de erro. Nenhuma segunda família. [3.5.1 §5]

| Peso | Onde |
|---|---|
| **Light 300** | número de KPI, título de tela (quando houver) |
| **Regular 400** | **todo o chassi**: `OIKOS` na barra, ferramenta, campo, botão, lista |
| **Medium 500** | header de tabela, rótulo UPPERCASE, total, `<b>`/`<strong>` |

**Bold (600/700) não existe no padrão.** `font-synthesis:none` impede o
navegador de fabricar negrito.

### 5.2 Carregamento

```css
@font-face{ font-family:"Aeonik"; font-weight:400; font-display:block;
  src:local("Aeonik Regular"), local("Aeonik-Regular"),
      url("/branding/FONTE/Aeonik-Full-Family-Desktop/Aeonik-Regular.otf") format("opentype"); }
```

Os três pesos estão no Apêndice A. `local()` antes de `url()`;
`font-display:block` para a tela nunca aparecer em Arial. ⚠️ A Aeonik da pasta é
EULA desktop (§19).

### 5.3 A regra do chassi: um corpo, quatro tintas

O traço mais forte das pranchas é que **barra, ferramentas, campos, botões,
cards e listas usam o mesmo tamanho de texto**. A hierarquia vem só
da tinta:

```
16px Regular  ─┬─ #FDFDFD  principal   (OIKOS na barra, nome de arquivo, item)
               ├─ #ECECEC  secundário  (valor em campo, nome no menu)
               └─ #C9CBCC  apoio       (metadado, placeholder, botão secundário)
```

- **Não crie tamanhos intermediários no chassi** (15, 17, 18px). Uma informação
  é mais importante pela tinta ou pela posição, não pelo corpo.
- **Sem exceção na barra:** o `OIKOS` ao lado do disco também é 16px (§6.2).

### 5.4 Escala da área de dado

Dentro do palco, onde ficam tabelas, KPIs e gráficos, vale uma escala própria:

| Classe | px | Peso | Line-height | Caixa | Uso |
|---|---|---|---|---|---|
| `.t-page` | 28 | 300 (+400) | 1.15 | UPPER | título de tela de dados (opcional) |
| `.t-section` | 20 | 400 | 1.25 | normal | título de bloco |
| `.t-ui` | **16** | 400 | 1.4 | normal | **o corpo do chassi** |
| `.t-cell` | 14 | 400 | 1.4 | normal | célula de tabela densa |
| `.t-label` | 12 | 500 | 1.3 | UPPER `.06em` | header de tabela, eyebrow, chip |
| `.t-meta` | 12 | 400 | 1.4 | normal | contador, data de atualização |
| `.t-kpi` | 32 | 300 | 1.1 | — | número de KPI |

- **Piso de 12px**, e só em `.t-label` e `.t-meta`. Não cabe? Corta palavra ou
  trunca com tooltip. Nunca reduz fonte.
- **Todo número com `tabular-nums`**, que já vem no `body`.
- `letter-spacing` só em UPPERCASE pequeno (`.04em`–`.06em`). Nunca negativo.
- **Título de tela** (`.t-page`): mesma regra do slide. UPPERCASE via CSS, Light
  com a parte enfatizada em Regular, separador ` | `, uma linha, sem régua
  abaixo. [3.5.1 §5.1]

---

## 6. A marca no app

### 6.1 Casinha — o símbolo

Proporção **54 : 72,843 (0,741)**: não deformar, girar, contornar nem pôr
sombra. Path de contorno e path cheio em 3.5.1 §9.1 e §15.2.

### 6.2 Disco da marca — a assinatura de todo app

**O canto esquerdo da barra superior é sempre o disco:** círculo **green-200
`#B7E583`** com a **casinha cheia** em `#1B2023`, seguido da palavra **`OIKOS`**
e de nada mais. [prancha]

```html
<button class="brand" aria-haspopup="menu" aria-expanded="false" aria-label="Oikos — menu">
  <svg class="brand-disc" viewBox="0 0 27 27" aria-hidden="true">
    <circle cx="13.5" cy="13.5" r="13.5" fill="#B7E583"/>
    <path d="M13.5 6.33L7.17 12.66V18.98H19.83V12.66Z" fill="#1B2023"/>
  </svg>
  <span class="brand-name">Oikos</span>
  <svg class="ic sm" aria-hidden="true"><use href="/static/icons.svg#ic-drop-down-arrow"/></svg>
</button>
```

| | Prancha | Tela |
|---|---|---|
| Disco | 27 | 22 |
| Casinha dentro | 12,7 de largura | 10 |
| Disco ↔ `OIKOS` | 10 | 8 |
| `OIKOS` | 27px na prancha, **reduzido** | **16px** Regular UPPERCASE `#FDFDFD` |
| Margem esquerda da barra | 21 | 16 |

- **Só `OIKOS`, sem o nome do app.** Nada de `OIKOS STUDIO`, `OIKOS PAINEL`
  ou qualquer composição: a barra assina a casa, não o produto. O nome do app,
  quando precisar aparecer, vai no título da aba do navegador e, se fizer
  sentido, no contexto da barra (à direita do divisor), nunca colado ao
  `OIKOS`.
- ⚖️ **`OIKOS` em 16px, menor que na prancha** (27px ≈ 22px de tela). Fica no
  mesmo corpo do resto do chassi: o disco faz o papel de marca e a palavra
  apenas o acompanha.
- **`OIKOS` não é logotipo:** sem peso especial, sem cor de marca, sem tracking.
  Escreve-se `Oikos` e o CSS faz a caixa alta.
- **O conjunto é um botão:** abre o menu do app (arquivos, telas,
  configurações). O triângulo à direita indica isso. [prancha]
- ⚖️ O favicon do site é lima com casinha de contorno. **Nos apps, o ícone da
  aba do navegador é o disco da prancha** (green-200 + casinha cheia), para que
  todos os apps abertos se reconheçam lado a lado.

### 6.3 Lettering vertical `O I K O S`

`viewBox 0 0 50 175`, paths em 3.5.1 §9.2. **No app, só na tela de login e na
tela de carregamento inicial**, sobre `#1B2023`, em `#FDFDFD`, com no mínimo 48px
de largura. Nunca na barra, nunca em card, nunca montado com `<text>`.

### 6.4 O que não existe

- **Logo horizontal**, nem montado com a casinha e "OIKOS" em Aeonik.
- **Fotografia**, ilustração, mascote, 3D, emoji.
- **Avatar com foto.** Pessoa aparece como **avatar de letra**: círculo 28px,
  iniciais 12px Medium `#1B2023` sobre `#ECECEC`.
- **Miniatura decorativa.** Card de arquivo sem prévia mostra só o texto de
  estado centralizado (§10.7), nunca imagem de banco ou padrão gráfico.

---

## 7. Ícones

### 7.1 A biblioteca

**Só a biblioteca da marca** (`Branding/ÍCONES/`, transcrita no 3.5.1 §10.5).

⚖️ **As pranchas usam glifos genéricos de UI** (lupa, seta de envio, recarregar,
olho) como marcação de lugar. **Na implementação, cada um é trocado pelo
equivalente da biblioteca** do mapa abaixo. O desenho da prancha indica posição
e tamanho, não o glifo.

**O mapa abaixo não é lista de ações que o app deve ter.** Ele só diz qual
ícone usar **se** a ação já existir no app ou for pedida. Não se acrescenta
`Novo`, `Importar`, `Exportar`, `Buscar` ou qualquer outra ação por ela estar
aqui.

| Ação (se existir) | Ícone | | Ação (se existir) | Ícone |
|---|---|---|---|---|
| Menu do app | `Drop Down Arrow` | | Buscar / zoom | `Search` |
| Novo | `Add` | | Editar | `Edit` |
| Excluir / lixeira | `Delete` | | Duplicar | `Copy` |
| Fechar / limpar | `Close` | | Concluído | `Check` |
| Restaurar / atualizar | `Refresh` | | Exportar / baixar | `File Download` |
| Importar / enviar arquivo | `File Upload` | | PDF | `PDF` |
| Tela cheia | `Open Full` | | Selecionar tudo | `Select All` |
| Mostrar / ocultar | `Visibility` · `Visibilityoff` | | Data | `Date` |
| Notificações | `Notifications` | | Sair | `Logout` |
| Informação | `Info 2` | | Atenção / erro | `Alert` |
| Pendente | `Pending` · `Clock` | | Ver todos (grade) | `Apresentação` |
| Filtrar · Mais · Ajustes | `Filter` · `More` · `Settings` ⚠️ png | | Onshore · Offshore | `Brasil` · `Global` |

**Nomes que se confundem:** `Info` = casinha cheia (marcador de legenda);
`Info2` = casinha de contorno; `Info 2` = círculo com "i".

### 7.2 Tamanho e cor

| Token | px | Uso |
|---|---|---|
| `--ic-sm` | 16 | célula, campo, triângulo do menu |
| `--ic-md` | 20 | **padrão**: ferramenta, botão, item de lista |
| `--ic-lg` | 24 | ação isolada na barra |
| `--ic-xl` | 48 | estado vazio |

- **Em repouso o ícone é `--ok-icon` (`#919398`). Com hover, foco ou rótulo ao
  lado, ele vai para a tinta do texto** (`currentColor`). [prancha]
- Área clicável mínima de **32×32**, mesmo com glifo de 16–20.
- Botão só com ícone tem `aria-label` + tooltip.

### 7.3 Recolorir e empacotar

```js
// só a tinta da marca (fill E stroke). Preserva o fill="white" da máscara de clip
svg = svg.replace(/(fill|stroke)="#1B2023"/g, '$1="currentColor"');
```

Gerar **uma vez** um `static/icons.svg` (sprite com `<symbol id="ic-<nome>">` já
em `currentColor`, nomes em minúsculas e sem acento: `ic-drop-down-arrow`,
`ic-apresentacao`) e usar `<svg><use href="/static/icons.svg#ic-…"/></svg>` em
todos os apps.

---

## 8. Estrutura de tela

> **Esta seção é exemplo (§0).** As duas anatomias abaixo mostram como as
> regras se aplicam a um editor e a uma tela de arquivos, os dois casos das
> pranchas. Um app com outra estrutura, existente ou gerada a partir do
> pedido, **mantém a própria estrutura** e usa daqui só o que servir: os
> tokens de cada região, a forma de cada peça, as medidas como ponto de
> partida.

### 8.1 Anatomia — exemplo: editor

```
┌───────────────────────────────────────────────────────────────────────────────┐
│ ◉ OIKOS ▾ │ arquivo-atual.json                                     Salvo       │ barra 60  #1B2023
├───────────────────────────────────────────────────────────────────────────────┤
│  (Guias) (⌕ Zoom) (⇪ Exportar PDF) (↻ Restaurar)                              │
│                                                                               │
│  [01]                                                               👁        │
│  ┌─────────────────────────────────────────────────────────────────┐          │
│  │                                                                 │          │
│  │            conteúdo claro (slide, documento)                    │          │
│  │                                                                 │          │
│  └─────────────────────────────────────────────────────────────────┘          │
│                                                                               │
│                                                          (▦ Ver todos)        │
│  palco #242C2F                                                                │
└───────────────────────────────────────────────────────────────────────────────┘
```

### 8.2 Anatomia — exemplo: grade de arquivos

```
┌───────────────────────────────────────────────────────────────────────────────┐
│ ◉ OIKOS ▾                                                                     │
├───────────────────────────────────────────────────────────────────────────────┤
│  96  ████ Recentes ████                                                       │
│      ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐                   │
│      │Nome    │ │Nome    │ │Nome    │ │Nome    │ │Nome    │   cards 330×172   │
│      │ estado │ │ estado │ │ estado │ │ estado │ │ estado │   gap 16          │
│      └────────┘ └────────┘ └────────┘ └────────┘ └────────┘                   │
│                                                                               │
│      ▒▒▒ Arquivos ▒▒▒▕⌕ Nome            ▏                                     │
│      ┌────────┐ ┌────────┐ ...                                                │
└───────────────────────────────────────────────────────────────────────────────┘
```

### 8.3 As regiões — quando o app as tiver

Nenhuma região é obrigatória. **Se o app tiver** uma delas, ela segue a linha
correspondente:

| Região | Tela | Regra |
|---|---|---|
| **Barra superior** | 60px, `--ok-bar`, largura total | disco + nome + ▾ · divisor vertical 1px `#3A4145` × 20px · contexto (arquivo, cliente) em `--ok-ink-2` truncado · *(espaço)* · pílula de estado · ações globais |
| **Palco** | `--ok-stage`, padding 32 (editor) ou 96 lateral (grade) | onde o conteúdo vive; rola na vertical |
| **Ferramentas** (opcional) | pílulas flutuantes, 32px abaixo da barra, 40px da esquerda | só se o app já tiver ou for pedido; **sem barra atrás**: flutuam sobre o palco (§10.2) |
| **Botão flutuante** | canto inferior direito do palco | uma ação de modo (`Ver todos`) (§10.8) |
| **Menu do app** | gaveta de 368px saindo da esquerda, sob a barra, `--ok-surface`, véu no palco | aberto pelo disco da marca |

- **Navegação:** a que o app já tem continua. Em app novo, o menu aberto pelo
  disco da marca é a sugestão; barra lateral fixa, abas no topo ou outra forma
  também servem, desde que usem os tokens e as formas deste documento.
- **Barra superior, quando existir:** fundo `#1B2023` com o disco da marca à
  esquerda (§6.2). É o elemento que mais ajuda a reconhecer os apps da casa
  entre si. O resto da barra é do app.

### 8.4 Espaço

Base 4px, só estes degraus:

```
4 · 8 · 12 · 16 · 20 · 24 · 32 · 40 · 48 · 64 · 96
```

| Uso | Valor |
|---|---|
| Ícone ↔ rótulo | 8 |
| Entre ferramentas (pílulas) | 16 |
| Entre botões lado a lado | 12 |
| Rótulo de seção → grade | 24 |
| Gap da grade de cards | 16 |
| Entre seções da grade | 48 |
| Padding do campo | 12 horizontal |

### 8.5 Telas e zoom

- **Viewport-alvo: 1280–1920px.** Conferir em 1280, 1440 e 1920. A grade de
  cards se ajusta pelo número de colunas (`auto-fill` com 330px mínimos), nunca
  encolhendo o card.
- **200% de zoom** sem perda de conteúdo.

---

## 9. Forma

### 9.1 Três formas, três significados [prancha]

| Forma | Raio | Quem usa | O que comunica |
|---|---|---|---|
| **Canto reto** | 0 | card, rótulo de seção, header de tabela, toda marca de gráfico | **estrutura**: é lugar, não ação |
| **Retângulo suave** | 4 | campo, botão de formulário, popover, menu, modal, chip de índice | **controle**: aqui se digita ou se confirma |
| **Pílula** | 999px | ferramenta flutuante, botão flutuante, pílula de status, contador | **ferramenta**: muda o modo ou a vista |

- **Não trocar formas entre papéis.** Botão `Salvar` em pílula ou ferramenta em
  retângulo quebram a leitura que a pessoa já aprendeu.
- **Gráfico nunca tem canto arredondado.** [3.5.1 §14.1]

### 9.2 Linhas

- Contorno de campo e de botão secundário: 1px `--ok-line`.
- Divisória de lista e de tabela: 1px `--ok-line`, **todas iguais, a última
  inclusive**. [3.5.1 §12.1]
- **Nenhuma linha colorida abaixo de texto.** Estado ativo é fundo, não
  sublinhado. [3.5.1 §4.3]
- **Exceção única:** a **moldura de foco do item ativo no palco** (slide,
  documento, card aberto), com 4px em green-500 sobreposta à borda. Ela marca o
  objeto em edição, não um texto. [studio]

### 9.3 Profundidade sem sombra

- **A profundidade é o degrau de cinza**: palco `#242C2F` → card `#3F4649` →
  campo `#5A6063`. Quanto mais "à frente", mais claro.
- **Sombra só no que flutua por cima de tudo** (menu, popover, modal, gaveta):
  `0 14px 40px rgba(0,0,0,.45)`. Modal: `0 24px 70px rgba(0,0,0,.5)`. [studio]
- Ferramentas e botão flutuante **não** levam sombra. O contraste com o palco
  basta.
- Véu de gaveta e de modal: `rgba(27,32,35,.62)`.

---

## 10. Componentes

> Cada receita diz **como a peça é** quando o app a tem. Não é lista de peças
> que todo app precisa ter. Medidas são o ponto de partida. Se o app existente
> já usa outra altura ou largura que funciona, mantém-se, desde que fique na
> grade de 4px e respeite a forma pelo papel (§9.1).

### 10.1 Barra superior

```
Altura      60 · fundo --ok-bar · padding 0 16
Esquerda    disco + OIKOS + ▾ (§6.2), hover rgba(255,255,255,.06) raio 4
Divisor     1px #3A4145 × 20px, margem 16
Contexto    nome do arquivo/cliente/tela, 16px --ok-ink-2, truncado com reticência
Direita     o que o app já tiver ali (pílula de estado, ações globais), ou nada
```

A barra **não precisa ter** contexto, pílula de estado nem ações globais. Esses
itens só entram se o app já os tem ou se o usuário pedir. A receita diz como
ficam quando existem.

**Pílula de estado** (se existir) [studio]: `Salvo` (`--ok-mut`) · `Salvando` (green-500) ·
`Não salvo` (`--ok-warn`) · `Offline` (`--ok-mut`). Sem reticências. Fica em
`aria-live="polite"`.

### 10.2 Ferramentas — pílulas flutuantes [prancha]

> ⚠️ **A barra de ferramentas não é obrigatória.** Nenhum app precisa ter
> pílulas de ação (`+ Novo`, `Importar`, `Exportar`, `Zoom`, `Guias` etc.), e
> nenhuma dessas ações deve ser criada por estar descrita aqui. Esta receita
> vale **só** para quando o app já tem ferramentas desse tipo ou o usuário
> pedir. Se o app já organiza as ações de outro jeito (menu, botões no
> cabeçalho, ações por linha), **mantém-se o jeito do app**.

```
Forma       pílula · altura 36 · padding 0 16 · gap entre pílulas 16
Fundo       --ok-surface #3F4649 · hover --ok-hover #4B5356
Conteúdo    ícone 20 + rótulo 16px Regular --ok-ink, 8px entre eles
Ligada      fundo green-500 #6EC26A · texto e ícone #1B2023 · aria-pressed="true"
Desligada   opacity .45 · sem hover
Posição     fixa na tela (não rola com o conteúdo), sobre o palco, sem barra atrás
```

- **Uma ferramenta = um verbo ou um modo.** Os nomes citados aqui são
  exemplos, não um conjunto a implementar. Rótulo sempre visível; só ícone
  quando o ícone é inequívoco (`+`, `−`).
- **Ordem**, quando o app não tiver uma própria: modos de visualização →
  exportação → reversão, com a destrutiva por último. Se o app já tem uma
  ordem, ela fica.
- Ferramenta com opções abre **popover** ancorado (§10.9), com ▾ à direita do
  rótulo.
- **Zoom** (quando houver canvas): `−` · nível · `+`, níveis
  `10 · 40 · 70 · 100` + `Encaixar`. [CLAUDE.md]
- **Rótulo não anuncia tecla.** O atalho aparece no tooltip.

### 10.3 Campos

```
Fundo        --ok-raised #5A6063 · contorno 1px --ok-line · raio 4
Altura       40 (uma linha) · área de texto mín. 96, cresce até 240 e rola
Texto        16px Regular --ok-ink-2 · padding 0 12 (área: 12)
Placeholder  --ok-mut · exemplo real de uso, nunca substituto do rótulo
Rótulo       acima, 12px Medium UPPERCASE .06em --ok-mut, 6px de folga
Foco         contorno 1px green-500 [studio] + anel :focus-visible
Erro         contorno 1px --ok-neg + mensagem 12px --ok-neg com Alert 16
Desabilitado opacity .45
Busca        ícone Search 16 --ok-icon à esquerda, Close para limpar
```

- **Placeholder ensina pelo exemplo:** `Ex.: 29/11/2025`, `Ex.: NTN-B 2035`.
  Instrução de teclado vai em `.t-meta` abaixo do campo, não dentro do
  placeholder.
- **Busca colada a rótulo de seção** (§10.6) tem a mesma altura do rótulo e canto
  reto, porque faz parte da faixa.
- Valor monetário e percentual: alinhado à direita, `tabular-nums`, máscara
  pt-BR.
- Validação ao sair do campo. A mensagem diz o que fazer.

### 10.4 Botões de formulário

| Variante | Fundo | Contorno | Texto | Uso |
|---|---|---|---|---|
| **Primário** | green-400 `#92D476` | — | `#1B2023` | **uma** por formulário/modal: `Salvar`, `Confirmar` |
| **Secundário** | `--ok-stage` `#242C2F` | 1px `--ok-line` | `--ok-mut` | `Cancelar`, `Limpar filtros` |
| **Fantasma** | transparente | — | `--ok-ink` | ação de linha, link de ação |
| **Destrutivo** | `--ok-neg` | — | `#FDFDFD` | só na confirmação de exclusão |

```
Forma       retângulo · raio 4 · altura 40 (32 em linha de lista)
Texto       16px Regular, caixa normal, centralizado
Em par      mesma largura, gap 12, secundário à esquerda e primário à direita
Hover       primário → green-500 · secundário → --ok-hover · fantasma → rgba(255,255,255,.08)
Carregando  rótulo mantido + indicador 16px; largura não muda
```

⚖️ **O secundário da prancha usa texto `#767A7E`, que dá 3,3:1 sobre o palco.**
Fica `--ok-mut` `#C9CBCC`. O botão continua recessivo, mas legível.

- **Rótulo:** infinitivo + objeto (`Salvar carteira`, `Exportar PDF`) ou verbo
  curto quando o contexto basta (`Salvar`). Nunca `OK`, `Sim` ou `Clique aqui`.

### 10.5 Chip de índice e moldura do item ativo [prancha · studio]

```
Chip        acima do item, à esquerda · 40×28 · raio 4 · número 16px tabular-nums
  ativo     fundo green-300 a 45% · número --ok-ink
  inativo   fundo rgba(145,147,152,.22) · número --ok-icon
  fora      fundo rgba(145,147,152,.14) · número #6E757B · item a 40% de opacidade
Moldura     item ativo: 4px green-500 sobre a borda (2 para dentro, 2 para fora)
Olho        à direita do chip, Visibility/Visibilityoff 20, --ok-icon:
            liga e desliga o item da saída (PDF, exportação)
```

### 10.6 Rótulo de seção — faixa sólida [prancha]

O título de seção no chassi **não é texto solto: é uma faixa sólida de canto
reto**, herdeira do chip de seção do slide [3.5.1 §13.2].

```
Faixa       altura 24 · largura 248 · canto reto · texto 16px Regular, padding 0 16
  atual     fundo green-300 #A5DD7D · texto #1B2023
  demais    fundo --ok-raised #5A6063 · texto --ok-ink
Busca       pode encostar à direita da faixa: mesma altura, canto reto,
            fundo --ok-surface, Search 16 + placeholder, largura 164
Distância   24 até a grade abaixo · 48 entre seções
```

- **Nome da seção = substantivo no plural** (`Recentes`, `Arquivos`,
  `Carteiras`, `Lixeira`).
- **Uma seção atual por tela.**

### 10.7 Grade de cards [prancha]

```
Grade       auto-fill, colunas de 330px, gap 16 · margem lateral 96
Card        330×172 · fundo --ok-surface · canto reto · sem contorno, sem sombra
  título    topo esquerdo, padding 12 16 · 16px --ok-ink · truncado em 1 linha
  prévia    área restante: miniatura real do conteúdo, ou texto de estado
            centralizado em --ok-mut ("Sem prévia", "Arquivo vazio")
  meta      opcional, rodapé esquerdo, .t-meta --ok-mut ("há 2 h · 6 slides")
Hover       fundo --ok-hover · ações do card aparecem no canto superior direito
Selecionado moldura 4px green-500 (§9.2)
Abrir       clique no card · ações (renomear, duplicar, excluir) em botões fantasma
```

- **Miniatura é o próprio conteúdo reduzido**, nunca imagem decorativa.
- Mesma altura para todos os cards da grade, com ou sem prévia.

### 10.8 Botão flutuante [prancha · studio]

```
Posição     canto inferior direito do palco, 24 da borda
Forma       pílula · altura 36 · padding 0 12
Fundo       rgba(27,32,35,.62) · hover rgba(27,32,35,.78) · contorno 1px --ok-surface
Conteúdo    ícone 16 --ok-ink-2 + rótulo 16px --ok-ink-2 ("Ver todos")
Ligado      fundo green-500 · texto #1B2023
```

Um por tela, para **troca de modo de visualização** (rolagem ↔ grade). Não é
atalho para a ação principal.

### 10.9 Menu, gaveta, popover e tooltip

```
Popover     --ok-raised · contorno 1px --ok-line · raio 4 · padding 6 · sombra §9.3
  item      altura 40 · padding 0 12 · ícone 20 --ok-ink-2 + rótulo 16px
            hover rgba(255,255,255,.08) · destrutivo em --ok-neg, por último, após divisória
Gaveta      368 · --ok-surface · da esquerda, sob a barra · véu no palco
  linhas    40 · nome 16px --ok-ink + meta 12px --ok-mut abaixo
            ativa green-300 a 45% · ações da linha só no hover/foco
  seções    eyebrow .t-label --ok-mut, divisória 1px --ok-line entre blocos
Tooltip     #1B2023 · texto #FDFDFD 12px · raio 4 · padding 6 10 · atraso 400ms
```

### 10.10 Modal, confirmação e toast

```
Modal       largura 520 · --ok-surface · contorno 1px --ok-line · raio 4 · padding 24
            título 20px Regular · corpo 16px --ok-ink-2 · rodapé: par de botões (§10.4)
            fecha com Esc, Close e clique no véu (se nada foi digitado)
Toast       canto inferior esquerdo do palco · #1B2023 · texto 16px #FDFDFD · raio 4
            ícone de status 16 · ação opcional em fantasma green-300 ("Desfazer")
            some em 5s; erro fica até fechar
```

**Ação destrutiva** [CLAUDE.md]:

1. **Prefira reversível:** excluir manda para a lixeira (seção `Lixeira` na
   gaveta, com contador) e o toast oferece `Desfazer`.
2. Irreversível: o modal **nomeia o objeto** e **diz que não dá para desfazer**.
3. O botão diz o que faz (`Excluir arquivo`), nunca `OK`.
4. Ação destrutiva não tem atalho de teclado.

### 10.11 Tabela de dados

A tabela vive no palco. No Grafite, ela fica sobre `--ok-surface`. No Papel,
segue a receita do slide. [3.5.1 §12]

```
Header      fundo #1B2023 nos dois temas · texto #FDFDFD 12px Medium UPPERCASE .04em
            altura 40 · vertical-align middle · NENHUMA linha dentro do preto
Linha       40 (32 compacta) · padding 0 12 · texto 14px --ok-ink
            divisória 1px --ok-line em todas, a última inclusive
Hover       fundo --ok-hover
Selecionada fundo --ok-raised (NEUTRO — §4.2)
Total       fundo --ok-raised · Medium · fixa no rodapé
1ª coluna   à esquerda · Medium · fixa na rolagem horizontal
Números     à direita · tabular-nums · mesma quantidade de casas na coluna
Vazio/zero  "—" em --ok-mut
Negativo    "−1.234,56" em --ok-neg
Jurisdição  chip ONSHORE/OFFSHORE (§10.12) ou ícone Brasil/Global 16
```

- **Uma cor de linha por tabela, no máximo, e só com motivo declarável**
  (jurisdição, ativo em foco). No Grafite: onshore `rgba(165,221,125,.14)`,
  offshore `rgba(183,205,255,.14)`. No Papel: `#F1F8DE` / `#EEF2FF`. Tingiu,
  tinge a linha inteira.
- Ordenação no clique do header, com `Down` 12 ao lado do rótulo ativo e
  `aria-sort`.
- Escala no header da coluna (`VALOR (R$ MI)`), não em cada célula.

### 10.12 Chips e status

```
Forma       pílula · altura 24 · padding 0 10 · 12px Medium UPPERCASE .04em
Onshore     fundo #A5DD7D · texto #1B2023
Offshore    fundo #B7CDFF · texto #1B2023
Neutro      fundo --ok-raised · texto --ok-ink
Contador    fundo rgba(255,255,255,.12) · 12px Regular tabular-nums [studio]
```

| Status | Glifo | Fundo (Grafite) | Texto |
|---|---|---|---|
| OK | `Check` green-300 | `rgba(165,221,125,.16)` | `--ok-ink` |
| Atenção | `Alert` yellow-500 | `rgba(255,229,0,.14)` | `--ok-ink` |
| Crítico | `Alert` red-500 | `rgba(238,78,59,.18)` | `--ok-ink` |
| Pendente | `Pending` `--ok-icon` | `--ok-raised` | `--ok-ink` |

**Cor no glifo, texto na tinta, rótulo sempre visível.** Não existe status azul.

### 10.13 KPIs

3 a 5 em faixa, painéis `--ok-surface`, gap 16, **exatamente um** destacado
(fundo green-300 a 45%). Ordem: número `.t-kpi` Light → rótulo `.t-label` →
variação `.t-meta` com sinal. [3.5.1 §13.1]

### 10.14 Estados de área

Como cada estado se parece **quando o app o tem**. Não é obrigação criar os
quatro, nem acrescentar botões a eles.

| Estado | Como aparece |
|---|---|
| **Carregando** | esqueleto em `--ok-surface`, canto reto, pulso de opacidade 1 ↔ .6 em 1,2s. Abaixo de 300ms, nada aparece |
| **Vazio** | ícone 48 em `--ok-icon` · frase 16px `--ok-ink` dizendo o que falta (`Nenhum arquivo`). Botão de ação só se o app já oferece essa ação |
| **Sem resultado** | `Nenhum arquivo com "texto"` · `Limpar busca`, se a busca existir |
| **Erro** | `Alert` 48 em `--ok-neg` · o que falhou, em português · `Tentar de novo`, se a ação existir · detalhe técnico em `<details>` |

---

## 11. Gráficos

Tudo de 3.5.1 §14–§15 vale:

- **Aeonik em todo rótulo.** Configurar a fonte na biblioteca de gráficos.
- **Cantos retos.** Sem grade completa, moldura, sombra, 3D ou gradiente.
- **Cores:** onshore `#A5DD7D`, offshore `#B7CDFF`, referência `#A7A8A8`. No
  Grafite, as séries ficam nos tons 100–400 de cada escala.
- **Rótulo direto na marca** sempre que der. **Legenda só quando resolve
  identidade** (o *teste da mão*), levando nome e nunca valor.
- **Marcador de legenda = casinha cheia** (`Info`, path
  `M36 9L9 36V63H63V36L36 9Z`), 16px na cor da série. Rótulo em `--ok-mut`:
  **cor de série nunca vai no texto**.
- **Tooltip** com série e valor pt-BR; o hover esmaece as outras séries a 40%.
- **`Ver dados`** alterna gráfico ↔ tabela em todo gráfico.
- **Dado editável** (quando o app gera peça): séries, cores **só da paleta** e
  tipo de gráfico editáveis. [CLAUDE.md]

---

## 12. Números e datas [3.5.1 §8, §5.5 E]

- **`Intl.NumberFormat('pt-BR')` e `Intl.DateTimeFormat('pt-BR')`** sempre.
- Vírgula decimal, ponto de milhar · **zero e ausente: `—`**.
- Sinal explícito em variação (`+4,15%` · `−2,30%`, com U+2212).
- **Uma escala por coluna/painel** (`R$`, `mil` ou `mi`), escrita no header.
- `IPCA + 15% a.a.` · `2,5x` · faixa `15,0% - 22,5%`.
- Data `dd/mm/aaaa` · metadado `29 nov 2025` · hora `14:30` · relativo (`há 2 h`)
  só em metadado, com a data absoluta no tooltip.

**Dado sensível:**

- Valores patrimoniais podem ser mascarados (`R$ ••••••`) pelo `Visibility` na
  barra. A preferência fica salva por usuário.
- Nome de cliente **fora de** título de aba do navegador, URL e nome de arquivo
  exportado. [3.5.1]

---

## 13. Escrita na interface [3.5.1 §5.4–5.5]

| Elemento | Forma | Exemplo |
|---|---|---|
| Nome de seção | substantivo plural | `Recentes` · `Arquivos` · `Lixeira` |
| Ferramenta | verbo ou modo | `Guias` · `Zoom` · `Exportar PDF` · `Restaurar edição` |
| Botão | infinitivo (+ objeto) | `Salvar` · `Salvar carteira` · `Limpar filtros` |
| Faixa de estado | fato ` \| ` consequência | `Modo offline \| sem chave de API` |
| Placeholder | `Ex.:` + pedido real | `Ex.: aumente o offshore da sugestão para 25%` |
| Estado vazio | o que falta | `Nenhum arquivo nesta seção` |
| Erro | o que houve + o que fazer | `Não foi possível exportar. Tente de novo em alguns minutos` |
| Toast | particípio | `Arquivo salvo` · `3 arquivos na lixeira` |

- **Sem ponto final** em rótulo, botão, aba, item, toast e frase única.
- **Separador ` | `**, aposto ` — `, hífen só em intervalo numérico. Nunca
  `Modo offline - sem chave`.
- **Sentence case** em tudo; a caixa alta é do CSS.
- **Sem primeira pessoa, sem intimidade** ("Ops", "Oba", "Que pena"), sem
  exclamação, emoji ou reticências.
- **Texto de exemplo nunca chega à tela entregue:** `Lorem ipsum`, `Nome
  arquivo`, `Teste`.
- **Termo é termo:** o mesmo objeto tem o mesmo nome em todos os apps.

---

## 14. Comportamento

### 14.1 Teclado [CLAUDE.md]

```js
function digitando(e){
  const t = e.target;
  return t.isContentEditable || /^(INPUT|SELECT|TEXTAREA)$/.test(t.tagName);
}
document.addEventListener('keydown', e => { if (digitando(e)) return; /* atalhos */ });
```

- Comuns a todos os apps: `/` foca a busca · `Esc` fecha
  popover/gaveta/modal · `Ctrl+Z` desfaz.
- **Atalho é bônus:** toda ação tem botão. Ação destrutiva e liga/desliga de
  modo de edição **não têm atalho**.

### 14.2 Edição no lugar

`Enter` confirma sem criar `<div>`/`<br>`; `Esc` cancela; colar entra como texto
puro em uma linha.

### 14.3 Salvamento

- **Automático por padrão**, refletido na pílula de estado (§10.1).
- Preferências (tema, densidade, filtro, modo de visualização) em `localStorage`
  `oikos:<app>:<recurso>:v1`, com `try/catch`, funcionando sem ele.
- **Dado de negócio nunca vive só no navegador.**
- Cada reversão tem o seu botão: `Restaurar edição` não desfaz ordem nem
  descarte. [CLAUDE.md]

### 14.4 Foco

```css
:focus-visible{ outline:2px solid #6EC26A; outline-offset:2px; }   /* green-500, nos dois temas */
```

Nunca `outline:none` sem substituto.

### 14.5 Movimento

```
120ms   hover, troca de cor, pressionar
150ms   giro do ▾ do menu (180°) [studio]
200ms   abrir gaveta, popover, toast
easing  cubic-bezier(.2,.7,.2,1)
```

Hover não escala, não eleva, não pula. `prefers-reduced-motion` zera transições
acima de 120ms.

### 14.6 Saída para cliente

O que sai do app para o cliente é gerado pelo padrão de slide 3.5.1 (geometria
1920×1080, contracapa, disclaimer literal). **Nada do chassi** (barra,
ferramentas, chips de índice, molduras) aparece na saída.

---

## 15. Acessibilidade — mínimo obrigatório

- Contraste AA conferido com §4.5. `#767A7E` não é cor de texto.
- **Texto sobre verde é `#1B2023`.**
- Foco visível em todo controle; ordem de tabulação = ordem visual.
- Área clicável ≥ 32×32.
- HTML semântico: `<header>`, `<main>`, `<nav>` na gaveta, `<button>` para
  ação, `<table>` com `<th scope>`.
- `lang="pt-BR"`.
- Cor nunca é o único sinal (status com rótulo, negativo com sinal, jurisdição
  com nome).
- Estado de salvamento e toast em `aria-live="polite"`.
- 200% de zoom sem perda de conteúdo.

---

## 16. Antipadrões

1. Outra fonte que não Aeonik; peso 600/700.
2. Tamanhos intermediários no chassi (15, 17, 18px). A hierarquia é pela tinta.
3. `#767A7E` como cor de texto; texto branco sobre verde.
4. Verde de interface dentro da área de dado (seleção de linha verde).
5. Verde para "positivo", azul para "informação".
6. Onshore em azul, offshore em verde.
7. Botão de formulário em pílula, ferramenta em retângulo, card com raio.
8. Estado ativo por sublinhado; qualquer linha colorida abaixo de texto.
9. Sombra em ferramenta ou card. A profundidade é o degrau de cinza.
10. Barra de ferramentas com fundo atrás das pílulas.
11. Mais de uma ação primária por formulário ou modal.
12. Fotografia, ilustração, avatar com foto, miniatura decorativa, emoji.
13. Logo horizontal; lockup de casinha + texto; nome do app colado ao `OIKOS`
    na barra (`OIKOS STUDIO`, `OIKOS PAINEL`); `OIKOS` maior que 16px ou em
    peso/cor de marca.
14. Glifo genérico de UI no lugar do ícone da biblioteca.
15. Hífen como separador; `Lorem ipsum` na tela entregue.
16. Escala global da interface por largura de janela (`--k`).
17. Hex, `font-size` ou raio literal em `app.css`.
18. `0`, `N/A`, `-` ou vazio no lugar de `—`.
19. Atalho que dispara enquanto se digita; `OK` em confirmação.
20. Tela do app enviada ao cliente como material.

---

## 17. Componente novo — como entra

> ⚠️ **Só quando o usuário pedir.** Componente novo nunca nasce por iniciativa
> própria (ver o aviso no topo). O passo zero é: o usuário pediu essa peça?
> Se não, não se cria.

1. Confirmar que nenhum componente de §10 resolve, nem combinado.
2. Escolher a **forma pelo papel** (§9.1) e o **degrau de verde pelo papel**
   (§4.2). Se nenhum papel serve, o componente está fora do padrão.
3. Desenhar só com tokens. Precisou de token novo? Rever o componente.
4. Descrever aqui e no Apêndice A. Só então implementar.

---

## 18. Checklist antes de liberar

- [ ] Feito só o que o usuário pediu; nada criado, removido ou trocado além disso
- [ ] Interface existente preservada: telas, layout, navegação, componentes e
      fluxos como estavam; nada redesenhado para imitar o exemplo (§0)
- [ ] Diferenças notadas entre o app e o padrão foram **mencionadas** ao
      usuário, não aplicadas por conta própria
- [ ] `oikos-ui.css` sem edição; `app.css` sem hex, `font-size` ou raio literal
- [ ] Aeonik carregando; só 300/400/500
- [ ] Disco da marca (green-200 + casinha cheia) + só `OIKOS` em 16px, sem nome do app; barra `#1B2023`, se houver barra
- [ ] Um tema por tela (Grafite ou Papel)
- [ ] Chassi em 16px; hierarquia por tinta; nada de `#767A7E` em texto
- [ ] Verde só nos papéis de §4.2; texto sobre verde em `#1B2023`
- [ ] Seleção dentro de tabela/gráfico neutra
- [ ] Formas pelo papel: reto (estrutura) · 4 (controle) · pílula (ferramenta)
- [ ] Ícones só da biblioteca, pelo mapa de §7.1
- [ ] Nenhuma foto, ilustração ou logo horizontal
- [ ] Onshore verde / offshore azul; positivo/negativo por sinal
- [ ] Tabela: header escuro contínuo, divisórias iguais, `—` no vazio
- [ ] Estados de área que o app já tem seguem §10.14 (nenhum criado sem pedido)
- [ ] Nenhuma barra de ferramentas, ação ou botão (`+ Novo`, `Importar`,
      `Exportar`…) acrescentado por constar no documento
- [ ] Números e datas por `Intl` pt-BR
- [ ] Contraste AA; foco green-500 visível; 200% de zoom
- [ ] Atalhos ignoram campos; destrutiva confirmada e sem atalho
- [ ] Conferido em 1280, 1440 e 1920
- [ ] Nenhum texto de exemplo na tela

---

## 19. Em aberto

| # | Ponto | O que falta | Enquanto isso |
|---|---|---|---|
| 1 | Licença da Aeonik | confirmar se a EULA desktop cobre servir a fonte num app interno | só em app interno, nunca em domínio público |
| 2 | `Filter`, `More`, `Settings` | versão vetorial | PNG no tamanho nativo; nunca ícone externo |
| 3 | `red-700/300/100` | HEX corretos | não usar |
| 4 | Oikos Studio | alinhar texto de apoio (`#C9CBCC`), texto sobre verde (`#1B2023`), escala fixa no lugar de `--k` e ícones da biblioteca | Studio segue até a revisão |
| 5 | Tema Papel | validar com o design numa tela real | usar só em tela de tabela/cadastro longo |

---

## Apêndice A — `oikos-ui.css`

Copiar inteiro para `static/oikos-ui.css`. **Não editar por app.**

```css
/* =========================================================================
   oikos-ui.css — Padrão de UI Oikos v1. NÃO EDITAR POR APP.
   Medidas de tela = prancha 2382×1110 × 0,8, na grade de 4px.
   ========================================================================= */

@font-face{font-family:"Aeonik";font-weight:300;font-style:normal;font-display:block;
  src:local("Aeonik Light"),local("Aeonik-Light"),
      url("/branding/FONTE/Aeonik-Full-Family-Desktop/Aeonik-Light.otf") format("opentype")}
@font-face{font-family:"Aeonik";font-weight:400;font-style:normal;font-display:block;
  src:local("Aeonik Regular"),local("Aeonik-Regular"),local("Aeonik"),
      url("/branding/FONTE/Aeonik-Full-Family-Desktop/Aeonik-Regular.otf") format("opentype")}
@font-face{font-family:"Aeonik";font-weight:500;font-style:normal;font-display:block;
  src:local("Aeonik Medium"),local("Aeonik-Medium"),
      url("/branding/FONTE/Aeonik-Full-Family-Desktop/Aeonik-Medium.otf") format("opentype")}

/* ---- Tema Grafite (padrão) ---- */
:root{
  --ok-font:"Aeonik","Helvetica Neue",Arial,sans-serif;

  --ok-bar:#1B2023; --ok-stage:#242C2F; --ok-surface:#3F4649; --ok-raised:#5A6063;
  --ok-line:#686D71; --ok-hover:#4B5356; --ok-bar-sep:#3A4145;
  --ok-ink:#FDFDFD; --ok-ink-2:#ECECEC; --ok-mut:#C9CBCC; --ok-icon:#919398;
  --ok-ghost:rgba(255,255,255,.08);

  /* verde de interface — papéis fixos (§4.2) */
  --ok-brand:#B7E583;                    /* green-200: disco */
  --ok-section:#A5DD7D;                  /* green-300: seção atual */
  --ok-sel:rgba(165,221,125,.45);        /* green-300 45%: selecionado */
  --ok-primary:#92D476;                  /* green-400: ação primária */
  --ok-on:#6EC26A;                       /* green-500: ligado / ativo / foco */
  --ok-on-ink:#1B2023;                   /* texto sobre qualquer verde */

  /* dado */
  --ok-onshore:#A5DD7D; --ok-offshore:#B7CDFF; --ok-ref:#A7A8A8;
  --ok-neg:#EE4E3B; --ok-warn:#FFE500;
  --ok-row-on:rgba(165,221,125,.14); --ok-row-off:rgba(183,205,255,.14);
  --ok-data-sel:#5A6063;                 /* seleção NEUTRA na área de dado */

  --g900:#008D44; --g800:#259F51; --g700:#49B05D; --g600:#5CB964; --g500:#6EC26A;
  --g400:#92D476; --g300:#A5DD7D; --g200:#B7E583; --g100:#DBF68F; --g50:#E6F9B4;
  --b900:#182662; --b800:#213282; --b700:#273A98; --b600:#384BA4; --b500:#495BAF;
  --b400:#586BBB; --b300:#677AC6; --b200:#8FA4E3; --b100:#B7CDFF; --b50:#D6E2FF;

  --r-0:0; --r-1:4px; --r-pill:999px;
  --sh-float:0 14px 40px rgba(0,0,0,.45);
  --sh-modal:0 24px 70px rgba(0,0,0,.5);
  --veil:rgba(27,32,35,.62);

  --bar-h:60px; --drawer-w:368px;
  --tool-h:36px; --ctl-h:40px; --row-h:40px;
  --card-w:330px; --card-h:172px; --grid-x:96px;

  --ic-sm:16px; --ic-md:20px; --ic-lg:24px; --ic-xl:48px;
  --dur-1:120ms; --dur-2:200ms; --ease:cubic-bezier(.2,.7,.2,1);
}
[data-density="compact"]{ --row-h:32px; }

/* ---- Tema Papel (variante clara) ---- */
[data-theme="paper"]{
  --ok-stage:#FDFDFD; --ok-surface:#F4F4F4; --ok-raised:#ECECEC;
  --ok-line:#D7D8D5; --ok-hover:#ECECEC;
  --ok-ink:#1B2023; --ok-ink-2:#3F4649; --ok-mut:#686D71; --ok-icon:#686D71;
  --ok-ghost:rgba(27,32,35,.06);
  --ok-neg:#B22B20; --ok-warn:#D9C300;
  --ok-row-on:#F1F8DE; --ok-row-off:#EEF2FF; --ok-data-sel:#ECECEC;
  --sh-float:0 8px 24px rgba(27,32,35,.12);
  --sh-modal:0 24px 64px rgba(27,32,35,.24);
}

/* ---- Base ---- */
*,*::before,*::after{ box-sizing:border-box; font-synthesis:none; }
[hidden]{ display:none !important; }
html,body{ margin:0; height:100%; }
body{
  font-family:var(--ok-font); font-size:16px; font-weight:400; line-height:1.4;
  color:var(--ok-ink); background:var(--ok-stage);
  font-variant-numeric:tabular-nums; font-kerning:normal; letter-spacing:normal;
  hyphens:none; text-align:left; -webkit-font-smoothing:antialiased;
  display:flex; flex-direction:column; overflow:hidden;
}
b,strong{ font-weight:500; }
:focus-visible{ outline:2px solid var(--ok-on); outline-offset:2px; }
*{ scrollbar-width:thin; scrollbar-color:var(--ok-raised) transparent; }
@media (prefers-reduced-motion:reduce){ *{ transition-duration:0s !important; animation:none !important; } }

/* ---- Tipografia da área de dado ---- */
.t-page   { font-size:28px; font-weight:300; line-height:1.15; text-transform:uppercase;
            white-space:nowrap; overflow:hidden; text-overflow:ellipsis; margin:0; }
.t-page .r{ font-weight:400; }
.t-section{ font-size:20px; font-weight:400; line-height:1.25; margin:0; }
.t-ui     { font-size:16px; }
.t-cell   { font-size:14px; }
.t-label  { font-size:12px; font-weight:500; line-height:1.3; text-transform:uppercase;
            letter-spacing:.06em; color:var(--ok-mut); }
.t-meta   { font-size:12px; line-height:1.4; color:var(--ok-mut); }
.t-kpi    { font-size:32px; font-weight:300; line-height:1.1; }
.neg      { color:var(--ok-neg); }
.nil      { color:var(--ok-mut); }

/* ---- Ícone ---- */
.ic{ width:var(--ic-md); height:var(--ic-md); flex:none; display:block; fill:currentColor; }
.ic.sm{ width:var(--ic-sm); height:var(--ic-sm); } .ic.lg{ width:var(--ic-lg); height:var(--ic-lg); }

/* ---- Barra superior ---- */
.bar{ height:var(--bar-h); flex:none; display:flex; align-items:center; gap:16px;
      padding:0 16px; background:var(--ok-bar); color:#FDFDFD; }
.bar .grow{ flex:1; }
.bar .sep{ width:1px; height:20px; background:var(--ok-bar-sep); }
.bar .ctx{ color:#ECECEC; white-space:nowrap; overflow:hidden; text-overflow:ellipsis; min-width:0; }
.bar .state{ color:#C9CBCC; white-space:nowrap; }
.bar .state.busy{ color:var(--ok-on); } .bar .state.warn{ color:#FFE500; }
.brand{ display:flex; align-items:center; gap:8px; padding:4px 6px 4px 0; margin-left:-4px;
        background:none; border:0; border-radius:var(--r-1); color:#FDFDFD;
        font:inherit; cursor:pointer; }
.brand:hover{ background:rgba(255,255,255,.06); }
.brand-disc{ width:22px; height:22px; display:block; }
.brand-name{ font-size:16px; line-height:1; text-transform:uppercase; white-space:nowrap; }
.brand .ic{ color:#919398; transition:transform 150ms var(--ease); }
.brand[aria-expanded="true"] .ic{ transform:rotate(180deg); }

/* ---- Corpo: palco ---- */
.work{ flex:1; min-height:0; display:flex; }
.stage{ position:relative; flex:1; min-width:0; overflow:auto; background:var(--ok-stage); padding:32px; }
.stage.grid-view{ padding:32px var(--grid-x) 64px; }

/* ---- Ferramentas (pílulas flutuantes) ---- */
.tools{ position:sticky; top:0; z-index:30; display:flex; gap:16px; padding:0 0 24px 8px;
        pointer-events:none; }
.tool{ pointer-events:auto; display:inline-flex; align-items:center; gap:8px;
       height:var(--tool-h); padding:0 16px; border:0; border-radius:var(--r-pill);
       background:var(--ok-surface); color:var(--ok-ink); font:inherit; white-space:nowrap;
       cursor:pointer; transition:background var(--dur-1) var(--ease); }
.tool:hover{ background:var(--ok-hover); }
.tool[aria-pressed="true"]{ background:var(--ok-on); color:var(--ok-on-ink); }
.tool:disabled{ opacity:.45; cursor:default; background:var(--ok-surface); }

/* ---- Campos ---- */
.field{ display:flex; flex-direction:column; gap:6px; margin-bottom:20px; }
.field > span{ font-size:12px; font-weight:500; text-transform:uppercase; letter-spacing:.06em; color:var(--ok-mut); }
.input{ width:100%; height:var(--ctl-h); padding:0 12px; font:inherit;
        background:var(--ok-raised); color:var(--ok-ink-2);
        border:1px solid var(--ok-line); border-radius:var(--r-1); }
textarea.input{ height:auto; min-height:96px; max-height:240px; padding:12px; resize:vertical; line-height:1.5; }
.input::placeholder{ color:var(--ok-mut); }
.input:focus{ outline:none; border-color:var(--ok-on); }
.input.num{ text-align:right; }
.field.error .input{ border-color:var(--ok-neg); }
.field .help{ font-size:12px; color:var(--ok-mut); }
.field.error .help{ color:var(--ok-neg); }

/* ---- Botões de formulário (retângulo 4) ---- */
.btn{ display:inline-flex; align-items:center; justify-content:center; gap:8px;
      height:var(--ctl-h); padding:0 16px; font:inherit; white-space:nowrap; cursor:pointer;
      border:1px solid var(--ok-line); border-radius:var(--r-1);
      background:var(--ok-stage); color:var(--ok-mut);
      transition:background var(--dur-1) var(--ease); }
.btn:hover{ background:var(--ok-hover); }
.btn.primary{ background:var(--ok-primary); color:var(--ok-on-ink); border-color:transparent; }
.btn.primary:hover{ background:var(--ok-on); }
.btn.ghost{ background:transparent; border-color:transparent; color:var(--ok-ink); }
.btn.ghost:hover{ background:var(--ok-ghost); }
.btn.danger{ background:var(--ok-neg); color:#FDFDFD; border-color:transparent; }
.btn.sm{ height:32px; padding:0 12px; }
.btn.icon{ width:var(--ctl-h); padding:0; }
.btn:disabled{ opacity:.45; cursor:default; }

/* ---- Item no palco: índice + moldura ---- */
.item{ display:flex; flex-direction:column; gap:12px; }
.item-head{ display:flex; align-items:center; }
.idx{ display:flex; align-items:center; justify-content:center; width:40px; height:28px;
      border-radius:var(--r-1); background:rgba(145,147,152,.22); color:var(--ok-icon); }
.item.is-active .idx{ background:var(--ok-sel); color:var(--ok-ink); }
.item.is-out .idx{ background:rgba(145,147,152,.14); color:#6E757B; }
.item.is-out .frame{ opacity:.4; }
.item .viz{ margin-left:auto; color:var(--ok-icon); background:none; border:0; padding:0; cursor:pointer; }
.item .viz:hover{ color:var(--ok-ink); }
.frame{ position:relative; }
.item.is-active .frame::after{ content:""; position:absolute; inset:2px; pointer-events:none;
      box-shadow:0 0 0 4px var(--ok-on); }

/* ---- Rótulo de seção (faixa) + busca colada ---- */
.section{ display:flex; align-items:stretch; height:24px; margin:0 0 24px; }
.section + .grid{ margin-bottom:48px; }
.section-label{ display:flex; align-items:center; width:248px; padding:0 16px;
                background:var(--ok-raised); color:var(--ok-ink); }
.section-label.current{ background:var(--ok-section); color:var(--ok-on-ink); }
.section-search{ display:flex; align-items:center; gap:8px; width:164px; padding:0 12px;
                 background:var(--ok-surface); color:var(--ok-ink-2); }
.section-search input{ flex:1; min-width:0; border:0; background:none; color:inherit; font:inherit; }
.section-search input::placeholder{ color:var(--ok-mut); }
.section-search input:focus{ outline:none; }
.section-search:focus-within{ outline:2px solid var(--ok-on); outline-offset:0; }

/* ---- Grade de cards ---- */
.grid{ display:grid; grid-template-columns:repeat(auto-fill, var(--card-w)); gap:16px; }
.card{ position:relative; width:var(--card-w); height:var(--card-h); display:flex; flex-direction:column;
       background:var(--ok-surface); border-radius:0; cursor:pointer; }
.card:hover{ background:var(--ok-hover); }
.card-title{ padding:12px 16px 0; white-space:nowrap; overflow:hidden; text-overflow:ellipsis; }
.card-preview{ flex:1; display:flex; align-items:center; justify-content:center; color:var(--ok-mut); overflow:hidden; }
.card-meta{ padding:0 16px 12px; font-size:12px; color:var(--ok-mut); }
.card .acts{ position:absolute; top:8px; right:8px; display:flex; gap:2px; opacity:0; }
.card:hover .acts, .card:focus-within .acts{ opacity:1; }
.card[aria-selected="true"]::after{ content:""; position:absolute; inset:2px; pointer-events:none;
       box-shadow:0 0 0 4px var(--ok-on); }

/* ---- Botão flutuante ---- */
.fab{ position:fixed; z-index:40; right:24px; bottom:24px;
      display:flex; align-items:center; gap:8px; height:var(--tool-h); padding:0 12px;
      border:1px solid var(--ok-surface); border-radius:var(--r-pill);
      background:rgba(27,32,35,.62); color:var(--ok-ink-2); font:inherit; cursor:pointer; }
.fab:hover{ background:rgba(27,32,35,.78); }
.fab[aria-pressed="true"]{ background:var(--ok-on); color:var(--ok-on-ink); }

/* ---- Gaveta, popover, tooltip ---- */
.veil{ position:fixed; inset:var(--bar-h) 0 0 0; z-index:50; background:var(--veil); }
.drawer{ position:fixed; z-index:51; top:var(--bar-h); left:0; bottom:0; width:var(--drawer-w);
         display:flex; flex-direction:column; background:var(--ok-surface); box-shadow:var(--sh-float); }
.drawer-body{ flex:1; overflow-y:auto; padding:16px; }
.row{ display:flex; align-items:center; gap:10px; min-height:40px; padding:8px 12px;
      border-radius:var(--r-1); cursor:pointer; }
.row:hover, .row:focus-visible{ background:var(--ok-raised); }
.row[aria-current="true"]{ background:var(--ok-sel); }
.row .main{ flex:1; min-width:0; display:flex; flex-direction:column; gap:2px; }
.row .name{ white-space:nowrap; overflow:hidden; text-overflow:ellipsis; }
.row .meta{ font-size:12px; color:var(--ok-mut); }
.row .acts{ display:flex; gap:2px; opacity:0; }
.row:hover .acts, .row:focus-within .acts{ opacity:1; }
.rule{ border:0; border-top:1px solid var(--ok-line); margin:16px 12px; }
.count{ min-width:24px; padding:0 7px; border-radius:var(--r-pill); text-align:center;
        background:rgba(255,255,255,.12); font-size:12px; }
.pop{ position:absolute; z-index:60; min-width:264px; padding:6px;
      background:var(--ok-raised); border:1px solid var(--ok-line);
      border-radius:var(--r-1); box-shadow:var(--sh-float); }
.pop-item{ display:flex; align-items:center; gap:12px; width:100%; height:40px; padding:0 12px;
           border:0; border-radius:var(--r-1); background:none; color:var(--ok-ink);
           font:inherit; text-align:left; cursor:pointer; }
.pop-item .ic{ color:var(--ok-ink-2); }
.pop-item:hover{ background:var(--ok-ghost); }
.pop-item.danger{ color:var(--ok-neg); }
.tip{ position:absolute; z-index:80; padding:6px 10px; border-radius:var(--r-1);
      background:#1B2023; color:#FDFDFD; font-size:12px; pointer-events:none; }

/* ---- Modal e toast ---- */
.modal-veil{ position:fixed; inset:0; z-index:70; background:var(--veil);
             display:flex; align-items:center; justify-content:center; padding:24px; }
.modal{ width:min(100%,520px); max-height:100%; overflow:auto; padding:24px;
        background:var(--ok-surface); border:1px solid var(--ok-line);
        border-radius:var(--r-1); box-shadow:var(--sh-modal); }
.modal h2{ margin:0 0 16px; font-size:20px; font-weight:400; }
.modal p{ margin:0 0 24px; color:var(--ok-ink-2); line-height:1.5; }
.modal .acts{ display:flex; gap:12px; } .modal .acts .btn{ flex:1; }
.toast{ position:fixed; left:24px; bottom:24px; z-index:90; display:flex; align-items:center; gap:12px;
        padding:12px 16px; background:#1B2023; color:#FDFDFD; border-radius:var(--r-1); box-shadow:var(--sh-float); }
.toast .btn.ghost{ color:var(--ok-section); }

/* ---- Tabela ---- */
.tbl-wrap{ overflow:auto; max-width:100%; background:var(--ok-surface); }
.tbl{ width:100%; border-collapse:collapse; border-spacing:0; font-size:14px; }
.tbl thead, .tbl thead th{ background:#1B2023; color:#FDFDFD; }
.tbl thead th{ height:40px; padding:0 12px; vertical-align:middle; border:0; text-align:left;
               font-size:12px; font-weight:500; text-transform:uppercase; letter-spacing:.04em;
               white-space:nowrap; position:sticky; top:0; z-index:1; }
.tbl th.num, .tbl td.num{ text-align:right; }
.tbl tbody td{ height:var(--row-h); padding:0 12px; border-bottom:1px solid var(--ok-line);
               color:var(--ok-ink); white-space:nowrap; overflow:hidden; text-overflow:ellipsis; max-width:320px; }
.tbl tbody td:first-child{ font-weight:500; }
.tbl tbody tr:hover td{ background:var(--ok-hover); }
.tbl tbody tr[aria-selected="true"] td{ background:var(--ok-data-sel); }
.tbl tr.on td{ background:var(--ok-row-on); }
.tbl tr.off td{ background:var(--ok-row-off); }
.tbl tr.tot td, .tbl tr.grp td{ background:var(--ok-raised); font-weight:500; }

/* ---- Chips e status ---- */
.chip, .status{ display:inline-flex; align-items:center; gap:6px; height:24px; padding:0 10px;
                border-radius:var(--r-pill); font-size:12px; font-weight:500;
                text-transform:uppercase; letter-spacing:.04em; }
.chip{ background:var(--ok-raised); color:var(--ok-ink); }
.chip.on{ background:#A5DD7D; color:#1B2023; }
.chip.off{ background:#B7CDFF; color:#1B2023; }
.status{ color:var(--ok-ink); } .status .ic{ width:14px; height:14px; }
.status.ok  { background:rgba(165,221,125,.16); } .status.ok .ic  { color:#A5DD7D; }
.status.warn{ background:rgba(255,229,0,.14); }   .status.warn .ic{ color:#FFE500; }
.status.crit{ background:rgba(238,78,59,.18); }   .status.crit .ic{ color:#EE4E3B; }
.status.pend{ background:var(--ok-raised); }     .status.pend .ic{ color:var(--ok-icon); }

/* ---- KPI ---- */
.kpis{ display:grid; grid-template-columns:repeat(auto-fit,minmax(200px,1fr)); gap:16px; }
.kpi{ background:var(--ok-surface); padding:20px; }
.kpi.acc{ background:var(--ok-sel); }

/* ---- Estados ---- */
.empty{ display:flex; flex-direction:column; align-items:center; gap:12px; padding:64px 24px;
        text-align:center; color:var(--ok-ink); }
.empty .ic{ width:var(--ic-xl); height:var(--ic-xl); color:var(--ok-icon); }
.skel{ background:var(--ok-surface); animation:ok-pulse 1.2s var(--ease) infinite alternate; }
@keyframes ok-pulse{ from{opacity:1} to{opacity:.6} }

/* ---- Avatar de letra ---- */
.avatar{ width:28px; height:28px; border-radius:50%; flex:none; display:inline-flex;
         align-items:center; justify-content:center; background:#ECECEC; color:#1B2023;
         font-size:12px; font-weight:500; }

/* ---- Legenda de gráfico ---- */
.legend{ display:flex; flex-wrap:wrap; justify-content:center; align-items:center;
         column-gap:32px; row-gap:12px; font-size:14px; color:var(--ok-mut); }
.legend span{ display:inline-flex; align-items:center; gap:8px; white-space:nowrap; }
.legend svg{ width:16px; height:16px; }
```

---

## Apêndice B — exemplo de tela (opcional)

**Isto é exemplo, não modelo obrigatório (§0).** Serve para ver as classes do
Apêndice A funcionando juntas. Se o app já existe, ou se o pedido pede outra
estrutura, **não se parte daqui**: aplicam-se as classes e os tokens à
estrutura real. Use este esqueleto só quando não houver nada em mãos e ele de
fato servir ao que a ferramenta faz. Mesmo assim, ajuste regiões, peças e
textos ao pedido.

```html
<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>«Tela» | Oikos «Nome»</title>
  <link rel="icon" type="image/svg+xml"
        href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 27 27'%3E%3Ccircle cx='13.5' cy='13.5' r='13.5' fill='%23B7E583'/%3E%3Cpath d='M13.5 6.33L7.17 12.66V18.98H19.83V12.66Z' fill='%231B2023'/%3E%3C/svg%3E">
  <link rel="stylesheet" href="/static/oikos-ui.css">
  <link rel="stylesheet" href="/static/app.css">
</head>
<body>

  <header class="bar">
    <button class="brand" aria-haspopup="menu" aria-expanded="false">
      <svg class="brand-disc" viewBox="0 0 27 27" aria-hidden="true">
        <circle cx="13.5" cy="13.5" r="13.5" fill="#B7E583"/>
        <path d="M13.5 6.33L7.17 12.66V18.98H19.83V12.66Z" fill="#1B2023"/>
      </svg>
      <span class="brand-name">Oikos</span>
      <svg class="ic sm"><use href="/static/icons.svg#ic-drop-down-arrow"/></svg>
    </button>
    <span class="sep" aria-hidden="true"></span>
    <span class="ctx">«contexto»</span>
    <span class="grow"></span>
    <span class="state" aria-live="polite">Salvo</span>
  </header>

  <div class="work">
    <main class="stage grid-view">
      <!-- Ferramentas: OPCIONAL. Só se o app já tem ou o usuário pediu (§10.2). -->
      <div class="tools" role="toolbar" aria-label="Ferramentas">
        <button class="tool" aria-pressed="false">
          <svg class="ic"><use href="/static/icons.svg#ic-search"/></svg>«Ferramenta»
        </button>
        <button class="tool">
          <svg class="ic"><use href="/static/icons.svg#ic-file-download"/></svg>«Exportar PDF»
        </button>
      </div>

      <div class="section">
        <span class="section-label current">Recentes</span>
      </div>
      <div class="grid">
        <article class="card" tabindex="0">
          <div class="card-title">«nome-do-arquivo»</div>
          <div class="card-preview">Sem prévia</div>
          <div class="card-meta">«há 2 h»</div>
        </article>
      </div>

      <div class="section">
        <span class="section-label">Arquivos</span>
        <label class="section-search">
          <svg class="ic sm" aria-hidden="true"><use href="/static/icons.svg#ic-search"/></svg>
          <input type="search" placeholder="Nome" aria-label="Buscar arquivo">
        </label>
      </div>
      <div class="grid"><!-- cards --></div>

      <button class="fab" aria-pressed="false">
        <svg class="ic sm"><use href="/static/icons.svg#ic-apresentacao"/></svg>Ver todos
      </button>
    </main>
  </div>

</body>
</html>
```

---

*v1 — outubro de 2026. Base: `PADRAO-SLIDE-OIKOS_v3.5.1.md`, `CLAUDE.md`,
`Branding/`, pranchas de UI do Oikos Studio (2382×1110) e
`oikos-studio/static/app.css`.*
