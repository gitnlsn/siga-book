# Ilustrações das aberturas de parte

Uma por parte, em **bico de pena preto e branco**, nanquim com hachuras finas, a
mesma família de *Quarenta dias úteis*. As cenas são quase sempre lugares e
objetos, com gente pequena, de costas ou ausente. Gerar no Gemini (navegador),
uma imagem por conversa, sempre colando primeiro o bloco de estilo. Decidido
pelo autor em 2026-10-18; a xilogravura foi descartada.

**Arquivo final:** `books/siga/illustrations/masters/0N-parte-N.jpeg`, em
retrato 4:5 (928×1152 ou maior). Depois rodar `make`. O build converte para
escala de cinza a 300 dpi.

## Bloco de estilo (colar antes de cada prompt)

> Black-and-white pen-and-ink illustration, fine crosshatching and stippling,
> detailed realistic linework like a literary book illustration, deep black
> shadows built from dense hatching, white paper for light. No color, no gray
> wash. Vertical portrait composition, 4:5 aspect ratio, the drawing fading out
> softly at the edges into white paper. Quiet, still, slightly melancholic mood,
> the feeling of a moment just after something happened. No text, no readable
> letters or numbers, no logos, no flags, no recognizable real people. If people
> appear they are small, seen from behind, ordinary Brazilians.

## I — 15 de novembro

> A long office corridor in a government building at 3 a.m., seen in strong
> one-point perspective. Closed wooden office doors on both sides, each with a
> small card reader next to it; the nearest reader glows with a single small
> light. On the floor, leaning against the wall by that door, a man's necktie
> has fallen and a phone lies face up, its screen glowing white. Halfway down the
> corridor a cleaning cart with a mop bucket stands abandoned. Fluorescent tubes,
> half of them off. A tall narrow window at the far end shows the night sky and
> the faint silhouette of the twin towers of Brasília's National Congress.

## II — A métrica

> An Amazon riverbank seen from the water: a wooden stilt house, a canoe tied to
> a small plank pier, and behind the house a cleared patch of cassava field with
> a thin column of smoke rising straight up. A small figure of an older woman
> with a hoe on her shoulder stands at the edge of the field, looking up. Over
> the whole forest canopy, the sky is overlaid with a faint, perfectly regular
> grid of thin ruled lines, like a satellite map, and the single square directly
> over her field is filled with dense black crosshatching.

## III — O recurso

> A small Brazilian snack bar in the afternoon: a plastic table and two plastic
> chairs, a half-eaten pastel on a paper napkin, a glass bottle of soda, an old
> phone, and a sheet of paper folded into eight lying open on the table, covered
> in lines too small to read. A ceiling fan, a tiled counter with a glass display
> case, a calendar on the wall. Through the open door, outside, a patient queue
> of ordinary people waiting on the sidewalk, each holding a folded paper.

## IV — O segundo sim

> A public-school classroom turned into a polling station: student desks pushed
> against the walls, a blue plastic tarp tied under a leak in the ceiling,
> late-afternoon light falling in long stripes through a barred window. In the
> center, a cardboard voting booth seen from behind, and inside it a young woman
> of eighteen, from behind, her right hand raised and not yet touching the voting
> machine. Through the open classroom door, a queue of people waiting in the
> corridor. A suspended, silent moment.

## Capa do eBook

O build compõe o título no alto e a autora embaixo, por cima da arte, com uma
faixa escura em degradê (o verde-escuro `#1d2a22` do `book.yaml`). A arte vai
**sangrada**, sem margem branca, em **5:8** (1600×2560). O terço de cima e a
faixa de baixo ficam escuros e calmos.

Aqui, e só aqui, entra uma cor: o bico de pena continua preto e branco, com
**uma única cor de destaque, amarelo-ouro**, nas telas acesas.

> Pen-and-ink illustration with fine crosshatching, black ink only, with ONE
> spot color: warm golden yellow (#d8b43a), used only for glowing phone screens.
> Full bleed, no white margins, vertical 5:8 aspect ratio. Night in Brasília: the
> Esplanada dos Ministérios seen from ground level, the National Congress by
> Oscar Niemeyer in the distance (two thin twin towers between one upturned bowl
> and one downturned dome), completely dark, every window unlit. In the
> foreground, a large silent crowd of ordinary Brazilians seen from behind, each
> person looking down at a phone, and every screen glows golden yellow, hundreds
> of small yellow lights spreading toward the dark building. The upper third of
> the image is empty, deep black night sky with a few stars, left clear for the
> title. The bottom edge is darker, calm. No text, no letters, no logos, no flags,
> no recognizable real people.

Alternativa mais seca, se a primeira ficar carregada:

> Same style and spot color. At dawn, a single plain traffic sign on a metal pole
> with a straight arrow pointing ahead, standing at the side of an empty red-dirt
> road that runs toward the distant dark silhouette of Brasília's National
> Congress. The only color is the golden-yellow arrow. The upper third is empty
> dark sky for the title. No text on the sign.

Salvar como `books/siga/illustrations/masters/cover.jpeg`. A capa impressa
continua só tipográfica.

## Dicas para o Gemini

- Se vier colorida ou com aguada cinza: "pure black ink on white paper, only
  hatching, no color, no gray wash".
- Se aparecer texto ou letreiro: "remove all text, letters and numbers".
- Se o Congresso sair errado: "Oscar Niemeyer's Brazilian National Congress: two
  thin twin towers between one upturned bowl and one downturned dome".
- Para as quatro saírem coerentes, gere todas na mesma conversa e peça "same
  style as the previous image".
