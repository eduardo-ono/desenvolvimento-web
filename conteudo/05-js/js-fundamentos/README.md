> ### Desenvolvimento Web (Front-End)

# JavaScript - Fundamentos da Linguagem

Prof. Eduardo Ono

<br>

## Descrição

<br>

## Fundamentos da Linguagem

<details>
  <summary>
    <strong>Variáveis e Constantes</strong>
  </summary>
  <section markdown="1">

  * **_const_**

  ```js
  const pi = 3.14;
  pi = 3.1416;
  const e; // ERRO! Constante não inicializada
  ```

  * **_var_ e _let_ (ES6)**

  ```js
  var num = 10;
  num2 = 5; // ERRO! Variável não declarada

  for (i = 0; i < 6; i++)
  {
    console.log(i);
  }
  console.log('Valor de i = ' + i);


  for (var i = 0; i < 6; i++)
  {
    console.log(i);
  }
  console.log('Valor de i = ' + i);


  for (let i = 0; i < 10; i++)
  {
    console.log(i);
  }
  console.log('Valor de i = ' + i); // ERRO! A variável i não foi "definida".
  ```

  </section>
</details>

<details>
    <summary>
      <strong>Funções Anônimas</strong>
    </summary>

```js
//  Função tradicional:
function calcularIMC(peso, altura) {
    let imc = 0;
    if (peso > 0 && altura > 0) {
        imc = peso / (altura ** 2);
    }
    return imc;
}

let imc = calcularIMC(67, 1.73);
console.log(imc.toFixed(1));

// Função Anônima (função que não possui um nome):
const calcularImc = (peso, altura) => {
    let imc = 0;
    if (peso > 0 && altura > 0) {
        imc = peso / (altura ** 2);
    }
    return imc;
}

console.log(calcularImc(67, 1.73).toFixed(1));

// Função Anônima "auto-executável":
(function () {
    var now = new Date();
    var time = ("0" + now.getHours()).slice(-2) + ":" +
        ("0" + now.getMinutes()).slice(-2) + ":" +
        ("0" + now.getSeconds()).slice(-2);
    console.log(time);
})();
```

</details>

<details>
  <summary>
    <strong>Vetores (Arrays)</strong>
  </summary>

```js
const frutas = [ 'maçã', 'laranja', 'pera' ];
frutas[3] = 'uva'; // Cuidado!
frutas.push('manga'); // Insere como último elemento
frutas.unshift('morango'); // Insere como primeiro elemento
frutas.pop(); // Remove o último elemento
console.log(Array.isArray(frutas));
console.log(frutas);
console.log(frutas.indexOf('laranja'));

const coisas = [ 'maçã', 'laranja', 10, true ];
console.log(Array.isArray(frutas)); // => true
console.log(coisas);
 ```

</details>

<details>
  <summary>
    <strong>Objetos Literais</strong>
  </summary>

  * **Objetos**

  ```js
  const pessoa = {
    nome: 'Fulano',
    sobrenome: 'de tal',
    idade: 91,
    hobbies: [ 'música', 'filmes', 'esporte' ],
    endereco: {
      rua: 'Francisco Glicério',
      numero: 1,
      cidade: 'Campinas',
      uf: 'SP'
    },
  };

  console.log(pessoa);
  console.log(pessoa.nome, pessoa.sobrenome);
  console.log(pessoa.hobbies[1]); // => filmes
  console.log(pessoa.endereco.cidade); // Campinas

  pessoa.email = 'fulano@umbrella.com';
  console.log(pessoa);
  ```

  * **Vetor de Objetos**

```js
const musicas = [
  {
    id: 'aaaaaaaa',
    musica: 'Sultans of Swing',
    album: 'Dire Straits',
    artista: 'Dire Straits',
    ano: 1978,
  },
  {
    id: 'bbbbbbbb',
    musica: 'Tears in Heaven',
    album: 'Unplugged',
    artista: 'Eric Clapton',
    ano: 1992,
  },
  {
    id: 'ccccccccc',
    musica: 'So far Away',
    album: 'Brothers in Arms',
    artista: 'Dire Straits',
    ano: 1985,
  },
];

console.log(musicas);

const json = JSON.stringify(musicas);
console.log(json);

var str = '\n';
for (let i = 0; i < musicas.length; i++)
{
  str += 'Música: ' + musicas[i]['musica'] + '\n';
  str += 'Artista: ' + musicas[i]['artista'] + '\n';
  str += 'Album: ' + musicas[i]['album'] + '\n';
  str += 'Ano: ' + musicas[i]['ano'] +'\n\n';
}
console.log(str);

// ES6
str = '\n';
for (let i = 0; i < musicas.length; i++)
{
  str += `Música: ${musicas[i]['musica']}\n`;
  str += `Artista: ${musicas[i]['artista']}\n`;
  str += `Album: ${musicas[i]['album']}\n`;
  str += `Ano: ${musicas[i]['ano']}\n\n`;
}
console.log(str);

console.log('--- forEach ---');
musicas.forEach(function (elemento) {
  console.log(elemento.musica);
});

console.log('\n--- forEach (ES6) ---');
musicas.forEach( elemento => {
  console.log(elemento.musica);
});
```

