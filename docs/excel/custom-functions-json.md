---
ms.date: 11/06/2020
description: Definir metadados JSON para funções personalizadas no Excel e associar suas propriedades de ID de função e nome.
title: Criar manualmente metadados JSON para funções personalizadas no Excel
localization_priority: Normal
ms.openlocfilehash: adbcbb9d2705a38b1ed9ff5cdffa6162b9d93a9c
ms.sourcegitcommit: 5bfd1e9956485c140179dfcc9d210c4c5a49a789
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2020
ms.locfileid: "49071638"
---
# <a name="manually-create-json-metadata-for-custom-functions"></a>Criar manualmente metadados JSON para funções personalizadas

Conforme descrito no artigo [visão geral das funções personalizadas](custom-functions-overview.md) , um projeto de funções personalizadas deve incluir um arquivo de metadados JSON e um arquivo de script (JavaScript ou TypeScript) para registrar uma função, tornando-a disponível para uso. As funções personalizadas são registradas quando o usuário executa o suplemento pela primeira vez e depois que eles estão disponíveis para o mesmo usuário em todas as pastas de trabalho.

[!include[Excel custom functions note](../includes/excel-custom-functions-note.md)]

Recomendamos usar a autogeração JSON quando possível, em vez de criar seu próprio arquivo JSON. A autogeração está menos sujeita ao erro do usuário e os `yo office` arquivos do estruturado já incluem isso. Para obter mais informações sobre marcas JSDoc e o processo de autogeração JSON, consulte [AutoGenerate Metadata JSON para funções personalizadas](custom-functions-json-autogeneration.md).

No entanto, você pode criar um projeto de funções personalizadas a partir do zero. Esse processo exige:

- Escreva o arquivo JSON.
- Verifique se o arquivo de manifesto está conectado ao arquivo JSON.
- Associe suas funções `id` e `name` Propriedades no arquivo de script para registrar suas funções.

A imagem a seguir explica as diferenças entre o uso `yo office` de arquivos do estruturar e a gravação de JSON do zero.

![Imagem das diferenças entre usar Yo Office e escrever seu próprio JSON](../images/custom-functions-json.png)

> [!NOTE]
> Lembre-se de conectar seu manifesto ao arquivo JSON criado por você, através da `<Resources>` seção no arquivo de manifesto XML, se você não usar o `yo office` gerador.

## <a name="authoring-metadata-and-connecting-to-the-manifest"></a>Criação de metadados e conexão com o manifesto

