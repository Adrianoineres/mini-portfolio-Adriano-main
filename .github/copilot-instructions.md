## Contexto rápido

Repositório: mini-portfólio estático (site de uma página). Não há build system, é um site static asset. Estrutura relevante:

- `index.html` — estrutura e marcação principal
- `src/js/index.js` — comportamento das abas (lógica de UI)
- `src/css/estilos.css` e `src/css/reset.css` — estilos
- `src/imagens/` — assets (ex.: `foto-perfil.png`, `200.webp`, `linkedingif.gif`)

## Objetivo do agente

Ajude a manter/estender este mini-portfólio estático: correções HTML/CSS/JS, adicionar seções/links, otimizar imagens e pequenas melhorias de acessibilidade. Não há backend ou CI complexo para integrar.

## Padrões e convenções do projeto (importantes)

- Navegação por abas: cada aba é um `<li class="aba" id="XYZ">` e seu conteúdo correspondente é `<div id="informacao-XYZ" class="informacao">`. O JavaScript constrói o mapeamento usando `informacao-${aba.id}` (veja `src/js/index.js`).
- Classe `selecionado` controla visibilidade/estado: aplicada tanto em abas (`.aba.selecionado`) quanto em conteúdos (`.informacao.selecionado`). Não alterar o nome da classe sem atualizar `index.js`.
- Assets referenciados por caminhos relativos a partir de `index.html` com prefixo `./src/...`. Preserve essa convenção ao mover/renomear arquivos.
- Fonte importada em `index.html` (Google Fonts) deve ser mantida se design depender dela (`VT323`).

## Como executar/visualizar localmente

- Não há build: abra `index.html` no navegador ou sirva a pasta com um servidor estático. Exemplo (local):

  - use `python -m http.server 8000` a partir da raiz do projeto e abra `http://localhost:8000`.

## Exemplos de mudanças seguras e como fazê-las

- Para adicionar uma nova aba 'Contato':
  1. Adicione `<li class="aba" id="contato">...</li>` dentro de `.abas` em `index.html`.
  2. Adicione o painel `<div id="informacao-contato" class="informacao">...</div>` dentro de `.informacoes-abas`.
  3. O `src/js/index.js` já vai mapear automaticamente pelo padrão `informacao-${aba.id}`.

- Para alterar o estilo visual de abas, edite `src/css/estilos.css` nas regras `.cartao .abas .aba` e `.cartao .abas .aba.selecionado`.

## Pontos de atenção / armadilhas comuns

- Não renomeie a classe `selecionado` ou os ids das abas sem tocar `src/js/index.js` — o script depende desses nomes.
- O `lang` do HTML está `en` enquanto o conteúdo é português — considere alinhar (trocar para `pt-BR`) se for alterar texto e metas.
- Verifique links externos (LinkedIn, currículo no Google Docs) ao atualizar a seção de redes; estão hard-coded em `index.html`.

## Integrações externas e dependências

- Google Fonts (externo) — carregado em `index.html`.
- Nenhuma dependência de npm, bundlers ou ferramentas de build detectada.

## Como contribuir com instruções para o agente

- Seja específico: referencie sempre caminhos/ids/classes exatos. Ex.: use `index.html` e o id informacao-minhas-redes.
- Para mudanças JS, indique comportamento esperado com exemplo: clique na aba com id minhas-redes deve mostrar o elemento informacao-minhas-redes.

---
Se quiser, aplico um ajuste inicial sugerido (por exemplo, trocar `lang="en"` para `pt-BR` ou adicionar uma aba de contato). Qual mudança prefere que eu faça primeiro?
