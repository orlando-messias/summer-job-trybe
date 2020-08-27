# map-reduce

```javascript
const dollarToday = 5.51;   // armazena o valor atual do dólar
const dollarValues = [2.35, 11, 7.3, 27.5, 200];  // array de valores em dólar
let realValues = [];  //  array inicial

for (let i = 0; i < dollarValues.length; i += 1) {
  realValues.push(dollarValues[i] * dollarToday);  //  lógica aplicada para cada item do array
}

console.log(realValues);  // [12.9485, 60.61, 40.223, 151.525, 1102]
```
