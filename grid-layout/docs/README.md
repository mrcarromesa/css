# Grid Layout

- Mais documentação sobre: [grid-layout](https://www.origamid.com/projetos/css-grid-layout-guia-completo/)
- [Grid-by-example](https://gridbyexample.com)
- [w3c](https://www.w3.org/TR/css-grid-1/)

## Columns

```html
<style>
  .grid {
    display: grid;
  }

  .grid-template-columns {
    grid-template-columns: 200px 200px;
    grid-column-gap: 10px;
    grid-row-gap: 5px;
  }
</style>

<div>
  <h1>grid-template-columns: 200px 200px;</h1>
  <section class="container grid grid-template-columns">
    <div class="item">1</div>
    <div class="item">2</div>
    <div class="item">3</div>
    <div class="item">4</div>
  </section>
</div>
```

- com `display: grid` definimos que queremos utilizar no modo grid
- com `grid-template-columns` definimos como queremos dispor nossas colunas

- podemos defini-lo de várias formas:

```scss
grid-template-columns: 200px 200px; // duas colunas de 200px
grid-template-columns: 1fr 1fr; // duas colunas de mesmo tamanho
grid-template-columns: 2fr 1fr 1fr; // 3 colunas a primeira 2 vezes maior que as demais e a segunda e terceira mesmo tamanho
grid-template-columns: repeat(3, 1fr); // 3 colunas de mesmo tamanho
grid-template-columns: repeat(3, 1fr) 2fr; // 3 colunas de mesmo tamanho e a última de 2 vezes maior que as demais
grid-template-columns: minmax(50px, 100px) 1fr 1f; // 3 colunas a primeira é 50px no minimo e 100px no máximo, as demais são de mesmo tamanho e irão se adequar ao espaço restante ocupado pela primeira
grid-template-columns: repeat(
  auto-fit,
  100px
); // Adiciona quantas colunas houverem sendo que elas devem ter 100px de largura

grid-template-columns: repeat(
  auto-fit,
  minmax(100px, auto)
); // Adiciona quantas colunas houverem sendo que elas devem ter 100px de largura
```

- O `fr` irá respeitar o conteúdo que tem prioridade mesmo que dessa forma estore o layout

- o auto-fit é mais interessante do que o auto-fill,
- o auto-fit preenche o espaço com o conteúdo que ele tem.
- o auto-fill ele preenche com base no tamanho e deixará lacunas vazias caso tenha mais espaços do que colunas para preencher.

---

## Rows

- A definição de rows já existe por padrão na template columns ou seja quando tenho mais itens do que colunas ele é quebrado em linhas

- Temos como definir medidas para essas linhas também:

```scss
grid-template-columns: 100px auto 50px;
grid-template-rows: 50px minmax(200px, auto) 50px;
```

- Podemos seguir as mesmas funções e medidas definidas no columns

## Template areas

- Para tal definimos como será a estrutura do grid definindo nomes aos items, dessa forma:

```scss
.grid-template-areas-1 {
  grid-template-areas:
    "logo nav nav"
    "sidenav content advert"
    "sidenav footer footer";
}
```

- E para que o css possa identificar qual item é qual precisamos defini-lo dessa forma:

```scss
.logo {
  grid-area: logo;
}

.nav {
  grid-area: nav;
}

//....
```

## Grid-gap

- grid-gap ou simplemente gap, adiciona uma laguna podendo ser horizontalmente ou verticalmente para todos os itens uniformimente do grid

```scss
grid-gap: 10px; // adiciona um gap de 10px tanto horizontal como vertial
gap: 10px; // adiciona um gap de 10px tanto horizontal como vertial
gap: 10px 20px; // adiciona um gap de 10px vertical e 20px horizontal

grid-column-gap: 20px; // adiciona gap apenas entre as colunas
grid-row-gap: 20px; // adiciona gap apenas entre as rows
```

## Auto columns

- define o tamanho automático para colunas quando for apropriado aplicar:

```scss
.grid-auto-colums-1 {
  grid-template-columns: 1fr 1fr;
  grid-auto-columns: 100px;
  // posso definir mais padroes
  grid-auto-columns: 50px 75px;
}

.item-n {
  grid-column: 50;
}
```

## Auto rows

- Segue o mesmo principio para o columns só que dessa vez para rows...

```scss
.grid-auto-colums-1 {
  grid-template-columns: 1fr 1fr;
  grid-auto-rows: 100px;
  // posso definir mais padroes
  grid-auto-rows: 50px 75px;
}
```

## grid-auto-flow

- Propriedades aceitas:
  - column: a cada item criado segue por padrão o fluxo de colunas desde que não haja template row definido
  - row: é o fluxo padrão de empilhar os items um abaixo do outro
  - dense: tenta encaixar os items não importa a ordem apenas desde que caiba nas lacunas

## Justify e align

- O justify alinha no eixo x
  - justify-content: alinha horizontalmente os items do container no eixo x
  - justify-items: alinha horizontalmente o conteúdo dos items no eixo x

```scss
// Content
justify-content: start
// Justifica os itens ao início.
justify-content: end
// Justifica os itens ao final.
justify-content: stretch
// Estica os itens.
justify-content: space-around
// Distribui espaço entre os elementos. (O início e final são menores que os espaços internos).
justify-content: space-between
// Cria um espaço entre os elementos, ignorando o início e final.
justify-content: space-evenly
// Cria um espaço igual entre as colunas (no início e final também).
justify-content: center
// Centraliza o conteúdo.

// ---

// Items
justify-items: start
// Justifica os itens ao início.
justify-items: end
// Justifica os itens ao final.
justify-items: center
// Centraliza o conteúdo.
justify-items: stretch
// Estica os itens.
```

- o Align alinha no eixo y
  - o align-content: alinha verticalmente os itens do container no eixo y
  - o align-items: alinha verticalmente o conteúdo dos itens do container no eixo y

```scss
// Content
align-content: start
// Alinha os itens ao início.
align-content: end
// Alinha os itens ao final.
align-content: stretch
// Estica os itens.
align-content: space-around
// Distribui espaço entre os elementos. (O início e final são menores que os espaços internos).
align-content: space-between
// Cria um espaço entre os elementos, ignorando o início e final.
align-content: space-evenly
// Cria um espaço igual entre as colunas (no início e final também).
align-content: center
// Centraliza o conteúdo.

// ---

// Items
align-items: start
// Alinha os itens ao início.
align-items: end
// Alinha os itens ao final.
align-items: center
// Centraliza o conteúdo.
align-items: stretch
// Estica os itens.

```

## Definindo grid items values

- podemos definir utilizando de forma nomeada:

```scss
.grid-column-5 .item-2 {
  grid-column-start: sidenav;
  grid-column-end: sidenav;
  grid-row-start: sidenav;
  grid-row-end: sidenav;
}

.grid-column-5 .item-3 {
  grid-column: content / content;
}
```

Definindo as linhas das colunas e ou linhas

```scss
.grid-column-6 .item-1 {
  grid-column: 1 / -1;
}

.grid-column-6 .item-2 {
  grid-column: 1;
  grid-row: 2 / 4;
}
```

- as linhas e colunas funcionam dessa forma:

!![Grid columns](https://s3-us-west-2.amazonaws.com/s.cdpn.io/64626/grid-column.png)

- Esse conceito é fundamental para o entendimento

- Também podemos mudar as colunas de lugar:

```scss
.grid-column-6 .item-1 {
  grid-column: 5;
}
```

---

## span

- Essa propriedade expande o item para quantidade de celulas definidas:

```scss
.grid-row-2 .item-5 {
  grid-row: span 3;
}
```

- Ele pode ser bem útil quando temos um layout grid e não termos que definir quais linhas ou colunas ele deve oculpar, simplesmte utilizamos o span e pronto!

---

## Mix blend mode

- Quando tenho um item na frente do outro eu posso utilizar o mix-blend-mode para misturar as cores deles para que fiquem visiveis:

```scss
mix-blend-mode
```

---

## Alinhamento proprio

- É possível alinhar/justificar os items do grid por eles mesmo:

```scss
.item1 {
  justify-self: end; // alinha no eixo x
  align-self: center; // alinha no eixo y
}
```
