---
ms.date: 11/06/2020
description: Saiba como usar parâmetros diferentes em suas funções personalizadas, como intervalos do Excel, parâmetros opcionais, contexto de invocação e muito mais.
title: Opções para funções personalizadas do Excel
localization_priority: Normal
ms.openlocfilehash: 0a803a4d41354530584b25d2bf9df944af430909
ms.sourcegitcommit: 5bfd1e9956485c140179dfcc9d210c4c5a49a789
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2020
ms.locfileid: "49071617"
---
# <a name="custom-functions-parameter-options"></a>Opções de parâmetros de funções personalizadas

As funções personalizadas são configuráveis com muitas opções de parâmetros diferentes.

[!include[Excel custom functions note](../includes/excel-custom-functions-note.md)]

## <a name="optional-parameters"></a>Parâmetros opcionais

Quando um usuário invoca uma função no Excel, os parâmetros opcionais são exibidos entre colchetes. No exemplo a seguir, a função Add pode opcionalmente adicionar um terceiro número. Essa função aparece como `=CONTOSO.ADD(first, second, [third])` no Excel.

#### <a name="javascript"></a>[JavaScript](#tab/javascript)

```js
/**
 * Calculates the sum of the specified numbers
 * @customfunction
 * @param {number} first First number.
 * @param {number} second Second number.
 * @param {number} [third] Third number to add. If omitted, third = 0.
 * @returns {number} The sum of the numbers.
 */
function add(first, second, third) {
  if (third === null) {
    third = 0;
  }
  return first + second + third;
}
```

#### <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
/**
 * Calculates the sum of the specified numbers
 * @customfunction
 * @param first First number.
 * @param second Second number.
 * @param [third] Third number to add. If omitted, third = 0.
 * @returns The sum of the numbers.
 */
function add(first: number, second: number, third?: number): number {
  if (third === null) {
    third = 0;
  }
  return first + second + third;
}
```

---

> [!NOTE]
> Quando nenhum valor é especificado para um parâmetro opcional, o Excel atribui a ele o valor `null` . Isso significa que os parâmetros inicializados por padrão no TypeScript não funcionarão conforme o esperado. Não use a sintaxe `function add(first:number, second:number, third=0):number` porque ela não será inicializada `third` como 0. Em vez disso, use a sintaxe do TypeScript, conforme mostrado no exemplo anterior.

Ao definir uma função que contenha um ou mais parâmetros opcionais, especifique o que acontece quando os parâmetros opcionais são nulos. No exemplo a seguir, `zipCode` e `dayOfWeek` são dois parâmetros opcionais da função `getWeatherReport`. Se o `zipCode` parâmetro for NULL, o valor padrão será definido como `98052` . Se o `dayOfWeek` parâmetro for NULL, ele será definido como quarta-feira.

#### <a name="javascript"></a>[JavaScript](#tab/javascript)

```js
/**
 * Gets a weather report for a specified zipCode and dayOfWeek
 * @customfunction
 * @param {number} [zipCode] Zip code. If omitted, zipCode = 98052.
 * @param {string} [dayOfWeek] Day of the week. If omitted, dayOfWeek = Wednesday.
 * @returns {string} Weather report for the day of the week in that zip code.
 */
function getWeatherReport(zipCode, dayOfWeek) {
  if (zipCode === null) {
    zipCode = 98052;
  }

  if (dayOfWeek === null) {
    dayOfWeek = "Wednesday";
  }

  // Get weather report for specified zipCode and dayOfWeek.
  // ...
}
```

#### <a name="typescript"></a>[TypeScript](#tab/typescript)

```typescript
/**
 * Gets a weather report for a specified zipCode and dayOfWeek
 * @customfunction
 * @param zipCode Zip code. If omitted, zipCode = 98052.
 * @param [dayOfWeek] Day of the week. If omitted, dayOfWeek = Wednesday.
 * @returns Weather report for the day of the week in that zip code.
 */
function getWeatherReport(zipCode?: number, dayOfWeek?: string): string {
  if (zipCode === null) {
    zipCode = 98052;
  }

  if (dayOfWeek === null) {
    dayOfWeek = "Wednesday";
  }

  // Get weather report for specified zipCode and dayOfWeek.
  // ...
}
```

---

## <a name="range-parameters"></a>Parâmetros de intervalo

Sua função personalizada pode aceitar um intervalo de dados de célula como um parâmetro de entrada. Uma função também pode retornar um intervalo de dados. O Excel passará um intervalo de dados de célula como uma matriz bidimensional.

Por exemplo, suponha que sua função retorne o segundo maior valor de um intervalo de números armazenados no Excel. A função a seguir aceita o parâmetro `values`, que é um tipo de parâmetro `Excel.CustomFunctionDimensionality.matrix`. Observe que, nos metadados JSON dessa função, a propriedade do parâmetro `type` é definida como `matrix` .

```js
/**
 * Returns the second highest value in a matrixed range of values.
 * @customfunction
 * @param {number[][]} values Multiple ranges of values.
 */
