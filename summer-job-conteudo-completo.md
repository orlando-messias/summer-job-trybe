# As Higher Order Functions MAP e REDUCE

## O que vamos aprender?

As últimas atualizações do Javascript trouxeram funcionalidades muito importantes e com grande enfoque em produtividade. Em se tratando de manipulação de dados, por exemplo, foram implementadas as funções **MAP** e **REDUCE** que garantem maior flexibilidade no tratamento de dados e permitem organizar e extrair informações de qualquer base de dados de maneira muito prática.

## Você será capaz de:
- Utilizar a **Função Map** para modificar dados de uma coleção e armazená-los como uma nova coleção;

- Utilizar a **Função Reduce** para extrair e obter informações importantes de um conjunto de dados e moldá-los à sua necessidade.

## Por que isso é importante?
Manipular dados é uma atividade comum na vida de um desenvolvedor e saber dominar as melhores ferramentas é importante para a produtividade na hora de programar. Uma grande massa de dados pode vir de um banco de dados ou de uma requisição a um servidor, por exemplo, e chegar à sua aplicação de forma desordenada. Você, como um bom desenvolvedor, precisa saber tratar, organizar e refinar estes dados para que eles possam ser utilizados da melhor maneira na sua aplicação.

## Conteúdos
:orange_book: Tempo sugerido para realização: 30 minutos

**MAP** e **REDUCE** são *Higher Order Functions*, ou seja, funções que recebem como parâmetro uma outra função contendo a lógica do que precisa ser realizado, modificado ou transformado a partir de um conjunto de dados. As funções que são passadas como parâmetro são chamadas de *callback* (em tradução literal, "*chamar novamente*"), isto porque elas são invocadas novamente pra cada elemento do array. **Map** e **Reduce** já possuem em seu *core*, em seu escopo, a funcionalidade de iterar sobre cada item de um array.

### Map: Conceito e Aplicação
A finalidade da função **map** é percorrer um array e aplicar, a cada item, alguma alteração, alguma transformação e armazenar o resultado em um novo array sem, no entanto, modificar o original. Como exemplo inicial, imagine uma lista de valores em formato dólar que precisam ser convertidos para a moeda real. 

Veja como seria o exemplo utilizando o comando `for`:

```javascript
const dollarToday = 5.51;   // contém o valor atual do dólar
const dollarValues = [2.35, 11, 7.3, 27.5, 200];  // array de valores em dólar
let realValues = [];  //  array inicial

for (let i = 0; i < dollarValues.length; i += 1) {
  realValues.push(dollarValues[i] * dollarToday);  //  lógica aplicada para cada item do array
}

console.log(realValues);  // [12.9485, 60.61, 40.223, 151.525, 1102]
```

Observe que foi utilizada uma quantidade considerável de código para a solução do problema, isto porque a própria estrutura do ```for``` necessita deste cenário, inclusive de uma variável extra para atingir seu objetivo, neste caso a variável ***i***.

Uma maneira mais prática e funcional de fazer o mesmo é utilizar a função **map**, passando  pra ela, via parâmetro, uma função contendo a lógica que fará a conversão de cada valor para a moeda real. A partir daí, **map** utilizará a mesma lógica para cada item do array.

Observe o exemplo abaixo:

```javascript
const realValues = dollarValues.map(function(value) {
  return value * dollarToday;
});
```

Veja que a função anônima passada via parâmetro pro **map** contém a lógica da conversão da moeda dólar pra real. A cada iteração no array, esta lógica será chamada novamente - *callback* - e trabalhará junto com o parâmetro ***value***, que neste exemplo é o parâmetro que representará o valor do elemento da vez a cada iteração. Observe que, diferente do comando `for`, não houve necessidade de usar uma variavel para iterar e nem tampouco dar `push` no array de destino. 

De maneira completa:

```javascript
const dollarToday = 5.51;
const dollarValues = [2.35, 11, 7.3, 27.5, 200];

const realValues = dollarValues.map(function(value) {
  return value * dollarToday;
});

console.log(realValues);  // [12.9485, 60.61, 40.223, 151.525, 1102]
```

