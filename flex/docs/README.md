# Flexbox

- [Origamid](https://origamid.com/projetos/flexbox-guia-completo/)
- [Curso](https://www.origamid.com/curso/css-flexbox/)

### flex-wrap

- Por padrão esse valor é `nowrap` ou seja em um display flex direction row ele sempre irá adicionar um item ao lado do outro e não quebrará linha
- para ter o comportamento de quebrar linhas para quando os itens não caibam mais precisamos que o `flex-wrap` seja de valor `wrap`

---

### flex-direction

- Por padrão é `row` que coloca uma ao lado do outro.
- Para empilhar um abaixo do outro só utilizar o `column`

### Align e justify

- Alinha os items conforme direction do flex.
- no caso do justify quando direction é row, alinha no eixo x.
- o align funciona praticamente da mesma forma só que sempre no eixo oposto do justify

- Valores do `justify-content`:

```scss
justify-content: flex-start;
// Alinha os itens ao início do container.
justify-content: flex-end;
// Alinha os itens ao final do container.
justify-content: center;
// Alinha os itens ao centro do container.
justify-content: space-between;
// Cria um espaçamento igual entre os elementos. Mantendo o primeiro grudado no início e o último no final.
justify-content: space-around;
// Cria um espaçamento entre os elementos. Os espaçamentos do meio são duas vezes maiores que o inicial e final.
```

- Valors do `align-items`:

```scss
align-items: stretch;
// Valor padrão, ele que faz com que os flex itens cresçam igualmente.
align-items: flex-start;
// Alinha os itens ao início.
align-items: flex-end;
// Alinha os itens ao final.
align-items: center;
// Alinha os itens ao centro.
align-items: baseline;
// Alinha os itens de acordo com a linha base da tipografia.
```

- O `align-content` é parecido com o `justify-content` porém ele alinha no eixo vertical, e é necessário que o `flex-wrap` seja de valor `wrap`, valores possíveis:

```scss
align-content: stretch;
// Valor padrão, ele que faz com que os flex itens cresçam igualmente na vertical.
align-content: flex-start;
// Alinha todas as linhas de itens ao início.
align-content: flex-end;
// Alinha todas as linhas de itens ao final.
align-content: center;
// Alinha todas as linhas de itens ao centro.
align-content: space-between;
// Cria um espaçamento igual entre as linhas. Mantendo a primeira grudada no topo e a última no bottom.
align-content: space-around;
// Cria um espaçamento entre as linhas. Os espaçamentos do meio são duas vezes maiores que o top e bottom.
```

## flex

- Ele é um atalho para `flex-grow`, `flex-basis` e `flex-shrink`

### flex-grow

- Por padrão é 0, define uma quantidade relativa de quanto o elemento deve crescer em relação aos demais irmãos...
- Ele define um espaço uniforme no inicio e no final do conteúdo do elemento...

```
[|GROW-0| |  GROW-1 | |  TEXTO-GROW-1  |]

[|GROW-0| |  GROW-1 | |    GROW-2    |]
```

- Perceba que na primeira linha o que tem grow 1 possuí um espaço no inicio e no fim, exatamente iguail o qual embrulha o conteúdo.
- Na segunda linha esse espaço no grow-2 é duas vezes maior!

### flex-basis

- Quando o `flex-grow` é zero e o `flex-basis` é um número > 0:

  - Ele irá tentar colocar o item com a largura conforme valor definido, porém respeitando em primeiro lugar:
    - O tamanho do conteúdo, ou seja se o tamanho do conteúdo for maior, o tamanho do conteúdo irá prevalecer
  - Também o tamanho do container irá prevalecer:
    - Caso o item for maior que o tamanho do container, ele se ajusta para caber.

- Quando o `flex-grow` é maior que zero e o `flex-basis` é um número > 0:

  - prevalece o `flex-grow`

- O valor `auto` é o padrão nesse caso predomina o que for definido no `flex-grow`.

- Quando o `flex-basis` for zero ele faz com que todos os itens tenham o mesmo tamanho, porém:
  - Prevalece priemiro o tamanho do conteúdo,
  - os demais itens que tem conteúdo menores ou iguais uns aos outros seguirão o mesmo tamanho e que tenham o mesmo valor de `flex-grow`
  - `width` será ignorado!
  - `min-width` ele respeita.

### flex-shrink

- Define quantas unidades o item deve tentar reduzir, o valor padrão é 1
- Quando definido zero, não será realizado a redução
- Quando definido um valor maior que zero ele irá reduzir os elementos, priorizando ou tentando diminuir os que tiverem os valores maiores para os menores, respeitando:

  - tamanho do conteúdo
  - flex-wrap

- Se o tamanho do `grow` for 1, o `shrink` for 0 e o `basis` tiver o tamanho maior que o container, ele deve ultrapassar o container para seguir com o valor do `basis`

- No safari tem alguns bugs quando utiliza o basis como zero ele não quebra mesmo quando a tipografia colapsa,
  para resolver isso utilizamos o `max-width` ou o `basis` com valor maior que zero

---

- O atalho `flex` ele define as 3 propriedades acima de uma só vez, o `flex-grow`, `flex-shrink` e `flex-basis`
- Quando definir o valor de `flex` = 1, ele assume esses valores:

```scss
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0;
```

- O valor padrão é `0 1 auto` ou seja:

- 0 de grow
- 1 de shrink
- e auto de basis
