# <a name="excel-javascript-api-core-concepts"></a>Principais conceitos da API JavaScript do Excel
 
Este artigo descreve como usar a [API JavaScript do Excel](http://dev.office.com/reference/add-ins/excel/excel-add-ins-reference-overview) para desenvolver suplementos para o Excel 2016. Ele apresenta os conceitos básicos que são fundamentais para usar a API e fornece orientações para executar tarefas específicas, como leitura ou gravação em um intervalo grande, atualização de todas as células do intervalo e muito mais.

## <a name="asynchronous-nature-of-excel-apis"></a>Natureza assíncrona das APIs do Excel

Os suplementos do Excel baseados na Web são executados dentro de um contêiner de navegador que é inserido no aplicativo do Office em plataformas baseadas em desktop, como Office para Windows, e executado dentro de um iFrame HTML no Office Online. Não é possível habilitar a API Office.js para interagir de modo síncrono com o host do Excel em todas as plataformas suportadas devido às considerações de desempenho. Desse modo, a chamada à API **sync()** na Office.js retorna uma [promessa](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) que é resolvida quando o aplicativo Excel conclui as ações solicitadas de leitura ou gravação. Além disso, você pode enfileirar várias ações, como configurar propriedades ou invocar métodos, e executá-las como um lote de comandos com uma única chamada a **sync()**, em vez de enviar uma solicitação separada para cada ação. As seções a seguir descrevem como fazer isso usando as APIs **Excel.run()** e **sync()**.
 
## <a name="excelrun"></a>Excel.run
 
A **Excel.run** executa uma função em que você especifica as ações a serem executadas no modelo de objeto do Excel. A **Excel.run** cria automaticamente um contexto de solicitação que pode ser usado para sua interação com os objetos do Excel. Quando a **Excel.run** é concluída, uma promessa é resolvida e todos os objetos que foram alocados em tempo de execução são lançados automaticamente.
 
O exemplo a seguir mostra como usar a **Excel.run**. A instrução catch captura e grava em log os erros que ocorrem na **Excel.run**.
 
```js
Excel.run(function (context) {
  // You can use the Excel JavaScript API here in the batch function
  // to execute actions on the Excel object model.
  console.log('Your code goes here.');
}).catch(function (error) {
  console.log('error: ' + error);
  if (error instanceof OfficeExtension.Error) {
    console.log('Debug info: ' + JSON.stringify(error.debugInfo));
  }
});
```

## <a name="request-context"></a>Contexto de solicitação
 
O Excel e seu suplemento são executados em dois processos diferentes. Como eles usam diferentes ambientes de tempo de execução, os suplementos do Excel exigem um objeto **RequestContext** para conectar o suplemento aos objetos no Excel, como planilhas, intervalos, gráficos e tabelas.
 
## <a name="proxy-objects"></a>Objetos proxy
 
Os objetos JavaScript do Excel que você declara e usa em um suplemento são objetos proxy. Todos os métodos invocados, ou as propriedades definidas ou carregadas em objetos proxy são simplesmente adicionados a uma fila de comandos pendentes. Quando você chama o método **sync()** no contexto de solicitação (por exemplo, `context.sync()`), os comandos enfileirados são expedidos para o Excel e executados. A API JavaScript do Excel é basicamente centrada em lote. Você pode enfileirar quantas alterações desejar no contexto de solicitação e depois chamar o método **sync()** para executar o lote de comandos enfileirados.
 
Por exemplo, o trecho de código a seguir declara o objeto JavaScript local **selectedRange** para fazer referência a um intervalo selecionado no documento do Excel e, em seguida, define algumas propriedades nesse objeto. O objeto **selectedRange** é um objeto proxy, de modo que as propriedades que são definidas e o método que é invocado nesse objeto não serão refletidos no documento do Excel até que o suplemento chame **context.sync()**.
 
```js
const selectedRange = context.workbook.getSelectedRange();
selectedRange.format.fill.color = "#4472C4";
selectedRange.format.font.color = "white";
selectedRange.format.autofitColumns();
```
 
### <a name="sync"></a>sync()
 
Chamar o método **sync()** no contexto de solicitação sincroniza o estado entre objetos proxy e objetos no documento do Excel. O método **sync()** executa todos os comandos que são enfileirados no contexto de solicitação e recupera valores para qualquer propriedade que deva ser carregada nos objetos proxy. O método **sync()** é executado de modo assíncrono e retorna uma [promessa](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise), que é resolvida quando o método **sync()** é concluído.
 
>**Observação**: Na API JavaScript do Excel, **sync()** é a única operação assíncrona. Para otimizar o desempenho, você deve enfileirar o máximo de alterações possíveis antes de chamar **sync()** e minimizar o número de vezes que chama **sync()**.
 
O exemplo a seguir mostra uma função de lote que define um objeto proxy JavaScript local (**selectedRange**), carrega uma propriedade desse objeto e, em seguida, usa o padrão Promessas do JavaScript para chamar **context.sync()** a fim de sincronizar o estado entre objetos proxy e objetos no documento do Excel.
 
```js
Excel.run(function (context) {
  const selectedRange = context.workbook.getSelectedRange();
  selectedRange.load('address');
  return context.sync()
    .then(function () {
      console.log('The selected range is: ' + selectedRange.address);
  });
}).catch(function (error) {
  console.log('error: ' + error);
  if (error instanceof OfficeExtension.Error) {
    console.log('Debug info: ' + JSON.stringify(error.debugInfo));
  }
});
```
 
No exemplo anterior, **selectedRange** está definido e sua propriedade **address** é carregada quando **context.sync()** é chamado.
 
Como **sync()** é uma operação assíncrona que retorna uma promessa, você sempre deve **retornar** a promessa (no JavaScript). Isso garante que a operação **sync()** seja concluída antes que o script continue sendo executado.
 
### <a name="load"></a>load()
 
Para que você possa ler as propriedades de um objeto proxy, é preciso carregar explicitamente as propriedades para popular o objeto proxy com dados do documento do Excel e chamar **context.sync()**. Por exemplo, se você criar um objeto proxy para fazer referência a um intervalo selecionado e, em seguida, quiser ler a propriedade **address** do intervalo selecionado, será preciso carregar a propriedade **address** para que seja possível lê-la. Para solicitar que as propriedades de um objeto proxy sejam carregadas, chame o método **load()** no objeto e especifique as propriedades a serem carregadas. 

>**Observação**: Se estiver apenas chamando métodos ou definindo propriedades em um objeto proxy, você não precisa chamar o método **load()**. O método **load()** é necessário somente quando você deseja ler propriedades em um objeto proxy.
 
Assim como as solicitações para definir propriedades ou invocar métodos em objetos proxy, as solicitações para carregar propriedades em objetos proxy são adicionadas à fila de comandos pendentes no contexto de solicitação, sendo executadas na próxima vez que você chamar o método **sync()**. Você pode enfileirar quantas chamadas a **load()** no contexto de solicitação forem necessárias.
 
No exemplo a seguir, somente propriedades específicas do intervalo são carregadas.
 
```js
Excel.run(function (context) {
  const sheetName = 'Sheet1';
  const rangeAddress = 'A1:B2';
  const myRange = context.workbook.worksheets.getItem(sheetName).getRange(rangeAddress);
 
  myRange.load(['address', 'format/*', 'format/fill', 'entireRow' ]);
 
  return context.sync()
    .then(function () {
      console.log (myRange.address);              // ok
      console.log (myRange.format.wrapText);      // ok
      console.log (myRange.format.fill.color);    // ok
      //console.log (myRange.format.font.color);  // not ok as it was not loaded
  });
}).then(function () {
  console.log('done');
}).catch(function (error) {
  console.log('Error: ' + error);
  if (error instanceof OfficeExtension.Error) {
    console.log('Debug info: ' + JSON.stringify(error.debugInfo));
  }
});
```
 
No exemplo anterior, como `format/font` não é especificado na chamada a **myRange.load()**, a propriedade `format.font.color` não pode ser lida.
 
Para otimizar o desempenho, você deve especificar explicitamente as propriedades e as relações a serem carregadas ao usar o método **load()** em um objeto. Por exemplo, se sua intenção é apenas ler a propriedade **address** de um objeto do intervalo, especifique somente essa propriedade quando chamar o método **load()**:
 
```js
range.load('address');
```
 
Você pode chamar o método **load()** de duas maneiras:
 
_Sintaxe:_
 
```js
object.load(string: properties);
// or
object.load(array: properties);
// or
object.load({ loadOption });
```
 
_Onde:_
 
* `properties` é a lista de propriedades e/ou nomes de relações a serem carregados, especificados como cadeias de caracteres delimitadas por vírgulas ou uma matriz de nomes. Para saber mais, veja os métodos **load()** definidos para objetos na [referência da API JavaScript do Excel](http://dev.office.com/reference/add-ins/excel/excel-add-ins-reference-overview).
* `loadOption` especifica um objeto que descreve as opções de seleção, expansão, topo e pulo. Confira as [opções](http://dev.office.com/reference/add-ins/excel/loadoption) de carregamento de objeto para saber mais.

Para saber mais sobre o método **load()**, confira os [conceitos avançados da API JavaScript do Excel](excel-add-ins-advanced-concepts.md).

## <a name="null-or-blank-property-values"></a>Valores de propriedade nula ou em branco
 
### <a name="null-input-in-2-d-array"></a>entrada nula em uma matriz 2D
 
No Excel, um intervalo é representado por uma matriz 2D, onde a primeira dimensão é linhas e a segunda dimensão é colunas. Para definir valores, o formato do número ou a fórmula apenas para células específicas em um intervalo, especifique os valores, o formato do número ou a fórmula para essas células na matriz 2D, bem como `null` para todas as outras células na matriz 2D.
 
Por exemplo, para atualizar o formato do número apenas para uma célula em um intervalo e manter o formato de número existente para todas as outras células no intervalo, especifique o novo formato de número para a célula a ser atualizada e `null` para todas as outras células. O trecho de código a seguir define um novo formato de número para a quarta célula no intervalo e não altera o formato de número para as primeiras três células no intervalo.
 
```js
range.values = [['Eurasia', '29.96', '0.25', '15-Feb' ]];
range.numberFormat = [[null, null, null, 'm/d/yyyy;@']];
```
 
### <a name="null-input-for-a-property"></a>Entrada nula para uma propriedade
 
`null` não é uma entrada válida para uma propriedade única. Por exemplo, o trecho de código a seguir não é válido, pois a propriedade **values** do intervalo não pode ser definida como `null`.
 
```js
range.values = null;
```
 
Da mesma forma, o trecho de código a seguir não é válido, pois `null` não é um valor válido para a propriedade **color**.
 
```js
range.format.fill.color =  null;
```
 
### <a name="null-property-values-in-the-response"></a>Valores da propriedade nula na resposta
 
A formatação de propriedades como `size` e `color` conterá valores `null` na resposta quando valores diferentes existirem no intervalo especificado. Por exemplo, se você recuperar um intervalo e carregar sua propriedade `format.font.color`:
 
* Se todas as células no intervalo tiverem a mesma cor de fonte, `range.format.font.color` especificará essa cor.
* Se houver várias cores de fonte dentro do intervalo, `range.format.font.color` será `null`.
 
### <a name="blank-input-for-a-property"></a>Entrada em branco para uma propriedade
 
Quando você especificar um valor em branco para uma propriedade (isto é, duas aspas sem espaço entre elas `''`), ele será interpretado como uma instrução para limpar ou redefinir a propriedade. Por exemplo:
 
* Se você especificar um valor em branco para a propriedade `values` de um intervalo, o conteúdo do intervalo será apagado.
 
* Se você especificar um valor em branco para a propriedade `numberFormat`, o formato de número será redefinido para `General`.
 
* Se você especificar um valor em branco para a propriedade `formula` e a propriedade `formulaLocale`, os valores de fórmula serão apagados.
 
### <a name="blank-property-values-in-the-response"></a>Valores da propriedade em branco na resposta
 
Para operações de leitura, um valor de propriedade em branco na resposta (isto é, duas aspas sem espaço entre elas `''`) indica que a célula não contém dados nem valor. No primeiro exemplo abaixo, a primeira e a última célula no intervalo não contêm dados. No segundo exemplo, as primeiras duas células no intervalo não contêm uma fórmula.
 
```js
range.values = [['', 'some', 'data', 'in', 'other', 'cells', '']];
```
 
```js
range.formula = [['', '', '=Rand()']];
```
 
## <a name="read-or-write-to-an-unbounded-range"></a>Ler ou gravar em um intervalo não limitado
 
### <a name="read-an-unbounded-range"></a>Ler um intervalo não limitado
 
Um endereço de intervalo não limitado é um endereço de intervalo que especifica colunas ou linhas inteiras. Por exemplo:
 
* Endereços de intervalo composto por colunas inteiras:<ul><li>`C:C`</li><li>`A:F`</li></ul>
* Endereços de intervalo composto por linhas inteiras:<ul><li>`2:2`</li><li>`1:4`</li></ul>
 
Quando uma API faz uma solicitação para recuperar um intervalo não limitado (por exemplo, `getRange('C:C')`), a resposta conterá valores `null` para as propriedades no nível de célula, como `values`, `text`, `numberFormat` e `formula`. Outras propriedades do intervalo, como `address` e `cellCount`, conterão valores válidos para o intervalo não limitado.
 
### <a name="write-to-an-unbounded-range"></a>Gravar em um intervalo não limitado
 
Não é possível definir propriedades no nível de célula, como `values`, `numberFormat` e `formula`, no intervalo não limitado, pois a solicitação de entrada é muito grande. Por exemplo, o trecho de código a seguir não é válida porque ele tenta especificar `values` para um intervalo não limitado. A API retornará um erro se você tentar definir as propriedades no nível de célula para um intervalo não limitado.
 
```js
const range = context.workbook.worksheets.getActiveWorksheet().getRange('A:B');
range.values = 'Due Date';
```
 
## <a name="read-or-write-to-a-large-range"></a>Ler ou gravar em um intervalo grande
 
Se um intervalo contiver um grande número de células, valores, formatos de número e/ou fórmulas, talvez não seja possível executar operações de API nesse intervalo. A API sempre fará a melhor tentativa de executar a operação solicitada em um intervalo (isto é, para recuperar ou gravar os dados especificados), mas tentar executar operações de leitura ou gravação para um intervalo grande pode resultar em um erro de API devido à utilização excessiva de recursos. Para evitar tais erros, é recomendável executar operações de leitura ou gravação separadas para subconjuntos menores de um intervalo grande, em vez de tentar executar uma única operação de leitura ou gravação em um intervalo grande.
 
## <a name="update-all-cells-in-a-range"></a>Atualizar todas as células em um intervalo
 
Para aplicar a mesma atualização a todas as células em um intervalo, (por exemplo, para popular todas as células com o mesmo valor, definir o mesmo formato de número ou popular todas as células com a mesma fórmula), defina a propriedade correspondente no objeto **range** para o valor (único) desejado.
 
O exemplo a seguir obtém um intervalo que contém 20 células e, em seguida, define o formato de número e popula todas as células do intervalo com o valor **11/3/2015**.
 
```js
Excel.run(function (context) {
  const sheetName = 'Sheet1';
  const rangeAddress = 'A1:A20';
  const worksheet = context.workbook.worksheets.getItem(sheetName);
 
  const range = worksheet.getRange(rangeAddress);
  range.numberFormat = 'm/d/yyyy';
  range.values = '3/11/2015';
  range.load('text');
 
  return context.sync()
    .then(function () {
      console.log(range.text);
  });
}).catch(function (error) {
  console.log('Error: ' + error);
  if (error instanceof OfficeExtension.Error) {
    console.log('Debug info: ' + JSON.stringify(error.debugInfo));
  }
});
```
 
## <a name="error-messages"></a>Mensagens de erro
 
Quando ocorrer um erro de API, a API retornará um objeto **error** que contém um código e uma mensagem. A tabela a seguir define uma lista de erros que a API pode retornar.
 
|error.code | error.message |
|:----------|:--------------|
|InvalidArgument |O argumento é inválido, está ausente ou tem um formato incorreto.|
|InvalidRequest  |Não é possível processar a solicitação.|
|InvalidReference|Esta referência não é válida para a operação atual.|
|InvalidBinding  |Esta associação de objetos não é mais válida devido às atualizações anteriores.|
|InvalidSelection|A seleção atual é inválida para esta operação.|
|Unauthenticated |Informações de autenticação necessárias estão ausentes ou inválidas.|
|AccessDenied |Você não pode realizar a operação solicitada.|
|ItemNotFound |O recurso solicitado não existe.|
|ActivityLimitReached|O limite de atividades foi alcançado.|
|GeneralException|Ocorreu um erro interno ao processar a solicitação.|
|NotImplemented  |O recurso solicitado não foi implementado.|
|ServiceNotAvailable|O serviço não está disponível.|
|Conflito              |A solicitação não pôde ser processada devido a um conflito.|
|ItemAlreadyExists|O recurso que está sendo criado já existe.|
|UnsupportedOperation|Não há suporte para a operação que está sendo tentada.|
|RequestAborted|A solicitação foi anulada durante o tempo de execução.|
|ApiNotAvailable|A API solicitada não está disponível.|
|InsertDeleteConflict|A tentativa de operação de exclusão ou inserção resultou em um conflito.|
|InvalidOperation|A tentativa de operação é inválida no objeto.|
 
## <a name="additional-resources"></a>Recursos adicionais
 
* [Introdução aos suplementos do Excel](excel-add-ins-get-started-overview.md)
* [Exemplos de código de suplementos do Excel](http://dev.office.com/code-samples#?filters=excel,office%20add-ins)
* [Referência da API JavaScript do Excel](http://dev.office.com/reference/add-ins/excel/excel-add-ins-reference-overview)