Como dito anteriormente, a função **map** não modificará o array original ***dollarValues***, por isto o resultado foi armazenado em outro local, neste caso na constante ***realValues***.
Para tornar ainda mais funcional, utilize uma arrow function no lugar da function comum.

```javascript
const dollarToday = 5.51;
const dollarValues = [2.35, 11, 7.3, 27.5, 200];

const realValues = dollarValues.map((value) => value * dollarToday);

console.log(realValues);  // [12.9485, 60.61, 40.223, 151.525, 1102]
```
Onde **```(value) => value * dollarToday```** é a arrow function que ensina a este map o que fazer com cada valor do array original ***dollarValues***. Neste caso, foi dado o nome de ***value*** pra cada item do array e em seguida o que deve ser feito com cada um. Daí então, esta lógica é *called back* (chamada novamente) sempre que a função **map** iterar para o próximo item. Ao final da iteração, a constante ***realValues*** conterá um array com todos os novos valores convertidos e a constante ***dollarValues*** permanecerá com seus valores originais, sem qualquer alteração.

Veja agora um exemplo utilizando strings:

```javascript
const names = ['Ariana', 'Emilly', 'osmar', 'Jhon', 'VICENTE', 'Ivan'];
const lowerNames = names.map((name) => name.toLowerCase());

console.log(lowerNames);  // ['ariana', 'emilly', 'osmar', 'jhon', 'vicente', 'ivan']
```

Onde **```(name) => name.toLowerCase()```** é a arrow function que ensina a este **map** o que fazer com cada nome do array ***names***. Neste caso, eles estão sendo convertidos para letras minúsculas através da função `toLowerCase()`.

No próximo exemplo você tem disponível um array de objetos e dele será retornado um array de strings com os nomes de cada veículo:

```javascript
const vehicles = [
  { cod: 'c9880', name: 'A3 Sedan', brand: 'Audi' },
  { cod: '2a193', name: 'HB20', brand: 'Hyundai' },
  { cod: 'c4d23', name: 'Tucson', brand: 'Hyundai' },
  { cod: '3a256', name: 'Captur', brand: 'Renault' },
  { cod: 'ba210', name: 'Ecosport', brand: 'Ford' },
  { cod: 'hc502', name: 'Duster', brand: 'Renault' },
];

const vehicleNames = vehicles.map((vehicle) => vehicle.name);

console.log(vehicleNames);  // ['A3 Sedan' 'HB20', 'Tucson', 'Captur', 'Ecosport', 'Duster']
```

Onde **```(vehicle) => vehicle.name```**  retorna apenas a propriedade *name* de cada objeto do array ***vehicles***.

Abaixo você tem um exemplo de como retornar, além do nome do veículo, a sua marca. Veja como fica a escrita:

```javascript
const vehicleNames = vehicles.map((vehicle) => {
  return {  // é necessário abrir chaves caso o corpo do return contenha mais de uma linha ou comando
    name: vehicle.name,
    brand: vehicle.brand,
  }
}); 

console.log(vehicleNames);
/*
  [
    { name: 'A3 Sedan', brand: 'Audi' },
    { name: 'HB20', brand: 'Hyundai' }
    { name: 'Tucson', brand: 'Hyundai' },
    { name: 'Captur', brand: 'Renault' },
    { name: 'Ecosport', brand: 'Ford' },
    { name: 'Duster', brand: 'Renault' },
  ]
*/
```

**Map** também disponibiliza um índice que pode ser utilizado a cada iteração. Isto é interessante porque, como você já estudou, cada item de um array também possui um índice, então desta forma é possível combiná-los - índice do map e do array - para obter resultados ainda mais dinâmicos. No próximo exemplo, a função **map** receberá um índice chamado ***index*** que, assim como os índices de um array, começa valendo 0.

```javascript
const vehicles = [
  { cod: 'c9880', name: 'A3 Sedan', brand: 'Audi' },
  { cod: '2a193', name: 'HB20', brand: 'Hyundai' },
  { cod: 'c4d23', name: 'Tucson', brand: 'Hyundai' },
  { cod: '3a256', name: 'Captur', brand: 'Renault' },
  { cod: 'ba210', name: 'Ecosport', brand: 'Ford' },
  { cod: 'hc502', name: 'Duster', brand: 'Renault' },
];

const vehicleNames = vehicles.map((vehicle, index) => (
  `<tr>
    <td>${index + 1}</td>
    <td>${vehicle.name}</td>
  </tr>`
));
```

