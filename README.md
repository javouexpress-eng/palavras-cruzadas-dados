# Dados do app Palavras Cruzadas

Arquivos JSON estáticos usados pelo app Android "Palavras Cruzadas" para carregar temas e grades sem precisar de servidor.

- `themes.json` — lista de temas disponíveis (slug + nome de exibição + dificuldade + nº de fases).
- `crosswords/<slug>/<fase>.json` — grade e palavras da fase N de um tema (ex.: `crosswords/animais/2.json`).

## Fases

Cada tema pode ter uma ou várias fases numeradas (1, 2, 3, ...). No app,
a fase 1 vem sempre liberada; a fase N só libera depois que o jogador
conclui a fase N-1 (isso é controlado pelo app, não pelos dados aqui).

Hoje só **Animais** e **Oceano** têm 3 fases, como prova de conceito do
sistema. Os demais temas têm 1 fase só (`"phases": 1`) — adicionar mais
fases neles é só criar os arquivos e atualizar o número abaixo.

## Para adicionar uma fase nova a um tema existente

1. Crie `crosswords/<slug>/<próximo-número>.json` seguindo o formato dos
   existentes (dica: use `tools/gerador_tema.py` no repositório do app —
   ele monta a grade sozinho a partir de uma lista de palavras/dicas e
   garante que nenhuma fique solta nem colada sem cruzar).
2. Aumente o `"phases"` desse tema em `themes.json`.
3. Faça commit/push.

## Para adicionar um tema novo

1. Crie `crosswords/<novo-slug>/1.json` (e `2.json`, `3.json`... se quiser
   mais de uma fase já de início).
2. Adicione em `themes.json`:
   ```json
   { "slug": "...", "theme": "...", "difficulty": "...", "phases": N }
   ```
   `difficulty` é `"facil"`, `"medio"` ou `"dificil"` — o app usa isso pra
   mostrar o selo colorido (verde/laranja/vermelho) e pra ordenar o menu
   do mais fácil ao mais difícil.
3. Faça commit/push — o app já busca a versão mais recente automaticamente
   (sem precisar lançar nova versão do app). Dificuldade, fases e ordem
   vêm todos daqui.
