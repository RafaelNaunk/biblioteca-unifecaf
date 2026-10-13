# Biblioteca Digital UniFECAF

Projeto acadêmico de Design Web desenvolvido com HTML e CSS. A página apresenta uma proposta de biblioteca digital com navegação, áreas de conhecimento, seis livros demonstrativos, três unidades ilustrativas e acesso ao atendimento oficial da instituição.

Os títulos, capas e ambientes são demonstrativos. As unidades não representam instalações reais. O site não oferece empréstimos, login nem download de livros.

## Abrir e editar no Windows

1. Extraia o ZIP com a opção **Extrair tudo**.
2. No Visual Studio Code, use **Arquivo > Abrir Pasta** e escolha a pasta que contém `index.html`.
3. Abra `index.html` no navegador. O projeto funciona sem instalação de dependências.
4. Ao alterar o código, salve com `Ctrl + S` e atualize a página no navegador.

## Organização dos arquivos

| Arquivo ou pasta | Função |
| --- | --- |
| `index.html` | Define o conteúdo, a ordem e o significado das seções. |
| `css/style.css` | Define cores, fontes, espaçamentos, colunas e adaptações de tamanho. |
| `assets/imagens/` | Guarda as 17 ilustrações SVG utilizadas na página. |
| `README.md` | Explica o projeto, a revisão e os próximos testes. |

Os caminhos das imagens são relativos. Por exemplo, `assets/imagens/programacao.svg` parte da pasta de `index.html`. Manter as pastas juntas permite abrir o projeto em outro computador e publicá-lo.

## Entendendo as principais decisões

- **HTML semântico:** `header`, `nav`, `main`, `section`, `article` e `footer` indicam a função de cada parte da página. O título principal usa `h1`, as seções usam `h2` e os livros e unidades usam `h3`.
- **Links internos:** `href="#livros"` leva ao elemento com `id="livros"`. Por isso, cada identificador precisa ser único e existir na página.
- **CSS separado:** o HTML cuida da estrutura; a folha de estilos concentra a apresentação e facilita alterações.
- **Grid e Flexbox:** Grid organiza blocos em colunas, como os cartões de livros. Flexbox organiza elementos como a marca e o menu e permite que eles mudem de linha.
- **Responsividade:** regras `@media` mudam o layout conforme a largura disponível. Até 900 pixels, banners, apresentação, unidades e contatos usam uma coluna, e as categorias usam duas. Até 700 pixels, os livros também usam uma coluna.
- **Detalhes expansíveis:** `details` e `summary` oferecem o controle “Saiba mais” com recursos nativos do navegador, sem JavaScript.
- **Imagens:** SVG mantém a nitidez ao mudar de tamanho. Imagens decorativas usam `alt=""`; as informativas têm uma descrição. As legendas das categorias já apresentam o significado das respectivas ilustrações.
- **Legibilidade:** a fonte Arial, o espaçamento entre linhas e o contraste entre texto e fundo ajudam a leitura. O foco visível permite acompanhar a navegação pelo teclado.

## Cores por categoria

Cada categoria tem uma cor principal e um fundo suave:

| Categoria | Cor principal | Fundo suave |
| --- | --- | --- |
| Tecnologia | Azul `#005fa3` | `#eaf4fc` |
| Design | Roxo `#6d28d9` | `#f4edff` |
| Gestão | Verde `#176b45` | `#ecf8f1` |
| Pesquisa | Laranja escuro `#9a4600` | `#fff4e7` |

A mesma cor aparece na faixa superior do cartão, na etiqueta, no botão “Saiba mais”, na capa e na área de conhecimento correspondente. Repetir essa associação ajuda a reconhecer livros da mesma categoria. Os nomes das categorias permanecem escritos para que a identificação também funcione sem distinguir as cores.

O HTML aplica duas classes ao cartão. A primeira define o formato comum; a segunda escolhe o tema:

```html
<article class="cartao-livro tema-design">
```

No CSS, o tema guarda as cores em variáveis:

```css
.tema-design {
    --cor-categoria: #6d28d9;
    --fundo-categoria: #f4edff;
}
```

Essas variáveis são herdadas pelos elementos dentro do cartão. A regra do botão, por exemplo, usa `background-color: var(--cor-categoria, #005fa3);`. A função `var()` lê a cor escolhida. O segundo valor fornece um azul padrão caso a variável não exista.

Assim, mudar `--cor-categoria` de Design atualiza os elementos que usam essa variável, sem precisar repetir uma regra de botão para cada categoria. Os SVGs externos das capas e das ilustrações também foram recoloridos; eles não herdam automaticamente as variáveis do CSS da página.