O exemplo acima gera, para cada iteração da função **map**, uma nova linha `tr` e, pra cada nova linha, duas colunas `td`, na construção de uma tabela qualquer. Ele adiciona na primeira coluna um número para o veículo e na segunda coluna o nome, construindo assim o código HTML das linhas de uma tabela com valores do array ***vehicles***.

### Reduce: Conceito e Aplicação
**Reduce**, assim como **map**, também percorre um array, porém ao invés de sempre retornar um novo array modificado, ele abstrai todos os itens e os reduz trazendo como resultado uma informação concreta que pode ser em qualquer formato: um outro array, uma string, um boolean, um objeto, enfim, ele transformará os dados e os reduzirá no formato que você definir. Um exemplo prático seria uma lista de produtos em que é necessário calcular o resultado da soma dos preços de todos eles.

Resolvendo o problema utilizando o comando `for`:

```javascript
const productsPrices = [200, 59.9, 1300, 170, 225.8];
let sum = 0;  // nosso acumulador;

for (let i = 0; i < productsPrices.length; i += 1) {
  sum = sum + productsPrices[i];
}

console.log('Result: ', sum);   // Result: 1955.7
```

Você pode resolver o mesmo problema de maneira mais prática utilizando **reduce**. Antes, veja a sintaxe:

```
array.reduce(funcao_base, valor_inicial)
```


onde | refere-se a
------------ | -------------
*funcao_base* | uma funcao, de preferência arrow function, que conterá as regras de negócio, a lógica que será executada pra cada item do array;
*valor_inicial*| o valor inicial para o cálculo.

Para este exemplo, utilize um número como *valor_inicial* porque será necessário retornar um número como valor final, mas em outra situação e dependendo da sua necessidade, você poderá utilizar um boolean, caso queira retornar um boolean, ou um objeto com alguma propriedade inicial, caso pretenda retornar um objeto, ou qualquer outra coisa, pois o **reduce** pode retornar qualquer informação a partir de um valor inicial.

##### Dissecando a *funcao_base*:
```
array.reduce((acumulador, valor_atual) => logica, valor_inicial)
```

onde | refere-se a
------------ | -------------
*acumulador* | à medida que o **reduce** vai iterando pelos elementos do array, o resultado vai acumulando nesta variável. Na primeira iteração, seu valor é o mesmo que *valor_inicial*;
*valor_atual*| o elemento da vez naquela iteração. Tomando o array ***productsPrices*** como exemplo, na primeira iteração *valor_atual* valerá 200, na segunda iteração 59.9 e assim por diante até o último elemento do array;
*logica*	| a lógica da função que será utilizada para o resultado.


E finalmente você poderá usar o **reduce** para resolver o caso acima. Neste exemplo, o resultado será armazenado na constante ***sumOfPrices***:

```javascript
const productsPrices = [200, 59.9, 1300, 170, 225.8];
const sumOfPrices = productsPrices.reduce((acc, current) => acc + current, 0);

console.log('Result: ', sumOfPrices);  // Result: 1955.7
```

Resultados das iterações do código acima passo a passo: |
------------ |
1ª iteração: (**0**, 200) => 0 + 200  → **200** |
2ª iteração: (**200**, 59.9) => 200 + 59.9 → **259.9** |
3ª iteração: (**259.9**, 1300) => 259.9 + 1300 → **1559.9** |
4ª iteração: (**1559.9**, 170) => 1559.9 + 170 → **1729.9** |
5ª iteração: (**1729.9**, 225.8) => 1729.9 + 225.8 → **1955.7** |

Se houver necessidade de aplicar mais lógica à função que foi passada como parâmetro, basta abrir chaves `{` e utilizar o `return`. Abaixo estão sendo somados apenas os números pares de um array de números:

