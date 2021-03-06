---
title: Programação assíncrona em Suplementos do Office
description: Saiba como a biblioteca JavaScript do Office usa a programação assíncrona em suplementos do Office.
ms.date: 09/08/2020
localization_priority: Normal
ms.openlocfilehash: 96805ee0f78caedd718642a97828db26f0de7900
ms.sourcegitcommit: c6308cf245ac1bc66a876eaa0a7bb4a2492991ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "47408576"
---
# <a name="asynchronous-programming-in-office-add-ins"></a>Programação assíncrona em Suplementos do Office

[!include[information about the common API](../includes/alert-common-api-info.md)]

Por que a API de Suplementos do Office usa a programação assíncrona? Como o JavaScript é uma linguagem de thread único, se o script invocar um processo síncrono demorado, todas as execuções subsequentes do script serão bloqueadas até que o processo seja concluído. Como determinadas operações com clientes Web do Office (mas também clientes avançados) podem bloquear a execução se forem executadas de forma síncrona, a maioria das APIs JavaScript do Office é projetada para ser executada de forma assíncrona. Isso garante que os suplementos do Office sejam responsivos e rápidos. Em geral, isso também requer que você escreva funções de retorno de chamada ao trabalhar com esses métodos assíncronos.

Os nomes de todos os métodos assíncronos na API terminam com "Async", como `Document.getSelectedDataAsync` os `Binding.getDataAsync` métodos, ou `Item.loadCustomPropertiesAsync` . Quando um método "Async" é chamado, ele é executado imediatamente e qualquer execução subsequente do script poderá continuar. A função de retorno de chamada opcional que você passar para um método de "Async" é executada assim que os dados ou a operação solicitada está pronta. Isso geralmente ocorre imediatamente, mas pode haver um pequeno atraso antes de retornar.

O diagrama a seguir mostra o fluxo de execução de uma chamada para um método "Async" que lê os dados que o usuário selecionou em um documento aberto no Word baseado no servidor ou no Excel. No ponto em que a chamada "Async" é feita, o thread de execução do JavaScript é livre para executar qualquer processamento adicional no lado do cliente (embora nenhum seja mostrado no diagrama). Quando o método "Async" retorna, o retorno de chamada continua a execução no thread e o suplemento pode acessar os dados, fazer algo com ele e exibir o resultado. O mesmo padrão de execução assíncrona é executado ao trabalhar com os aplicativos cliente avançados do Office, como o Word 2013 ou o Excel 2013.

*Figura 1. Fluxo de execução da programação assíncrona*

![Asynchronous programming thread execution flow](../images/office-addins-asynchronous-programming-flow.png)

O suporte a este design assíncrono em clientes Web e avançados faz parte das metas de design "gravar plataforma cruzada já executada" do modelo de desenvolvimento de Suplementos do Office. Por exemplo, você pode criar um suplemento do painel de tarefas ou conteúdo com uma única base de código que será executada no Excel 2013 e Excel Online.

## <a name="writing-the-callback-function-for-an-async-method"></a>Gravar a função de retorno de chamada para um método "Async"


A função de retorno de chamada passada como o argumento de _retorno de chamada_ para um método "Async" deve declarar um único parâmetro que o tempo de execução do suplemento usará para fornecer acesso a um objeto [AsyncResult](/javascript/api/office/office.asyncresult) quando a função de retorno de chamada for executada. Você pode gravar:


- Uma função anônima que deve ser gravada e transmitida diretamente em linha com a chamada para o método "Async" como o parâmetro _callback_ do método "Async".

- Uma função nomeada, passando o nome dessa função como o parâmetro _callback_ de um método "Async".

Uma função anônima é útil se você só for usar seu código uma vez – porque ele não possui um nome, você não pode referenciá-la em outra parte do seu código. Uma função nomeada é útil se você quiser reutilizar a função retorno de chamada para mais de um método "Async".


### <a name="writing-an-anonymous-callback-function"></a>Gravar uma função de retorno de chamada anônima