Crie um arquivo JSON em seu projeto e forneça todos os detalhes sobre suas funções nele, como os parâmetros da função. Consulte o [exemplo de metadados a seguir](#json-metadata-example) e [a referência de metadados](#metadata-reference) para obter uma lista completa das propriedades de função.

Verifique se o arquivo de manifesto XML faz referência ao arquivo JSON na `<Resources>` seção, semelhante ao exemplo a seguir.

```json
<Resources>
    <bt:Urls>
        <bt:Url id="JSON-URL" DefaultValue="https://subdomain.contoso.com/config/customfunctions.json"/>
        <bt:Url id="JS-URL" DefaultValue="https://subdomain.contoso.com/dist/win32/ship/index.win32.bundle"/>
            <bt:Url id="HTML-URL" DefaultValue="https://subdomain.contoso.com/index.html"/>
    </bt:Urls>
    <bt:ShortStrings>
        <bt:String id="namespace" DefaultValue="CONTOSO"/>
    </bt:ShortStrings>
</Resources>
```

## <a name="json-metadata-example"></a>Exemplo de metadados JSON

O exemplo a seguir mostra o conteúdo de um arquivo de metadados JSON para um suplemento que define funções personalizadas. As seções que seguem este exemplo fornecem informações detalhadas sobre as propriedades individuais neste exemplo de JSON.

```json
{
  "functions": [
    {
      "id": "ADD",
      "name": "ADD",
      "description": "Add two numbers",
      "helpUrl": "http://www.contoso.com/help",
      "result": {
        "type": "number",
        "dimensionality": "scalar"
      },
      "parameters": [
        {
          "name": "first",
          "description": "first number to add",
          "type": "number",
          "dimensionality": "scalar"
        },
        {
          "name": "second",
          "description": "second number to add",
          "type": "number",
          "dimensionality": "scalar"
        }
      ]
    },
    {
      "id": "GETDAY",
      "name": "GETDAY",
      "description": "Get the day of the week",
      "helpUrl": "http://www.contoso.com/help",
      "result": {
        "dimensionality": "scalar"
      },
      "parameters": []
    },
    {
      "id": "INCREMENTVALUE",
      "name": "INCREMENTVALUE",
      "description": "Count up from zero",
      "helpUrl": "http://www.contoso.com/help",
      "result": {
        "dimensionality": "scalar"
      },
      "parameters": [
        {
          "name": "increment",
          "description": "the number to be added each time",
          "type": "number",
          "dimensionality": "scalar"
        }
      ],
      "options": {
        "stream": true,
        "cancelable": true
      }
    },
    {
      "id": "SECONDHIGHEST",
      "name": "SECONDHIGHEST",
      "description": "Get the second highest number from a range",
      "helpUrl": "http://www.contoso.com/help",
      "result": {
        "dimensionality": "scalar"
      },
      "parameters": [
        {
          "name": "range",
          "description": "the input range",
          "type": "number",
          "dimensionality": "matrix"
        }
      ]
    }
  ]
}
```

> [!NOTE]
> Um arquivo JSON de exemplo completo está disponível no histórico de confirmação do repositório do GitHub do [OfficeDev/Excel-Custom-Functions](https://github.com/OfficeDev/Excel-Custom-Functions/blob/77760adb1dcc53469183049bea08196734dbc114/config/customfunctions.json) . À medida que o projeto é ajustado para gerar JSON automaticamente, um exemplo completo de JSON manuscrito só está disponível em versões anteriores do projeto.

## <a name="metadata-reference"></a>Referência de metadados

### <a name="functions"></a>functions

A propriedade `functions` é um conjunto de objetos de funções personalizadas. A tabela a seguir lista as propriedades de cada objeto.

| Propriedade      | Tipo de dados | Obrigatório | Descrição                                                                                                                                                                      |
| :------------ | :-------- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `description` | string    | Não       | Descrição da função que é exibida aos usuários finais no Excel. Por exemplo, **Converte um valor em Celsius para Fahrenheit**.                                                            |
| `helpUrl`     | string    | Não       | A URL que fornece informações sobre a função. (Ela é exibida em um painel de tarefas). Por exemplo, `http://contoso.com/help/convertcelsiustofahrenheit.html`.                      |
| `id`          | string    | Sim      | Identificação exclusiva para a função. Essa ID pode conter apenas caracteres alfanuméricos e pontos e não deve ser alterada depois de configurada.                                            |
| `name`        | string    | Sim      | O nome da função que é exibida aos usuários finais no Excel. No Excel, esse nome de função é prefixado pelo namespace de funções personalizadas que é especificado no arquivo de manifesto XML. |
| `options`     | object    | Não       | Permite que você personalize alguns aspectos de como e quando o Excel executa a função. Confira [opções](#options) para obter detalhes.                                                          |
| `parameters`  | array     | Sim      | Matriz que define os parâmetros de entrada para a função. Confira os [parâmetros](#parameters) para obter detalhes.                                                                             |
| `result`      | object    | Sim      | Objeto que define o tipo de informação que é retornada pela função do Excel. Confira [resultado](#result) para obter detalhes.                                                                 |

### <a name="options"></a>options

O objeto `options` permite que você personalize alguns aspectos de como e quando o Excel executa a função. A tabela a seguir lista as propriedades do objeto `options`.

| Propriedade          | Tipo de dados | Obrigatório                               | Descrição |
| :---------------- | :-------- | :------------------------------------- | :---------- |
| `cancelable`      | booliano   | Não<br/><br/>O valor padrão é `false`.  | Se o valor for `true`, o Excel chamará o manipulador `CancelableInvocation` sempre que o usuário realizar uma ação que tenha o efeito de cancelar a função, por exemplo, manualmente acionar um recálculo ou editar uma célula referenciada pela função. As funções de cancelamento normalmente são usadas apenas para funções assíncronas que retornam um único resultado e precisam lidar com o cancelamento de uma solicitação de dados. Uma função não pode ser streaming e cancelamento. Para obter mais informações, consulte a observação próxima ao final de [fazer uma função de streaming](custom-functions-web-reqs.md#make-a-streaming-function). |
| `requiresAddress` | booliano   | Não <br/><br/>O valor padrão é `false`. | Se `true` , sua função personalizada pode acessar o endereço da célula que invocou sua função personalizada. Para obter o endereço da célula que chamou sua função personalizada, use Context. Address em sua função personalizada. As funções personalizadas não podem ser definidas como streaming e requiresAddress. Ao usar essa opção, o parâmetro "invocar" deve ser o último parâmetro passado em opções. |
| `stream`          | booliano   | Não<br/><br/>O valor padrão é `false`.  | Se o valor for `true`, a função poderá gerar uma saída para a célula de forma repetida, mesmo quando invocada somente uma vez. Essa opção é útil para fontes de dados que mudam constantemente, como preços de ações. A função não deve ter instruções `return`. Em vez disso, o valor resultante é passado como o argumento do método de retorno `StreamingInvocation.setResult`. Para saber mais informações, confira [Funções de streaming](custom-functions-web-reqs.md#make-a-streaming-function). |
| `volatile`        | booliano   | Não <br/><br/>O valor padrão é `false`. | Se `true` , a função será recalculada sempre que o Excel for recalculado, em vez de apenas quando os valores dependentes da fórmula tiverem sido alterados. Uma função não pode ser de streaming e volátil ao mesmo tempo. Se as propriedades `stream` e `volatile` forem definidas como `true`, a opção volátil será ignorada. |

### <a name="parameters"></a>parâmetros

A propriedade `parameters` é uma matriz de objetos de parâmetro. A tabela a seguir lista as propriedades de cada objeto.

|  Propriedade  |  Tipo de dados  |  Obrigatório  |  Descrição  |
|:-----|:-----|:-----|:-----|
|  `description`  |  string  |  Não |  Uma descrição do parâmetro. Isso é exibido no IntelliSense do Excel.  |
|  `dimensionality`  |  string  |  Não  |  Deve ser **escalar** (um valor não matriz) ou **matriz** (uma matriz de 2 dimensões).  |
|  `name`  |  string  |  Sim  |  O nome do parâmetro. Esse nome é exibido no IntelliSense do Excel.  |
|  `type`  |  string  |  Não  |  O tipo de dados do parâmetro. Pode ser **booliano** , **número** , **cadeia de caracteres** ou **qualquer** , que permita usar qualquer um dos três tipos anteriores. Se essa propriedade não for especificada, o tipo de dados padrão será **qualquer**. |
|  `optional`  | booliano | Não | Se for `true`, o parâmetro será opcional. |
|`repeating`| booliano | Não | Se `true` , os parâmetros são preenchidos de uma matriz especificada. Observe que funções todos os parâmetros de repetição são considerados parâmetros opcionais por definição.  |

### <a name="result"></a>result

O objeto `result` que define o tipo de informação que é retornado pela função. A tabela a seguir lista as propriedades do objeto `result`.

| Propriedade         | Tipo de dados | Obrigatório | Descrição                                                                          |
| :--------------- | :-------- | :------- | :----------------------------------------------------------------------------------- |
| `dimensionality` | string    | Não       | Deve ser **escalar** (um valor não matriz) ou **matriz** (uma matriz de 2 dimensões). |

## <a name="associating-function-names-with-json-metadata"></a>Associar os nomes de função com metadados JSON

Para que uma função funcione corretamente, você precisa associar a propriedade da função à `id` implementação do JavaScript. Verifique se há uma associação, caso contrário, a função não será registrada e não é utilizável no Excel. O exemplo de código a seguir mostra como fazer a Associação usando o `CustomFunctions.associate()` método. A amostra define a função personalizada `add` e associa com o objeto no arquivo de metadados JSON onde o valor da `id` propriedade é **adicionar**.

```js
/**
 * Add two numbers
 * @customfunction
 * @param {number} first First number
 * @param {number} second Second number
 * @returns {number} The sum of the two numbers.
 */
function add(first, second) {
  return first + second;
}

CustomFunctions.associate("ADD", add);
```

O JSON a seguir mostra os metadados JSON que estão associados ao código JavaScript da função personalizada anterior.

```json
{
  "functions": [
    {
      "description": "Add two numbers",
      "id": "ADD",
      "name": "ADD",
      "parameters": [
        {
          "description": "First number",
          "name": "first",
          "type": "number"
        },
        {
          "description": "Second number",
          "name": "second",
          "type": "number"
        }
      ],
      "result": {
        "type": "number"
      }
    }
  ]
}
```

Lembre-se das seguintes práticas recomendadas quando criar funções personalizadas no arquivo JavaScript e especificar as informações correspondentes no arquivo de metadados JSON.

- No arquivo de metadados JSON, verifique se o valor de cada propriedade `id` contém apenas caracteres alfanuméricos e pontos.

- No arquivo de metadados JSON, garanta que o valor de cada propriedade `id` seja exclusivo dentro do escopo do arquivo. Ou seja, nenhum objeto de duas funções no arquivo de metadados deve ter o mesmo valor `id`.

- Não altere o valor de uma propriedade `id` no arquivo de metadados JSON, depois de mapeá-lo para um nome de função JavaScript correspondente. Para alterar o nome da função que os usuários finais visualizam no Excel, atualize a propriedade `name` no arquivo de metadados JSON. No entanto, nunca altere o valor de uma propriedade `id` depois de estabelecida.

- No arquivo JavaScript, especifique uma associação de função personalizada usando `CustomFunctions.associate` após cada função.

O exemplo a seguir mostra os metadados JSON que correspondem às funções definidas no exemplo de código JavaScript anterior. Os `id` `name` valores de propriedade e estão em letras maiúsculas, o que é uma prática recomendada ao descrever suas funções personalizadas. Você só precisará adicionar esse JSON se estiver preparando seu próprio arquivo JSON manualmente e não usando a autogeração. Para obter mais informações sobre a autogeração, consulte [AutoGenerate metadados JSON para funções personalizadas](custom-functions-json-autogeneration.md).

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/office-js/custom-functions.schema.json",
  "functions": [
    {
      "id": "ADD",
      "name": "ADD",
      ...
    },
    {
      "id": "INCREMENT",
      "name": "INCREMENT",
      ...
    }
  ]
}
```

## <a name="next-steps"></a>Próximas etapas

Conheça as [práticas recomendadas para nomear sua função](custom-functions-naming.md) ou descubra como [localizar sua função](custom-functions-localize.md) usando o método JSON manuscrito descrito anteriormente.

## <a name="see-also"></a>Confira também

- [Gerar metadados JSON automaticamente para funções personalizadas](custom-functions-json-autogeneration.md)
- [Opções de parâmetros de funções personalizadas](custom-functions-parameter-options.md)
- [Criar funções personalizadas no Excel](custom-functions-overview.md)
