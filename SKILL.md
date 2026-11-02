---
name: efeitos
description: Adiciona qualquer um de 45 efeitos de vídeo num vídeo de pessoa falando pra câmera (órbita, holofote, widgets de vidro, timeline, checklist, parede de manchetes, caixa de comentário, leque de celulares, gráfico de vidro líquido, match cut, botões do iPhone, letreiro de LED, zoom por cima do ombro, notificações do iMessage, grade do perfil e mais). Os efeitos seguem o rosto e podem ficar atrás da cabeça. Use quando a pessoa digitar /efeitos ou /effects, citar um dos efeitos, ou pedir efeito, zoom, cor, figurinha ou animação no vídeo.
---

# Efeitos: 45 efeitos de vídeo para o Claude

Quem usa normalmente não é técnico. Responda curto, em português do Brasil, simpático, faça o trabalho pela pessoa e nunca peça pra ela rodar comando.

Todos os caminhos abaixo são relativos à pasta desta skill (a pasta onde está este SKILL.md). Use o caminho absoluto nos comandos.

## 1. Primeira vez: instalar (uma vez só)
Rode `bash scripts/setup.sh`. Aparece `READY` quando terminar (a primeira vez leva de 1 a 3 minutos).
- `NEED_FFMPEG`: instale pra pessoa. No Mac: `brew install ffmpeg` (se não tiver `brew`, peça pra instalar o Homebrew em brew.sh). No Windows: `winget install ffmpeg`.
- `NEED_PYTHON`: instale o Python 3.12 (Mac: `brew install python@3.12`, Windows: `winget install Python.Python.3.12`) e rode o setup de novo.
- No Windows, o Python fica em `.venv\Scripts\python.exe` em vez de `.venv/bin/python`.

## 2. Pegar o vídeo e o efeito
- Vídeo: a pessoa arrasta o arquivo pro chat ou passa o caminho. Vídeo vertical de celular funciona melhor.
- Efeito: vem de `/efeitos <nome>` ou da descrição dela. Relacione as palavras dela com a tabela abaixo. Na dúvida, mostre a lista.

## 3. Achar o tempo certo
- Se ela disser "na palavra X" ou "quando eu falo ...", rode `.venv/bin/python scripts/words.py <vídeo>` e use esses tempos.
- Se não disser o tempo, aplique no vídeo inteiro ou pergunte qual parte (uma pergunta curta).
- Janelas curtas ficam melhores: de 1,5 a 4 segundos por efeito.
- Textos que aparecem no vídeo devem ficar em português, a menos que a pessoa peça outro idioma.

## 4. Planejar, conferir, renderizar
1. Escreva o plano ao lado do vídeo como `<nome-do-video>_effects.json`:
   ```json
   {"effects": [
     {"fx": "orbit", "start": 3.2, "end": 6.0},
     {"fx": "backdrop-word", "start": 14.0, "end": 16.3, "text": "CLAUDE"}
   ]}
   ```
2. Confira os frames antes (rápido): `.venv/bin/python scripts/fx.py --plan <plano.json> <vídeo> <pasta>/check.png --still 4.5,15.2`, usando o meio de cada efeito. Olhe os PNGs você mesmo. Corrija texto, tempo ou opções se algo estiver errado (cobrindo o rosto, cortado na borda, ilegível).
3. Renderize: `.venv/bin/python scripts/fx.py --plan <plano.json> <vídeo> <nome-do-video>_effects.mp4`. O áudio original fica igual. Sai em 1080p por padrão; use `--width 2160` pra 4K (mais lento).
4. Diga onde está o arquivo. Lembre em uma linha de assistir antes de postar: a skill faz o rascunho, a pessoa aprova.

Um efeito só não precisa de plano: `.venv/bin/python scripts/fx.py orbit <vídeo> <saida.mp4> --start 3 --end 6 --text "..." --opt key=value`.