A seguinte função de retorno de chamada anônima declara um único parâmetro chamado `result` que recupera os dados da propriedade [AsyncResult. Value](/javascript/api/office/office.asyncresult#value) quando o retorno de chamada retorna.


```js
function (result) {
        write('Selected data: ' + result.value);
}
```

O exemplo a seguir mostra como passar essa função de retorno de chamada anônima em linha no contexto de uma chamada de método "Async" completa para o `Document.getSelectedDataAsync` método.


- O primeiro argumento _coercionType_ , `Office.CoercionType.Text` , especifica para retornar os dados selecionados como uma cadeia de texto.

- O segundo argumento de _retorno de chamada_ é a função anônima passada na linha para o método. Quando a função é executada, ela usa o parâmetro _Result_ para acessar a `value` Propriedade do `AsyncResult` objeto para exibir os dados selecionados pelo usuário no documento.


```js
Office.context.document.getSelectedDataAsync(Office.CoercionType.Text, 
    function (result) {
        write('Selected data: ' + result.value);
    }
});

// Function that writes to a div with id='message' on the page.
function write(message){
    document.getElementById('message').innerText += message; 
}
```

Você também pode usar o parâmetro de sua função de retorno de chamada para acessar outras propriedades do `AsyncResult` objeto. Use a propriedade [AsyncResult.status](/javascript/api/office/office.asyncresult#status) para determinar se a chamada teve êxito ou falhou. Se sua chamada falhar, você pode usar a propriedade [AsyncResult.error](/javascript/api/office/office.asyncresult#error) para acessar um objeto [Error](/javascript/api/office/office.error) para informações sobre o erro.

Para obter mais informações sobre como usar o `getSelectedDataAsync` método, confira [ler e gravar dados na seleção ativa em um documento ou planilha](read-and-write-data-to-the-active-selection-in-a-document-or-spreadsheet.md). 


### <a name="writing-a-named-callback-function"></a>Gravar uma função de retorno de chamada nomeada

Como alternativa, você pode escrever uma função nomeada e passar seu nome para o parâmetro _callback_ de um método "Async". Por exemplo, o exemplo anterior pode ser reescrito para transmitir uma função chamada `writeDataCallback` como o parâmetro _callback_ assim.


```js
Office.context.document.getSelectedDataAsync(Office.CoercionType.Text, 
    writeDataCallback);

// Callback to write the selected data to the add-in UI.
function writeDataCallback(result) {
    write('Selected data: ' + result.value);
}

// Function that writes to a div with id='message' on the page.
function write(message){
    document.getElementById('message').innerText += message; 
}
```


## <a name="differences-in-whats-returned-to-the-asyncresultvalue-property"></a>Diferenças entre o que é retornado para a propriedade AsyncResult.value


As `asyncContext` `status` Propriedades,, e `error` do `AsyncResult` objeto retornam os mesmos tipos de informações para a função de retorno de chamada passada para todos os métodos "Async". No entanto, o que é retornado para a `AsyncResult.value` Propriedade varia dependendo da funcionalidade do método "Async".

Por exemplo, os `addHandlerAsync` métodos (dos objetos [Binding](/javascript/api/office/office.binding), [CustomXMLPart](/javascript/api/office/office.customxmlpart), [Document](/javascript/api/office/office.document), [RoamingSettings](/javascript/api/outlook/office.roamingsettings)e [Settings](/javascript/api/office/office.settings) ) são usados para adicionar funções de manipulador de eventos aos itens representados por esses objetos. Você pode acessar a `AsyncResult.value` propriedade da função de retorno de chamada passada para qualquer um dos `addHandlerAsync` métodos, mas como nenhum dado ou objeto está sendo acessado quando você adiciona um manipulador de eventos, a `value` propriedade sempre retorna **undefined** se você tentar acessá-lo.

Por outro lado, se você chamar o `Document.getSelectedDataAsync` método, ele retornará os dados que o usuário selecionou no documento para a `AsyncResult.value` propriedade no retorno de chamada. Ou, se você chamar o método [bindings. getAllAsync](/javascript/api/office/office.bindings#getallasync-options--callback-) , ele retornará uma matriz de todos os `Binding` objetos no documento. E, se você chamar o método [bindings. getByIdAsync](/javascript/api/office/office.bindings#getbyidasync-id--options--callback-) , ele retornará um único `Binding` objeto.

Para obter uma descrição do que é retornado para a `AsyncResult.value` propriedade de um `Async` método, consulte a seção "valor de retorno de chamada" do tópico de referência desse método. Para obter um resumo de todos os objetos que fornecem `Async` métodos, consulte a tabela na parte inferior do tópico do objeto [AsyncResult](/javascript/api/office/office.asyncresult) .


## <a name="asynchronous-programming-patterns"></a>Padrões de programação assíncrona


A API JavaScript do Office oferece suporte a dois tipos de padrões de programação assíncrono:


- Usando retornos de chamada aninhados
    
- Usando o padrão de promessas
    
A programação assíncrona com funções de retorno de chamada frequentemente exigem que você aninhe o resultado retornado de um retorno de chamada dentro de dois ou mais retornos de chamada. Se você precisar fazer isso, é possível usar retornos de chamada aninhados de todos os métodos "Async" da API.

Usar retornos de chamada aninhados é um padrão de programação familiar para a maioria dos desenvolvedores de JavaScript, mas códigos com retornos de chamada profundamente aninhados podem ser difíceis de ler e entender. Como alternativa para retornos de chamada aninhados, a API JavaScript do Office também oferece suporte a uma implementação do padrão de promessas. 

> [!NOTE]
> Na versão atual da API JavaScript do Office, o suporte *interno* para o padrão de promessas só funciona com o código para [associações em documentos do Word e planilhas do Excel](bind-to-regions-in-a-document-or-spreadsheet.md). No entanto, você pode quebrar outras funções que têm retornos de chamada dentro de sua própria função de retorno de promessa personalizada. Para obter mais informações, consulte [quebra de APIs comuns em funções que retornam a promessa](#wrap-common-apis-in-promise-returning-functions).


### <a name="asynchronous-programming-using-nested-callback-functions"></a>Programação assíncrona usando funções aninhadas de retorno de chamada

Frequentemente, você precisa executar duas ou mais operações assíncronas para concluir uma tarefa. Para fazer isso, você pode aninhar uma chamada "Async" dentro de outra.

O exemplo de código a seguir aninha duas ou mais chamadas assíncronas.


- Primeiro, o método [Bindings.getByIdAsync](/javascript/api/office/office.bindings#getbyidasync-id--options--callback-) é chamado para acessar uma associação no documento chamado "MyBinding". O `AsyncResult` objeto retornado para o `result` parâmetro desse retorno de chamada fornece acesso ao objeto Binding especificado a partir da `AsyncResult.value` propriedade.

- Em seguida, o objeto de vinculação acessado do primeiro `result` parâmetro é usado para chamar o método [Binding. getDataAsync](/javascript/api/office/office.binding#getdataasync-options--callback-) .

- Por fim, o `result2` parâmetro do retorno de chamada passado para o `Binding.getDataAsync` método é usado para exibir os dados na associação.


```js
function readData() {
    Office.context.document.bindings.getByIdAsync("MyBinding", function (result) {
        result.value.getDataAsync({ coercionType: 'text' }, function (result2) {
            write(result2.value);
        });
    });
}

// Function that writes to a div with id='message' on the page.
function write(message){
    document.getElementById('message').innerText += message; 
}
```

Este padrão de retorno de chamada aninhado básico pode ser usado para todos os métodos assíncronos na API JavaScript do Office.

As seções a seguir mostram como usar funções anônimas ou nomeadas para retornos de chamada aninhados em métodos assíncronos.


#### <a name="using-anonymous-functions-for-nested-callbacks"></a>Usando funções anônimas para retornos de chamada aninhados

No exemplo a seguir, duas funções anônimas são declaradas embutidas e passadas para os `getByIdAsync` `getDataAsync` métodos e como callbacks aninhados. Como as funções são simples e embutidas, a intenção da implementação fica imediatamente clara.


```js
Office.context.document.bindings.getByIdAsync('myBinding', function (bindingResult) {
    bindingResult.value.getDataAsync(function (getResult) {
        if (getResult.status == Office.AsyncResultStatus.Failed) {
            write('Action failed. Error: ' + asyncResult.error.message);
        } else {
            write('Data has been read successfully.');
        }
    });
});

// Function that writes to a div with id='message' on the page.
function write(message){
    document.getElementById('message').innerText += message;
}
```


#### <a name="using-named-functions-for-nested-callbacks"></a>Usando funções nomeadas para retornos de chamada aninhados

Em implementações complexas, pode ser útil usar funções nomeadas para facilitar a leitura, manutenção e reutilização do seu código. No exemplo a seguir, as duas funções anônimas do exemplo na seção anterior foram reescritas como funções chamadas `deleteAllData` e `showResult` . Essas funções nomeadas são então passadas para os `getByIdAsync` `deleteAllDataValuesAsync` métodos e como callbacks por nome.


```js
Office.context.document.bindings.getByIdAsync('myBinding', deleteAllData);

function deleteAllData(asyncResult) {
    asyncResult.value.deleteAllDataValuesAsync(showResult);
}

function showResult(asyncResult) {
    if (asyncResult.status == Office.AsyncResultStatus.Failed) {
        write('Action failed. Error: ' + asyncResult.error.message);
    } else {
        write('Data has been deleted successfully.');
    }
}

// Function that writes to a div with id='message' on the page.
function write(message){
    document.getElementById('message').innerText += message;
}
```


### <a name="asynchronous-programming-using-the-promises-pattern-to-access-data-in-bindings"></a>Programação assíncrona usando o padrão de promessas para acessar dados em associações


Em vez de transmitir a função de retorno de chamada e aguardar até que a função retorne antes da continuação da execução, o padrão de programação de promessas retorna imediatamente retorna um objeto de promessa que representa o resultado desejado. No entanto, ao contrário da verdadeira programação síncrona, nos bastidores o cumprimento do resultado prometido é, na verdade, adiado até que o ambiente de tempo de execução dos Suplementos do Office possa concluir a solicitação. Um manipulador _onError_ é fornecido para atender a situações em que a solicitação não pode ser cumprida.


A API JavaScript do Office fornece o método [Office. Select](/javascript/api/office#office-select-expression--callback-) para dar suporte ao padrão de promessas para trabalhar com objetos Binding existentes. O objeto Promise retornado para o `Office.select` método suporta apenas os quatro métodos que você pode acessar diretamente a partir do objeto [Binding](/javascript/api/office/office.binding) : [getDataAsync](/javascript/api/office/office.binding#getdataasync-options--callback-), [setDataAsync](/javascript/api/office/office.binding#setdataasync-data--options--callback-), [addHandlerAsync](/javascript/api/office/office.binding#addhandlerasync-eventtype--handler--options--callback-)e [removeHandlerAsync](/javascript/api/office/office.binding#removehandlerasync-eventtype--options--callback-).


O padrão de promessas para funcionar com associações tem este formato:

 **Office. Select (**_selectorr_, _OnError_**).** _BindingObjectAsyncMethod_

O parâmetro _selectoré_ assume o formato `"bindings#bindingId"` , em que _BindingId_ é o nome ( `id` ) de uma associação que você criou anteriormente no documento ou planilha (usando um dos métodos "addfrom" do `Bindings` conjunto: `addFromNamedItemAsync` , `addFromPromptAsync` , ou `addFromSelectionAsync` ). Por exemplo, a expressão de seletor `bindings#cities` especifica que você deseja acessar a associação com uma **ID** de "cidades".

O parâmetro _OnError_ é uma função de tratamento de erros que usa um único parâmetro do tipo `AsyncResult` que pode ser usado para acessar um `Error` objeto, se o `select` método falhar ao acessar a associação especificada. O exemplo a seguir mostra uma função de manipulador de erro básica que pode ser transmitida para o parâmetro _onError_.




```js
function onError(result){
    var err = result.error;
    write(err.name + ": " + err.message);
}
// Function that writes to a div with id='message' on the page.
function write(message){
    document.getElementById('message').innerText += message; 
}
```

Substitua o espaço reservado _BindingObjectAsyncMethod_ por uma chamada para qualquer um dos quatro `Binding` métodos de objeto suportados pelo objeto Promise: `getDataAsync` , `setDataAsync` , `addHandlerAsync` ou `removeHandlerAsync` . As chamadas para esses métodos não oferecem suporte a promessas adicionais. Você deve chamá-los usando o [padrão de função de retorno de chamada aninhado](#asynchronous-programming-using-nested-callback-functions).

Depois que uma `Binding` promessa de objeto é atendida, ela pode ser reutilizada na chamada do método encadeado como se fosse uma associação (o tempo de execução do suplemento não tentará executar a promessa de forma assíncrona). Se a `Binding` promessa do objeto não puder ser atendida, o tempo de execução do suplemento tentará novamente acessar o objeto Binding na próxima vez que um de seus métodos assíncronos for chamado.

O exemplo de código a seguir usa o `select` método para recuperar uma associação com o `id` " `cities` " do `Bindings` conjunto e, em seguida, chama o método [addHandlerAsync](/javascript/api/office/office.binding#addhandlerasync-eventtype--handler--options--callback-) para adicionar um manipulador de eventos para o evento [DataChanged](/javascript/api/office/office.bindingdatachangedeventargs) da associação.




```js
function addBindingDataChangedEventHandler() {
    Office.select("bindings#cities", function onError(){/* error handling code */}).addHandlerAsync(Office.EventType.BindingDataChanged,
    function (eventArgs) {
        doSomethingWithBinding(eventArgs.binding);
    });
}

```


> [!IMPORTANT]
> A `Binding` promessa do objeto retornada pelo `Office.select` método fornece acesso apenas aos quatro métodos do `Binding` objeto. Se você precisar acessar qualquer um dos outros membros do `Binding` objeto, em vez disso, deverá usar a `Document.bindings` propriedade e `Bindings.getByIdAsync` ou os `Bindings.getAllAsync` métodos para recuperar o `Binding` objeto. Por exemplo, se você precisar acessar qualquer uma das `Binding` Propriedades do objeto (as `document` Propriedades, `id` ou, `type` ) ou precisar acessar as propriedades dos objetos [matrixbinding](/javascript/api/office/office.matrixbinding) ou [TableBinding](/javascript/api/office/office.tablebinding) , você deve usar os `getByIdAsync` `getAllAsync` métodos ou para recuperar um `Binding` objeto.


## <a name="passing-optional-parameters-to-asynchronous-methods"></a>Transmitir parâmetros opcionais para métodos assíncronos


A sintaxe comum para todos os métodos "Async" segue este padrão:

 _AsyncMethod_ `(`_RequiredParameters_`, [`_OptionalParameters_`],`_CallbackFunction_`);`

Todos os métodos assíncronos dão suporte parâmetros opcionais, que são passados como um objeto JSON (JavaScript Object Notation) contendo um ou mais parâmetros opcionais. O objeto JSON que contém os parâmetros opcionais é uma coleção desordenada de pares de valores e chaves com o caractere ":" separando os valores e as chaves. Cada par do objeto é separado por vírgula e o conjunto completo de pares é incluído entre chaves. A chave é o nome do parâmetro e o valor é o valor a ser transmitido para esse parâmetro.

Você pode criar o objeto JSON que contém parâmetros opcionais embutidos ou criando um `options` objeto e transmitindo-o como o parâmetro _Options_ .


### <a name="passing-optional-parameters-inline"></a>Transmitir parâmetros opcionais embutidos

Por exemplo, a sintaxe para chamar o método [Document.setSelectedDataAsync](/javascript/api/office/office.document#setselecteddataasync-data--options--callback-) com parâmetros opcionais embutidos tem esta aparência:

```js
 Office.context.document.setSelectedDataAsync(data, {coercionType: 'coercionType', asyncContext: 'asyncContext'},callback);

```

Neste formulário da sintaxe de chamada, os dois parâmetros opcionais, _coercionType_ e _asyncContext_, são definidos como um objeto JSON embutido entre chaves.

O exemplo a seguir mostra como chamar o `Document.setSelectedDataAsync` método especificando parâmetros opcionais embutidos.


```js
Office.context.document.setSelectedDataAsync(
    "<html><body>hello world</body></html>",
    {coercionType: "html", asyncContext: 42},
    function(asyncResult) {
        write(asyncResult.status + " " + asyncResult.asyncContext);
    }
)

// Function that writes to a div with id='message' on the page.
function write(message){
    document.getElementById('message').innerText += message; 
}
```


> [!NOTE]
> É possível especificar parâmetros opcionais em qualquer ordem no objeto JSON desde que seus nomes sejam especificados corretamente.


### <a name="passing-optional-parameters-in-an-options-object"></a>Transmitir parâmetros opcionais em um objeto de opções

Como alternativa, você pode criar um objeto nomeado `options` que especifica os parâmetros opcionais separadamente da chamada do método e, em seguida, passar o `options` objeto como o argumento _Options_ .

O exemplo a seguir mostra uma maneira de criar o `options` objeto, onde `parameter1` , `value1` e assim por diante, são espaços reservados para os valores e nomes de parâmetro reais.




```js
var options = {
    parameter1: value1,
    parameter2: value2,
    ...
    parameterN: valueN
};

```

Que é semelhante ao exemplo a seguir quando usado para especificar os parâmetros [ValueFormat](/javascript/api/office/office.valueformat) e [FilterType](/javascript/api/office/office.filtertype).




```js
var options = {
    valueFormat: "unformatted",
    filterType: "all"
};
```

Esta é outra maneira de criar o `options` objeto.




```js
var options = {};
options[parameter1] = value1;
options[parameter2] = value2;
...
options[parameterN] = valueN;
```

Que é semelhante ao exemplo a seguir quando usado para especificar `ValueFormat` os `FilterType` parâmetros e:


```js
var options = {};
options["ValueFormat"] = "unformatted";
options["FilterType"] = "all";
```


> [!NOTE]
> Ao usar um dos métodos de criação do `options` objeto, você pode especificar parâmetros opcionais em qualquer ordem, desde que seus nomes sejam especificados corretamente.

O exemplo a seguir mostra como chamar o `Document.setSelectedDataAsync` método especificando parâmetros opcionais em um `options` objeto.




```js
var options = {
   coercionType: "html",
   asyncContext: 42
};

document.setSelectedDataAsync(
    "<html><body>hello world</body></html>",
    options,
    function(asyncResult) {
        write(asyncResult.status + " " + asyncResult.asyncContext);
    }
)

// Function that writes to a div with id='message' on the page.
function write(message){
    document.getElementById('message').innerText += message; 
}
```


Em ambos os exemplos de parâmetros opcionais, o parâmetro _callback_ é especificado como o último parâmetro (seguindo os parâmetros opcionais embutidos ou seguindo o objeto de argumento _Options_ ). Como alternativa, você pode especificar o parâmetro _callback_ dentro o objeto JSON embutido ou no objeto `options`. No entanto, você pode transmitir o parâmetro _callback_ em um só local: no objeto _options_ (embutido ou criado externamente) ou como o último parâmetro, mas não ambos.

## <a name="wrap-common-apis-in-promise-returning-functions"></a>Dispor APIs comuns em funções que retornam a promessa

Os métodos Common API (e do Outlook API) não retornam [promessas](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise). Portanto, você não pode usar [Await](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/await) para pausar a execução até que a operação assíncrona seja concluída. Se você precisar `await` de comportamento, você pode encapsule a chamada do método em uma promessa criada explicitamente. 

O padrão básico é criar um método assíncrono que retorna um objeto Promise imediatamente e *resolve* esse objeto Promise quando o método interno é concluído ou *rejeita* o objeto se o método falhar. Veja a seguir um exemplo simples

```javascript
function getDocumentFilePath() {
    return new OfficeExtension.Promise(function (resolve, reject) {
        try {
            Office.context.document.getFilePropertiesAsync(function (asyncResult) {
                resolve(asyncResult.value.url);
            });
        }
        catch (error) {
            reject(WordMarkdownConversion.errorHandler(error));
        }
    })
}
```

Quando esse método precisa ser aguardado, ele pode ser chamado com a `await` palavra-chave ou como a função passada para uma `then` função.

> [!NOTE]
> Essa técnica é especialmente útil quando você precisa chamar uma das APIs comuns dentro de uma chamada do `run` método em um dos modelos de objeto específicos do aplicativo. Para obter um exemplo da função acima sendo usada dessa forma, confira o arquivo [Home.js no exemplo de Word-Add-in-JavaScript-MDConversion](https://github.com/OfficeDev/Word-Add-in-MarkdownConversion/blob/master/Word-Add-in-JavaScript-MDConversionWeb/Home.js).

Veja a seguir um exemplo usando TypeScript.

```typescript
readDocumentFileAsync(): Promise<any> {
    return new Promise((resolve, reject) => {
        const chunkSize = 65536;
        const self = this;

        Office.context.document.getFileAsync(Office.FileType.Compressed, { sliceSize: chunkSize }, (asyncResult) => {
            if (asyncResult.status === Office.AsyncResultStatus.Failed) {
                reject(asyncResult.error);
            } else {
                // `getAllSlices` is a Promise-wrapped implementation of File.getSliceAsync.
                self.getAllSlices(asyncResult.value).then(result => {
                    if (result.IsSuccess) {
                        resolve(result.Data);
                    } else {
                        reject(asyncResult.error);
                    }
                });
            }
        });
    });
}
```

## <a name="see-also"></a>Confira também

- [Entendendo a API de JavaScript do Office](understanding-the-javascript-api-for-office.md)
- [API JavaScript para Office](../reference/javascript-api-for-office.md)