```javascript
const numbers = [2, 5, 8, 7, 1, 0, 22, 4];
const sumOfEven = numbers.reduce((acc, cur) => {
  if (cur % 2 === 0) return acc + cur;
  return acc;
}, 0);

console.log('Result: ', sumOfEven);  // Result: 36
```

##### Aprofundando um pouco mais:

Observe o array de produtos abaixo:

```javascript
const products = [
  { product: 'Refrigerador 371L', price: 2600 },
  { product: 'Lavadora de Roupas 13kg', price: 1550 },
  { product: 'Cooktop 5 bocas', price: 489 },
  { product: 'Smartphone Tela 6.55', price: 1299 },
  { product: 'Home Theater Entrada USB', price: 880.9 },
  { product: 'Tv Led 4K', price: 2198 },
  { product: 'Forno Microondas 20L', price: 450 },
  { product: 'Cooktop 4 bocas', price: 370 },
  { product: 'Lavadora de Roupas 11kg', price: 1390 },
];
```

Vocẽ pode utilizar o **reduce** para obter como saída um objeto único que agrupe os produtos por preços no formato abaixo:

```javascript
{
  expensive: [],
  cheap: [],
}
```

Considere, para este exemplo, que os preços abaixo de 500 são acessíveis e os preços a partir de 500 são considerados caros. Ao final, você obterá os produtos separados entre acessíveis e caros.

```javascript
const objGroupedByPrice = products.reduce((acc, cur) => {
  const expensiveOrCheap = cur.price > 500 ? 'expensive' : 'cheap';
  acc[expensiveOrCheap].push(cur);
  return acc;
}, { expensive: [], cheap: [] });
```

**Detalhando:**

**```expensiveOrCheap```** - constante que armazena, a cada iteração, uma string que identifica se o preço daquele produto da vez é considerado *"expensive"* ou *"cheap"*.

**```acc[expensiveOrCheap]```** - sabendo da informação de que o produto da vez é *"expensive"* ou *"cheap"*, adicione-o no objeto ***acc*** em sua chave correspondente.

**```{ expensive: [], cheap: [] }```** - valores iniciais do objeto que será construído.

Resultado final após **reduce**:

```javascript
objGroupedByPrice: {
  cheap: [
    { product: 'Cooktop 5 bocas', price: 489 },
    { product: 'Forno Microondas 20L', price: 450 },
    { product: 'Cooktop 4 bocas', price: 370 },
  ],
  expensive: [
    { product: 'Refrigerador 371L', price: 2600 },
    { product: 'Lavadora de Roupas 13kg', price: 1550 },
    { product: 'Smartphone Tela 6.55', price: 1299 },
    { product: 'Home Theater Entrada USB', price: 880.9 },
    { product: 'Tv Led 4K', price: 2198 },
    { product: 'Lavadora de Roupas 11kg', price: 1390 },
  ],
};
```

## Exercícios
:orange_book: Tempo sugerido para realização: 60 minutos

Hora de por a mão na massa!
1. Observe as funções anônimas passadas via parâmetro para cada **map** e converta-as em arrow functions:

```javascript
const numbers = [9, 27, 33, 201, 15];
const doubleNumbers = numbers.map(function(number) {
  return number * 2;
});
```

```javascript
const ages = [15, 19, 21, 18, 13, 42, 17, 38];
const underOrOverAges = ages.map(function(age) {
  return age < 18 ? 'underage' : 'overage';
});
```

```javascript
const fahrenheit = [22, 35, 1, 105, 72, 56];
const celsius = fahrenheit.map(function(temperature) {
  return Math.round((temperature - 32) * 5 / 9);
});
```

```javascript
const cities = [
  { city: 'Sete Lagoas', population: 208847 },
  { city: 'Cláudio', population: 28617 },
  { city: 'Ouro Preto', population: 70227 },
  { city: 'Capitólio', population: 7634 },
];
const citiesPopulation = cities.map(function(city) {
  return city.population;
});
```

