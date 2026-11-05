# Dados do app Palavras Cruzadas

Arquivos JSON estáticos usados pelo app Android "Palavras Cruzadas" para carregar temas e grades sem precisar de servidor.

- `themes.json` — lista de temas disponíveis (slug + nome de exibição).
- `crosswords/<slug>.json` — grade e palavras de cada tema.

Para adicionar um tema novo:
1. Crie `crosswords/<novo-slug>.json` seguindo o formato dos existentes.
2. Adicione `{ "slug": "...", "theme": "..." }` em `themes.json`.
3. Faça commit/push — o app já busca a versão mais recente automaticamente (sem precisar lançar nova versão do app).
