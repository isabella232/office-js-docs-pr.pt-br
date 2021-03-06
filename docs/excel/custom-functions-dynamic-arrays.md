---
ms.date: 05/11/2020
description: Retornar vários resultados de sua função personalizada em um suplemento do Office Excel.
title: Retornar vários resultados de sua função personalizada
localization_priority: Normal
ms.openlocfilehash: e25965277fbbe1c39007f79f401bf62b25760488
ms.sourcegitcommit: be23b68eb661015508797333915b44381dd29bdb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "44609647"
---
# <a name="return-multiple-results-from-your-custom-function"></a>Retornar vários resultados de sua função personalizada

Você pode retornar vários resultados de sua função personalizada que serão retornadas às células vizinhas. Esse comportamento é chamado de despejo. Quando sua função personalizada retorna uma matriz de resultados, ela é conhecida como uma fórmula de matriz dinâmica. Para obter mais informações sobre fórmulas de matriz dinâmicas no Excel, consulte [matrizes dinâmicas e comportamento de matriz despejada](https://support.office.com/article/dynamic-arrays-and-spilled-array-behavior-205c6b06-03ba-4151-89a1-87a7eb36e531).

A imagem a seguir mostra como a `SORT` função é despejada para baixo nas células vizinhas. Sua função personalizada também pode retornar vários resultados como este.

![Captura de tela da função "SORT" exibindo vários resultados em várias células.](../images/dynamic-array-spill.png)

Para criar uma função personalizada que seja uma fórmula de matriz dinâmica, ela deve retornar uma matriz bidimensional de valores. Se os resultados forem despejados em células vizinhas que já possuem valores, a fórmula exibirá um `#SPILL!` erro.

O exemplo a seguir mostra como retornar uma matriz dinâmica que derrama.

```javascript
/**
 * Get text values that spill down.
 * @customfunction
 * @returns {string[][]} A dynamic array with multiple results.
 */
function spillDown() {
  return [['first'], ['second'], ['third']];
}
```

O exemplo a seguir mostra como retornar uma matriz dinâmica que despeja à direita. 

```javascript
/**
 * Get text values that spill to the right.
 * @customfunction
 * @returns {string[][]} A dynamic array with multiple results.
 */
function spillRight() {
  return [['first', 'second', 'third']];
}
```

O exemplo a seguir mostra como retornar uma matriz dinâmica que é despejada para baixo e para a direita.

```javascript
/**
 * Get text values that spill both right and down.
 * @customfunction
 * @returns {string[][]} A dynamic array with multiple results.
 */
function spillRectangle() {
  return [
    ['apples', 1, 'pounds'],
    ['oranges', 3, 'pounds'],
    ['pears', 5, 'crates']
  ];
}
```

## <a name="see-also"></a>Confira também

- [Matrizes dinâmicas e comportamento de matriz derramada](https://support.microsoft.com/office/205c6b06-03ba-4151-89a1-87a7eb36e531)
- [Opções para funções personalizadas do Excel](custom-functions-parameter-options.md)