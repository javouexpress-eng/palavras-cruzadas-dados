# Dados do app Palavras Cruzadas

Arquivos JSON estáticos usados pelo app Android "Palavras Cruzadas" para carregar temas e grades sem precisar de servidor.

- `themes.json` — lista de temas disponíveis (slug + nome de exibição + dificuldade).
- `crosswords/<slug>.json` — grade e palavras de cada tema.

Para adicionar um tema novo:
1. Crie `crosswords/<novo-slug>.json` seguindo o formato dos existentes
   (dica: use `tools/gerador_tema.py` no repositório do app — ele monta a
   grade sozinho a partir de uma lista de palavras/dicas e garante que
   nenhuma fique solta).
2. Adicione `{ "slug": "...", "theme": "...", "difficulty": "..." }` em
   `themes.json`. `difficulty` é `"facil"`, `"medio"` ou `"dificil"` — o app
   usa isso pra mostrar o selo colorido (verde/laranja/vermelho) e pra
   ordenar o menu do mais fácil ao mais difícil.
3. Faça commit/push — o app já busca a versão mais recente automaticamente
   (sem precisar lançar nova versão do app). A dificuldade e a ordem também
   vêm daqui, então reclassificar um tema é só editar `difficulty` e dar
   push de novo.