2. Utilizando a função **map**, crie um array de inteiros que contenha somente a quantidade de clicks de cada curso:
```javascript
const courses = [
  { course: 'How to make a website using HTML/CSS', numberOfClicks: 970, level: 'beginner' },
  { course: 'Learn Javascript', numberOfClicks: 1240, level: 'beginner' },
  { course: 'Mysql Fundamentals', numberOfClicks: 1682, level: 'beginner' },
  { course: 'Python', numberOfClicks: 705, level: 'intermediate' },
  { course: 'ReactJs: Getting Started', numberOfClicks: 1712, level: 'beginner' },
  { course: 'Build a Rest API with Nodejs', numberOfClicks: 1041, level: 'intermediate' },
  { course: 'MongoDB Tutorial for Beginners', numberOfClicks: 408, level: 'beginner' },
  { course: 'Introduction to Ruby', numberOfClicks: 133, level: 'beginner' },
  { course: 'Learning Linux Training', numberOfClicks: 277, level: 'intermediate' },
];
```

3. Dada a relação de funcionários abaixo, todos os salários devem ser reajustados com aumento de 5.7%. Crie um novo array com os dados dos funcionários e seus novos salários. Salários devem conter 2 casas decimais:
```javascript
const employees = [
  { id: 1, name: 'Gustavo Trindade', salary: 2500.3 },
  { id: 2, name: 'Arnaldo Costa', salary: 3700 },
  { id: 3, name: 'Cintia Fonseca', salary: 3280 },
  { id: 4, name: 'Fabiano Lacerda', salary: 3300.6 },
  { id: 5, name: 'Gabriela Silva', salary: 2200.5 },
  { id: 6, name: 'Hugo Cabral', salary: 2690 },
  { id: 7, name: 'Helena Soares', salary: 2280.7 },
];
```

4. Crie um novo array que contenha: os títulos dos vídeos em letras minúsculas, a quantidade de views, a quantidade de likes e a duração do vídeo convertida em minutos exibindo 3 casas decimais:
```javascript
const videos = [
  {
    title: '[LIVE] Codenation agora é Trybe! Bate-papo com CEOs',
    views: '1k',
    likes: 170,
    duration: 3836,
  },
  {
    title: 'Trybe: Uma escola do futuro e para o futuro',
    views: '408k',
    likes: 184,
    duration: 71,
  },
  {
    title: 'DEPOIMENTO: Pedro Tófani - Estudante da Turma 2 | Trybe',
    views: '8.7k',
    likes: 54,
    duration: 174,
  },
  {
    title: '#EuSouTryber | TRYBE 1 ANO',
    views: '4k',
    likes: 160,
    duration: 225,
  },
  {
    title: '[LIVE] Pergunte-me qualquer coisa sobre modalidade Sem Hub',
    views: '1.6k',
    likes: 191,
    duration: 4251,
  },
  {
    title: 'Curso introdutório de Javascript GRATUITO - Dicas para aproveitar ao máximo',
    views: '8.6k',
    likes: 118,
    duration: 76,
  },
  {
    title: 'Tipos Primitivos - Curso Introdutório de JavaScript GRATUITO',
    views: '7.8k',
    likes: 121,
    duration: 477,
  },
  {
    title: '[LIVE] MeeTrybe #01 | Arquitetura de Software',
    views: '1.1k',
    likes: 219,
    duration: 8055,
  },
];
```

5. Utilizando **reduce**, calcule a soma das notas das pessoas estudantes que estão aprovadas, ou seja, aquelas cujas notas são maiores ou iguais a 70:
```javascript
const students = [
  { name: 'Luciano Noronha', grade: 72 },
  { name: 'Davi Vilela', grade: 69 },
  { name: 'Priscila Mascarenhas', grade: 60 },
  { name: 'Laura Santos', grade: 89 },
  { name: 'Fernando Sampaio', grade: 91 },
  { name: 'Cristiano Nobre', grade: 57 },
  { name: 'Paula Gomes', grade: 83 },
  { name: 'Maurício Costa', grade: 60 },
  { name: 'Angela Goncalves', grade: 99 },
];
```