## Os 45 efeitos
| # | nome `fx` | O que faz | Opções (todas opcionais) |
|---|---|---|---|
| 1 | `noise` | Reels se empilham atrás da sua cabeça, um a cada quarto de segundo | `images` (pasta de prints ou clipes), `size` |
| 2 | `lineup` | Cartões numerados abrem em arco acima da sua cabeça | `text` (nomes separados por `\|`) |
| 3 | `locked-on` | Cantoneiras travam no seu rosto e a câmera te segue | `zoom` (padrão 1.35), `text` (etiqueta) |
| 4 | `orbit` | Seus reels giram em volta da sua cabeça: na frente embaixo, atrás em cima | `images`, `count`, `speed`, `size` |
| 5 | `lean-in` | Um zoom rápido numa palavra | `zoom` (padrão 1.45, máx. 2), `speed` |
| 6 | `backdrop-word` | Uma palavra gigante cai atrás de você | `text`, `color` (hex), `font` (`bold` ou `serif`) |
| 7 | `spotlight` | Apaga as luzes e deixa só você iluminado | `text` (palavra brilhando atrás), `color`, `push` |
| 8 | `the-bill` | Imprime suas instruções como uma notinha na parede acima da cabeça | `text` (linhas com `\|`) |
| 9 | `moody` | Uma correção de cor com clima | `grade` (`moody`, `bw`, `warm`, `cool`, `pop`) |
| 10 | `swipe` | Um slider de antes e depois passa por você | `grade` (o visual do "depois") |
| 11 | `todo` | Um checklist ao lado da sua cabeça vai sendo marcado enquanto você fala | `text` (itens com `\|`), `ticks` (segundos com `\|`), `title` |
| 12 | `comment-box` | Uma caixa de comentário do Instagram digita uma palavra e publica | `text` (padrão EFEITOS) |
| 13 | `tap` | Um botão Seguir aparece e vira Seguindo | `at` (segundo da virada), `x`, `y` (0 a 1), `color` |
| 14 | `pause-point` | Congela a imagem e aponta pra você com uma seta desenhada | `text` (legenda), `color`, `label_x` |
| 15 | `uninstall` | Uma barra de desinstalação com glitch quebra a imagem | `text` |
| 16 | `reel-frame` | Seu vídeo encolhe num card de reel do Instagram | `text` (perfil) |
| 17 | `shortcut-rain` | Teclas do teclado chovem atrás de você | `text` (teclas com `\|`), `count` |
| 18 | `reject-stamp` | Um carimbo vermelho bate na tela | `text`, `color`, `angle`, `y` |
| 19 | `countdown-flip` | Um relógio de 3, 2, 1 acima da sua cabeça | `from` |
| 20 | `rabbit-hole` | A imagem vira um túnel girando pra dentro dela mesma | `ratio`, `speed`, `spin` |
| 21 | `cover-star` | Você vira capa de revista, com o título atrás da cabeça | `text` (título), `lines` (com `\|`), `issue`, `color` |
| 22 | `scribble` | Rabiscos de marcador se desenham em volta de você | `text` (legenda), `color` |
| 23 | `glass-widgets` | Widgets de vidro fosco flutuam em volta da cabeça, com a etiqueta Editado pelo Claude | `text` (número grande), `name`, `handle`, `look` (`simple` pra versão com 3 widgets) |
| 24 | `red-collage` | Você em preto e branco, palavra vermelha gigante atrás, três linhas entram | `text` (palavra vermelha), `lines` (com `\|`), `tag` |
| 25 | `split-headline` | Um card de manchete desce e te empurra pra metade de baixo | `text` (linhas com `\|`), `hl` (palavra destacada), `pill` |
| 26 | `pastel-word` | Sala lilás, palavra gigante atrás, um card de perfil ganha um seguidor | `text`, `name`, `handle` |
| 27 | `check-pills` | Sala de papel quadriculado, reels atrás, um cursor clica em botões azuis | `text` (botões com `\|`), `images` |
| 28 | `timeline` | Cor de filme vermelho escuro, com timeline de edição, REC e cursor brilhando | `text` (título), `sub`, `tc` |
| 29 | `headline-box` | Um zoom com manchete de duas linhas, a segunda numa caixa branca | `text` (linhas com `\|`), `zoom` |
| 30 | `profile-wall` | A grade dos seus reels enche a parede atrás enquanto um contador sobe | `images`, `count`, `label` |
| 31 | `tier-list` | Um tier list aparece e o Claude voa pro tier S | `title`, `item`, `others` |
| 32 | `broll-split` | B-roll em cima com etiqueta de preço, você embaixo | `images`, `text` (etiqueta) |
| 33 | `phone-fan` | Seus reels abrem como um leque de celulares embaixo de uma manchete | `images`, `text` (linhas com `\|`) |
| 34 | `dot-reveal` | Sua imagem se monta com pontinhos brilhantes e depois aparece inteira | `color`, `cell` |
| 35 | `headline-wall` | Suas manchetes se empilham atrás da cabeça e um total aparece na frente | `text` (`manchete::detalhe\|...`), `total`, `label` |
| 36 | `checklist` | Uma lista de tarefas do Claude embaixo do queixo: cada passo gira e fica verde | `text` (`passo::detalhe\|...`), `title` |
| 37 | `liquid-glass-graph` | Um card de vidro líquido embaixo do queixo: um gráfico verde sobe e o número conta | `text` (legenda), `from`, `to` (ex.: `197K`, `59%`), `color` |
| 38 | `carousel-spin` | Seus reels giram em volta de você num carrossel 3D e depois param | `images`, `count`, `size`, `turns` |
| 39 | `match-cut` | Páginas de notícia cortam numa palavra, travada numa caixa vermelha atrás da cabeça | `text` (a palavra, padrão Claude), `color` |
| 40 | `apple-toggles` | Um card de Ajustes do iPhone liga os botões, uma linha por vez | `text` (linhas com `\|`), `ticks` (segundos com `\|`), `color` |
| 41 | `led-sign` | As luzes baixam e um letreiro de LED se escreve atrás de você | `text` (linhas com `\|`), `color`, `push` |
| 42 | `slow-push` | Um zoom lento de cinema no seu rosto enquanto o fundo desfoca | `zoom` (padrão 1.6), `blur` |
| 43 | `over-the-shoulder-zoom` | A câmera vai pra um canto de cima e um gráfico de vidro aparece ao lado da cabeça (linha sobe, número conta), volta, e depois o outro canto com um segundo gráfico de barras. Sua cabeça fica na frente | `text` (duas legendas com `\|`), `to` (dois números com `\|`, ex.: `197K\|672K`), `zoom` (padrão 2.0) |
| 44 | `messages` | Notificações do iMessage aparecem uma atrás da outra, vidro claro com brilho suave | `text` (mensagens com `\|`), `title` (padrão Mensagens), `y` |
| 45 | `place-in-grid` | Você encolhe no quadrado do meio da sua grade 3x3 e 8 reels aparecem em volta, com views em cada um | `images` (pasta de reels ou capas), `views` (9 números com `\|`, o 9º é o seu) |

