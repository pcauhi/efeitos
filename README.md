# 45 efeitos de vídeo para o Claude

Joga seu vídeo no Claude, digita `/efeitos` e o nome do efeito. A edição é só isso.

Versão em português da skill criada por Vibha Ramprakash (licença MIT).

## Instalar

Cola isto no terminal:

```bash
git clone https://github.com/pcauhi/efeitos ~/.claude/skills/efeitos
```

Ou faça à mão:

1. Baixe e descompacte a pasta `efeitos`.
2. Mova a pasta para `~/.claude/skills/efeitos` (no Windows: `%USERPROFILE%\.claude\skills\efeitos`).
3. Reinicie o Claude Code. Pronto.

> Não sabe como? Abre o Claude Code e cola: **"Instala a skill da pasta efeitos em ~/.claude/skills/efeitos"**. O Claude faz pra você.

## Usar

1. Abra o Claude Code (o app ou o terminal).
2. Arraste o vídeo pro chat.
3. Digite o efeito que você quer:

```
/efeitos orbit do segundo 3 ao 6
/efeitos spotlight quando eu falar "apaga a luz", com a palavra CLAUDE atrás de mim
/efeitos comment-box no final, digitando EFEITOS
/efeitos glass-widgets nos primeiros 3 segundos
```

Na primeira vez, o Claude se configura sozinho (uns 2 minutos). Ele precisa do `ffmpeg` e do Python, e instala os dois se estiverem faltando.

O Claude confere alguns frames antes, corrige o que estiver cobrindo seu rosto e gera `seuvideo_effects.mp4` ao lado do original. Seu áudio fica igual.

Dá pra juntar vários efeitos de uma vez: *"Coloca locked-on do 6 ao 10, depois orbit do 10 ao 13, depois um carimbo quando eu falar 'não'."*

## Os 45 efeitos

| # | Digite | O que acontece |
|---|---|---|
| 1 | `noise` | Reels se empilham atrás da sua cabeça |
| 2 | `lineup` | Cartões numerados abrem acima da sua cabeça |
| 3 | `locked-on` | Cantoneiras travam no seu rosto e a câmera te segue |
| 4 | `orbit` | Seus reels giram em volta da sua cabeça |
| 5 | `lean-in` | Um zoom rápido numa palavra |
| 6 | `backdrop-word` | Uma palavra gigante cai atrás de você |
| 7 | `spotlight` | Apaga as luzes e deixa só você iluminado |
| 8 | `the-bill` | Suas instruções saem impressas como uma notinha |
| 9 | `moody` | Uma correção de cor com clima |
| 10 | `swipe` | Um slider de antes e depois |
| 11 | `todo` | Um checklist ao lado da cabeça que vai sendo marcado |
| 12 | `comment-box` | Um comentário do Instagram se digita e publica |
| 13 | `tap` | Um botão Seguir vira Seguindo |
| 14 | `pause-point` | Imagem congelada com uma seta desenhada |
| 15 | `uninstall` | Uma barra de desinstalação com glitch quebra a imagem |
| 16 | `reel-frame` | Seu vídeo encolhe num card de reel |
| 17 | `shortcut-rain` | Teclas do teclado chovem atrás de você |
| 18 | `reject-stamp` | Um carimbo vermelho bate na tela |
| 19 | `countdown-flip` | Um relógio de 3, 2, 1 acima da cabeça |
| 20 | `rabbit-hole` | O fundo vira um túnel atrás de você |
| 21 | `cover-star` | Você vira capa de revista |
| 22 | `scribble` | Rabiscos de marcador se desenham em volta de você |
| 23 | `glass-widgets` | Widgets de vidro fosco flutuam em volta da cabeça |
| 24 | `red-collage` | Você em preto e branco, palavra vermelha gigante atrás |
| 25 | `split-headline` | Um card de manchete te empurra pra metade de baixo |
| 26 | `pastel-word` | Sala lilás, palavra gigante atrás, um perfil ganha seguidor |
| 27 | `check-pills` | Sala quadriculada, seus reels atrás, botões azuis clicados |
| 28 | `timeline` | Cor de filme vermelho escuro com timeline de edição |
| 29 | `headline-box` | Um zoom com manchete limpa de duas linhas |
| 30 | `profile-wall` | A grade dos seus reels enche a parede enquanto um contador sobe |
| 31 | `tier-list` | Um tier list aparece e o Claude vai pro tier S |
| 32 | `broll-split` | B-roll em cima com etiqueta de preço, você embaixo |
| 33 | `phone-fan` | Seus reels abrem como um leque de celulares |
| 34 | `dot-reveal` | Sua imagem se monta com pontinhos brilhantes |
| 35 | `headline-wall` | Suas manchetes se empilham atrás e um total aparece |
| 36 | `checklist` | Uma lista de tarefas do Claude, cada passo fica verde |
| 37 | `liquid-glass-graph` | Um card de vidro líquido com gráfico subindo e número contando |
| 38 | `carousel-spin` | Seus reels giram em volta de você num carrossel 3D |
| 39 | `match-cut` | Páginas de notícia cortam numa palavra travada atrás da cabeça |
| 40 | `apple-toggles` | Botões do iPhone ligam, uma linha por vez |
| 41 | `led-sign` | As luzes baixam e um letreiro de LED se escreve atrás de você |
| 42 | `slow-push` | Um zoom lento de cinema enquanto o fundo desfoca |
| 43 | `over-the-shoulder-zoom` | Vai pra um canto, gráfico de vidro ao lado da cabeça, depois o outro canto com outro gráfico |
| 44 | `messages` | Notificações do iMessage aparecem uma atrás da outra |
| 45 | `place-in-grid` | Você encolhe no meio da sua grade 3x3 e seus reels aparecem em volta |

Visuais extras: `/efeitos glitter-spotlight` (raios dourados e faíscas), `cover-star look=editorial` (capa de revista clássica) e `liquid-glass-graph look=bento` (um painel de vidro em volta de você).

Todo efeito segue seu rosto. O que cobriria seu rosto vai pra trás da sua cabeça.

**Dicas**
- Vídeo vertical de celular, com você no quadro, funciona melhor.
- Fale o tempo do seu jeito ("quando eu falar 'olha'"). O Claude acha o segundo exato.
- Quer seus reels no `orbit`, `noise`, `phone-fan` ou `profile-wall`? Passe pro Claude uma pasta com prints.
- Gráficos, contadores e manchetes devem usar seus números reais. Conta pro Claude quais são.
- Sai em 1080p. Peça 4K se quiser (mais lento).

## Pra ser honesto
- São **versões iniciais**. Não vão ficar idênticas a um reel editado na mão, com design de som e tempo ajustado.
- A skill faz o rascunho, você aprova. Assista antes de postar.
- Não adiciona som nem legenda. Coloque no CapCut.

## Se der algo errado
É só falar pro Claude o que você está vendo ("a palavra cobre meu rosto", "tá rápido demais"). Ele ajusta o plano e renderiza de novo.

## Componentes
Rastreamento de rosto: OpenCV YuNet (MIT). Recorte da pessoa: MediaPipe Selfie Segmenter (Apache 2.0). Fontes: Archivo Black, Instrument Serif, Space Mono, Inter, Anton, Montserrat (SIL OFL) e Permanent Marker (Apache 2.0); as licenças estão em `fonts/`.