6. A partir do array ***courses*** crie um objeto que agrupe os cursos pelos níveis *beginner* e *intermediate*.  
`{ beginner: [], intermediate: [] }`
```javascript
const courses = [
  { course: 'How to make a website using HTML/CSS', numberOfClicks: 970, level: 'beginner' },
  { course: 'Learn Javascript', numberOfClicks: 1240, level: 'beginner' },
  { course: 'Mysql Fundamentals', numberOfClicks: 1682, level: 'beginner' },
  { course: 'Python', numberOfClicks: 705, level: 'intermediate' },
  { course: 'Build a Rest API with Nodejs', numberOfClicks: 1041, level: 'intermediate' },
  { course: 'MongoDB Tutorial for Beginners', numberOfClicks: 408, level: 'beginner' },
  { course: 'Introduction to Ruby', numberOfClicks: 133, level: 'beginner' },
  { course: 'Learning Linux Training',  numberOfClicks: 277, level: 'intermediate' },
];
```

## Bônus

1. Dado o array de objetos ***videos***, extraia somente o título, a quantidade de views e o comentário mais atual de cada video. Dica: use **map** e **reduce**:
```javascript
const videos = [
  {
    title: '[LIVE] Codenation agora é Trybe! Bate-papo com CEOs',
    views: '1k',
    likes: 170,
    duration: 3836,
    comments: [
      { date: '2020-07-19', comment: 'Live esclarecedora!' },
      { date: '2020-07-20', comment: 'Cara, eu sou LOUCO pra ser Trybe, fiz o desafio prático' },
      { date: '2020-07-18', comment: 'Salve, abram horários para noite :/' },
      { date: '2020-06-10', comment: 'Boa tarde quando vai começar a inscriçao' },
      { date: '2020-07-15', comment: 'HUB no RJ!' },
      { date: '2020-07-14', comment: 'Eu entrei na seleção da Trybe e estou em andamento ainda.' },
    ],
  },
  {
    title: 'Trybe: Uma escola do futuro e para o futuro',
    views: '408k',
    likes: 184,
    duration: 71,
    comments: [
      { date: '2020-02-05', comment: 'Show de bola. Acredite!' },
      { date: '2020-02-02', comment: 'É EAD ou presencial ???' },
      { date: '2019-12-03', comment: 'queria muito estudar com vocês, mais só posso a noite' },
      { date: '2020-03-11', comment: 'Como entramos?' },
      { date: '2019-11-26', comment: 'Fiz minha inscrição agora to estudando pra ser aprovado' },
    ],
  },
  {
    title: 'DEPOIMENTO: Pedro Tófani - Estudante da Turma 2 | Trybe',
    views: '8.7k',
    likes: 54,
    duration: 174,
    comments: [
      { date: '2020-03-12', comment: 'Vai Pedrinho!!!' },
      { date: '2020-02-07', comment: 'Quando irá ter um HUB em Brasilia ??' },
      { date: '2020-03-18', comment: 'está sendo 100% online agora por conta da pandemia' },
    ],
  },
  {
    title: '#EuSouTryber | TRYBE 1 ANO',
    views: '4k',
    likes: 160,
    duration: 225,
    comments: [
      { date: '2020-08-11', comment: 'Orgulho infinito em fazer parte! Foguete não tem ré!' },
      { date: '2020-08-15', comment: 'Demais!! Quantas conquistas em tão pouco tempo.' },
      { date: '2020-08-12', comment: 'Sensacional!!!! VQV' },
      { date: '2020-08-13', comment: 'Que video maravilhoso!! :DDDDDD' },
    ],
  },
  {
    title: '[LIVE] #PQC - Pergunte-me Qualquer Coisa sobre modalidade Sem Hub',
    views: '1.7k',
    likes: 191,
    duration: 4251,
    comments: [
      { date: '2020-03-06', comment: 'Qual dinamica do curso 1 ano é possível ser profissional?' },
      { date: '2020-03-08', comment: 'Sou iniciante qual primeiro passo para começar o curso?' },
      { date: '2020-03-07', comment: 'Sou do Guarujá. Litoral de Sao Paulo.' },
      { date: '2020-08-25', comment: 'A formação vai do básico ao full?' },
    ],
  },
  {
    title: 'Curso introdutório de Javascript GRATUITO - Dicas para aproveitar ao máximo! | Trybe',
    views: '8.7k',
    likes: 118,
    duration: 76,
    comments: [
      { date: '2020-03-01', comment: 'to adorando o material disponível no YouTube é muito bom' },
      { date: '2020-03-16', comment: 'Muito bom ótimas dicas' },
    ],
  },
  {
    title: 'Tipos Primitivos - Curso Introdutório de JavaScript GRATUITO | Trybe',
    views: '7.8k',
    likes: 121,
    duration: 477,
    comments: [
      { date: '2020-03-05', comment: 'Muito bom excelente explicação e didática parabéns' },
      { date: '2020-03-01', comment: 'além do slack posso usar aqui para tirar dúvidas?' },
      { date: '2020-03-02', comment: 'Adorei!' },
    ],
  },
  {
    title: '[LIVE] MeeTrybe #01 | Arquitetura de Software',
    views: '1.1k',
    likes: 219,
    duration: 8055,
    comments: [
      { date: '2020-07-27', comment: 'só assisti as primeiras duas palestras e achei muito bom' },
      { date: '2020-07-30', comment: 'cadê as recomendaçoes ?' },
      { date: '2020-07-25', comment: 'Igor mandou muito bem nos 1:01:01' },
      { date: '2020-07-26', comment: 'por definição temos alguns tipos dif arquitetos software' },
      { date: '2020-08-29', comment: 'O curso é pauleira mas é um esforço alegre' },
    ],
  },
];
```

