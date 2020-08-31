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
    }, '');
  },
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