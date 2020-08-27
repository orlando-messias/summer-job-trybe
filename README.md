# Higher Order Functions - MAP e REDUCE

## O que vamos aprender?
As últimas atualizações do Javascript trouxeram funcionalidades muito importantes com grande enfoque na produtividade de quem desenvolve. Em se tratando de manipulação de dados, por exemplo, as funções **MAP** e **REDUCE** são algumas das funções Javascript mais utilizadas para o refinamento de dados e extração de informações.

## Você será capaz de:
- Utilizar a **Função Map** para transformar dados de uma coleção e armazená-los como uma nova coleção;

- Utilizar a **Função Reduce** para extrair e obter informações importantes de um conjunto de dados e moldá-los à sua necessidade.

## Por que isso é importante?
Manipular dados é uma atividade comum na vida de um desenvolver e saber dominar as melhores ferramentas é importante para a produtividade na hora de programar. Uma grande massa de dados pode vir de um banco de dados ou de uma API, onde os dados chegam em sua forma bruta e você, como um bom desenvolver precisa tratar estes dados para que eles possam ser utilizados em sua aplicação.

## Conteúdos
**MAP** e **REDUCE** são *Higher-Order-Functions*, ou seja, funções que recebem como parâmetro uma outra função contendo a lógica ou regra do que precisa ser realizado, modificado ou transformado a partir de uma lista, um array. As funções que são passadas como parâmetro são chamadas de Callback (em tradução literal, chamar novamente), isto porque elas são invocadas novamente pra cada elemento do array.

### MAP: Conceito e Aplicação
A finalidade da função **Map** é percorrer um array e aplicar, a cada item, alguma alteração, alguma transformação e armazenar o resultado em um novo array sem, no entanto, modificar o original. Como exemplo inicial vamos utilizar uma lista de valores em formato dólar que precisam ser convertidos para a moeda real. 

Vejamos como seria o exemplo utilizando o comando **`for`**:

```javascript
const dollarToday = 5.51;   // armazena o valor atual do dólar
const dollarValues = [2.35, 11, 7.3, 27.5, 200];  // array de valores em dólar
let realValues = [];  //  array inicial

for (let i = 0; i < dollarValues.length; i += 1) {
  realValues.push(dollarValues[i] * dollarToday);  //  lógica aplicada para cada item do array
}

console.log(realValues);  // [12.9485, 60.61, 40.223, 151.525, 1102]
```

![test](https://github.com/orlando-messias/orlando-messias.github.io/blob/master/images/map_anonymous_function.png?raw=true)
