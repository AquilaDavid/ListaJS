# Métodos filter, map e reduce no JavaScript

## ✨ Introdução

Os métodos `filter`, `map` e `reduce` fazem parte do arsenal funcional do JavaScript para manipulação de arrays. Cada um possui uma finalidade específica e torna o código mais expressivo, legível e eficiente quando usado corretamente. Este documento traz uma visão geral com vantagens, desvantagens, callbacks e exemplos comentados para facilitar o aprendizado e consulta rápida.

Este documento apresenta vantagens, desvantagens, exemplos práticos e explicações detalhadas sobre os métodos `filter`, `map` e `reduce` no JavaScript.

---

## Método `filter`

### ✅ Vantagens

* Simplicidade e clareza para operações de filtragem.
* Não modifica o array original (imutável).
* Funciona bem em conjunto com outros métodos (encadeamento).

### ❌ Desvantagens

* Retorna um novo array mesmo que nenhum item passe no filtro.
* Pode ser menos eficiente em arrays muito grandes.

### 🔄 Callback

Parâmetros aceitos:

```js
(currentValue, index, array)
```

O callback recebe o valor atual do array, o índice atual e o array original. A função deve retornar `true` para manter o item ou `false` para descartá-lo. Internamente, o método percorre cada item e executa o callback sequencialmente para decidir se inclui ou não o elemento no novo array.

### 📝 Exemplos

```js
// Exemplo 1️⃣: Filtrar números pares
const nums = [1, 2, 3, 4, 5, 6];
const pares = nums.filter(n => n % 2 === 0);
console.log(pares); // [2, 4, 6]

// Exemplo 2️⃣: Filtrar palavras com mais de 5 letras
const palavras = ['casa', 'computador', 'sol', 'programação'];
const longas = palavras.filter(p => p.length > 5);
console.log(longas); // ['computador', 'programação']

// Exemplo 3️⃣: Filtrar objetos por propriedade
const usuarios = [
    { nome: 'Ana', ativo: true },
    { nome: 'Carlos', ativo: false },
    { nome: 'João', ativo: true }
];
const ativos = usuarios.filter(user => user.ativo);
console.log(ativos);
// [{ nome: 'Ana', ativo: true }, { nome: 'João', ativo: true }]
```

---

## Método `map`

### ✅ Vantagens

* Excelente para transformar valores de arrays.
* Mantém o array original intacto.
* Sintaxe simples e declarativa.

### ❌ Desvantagens

* Retorna sempre um array do mesmo tamanho.
* Não é ideal para efeitos colaterais (não transforma estado externo).

### 🔄 Callback

Parâmetros aceitos:

```js
(currentValue, index, array)
```

O callback recebe o valor atual, o índice atual e o array original. A função deve retornar o novo valor para substituir o item correspondente no novo array. O método aplica essa transformação para cada item, criando um array do mesmo tamanho com os valores transformados.

### 📝 Exemplos

```js
// Exemplo 1️⃣: Dobrar os números
const numeros = [1, 2, 3];
const dobrados = numeros.map(n => n * 2);
console.log(dobrados); // [2, 4, 6]

// Exemplo 2️⃣: Extrair nomes de objetos
const pessoas = [
    { nome: 'Maria', idade: 30 },
    { nome: 'Lucas', idade: 25 }
];
const nomes = pessoas.map(p => p.nome);
console.log(nomes); // ['Maria', 'Lucas']

// Exemplo 3️⃣: Transformar strings em uppercase
const frutas = ['maçã', 'banana', 'uva'];
const maiusculas = frutas.map(f => f.toUpperCase());
console.log(maiusculas); // ['MAÇÃ', 'BANANA', 'UVA']
```

---

## Método `reduce`

### ✅ Vantagens

* Muito versátil: transforma arrays em qualquer tipo de valor (número, string, objeto).
* Ótimo para cálculos acumulativos e agregações complexas.

### ❌ Desvantagens

* Mais difícil de entender para quem está começando.
* Requer atenção ao valor inicial.

### 🔄 Callback

Parâmetros aceitos:

```js
(acumulador, currentValue, index, array)
```

O callback recebe o acumulador (resultado parcial até o momento), o valor atual, o índice atual e o array original. O método também aceita um segundo argumento opcional para definir o valor inicial do acumulador. A cada iteração, o retorno do callback se torna o novo acumulador, até que todos os elementos sejam processados, produzindo um único resultado final.

### 📝 Exemplos

```js
// Exemplo 1️⃣: Somar números
const nums = [1, 2, 3, 4];
const soma = nums.reduce((acc, n) => acc + n, 0);
console.log(soma); // 10

// Exemplo 2️⃣: Contar ocorrências de letras
const letras = ['a', 'b', 'a', 'c', 'b', 'a'];
const contagem = letras.reduce((acc, letra) => {
    acc[letra] = (acc[letra] || 0) + 1;
    return acc;
}, {});
console.log(contagem); // { a: 3, b: 2, c: 1 }

// Exemplo 3️⃣: Criar uma string a partir de array
const palavras = ['Olá', 'mundo', '!'];
const frase = palavras.reduce((acc, palavra) => acc + ' ' + palavra);
console.log(frase); // 'Olá mundo !'
```
