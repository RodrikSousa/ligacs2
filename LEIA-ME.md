# Site da Liga CS2 — como atualizar

Toda a informação do site vem do ficheiro `dados.json`. O `index.html` não precisa de ser editado.

## Ficheiros

- `index.html`: o site. Não mexer.
- `dados.json`: equipas, jornadas, taça e notícias. É aqui que se faz tudo.

## Atualizar um resultado

Em `jornadas`, procura o jogo e troca os `null` pelas rondas. Formato de cada jogo: `["casa", "fora", rondas_casa, rondas_fora]`.

```json
["POR", "CMB", 13, 9]
```

Regras (MR12, BO1):
- Ganha quem chegar a 13 rondas. Máximo de 24 rondas.
- Um resultado só pode ser 13 contra 0 a 12, ou 12-12 (empate).
- Qualquer outro valor é marcado como inválido no site e não conta para a classificação.

## Adicionar uma notícia

Em `noticias`, acrescenta um objeto no topo da lista (o mais recente primeiro):

```json
{ "data": "2026-10-17", "titulo": "Título", "texto": "Texto da notícia." }
```

## Equipas

Cada equipa tem `id` (sigla de 3 letras, única), `nome`, `cidade`, `logo` (`null` ou o endereço de uma imagem), `coach` e `jogadores`. Para uma nova equipa, acrescenta um objeto em `equipas` e usa a mesma sigla nos jogos.

## Taça da Liga

Em `taca`, cada fase tem `eliminatorias` com `ra` e `rb` (rondas). Preenche `null` depois de cada jogo. As chaves são definidas pelo sorteio e não dependem da classificação.

## Verificar antes de publicar

- O ficheiro tem de ser JSON válido. Vírgulas e aspas são o erro mais comum. Podes colar o conteúdo em https://jsonlint.com para confirmar.
- Abre o site depois de publicar e confirma o calendário e a classificação.

## Publicar

Se o site estiver no GitHub Pages, basta fazer commit do `dados.json` alterado. O site fica atualizado em poucos minutos.

Para ver o site localmente, não basta abrir o `index.html` com duplo clique: é preciso um servidor local (por exemplo `python3 -m http.server` na pasta do site).