function secondHighest(values) {
  let highest = values[0][0],
    secondHighest = values[0][0];
  for (var i = 0; i < values.length; i++) {
    for (var j = 0; j < values[i].length; j++) {
      if (values[i][j] >= highest) {
        secondHighest = highest;
        highest = values[i][j];
      } else if (values[i][j] >= secondHighest) {
        secondHighest = values[i][j];
      }
    }
  }
  return secondHighest;
}
```

## <a name="repeating-parameters"></a>Parâmetros de repetição

Um parâmetro Repeating permite que o usuário insira uma série de argumentos opcionais para uma função. Quando a função é chamada, os valores são fornecidos em uma matriz para o parâmetro. Se o nome do parâmetro terminar com um número, o número de cada argumento aumentará de forma incremental, como `ADD(number1, [number2], [number3],…)` . Isso corresponde à Convenção usada para funções internas do Excel.

A função a seguir soma o total de números, endereços de célula, bem como intervalos, se inserido.

```TS
/**
* The sum of all of the numbers.
* @customfunction
* @param operands A number (such as 1 or 3.1415), a cell address (such as A1 or $E$11), or a range of cell addresses (such as B3:F12)
*/

function ADD(operands: number[][][]): number {
  let total: number = 0;

  operands.forEach(range => {
    range.forEach(row => {
      row.forEach(num => {
        total += num;
      });
    });
  });

  return total;
}
```

Essa função é mostrada `=CONTOSO.ADD([operands], [operands]...)` na pasta de trabalho do Excel.

<img alt="The ADD custom function being entered into cell of an Excel worksheet" src="../images/operands.png" />

### <a name="repeating-single-value-parameter"></a>Parâmetro de valor único repetido

Um parâmetro de valor único repetido permite que vários valores únicos sejam passados. Por exemplo, o usuário pode inserir ADD (1, B2, 3). O exemplo a seguir mostra como declarar um parâmetro de valor único.

```JS
/**
 * @customfunction
 * @param {number[]} singleValue An array of numbers that are repeating parameters.
 */
function addSingleValue(singleValue) {
  let total = 0;
  singleValue.forEach(value => {
    total += value;
  })

  return total;
}
```

### <a name="single-range-parameter"></a>Parâmetro de intervalo único

Um único parâmetro de intervalo não é tecnicamente um parâmetro de repetição, mas é incluído aqui porque a declaração é muito parecida com os parâmetros de repetição. Ele apareceria para o usuário como ADD (a2: B3), em que um único intervalo é passado do Excel. O exemplo a seguir mostra como declarar um único parâmetro de intervalo.

```JS
/**
 * @customfunction
 * @param {number[][]} singleRange
 */
function addSingleRange(singleRange) {
  let total = 0;
  singleRange.forEach(setOfSingleValues => {
    setOfSingleValues.forEach(value => {
      total += value;
    })
  })
  return total;
}
```

### <a name="repeating-range-parameter"></a>Parâmetro de intervalo de repetição

Um parâmetro de intervalo de repetição permite que vários intervalos ou números sejam passados. Por exemplo, o usuário pode inserir ADD (5, B2, C3, 8, E5: E8). Os intervalos de repetição normalmente são especificados com o tipo `number[][][]` , já que são matrizes tridimensionais. Para obter um exemplo, consulte o exemplo principal listado para parâmetros repetidos (#repeating-Parameters).


### <a name="declaring-repeating-parameters"></a>Declarando parâmetros de repetição
No typescript, indique que o parâmetro é multidimensional. Por exemplo,  `ADD(values: number[])` indicaria uma matriz unidimensional, `ADD(values:number[][])` indicaria uma matriz bidimensional e assim por diante.

Em JavaScript, use `@param values {number[]}` para matrizes unidimensionais, `@param <name> {number[][]}` para matrizes bidimensionais e assim por diante para mais dimensões.

Para o JSON com autoria, certifique-se de que seu parâmetro é especificado como `"repeating": true` em seu arquivo JSON, bem como Verifique se os parâmetros estão marcados como `"dimensionality": matrix` .

## <a name="invocation-parameter"></a>Parâmetro de invocação

Cada função personalizada é automaticamente passada um `invocation` argumento como o último argumento. Esse argumento pode ser usado para recuperar contexto adicional, como o endereço da célula de chamada. Ou pode ser usado para enviar informações para o Excel, como um manipulador de função para [cancelar uma função](custom-functions-web-reqs.md#make-a-streaming-function). Mesmo que você declare nenhum parâmetro, sua função personalizada tem esse parâmetro. Esse argumento não aparece para um usuário no Excel. Se você deseja usar `invocation` em sua função personalizada, declare-a como o último parâmetro.

No exemplo de código a seguir, o `invocation` contexto é explicitamente declarado para sua referência.

```js
/**
 * Add two numbers.
 * @customfunction
 * @param {number} first First number.
 * @param {number} second Second number.
 * @returns {number} The sum of the two (or optionally three) numbers.
 */
function add(first, second, invocation) {
  return first + second;
}
```

## <a name="next-steps"></a>Próximas etapas

Saiba como usar [valores voláteis em suas funções personalizadas](custom-functions-volatile.md).

## <a name="see-also"></a>Confira também

* [Receber e tratar dados com funções personalizadas](custom-functions-web-reqs.md)
* [Gerar metadados JSON automaticamente para funções personalizadas](custom-functions-json-autogeneration.md)
* [Criar manualmente metadados JSON para funções personalizadas](custom-functions-json.md)
* [Criar funções personalizadas no Excel](custom-functions-overview.md)
* [Tutorial de funções personalizadas do Excel](../tutorials/excel-tutorial-create-custom-functions.md)