**Visuais extras** (mesmo efeito, visual mais caprichado; não contam no total):
- `glitter-spotlight` = `spotlight` com `look=sparkle`: a sala escurece, raios dourados saem de trás da cabeça, uma palavra dourada com brilho passando, faíscas e um brilho em volta de você. `text` (a palavra), `color`, `push`.
- `cover-star` com `look=editorial`: visual de filme quente, título de revista clássica em serifa atrás da cabeça, linha da edição e chamadas elegantes. `text` (título), `issue`, `lines` (3 linhas com `\|`), `right` (linhas com `\|`), `color`, `accent`, `lines_y`, `right_y`.
- `liquid-glass-graph` com `look=bento`: o gráfico vai pra uma tela de vidro escuro atrás da cabeça, com blocos de vidro na sua frente (rosca, KPI, barras). `text`, `from`, `to`, `donut` (`29%::legenda`), `kpi` (`672K::legenda`), `bars` (`197\|140\|124::legenda`).
- `apple-toggles` agora fica acima de você, atrás da cabeça, com um zoom suave (`pos=below` pro card antigo embaixo do queixo; `overlap`, `zoom`).

Apelidos também funcionam: `bill`, `to-do`, `follow`, `stamp`, `countdown`, `cover`, `rain`, `pause`. Em português, relacione: órbita = `orbit`, holofote = `glitter-spotlight` (holofote neon = `spotlight`), carimbo = `reject-stamp`, contagem = `countdown-flip`, capa de revista = `cover-star`, notinha = `the-bill`, palavra atrás = `backdrop-word`, seguir = `tap`, comentário = `comment-box`, melhor efeito = `tier-list`, vidro = `glass-widgets`, órbita = `orbit`, lilás = `pastel-word`, colagem = `red-collage`.

## Regras
- Nunca cubra o rosto. Tudo vai atrás da pessoa ou desvia do rosto sozinho; se um frame de conferência ainda mostrar texto no rosto, mova (`x`, `y`) ou encurte o texto.
- Os efeitos rodam na ordem da lista. Coloque efeitos de câmera (`locked-on`, `lean-in`, `spotlight`) primeiro quando se sobrepõem a outros.
- O zoom nunca passa de 2x, pra imagem continuar nítida.
- Números em gráficos, contadores e manchetes devem ser os números reais da pessoa. Pergunte quais são; nunca invente.
- Esta skill adiciona só o visual. Som e legenda ficam com a pessoa (o CapCut funciona bem).
- São versões iniciais. Seja honesto sobre isso se a pessoa comparar com um reel que viu.
