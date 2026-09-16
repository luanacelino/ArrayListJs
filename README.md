# ArrayListJs

Nesta atividade iremos abordar três métodos de manipulação de arrays, são eles: `map()`, `filter()` e `reduce()`. Esses métodos possuem uma sintaxe mais sucinta e legível e nos permitem traduzir em poucas linhas o que precisaríamos fazer com outros métodos ou estruturas de repetição, como o `forEach()`, por exemplo. Vejamos agora a definição desses métodos e logo em seguida um tutorial de como utilizá-los.

## map()

O método `map()` executa uma função em todos os itens de um array. Seu objetivo é realizar uma determinada operação em cada elemento da lista.
O `map()` retorna um novo array após a manipulação, ou seja, não altera o array original.

Imaginemos que logo abaixo temos os preços de alguns produtos:

```javascript
const preçoProduto = [34.5, 90.3, 56.5, 85.8];
```

E queremos aumentar o preço deles. Para isso, podemos criar uma nova lista que vai receber os valores da lista original após a aplicação do `map()`:

```javascript
const novosPreços = preçoProduto.map(preco => {
    return preco * 1.5;
});

console.log(novosPreços);
```

O resultado será:
`
[51.75, 135.45, 84.75, 128.7]
`

Nesse exemplo, o map() percorreu cada preço da lista e multiplicou seu valor por 1.5. Dessa forma, cada produto teve seu preço aumentado em 50%.

A lista original continua com os mesmos valores:
```javascript
console.log(preçoProduto);
```

Resultado:
`
[34.5, 90.3, 56.5, 85.8]
`

## filter()
O método `filter()` é utilizado quando queremos selecionar determinados elementos de um array de acordo com uma condição. Diferentemente do `map()`, que transforma os elementos, o `filter()` verifica quais elementos atendem à condição definida e coloca esses elementos em um novo array.

Por exemplo, podemos ter uma lista contendo notas:
```javascript
const notas = [5, 2, 3.5, 7, 8.5, 10, 9.4, 7.9, 9];
```

Supondo que queremos obter somente as notas maiores ou iguais a 7, podemos utilizar o `filter()`:

```javascript
const notasAltas = notas.filter(nota => nota >= 7);

console.log(notasAltas);
```

O resultado será:

`
[7, 8.5, 10, 9.4, 7.9, 9]
`


Nesse caso, o `filter()` percorre cada nota e verifica se ela é maior ou igual a 7. Quando a condição é verdadeira, a nota é adicionada ao novo array. Quando a condição é falsa, ela não é adicionada.
Dessa forma, conseguimos separar somente as notas que atendem à condição que definimos.

## reduce()
O método `reduce()` possui uma utilização um pouco diferente dos métodos anteriores. Ele é utilizado para percorrer os elementos de um array e acumular informações até chegar a um resultado final.
Para isso, o `reduce()` utiliza um acumulador, que é responsável por armazenar o resultado durante a execução.
O acumulador pode assumir diferentes tipos, dependendo do que queremos fazer. Ele pode ser um número, uma string, um array ou até mesmo um objeto.
Um exemplo simples seria utilizar o `reduce()` para somar os valores de um array:

```javascript
const numeros = [1, 2, 3, 4, 5];

const soma = numeros.reduce((acumulador, numero) => {
    return acumulador + numero;
}, 0);

console.log(soma);
```

O resultado será:
`
15
`

Nesse exemplo, o acumulador começa com o valor 0 e, a cada elemento do array, recebe a soma do valor atual.

Porém, o reduce() não serve apenas para fazer cálculos. Ele também pode ser utilizado para contar ocorrências de informações dentro de uma lista.

## Contando ocorrências

Imagine que temos uma lista de produtos e alguns deles possuem a mesma categoria:

```javascript
const produtos = [
    { nome: "Notebook", categoria: "Eletrônico" },
    { nome: "Celular", categoria: "Eletrônico" },
    { nome: "Cadeira", categoria: "Móvel" },
    { nome: "Mesa", categoria: "Móvel" },
    { nome: "Fone", categoria: "Eletrônico" }
];
```

Nesse caso, temos três produtos da categoria Eletrônico e dois da categoria Móvel.
Podemos utilizar o reduce() para contar essas ocorrências:

```javascript
const ocorrencias = produtos.reduce((acumulador, produto) => {
    acumulador[produto.categoria] =
        (acumulador[produto.categoria] || 0) + 1;

    return acumulador;
}, {});

console.log(ocorrencias);
```

O resultado será:

`
{
    Eletrônico: 3,
    Móvel: 2
}
`

Nesse exemplo, o acumulador começa como um objeto vazio:

`
{}
`

A cada produto que o reduce() encontra, ele verifica qual é a categoria desse produto.

A expressão:

```javascript
acumulador[produto.categoria] || 0
```

verifica se aquela categoria já possui uma quantidade registrada no acumulador. Caso ainda não exista, o valor utilizado será 0.

Depois, adicionamos 1:

```javascript
(acumulador[produto.categoria] || 0) + 1
```

Dessa maneira, cada vez que uma categoria aparece, sua quantidade é aumentada.

Ao final da execução, temos:

```javascript
{
    Eletrônico: 3,
    Móvel: 2
}
```

Nesse exemplo, o acumulador está sendo utilizado como um objeto para armazenar a quantidade de ocorrências de cada categoria.

## Utilizando os métodos juntos

Além de utilizar `map()`, `filter()` e `reduce()` separadamente, também podemos utilizar os três em sequência.

Por exemplo:

```javascript
const numeros = [1, 2, 3, 4, 5, 6];

const resultado = numeros
    .filter(numero => numero % 2 === 0)
    .map(numero => numero * 2)
    .reduce((acumulador, numero) => acumulador + numero, 0);

console.log(resultado);
```

O resultado será:

`
24
`

Nesse exemplo, cada método realiza uma parte da operação.

Primeiro, o `filter()` seleciona somente os números pares:

`
[2, 4, 6]
`

Depois, o `map()` dobra cada um desses valores:

`
[4, 8, 12]
`

Por último, o `reduce()` soma os valores:

`
4 + 8 + 12 = 24
`

Assim, o resultado final é `24`.

## Conclusão

O `map()` pode ser utilizado para transformar os elementos de uma lista, o `filter()` para selecionar elementos que atendam a uma determinada condição e o `reduce()` para acumular informações e gerar um resultado final.
