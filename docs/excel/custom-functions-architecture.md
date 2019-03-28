---
ms.date: 03/20/2019
description: Saiba mais sobre o tempo de execução de funções personalizadas do Excel.
title: Arquitetura de funções personalizados (prévia)
localization_priority: Priority
ms.openlocfilehash: b3f3d6c5eda51639a734c6d0f162c596f0c1e41b
ms.sourcegitcommit: a2950492a2337de3180b713f5693fe82dbdd6a17
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2019
ms.locfileid: "30926635"
---
# <a name="custom-functions-architecture"></a>Arquitetura de funções personalizadas

 Funções personalizadas estão com tempos de execução exclusivos que priorizam a execução de cálculos. Este artigo aborda a diferenças entre o tempo de execução de funções personalizadas e o mecanismo de JavaScript baseados em navegador que habilita a maioria das outras partes do suplemento.

## <a name="custom-functions-runtime"></a>Tempo de execução de funções personalizadas

Um suplemento Web do Office pode interagir com o usuário como um painel de tarefas ou como um painel de conteúdo e pode incluir comandos e funções personalizadas. Todas essas partes são executadas em um tempo de execução do mecanismo do navegador, exceto para funções personalizadas. As funções personalizadas são executadas em um tempo de execução de funções personalizadas separado para otimizar a velocidade de cálculo.

Observe que, se você estiver usando o [gerador de suplementos do Office Yeoman](https://www.npmjs.com/package/generator-office) para gerar o seu projeto, o tempo de execução de funções personalizadas será carregado por meio do arquivo de script custom-functions.js mencionado no arquivo functions.html. O arquivo functions.html serve apenas para carregar o tempo de execução e não deve ser usado como painel de tarefas para o suplemento.

A tabela a seguir destaca as diferenças entre o tempo de execução de funções personalizadas e o tempo de execução do mecanismo do navegador:

| Tempo de execução de funções personalizadas  | Tempo de execução do mecanismo do navegador    |
|------------------------------------------------------------------ |-------------------------------------------------------------------------------------------------------------- |
| Suporte para retornar o valor de uma célula    | Suporte para APIs Office.js e elementos de interface do usuário   |
| Não tem objeto `localStorage`, em vez disso usa `AsyncStorage`  | Tem objeto `localStorage`, opcionalmente poderá usar o objeto`AsyncStorage`   |
| Não suporta a interação com o DOM ou o carregamento de  bibliotecas que dependem do DOM, como jQuery.    | Suporta interação com o DOM e com o carregamento de bibliotecas que dependem do DOM. |


## <a name="browser-engine-runtime"></a>Tempo de execução do mecanismo do navegador

O painel de tarefas o, suplemento de conteúdo e os comandos são executados em um tempo de execução do mecanismo do navegador.

APIs Office.js é compatível com o tempo de execução do mecanismo do navegador. Tenha em mente que qualquer uma das APIs do Excel, assim como APIs que permitem manipular tabelas do Excel, são executadas no tempo de execução do mecanismo do navegador, mas não são acessíveis diretamente do tempo de execução de funções personalizadas.

## <a name="communicate-between-runtimes"></a>Comunicar-se entre os tempos de execução

O código de funções personalizadas não pode interagir diretamente com o código em outras partes do seu suplemento da web, como o painel de tarefas porque estão em diferentes tempos de execução. Mas em alguns cenários, talvez seja necessário compartilhar dados, por exemplo, passando um token.

`AsyncStorage` pode ser usado para armazenar dados de suas funções personalizadas e para obter dados do seu código do painel de tarefas. Para saber mais sobre como armazenar e compartilhar dados, confira [Salvar e compartilhar estado](custom-functions-overview.md#saving-and-sharing-state).

Você pode ver um exemplo de código usando `AsyncStorage` neste [repositório Github](https://github.com/OfficeDev/PnP-OfficeAddins/tree/master/Excel-custom-functions/AsyncStorage) dedicado para padrões e práticas recomendadas.
Para saber mais sobre `AsyncStorage`, confira [tempo de execução de funções personalizadas](./custom-functions-runtime.md).

`AsyncStorage` também pode ser útil para autenticação. Para saber mais, confira [autenticação de funções personalizadas](custom-functions-authentication.md).

## <a name="see-also"></a>Confira também

* [Tempo de execução de funções personalizadas do Excel](custom-functions-runtime.md)
* [Práticas recomendadas de funções personalizadas](custom-functions-best-practices.md).
* [Metadados de funções personalizadas](custom-functions-json.md)
* [Log de alteração de funções personalizadas](custom-functions-changelog.md)
* [Tutorial de funções personalizadas do Excel](../tutorials/excel-tutorial-create-custom-functions.md)