2. Considerando o array do exercício anterior, calcule a média das visualizações de todos os vídeos. Dica: converta a quantidade de views para milhares, sendo *1k* = 1000 views.


## Recursos Adicionais

- [Página MDN sobre map](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
- [Página MDN sobre reduce](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)
- [W3schools sobre map](https://www.w3schools.com/jsref/jsref_map.asp)
- [W3schools sobre reduce](https://www.w3schools.com/jsref/jsref_reduce.asp)
- [Vídeo do Canal DevMedia - Map e Reduce na prática](https://www.youtube.com/watch?v=zTZNpBP-OJI&t=67s)

---
---

## Gabarito dos Exercícios

##### Exercícios Principais

**1.** Resoluções do exercício 01:
```javascript
const doubleNumbers = numbers.map((number) => number * 2);
```
```javascript
const underOrOverAges = ages.map((age) => age < 18 ? 'underage' : 'overage');
```
```javascript
const celsius = fahrenheit.map((temperature) => Math.round((temperature - 32) * 5 / 9));
```
```javascript
const citiesPopulation = cities.map((city) => city.population);
```

**2.** Resolução do exercício 02:
```javascript
const numberOfClicks = courses.map((course) => course.numberOfClicks);

// [970, 1240, 1682, 705, 1712, 1041, 408, 133, 277]
```

**3.** Resolução do exercício 03:
```javascript
const raise = employees.map(employee => Number((employee.salary * 1.057).toFixed(2)));

// [2642.82, 3910.90, 3466.96, 3488.73, 2325.93, 2843.33, 2410.70]
```

**4.** Resolução do exercício 04:
```javascript
const videosResult = videos.map((video) => {
  return {
    title: video.title.toLowerCase(),
    views: video.views,
    likes: video.likes,
    duration: Number((video.duration / 60).toFixed(2)),
  }
});

/*
[
  {
    title: "[live] codenation agora é trybe! bate-papo com ceos",
    views: "1k",
    likes: 170,
    duration: 63.93,
  },
  {
    title: "trybe: uma escola do futuro e para o futuro",
    views: "408k",
    likes: 184,
    duration: 1.18,
  },
    title: "depoimento: pedro tófani - estudante da turma 2 | trybe",
    views: "8.7k",
    likes: 54,
    duration: 2.90,
  }
  {
    title: "#eusoutryber | trybe 1 ano",
    views: "4k",
    likes: 160,
    duration: 3.75,
  },
  {
    title: "[live] pergunte-me qualquer coisa sobre modalidade sem hub",
    views: "1.6k",
    likes: 191,
    duration: 70.85,
  }
  {
    title: "curso introdutório de javascript gratuito - dicas para aproveitar ao máximo",
    views: "8.6k",
    likes: 118,
    duration: 1.27,
  },
  {
    title: "tipos primitivos - curso introdutório de javascript gratuito",
    views: "7.8k",
    likes: 121,
    duration: 7.95,
  },
  {
    title: "[live] meetrybe #01 | arquitetura de software",
    views: "1.1k",
    likes: 219,
    duration: 134.25,
  },
]
*/
```

**5.** Resolução do exercício 05:
```javascript
const sumOfApproved = students.reduce((acc, cur) => cur.grade >= 70 ? acc + cur.grade : acc, 0);

// 434
```

**6.** Resolução do exercício 06:
```javascript
const objGroupedByLevel = courses.reduce((acc, cur) => {
  acc[cur.level].push(cur);
  return acc;
}, { beginner: [], intermediate: [] });

/*
{
  beginner: [
    { course: "How to make a website using HTML/CSS", numberOfClicks: 970, level: "beginner" },
    { course: "Learn Javascript", numberOfClicks: 1240, level: "beginner" },
    { course: "Mysql Fundamentals", numberOfClicks: 1682, level: "beginner" },
    { course: "MongoDB Tutorial for Beginners", numberOfClicks: 408, level: "beginner" },
    { course: "Introduction to Ruby", numberOfClicks: 133, level: "beginner" },
  ],
  intermediate: [
    { course: "Python", numberOfClicks: 705, level: "intermediate" },
    { course: "Build a Rest API with Nodejs", numberOfClicks: 1041, level: "intermediate" },
    { course: "Learning Linux Training", numberOfClicks: 277, level: "intermediate" },
  ],
}
*/
```

##### Exercícios Bônus

**1.** Resolução do exercício bônus 01:
```javascript
const videosResult = videos.map(video => {
  return {
    title: video.title,
    views: video.views,
    comment: video.comments.reduce((acc, cur) => {
      if (acc.date > cur.date) return acc;
      return cur;
    }, {})
  }
});

/*
[
  {
    title: '[LIVE] Codenation agora é Trybe! Bate-papo com CEOs',
    views: '1k',
    comment: { date: '2020-07-20', comment: 'Cara, eu sou LOUCO pra ser Trybe },
  },
  {
    title: 'Trybe: Uma escola do futuro e para o futuro',
    views: '408k',
    comment: { date: '2020-03-11', comment: 'Como entramos?' },
  },
  {
    title: 'DEPOIMENTO: Pedro Tófani - Estudante da Turma 2 | Trybe',
    views: '8.7k',
    comments: { date: '2020-03-18', comment: 'está sendo 100% online agora por conta da pandemia' },
  },
  {
    title: '#EuSouTryber | TRYBE 1 ANO',
    views: '4k',
    comment: { date: '2020-08-15', comment: 'Demais!! Quantas conquistas em tão pouco tempo.' },
  },
  {
    title: '[LIVE] #PQC - Pergunte-me Qualquer Coisa sobre modalidade Sem Hub',
    views: '1.7k',
    comment: { date: '2020-03-07', comment: 'A formação vai do básico ao full?' },
  },
  {
    title: 'Curso introdutório de Javascript GRATUITO - Dicas para aproveitar ao máximo! | Trybe',
    views: '8.7k',
    comment: { date: '2020-03-16', comment: 'Muito bom ótimas dicas' },
  },
  {
    title: 'Tipos Primitivos - Curso Introdutório de JavaScript GRATUITO | Trybe',
    views: '7.8k',
    comment: { date: '2020-03-05', comment: 'Muito bom excelente explicação e didática parabéns' },
  },
  {
    title: '[LIVE] MeeTrybe #01 | Arquitetura de Software',
    views: '1.1k',
    comment: { date: '2020-08-29', comment: 'O curso é pauleira mas é um esforço alegre' },
  },
]
*/
```

**2.** Resolução do exercício bônus 02:
```javascript
const averageOfViews = videos.reduce((acc, cur) => {
  const numberOfViews = Number(cur.views.substring(0, cur.views.length - 1)) * 1000;
  return acc + numberOfViews;
}, 0) / (videos.length);

// 55125
```

