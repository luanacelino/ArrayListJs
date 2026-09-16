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