</details>

<details>
    <summary>
      <strong>Arrow Functions</strong>
    </summary>

Função tradicional:

```js
function calcularIMC(peso, altura) {
    var imc = 0;
    if (peso > 0 && altura > 0) {
        imc = peso / (altura ** 2);
    }
    return imc;
}
```

Arrow Function:

```js
const imc = (peso, altura) => {
    var imc = 0;
    if (peso > 0 && altura > 0) {
        imc = peso / (altura ** 2);
    }
    return imc;
}

console.log(imc(68, 1.73).toFixed(1));

// ou

const imc = (peso, altura) => (peso > 0 && altura > 0) ? peso / (altura ** 2) : 0;

console.log(imc(68, 1.73).toFixed(1));
```

Arrow Function "auto-executável"

```js
(() => {
    var now = new Date();
    var time = ("0" + now.getHours()).slice(-2) + ":" +
        ("0" + now.getMinutes()).slice(-2) + ":" +
        ("0" + now.getSeconds()).slice(-2);
    console.log(time);
})();
```

  * **Arrow Function retornando um JSON**

```js
const pessoa = () => {
    return {"nome": "Fulano de Tal"};
}
// ou
const pessoa = () => ({"nome": "Fulano de Tal"});

console.log(pessoa());
```

</details>

<br>

### Vídeos Aulas

| Thumb | Descrição |
| :-: | --- |
| ![Thumb](https://img.youtube.com/vi/fju9ii8YsGs/default.jpg) | [Derek Banas]<br>[**JavaScript Tutorial**](https://www.youtube.com/watch?v=fju9ii8YsGs) (YouTube, 1:37:08, Set/2015)<br><br>Tópicos:
| ![Thumb](https://img.youtube.com/vi/hdI2bqOjy3c/default.jpg) | [Traversy Media]<br>[**JavaScript Crash Course for Beginners**](https://www.youtube.com/watch?v=hdI2bqOjy3c) (YouTube, 1:40:29, Mar/2019)<br><br>Tópicos: [Arrays](https://www.youtube.com/watch?v=hdI2bqOjy3c&t=1432s); [Objetos Literais](https://www.youtube.com/watch?v=hdI2bqOjy3c&t=1808s)
| ![Thumb](https://img.youtube.com/vi/NCwa_xi0Uuc/default.jpg) | [Programming with Mosh]<br>[**ES6 Tutorial: Learn Modern JavaScript in 1 Hour**](https://www.youtube.com/watch?v=NCwa_xi0Uuc) (YouTube, 50:04, Jun/2018)<br><br>Tópicos:


* [Derek Banas] [ECMAScript 6 Tutorial](https://youtu.be/Jakoi0G8lBg) (YouTube, 45:30)
* [Academind] [JavaScript Data Structures: Getting Started](https://youtu.be/41GSinwoMYA) (YouTube, 1:36:46)

<br>

## JavaScript Orientado a Objetos

### Vídeos Recomendados

* [Derek Banas] [Object Oriented JavaScript](https://youtu.be/O8wwnhdkPE4) (YouTube, 1:00:34)
* [Traversy Media] [JavaScript OOP Crash Course (ES5 & ES6)](https://youtu.be/vDJpGenyHaA) (YouTube, 40:20)

<br>

## Canais do YouTube Recomendados

* [queroser.ninja - Fernando Daciuk](https://www.youtube.com/channel/UCoMS25HuclMfa6IQJNcvh2w)

<br>

## Referências Bibliográficas

* FLANAGAN, David. [JavaScript - O Guia Definitivo, 6 ed.](https://www.academia.edu/40442620/JavaScript_O_Guia_Definitivo_v), Porto Alegre: Bookman, 2013.
* [JavaScript Notes for Professionals](https://goalkicker.com/HTML5Book/) (PDF)

<br>
