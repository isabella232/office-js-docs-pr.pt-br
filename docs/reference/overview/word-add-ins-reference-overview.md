# <a name="word-javascript-api-overview"></a><span data-ttu-id="46366-101">Visão geral da API JavaScript do Word</span><span class="sxs-lookup"><span data-stu-id="46366-101">Word JavaScript API overview</span></span>

<span data-ttu-id="46366-p101">O Word fornece um conjunto avançado de APIs que você pode usar para criar suplementos que interagem com o conteúdo e os metadados do documento. Use essas APIs para criar experiências convincentes que se integram e estendem o Word. Você pode importar e exportar conteúdo, montar novos documentos a partir de diferentes fontes de dados e integrar-se a fluxos de trabalho de documentos para criar soluções personalizadas de documentos.</span><span class="sxs-lookup"><span data-stu-id="46366-p101">Word provides a rich set of APIs that you can use to create add-ins that interact with document content and metadata. Use these APIs to create compelling experiences that integrate with and extend Word. You can import and export content, assemble new documents from different data sources, and integrate with document workflows to create custom document solutions.</span></span>

<span data-ttu-id="46366-105">Você pode usar duas APIs JavaScript para interagir com metadados e objetos em um documento do Word:</span><span class="sxs-lookup"><span data-stu-id="46366-105">You can use two JavaScript APIs to interact with the objects and metadata in a Word document:</span></span>

- <span data-ttu-id="46366-106">API JavaScript do Word – introduzida no Office 2016.</span><span class="sxs-lookup"><span data-stu-id="46366-106">Word JavaScript API - Introduced in Office 2016.</span></span>
- <span data-ttu-id="46366-107">[API JavaScript para Office](../javascript-api-for-office.md) (Office.js) – introduzida no Office 2013.</span><span class="sxs-lookup"><span data-stu-id="46366-107">[JavaScript API for Office](../javascript-api-for-office.md) (Office.js) - Introduced in Office 2013.</span></span>

## <a name="word-javascript-api"></a><span data-ttu-id="46366-108">API JavaScript do Word</span><span class="sxs-lookup"><span data-stu-id="46366-108">Word JavaScript API</span></span>

<span data-ttu-id="46366-p102">A API JavaScript do Word é carregada pelo Office.js. A API JavaScript do Word altera a maneira como você pode interagir com objetos como documentos e parágrafos. Em vez de fornecer APIs assíncronas individuais para recuperar e atualizar cada um desses objetos, a API JavaScript do Word fornece objetos JavaScript “proxy” que correspondem aos objetos reais em execução no Word. Você pode interagir com esses objetos proxy lendo e gravando suas propriedades de maneira síncrona e chamando métodos síncronos para executar operações neles. Essas interações com objetos proxy não são imediatamente realizadas no script em execução. O método **context.sync** sincroniza o estado entre o JavaScript em execução e os objetos reais no Office, executando instruções enfileiradas e recuperando propriedades de objetos Word carregados para uso em seu script.</span><span class="sxs-lookup"><span data-stu-id="46366-p102">The Word JavaScript API is loaded by Office.js. The Word JavaScript API changes the way that you can interact with objects like documents and paragraphs. Rather than providing individual asynchronous APIs for retrieving and updating each of these objects, the Word JavaScript API provides “proxy” JavaScript objects that correspond to the real objects running in Word. You can interact with these proxy objects by synchronously reading and writing their properties and calling synchronous methods to perform operations on them. These interactions with proxy objects aren’t immediately realized in the running script. The **context.sync** method synchronizes the state between your running JavaScript and the real objects in Office by executing queued instructions and retrieving properties of loaded Word objects for use in your script.</span></span>

## <a name="javascript-api-for-office"></a><span data-ttu-id="46366-115">API JavaScript para Office</span><span class="sxs-lookup"><span data-stu-id="46366-115">JavaScript API for Office</span></span>

<span data-ttu-id="46366-116">Você pode fazer referência ao Office.js nos seguintes locais:</span><span class="sxs-lookup"><span data-stu-id="46366-116">You can reference Office.js from the following locations:</span></span>

* <span data-ttu-id="46366-117">https://appsforoffice.microsoft.com/lib/1/hosted/office.js - use este recurso para suplementos de produção.</span><span class="sxs-lookup"><span data-stu-id="46366-117">https://appsforoffice.microsoft.com/lib/1/hosted/office.js - use this resource for production add-ins.</span></span>
* <span data-ttu-id="46366-118">https://appsforoffice.microsoft.com/lib/beta/hosted/office.js - use este recurso quando você estiver tentando os recursos de versão prévia.</span><span class="sxs-lookup"><span data-stu-id="46366-118">https://appsforoffice.microsoft.com/lib/beta/hosted/office.js - use this resource when you're trying out preview features.</span></span>

<span data-ttu-id="46366-p103">Se estiver usando o [Visual Studio](https://www.visualstudio.com/products/free-developer-offers-vs), você poderá baixar o [Office Developer Tools](https://www.visualstudio.com/features/office-tools-vs.aspx) para obter modelos de projeto que incluam o Office.js.  Você pode usar o [nuget para obter o Office.js](https://www.nuget.org/packages/Microsoft.Office.js/).</span><span class="sxs-lookup"><span data-stu-id="46366-p103">If you're using [Visual Studio](https://www.visualstudio.com/products/free-developer-offers-vs), you can download the [Office Developer Tools](https://www.visualstudio.com/features/office-tools-vs.aspx) to get project templates that include Office.js.  You can also use [nuget to get Office.js](https://www.nuget.org/packages/Microsoft.Office.js/).</span></span>

<span data-ttu-id="46366-121">Se você usar TypeScript e tiver npm, poderá obter as definições de TypeScript ao digitar isto na interface da linha de comando: `typings install office-js --ambient`.</span><span class="sxs-lookup"><span data-stu-id="46366-121">If you use TypeScript and have npm, you can get the the TypeScript definitions by typing this in your command line interface: `typings install office-js --ambient`.</span></span>

## <a name="running-word-add-ins"></a><span data-ttu-id="46366-122">Execução de suplementos do Word</span><span class="sxs-lookup"><span data-stu-id="46366-122">Running Word add-ins</span></span>

<span data-ttu-id="46366-p104">Para executar o suplemento, use um manipulador de eventos Office.initialize. Confira [Compreenda a API](https://docs.microsoft.com/office/dev/add-ins/develop/understanding-the-javascript-api-for-office) para saber mais sobre a inicialização de suplementos.</span><span class="sxs-lookup"><span data-stu-id="46366-p104">To run your add-in, use an Office.initialize event handler. For more information about add-in initialization, see [Understanding the API](https://docs.microsoft.com/office/dev/add-ins/develop/understanding-the-javascript-api-for-office) .</span></span>

<span data-ttu-id="46366-125">Os suplementos que segmentam o Word 2016 ou posterior executam passando uma função para o método **Word.run()** .</span><span class="sxs-lookup"><span data-stu-id="46366-125">Add-ins that target Word 2016 or later execute by passing a function into the **Word.run()** method.</span></span> <span data-ttu-id="46366-126">A função passada para o método **run** deve ter um argumento de contexto.</span><span class="sxs-lookup"><span data-stu-id="46366-126">The function passed into the **run** method must have a context argument.</span></span> <span data-ttu-id="46366-127">Este [objeto de contexto](/javascript/api/word/word.requestcontext) é diferente do objeto de contexto que você obtém do objeto Office, mas também é usado para interagir com o ambiente de tempo de execução do Word.</span><span class="sxs-lookup"><span data-stu-id="46366-127">This [context object](/javascript/api/word/word.requestcontext) is different than the context object you get from the Office object, but it is also used to interact with the Word runtime environment.</span></span> <span data-ttu-id="46366-128">O objeto de contexto fornece acesso ao modelo de objeto da API JavaScript do Word.</span><span class="sxs-lookup"><span data-stu-id="46366-128">The context object provides access to the Word JavaScript API object model.</span></span> <span data-ttu-id="46366-129">O exemplo a seguir mostra como inicializar e executar um suplemento do Word usando o método **Word.run()** .</span><span class="sxs-lookup"><span data-stu-id="46366-129">The following example shows how to initialize and execute a Word add-in by using the **Word.run()** method.</span></span>

```js
(function () {
    "use strict";

    // The initialize event handler must be run on each page to initialize Office JS.
    // You can add optional custom initialization code that will run after OfficeJS
    // has initialized.
    Office.initialize = function (reason) {
        // The reason object tells how the add-in was initialized. The values can be:
        // inserted - the add-in was inserted to an open document.
        // documentOpened - the add-in was already inserted in to the document and the document was opened.

        // Checks for the DOM to load using the jQuery ready function.
        $(document).ready(function () {
            // Set your optional initialization code.
            // You can also load saved settings from the Office object.
        });
    };

    // Run a batch operation against the Word JavaScript API object model.
    // Use the context argument to get access to the Word document.
    Word.run(function (context) {

        // Create a proxy object for the document.
        var thisDocument = context.document;
        // ...
    })
})();
```

### <a name="synchronizing-word-documents-with-word-javascript-api-proxy-objects"></a><span data-ttu-id="46366-130">Sincronização de documentos do Word com objetos proxy da API JavaScript do Word</span><span class="sxs-lookup"><span data-stu-id="46366-130">Synchronizing Word documents with Word JavaScript API proxy objects</span></span>

<span data-ttu-id="46366-p106">O modelo de objeto da API JavaScript do Word é fracamente acoplado aos objetos no Word. Os objetos da API JavaScript do Word são proxies de objetos em um documento do Word. Ações realizadas em objetos proxy não são realizadas no Word até que o estado do documento seja sincronizado. Por outro lado, o estado do documento do Word não é realizado nos objetos de proxy até que o estado do documento tenha sido sincronizado. Para sincronizar o estado do documento, você executa o método **context.sync()** . O exemplo a seguir cria um objeto de corpo de proxy e um comando enfileirado para carregar a propriedade de texto no objeto de corpo do proxy e usa o método **context.sync()** para sincronizar o corpo do documento do Word com o objeto proxy do corpo.</span><span class="sxs-lookup"><span data-stu-id="46366-p106">The Word JavaScript API object model is loosely coupled with the objects in Word. Word JavaScript API objects are proxies for objects in a Word document. Actions taken on proxy objects are not realized in Word until the document state has been synchronized. Conversely, the state of the Word document is not realized in the proxy objects until the document state has been synchronized. To synchronize the document state, you run the **context.sync()** method. The following example creates a proxy body object and a queued command to load the text property on the proxy body object, and uses the **context.sync()** method to synchronize the body of the Word document with the body proxy object.</span></span>

```js
// Run a batch operation against the Word object model.
Word.run(function (context) {

    // Create a proxy object for the document body.
    // The body object hasn't been set with any property values.
    var body = context.document.body;

    // Queue a command to load the text property for the proxy document body object.
    context.load(body, 'text');

    // Synchronize the document state by executing the queued commands,
    // and return a promise to indicate task completion.
    return context.sync().then(function () {
        console.log("Body contents: " + body.text);
    });
})
```

### <a name="executing-a-batch-of-commands"></a><span data-ttu-id="46366-137">Execução de um lote de comandos</span><span class="sxs-lookup"><span data-stu-id="46366-137">Executing a batch of commands</span></span>

<span data-ttu-id="46366-p107">Os objetos de proxy do Word possuem métodos para acessar e atualizar o modelo de objeto. Esses métodos são executados sequencialmente na ordem em que foram enfileirados no lote. Todos os comandos que estão enfileirados no lote são executados quando context.sync() é chamado.</span><span class="sxs-lookup"><span data-stu-id="46366-p107">The Word proxy objects have methods for accessing and updating the object model. These methods are executed sequentially in the order in which they were queued in the batch. All of the commands that are queued in the batch are executed when context.sync() is called.</span></span>

<span data-ttu-id="46366-p108">O exemplo a seguir mostra como funciona a fila de comandos. Quando o método **context.sync()** é chamado, o comando para carregar o corpo de texto é executado no Word. Em seguida, ocorre o comando para inserir o texto no corpo do Word. Os resultados são retornados ao objeto proxy do corpo. O valor da propriedade **body.text**, na API JavaScript do Word, é o valor do corpo do documento do Word, <u>antes</u> da inserção do texto no documento do Word.</span><span class="sxs-lookup"><span data-stu-id="46366-p108">The following example shows how the command queue works. When **context.sync()** is called, the command to load the body text is executed in Word. Then, the command to insert text into the body in Word occurs. The results are then returned to the body proxy object. The value of the **body.text** property in the Word JavaScript API is the value of the Word document body <u>before</u> the text was inserted into Word document.</span></span>


```js
// Run a batch operation against the Word JavaScript API.
Word.run(function (context) {

    // Create a proxy object for the document body.
    var body = context.document.body;

    // Queue a command to load the text property of the proxy body object.
    context.load(body, 'text');

    // Queue a command to insert text into the end of the Word document body.
    body.insertText('This is text inserted after loading the body.text property',
                    Word.InsertLocation.end);

    // Synchronize the document state by executing the queued commands,
    // and return a promise to indicate task completion.
    return context.sync().then(function () {
        console.log("Body contents: " + body.text);
    });
})
```

## <a name="word-javascript-api-open-specifications"></a><span data-ttu-id="46366-146">Especificações abertas da API JavaScript do Word</span><span class="sxs-lookup"><span data-stu-id="46366-146">Word JavaScript API open specifications</span></span>

<span data-ttu-id="46366-p109">À medida que projetamos e desenvolvemos novas APIs para suplementos do Word, disponibilizamos-as para seus comentários na nossa página [Especificações abertas da API](../openspec.md). Descubra quais novos recursos estão no pipeline para as APIs JavaScript do Word e forneça sua opinião sobre nossas especificações de design.</span><span class="sxs-lookup"><span data-stu-id="46366-p109">As we design and develop new APIs for Word add-ins, we'll make them available for your feedback on our [Open API specifications](../openspec.md) page. Find out what new features are in the pipeline for the Word JavaScript APIs, and provide your input on our design specifications.</span></span>

## <a name="word-javascript-api-reference"></a><span data-ttu-id="46366-149">Referências da API JavaScript do Word</span><span class="sxs-lookup"><span data-stu-id="46366-149">Word JavaScript API reference</span></span>

<span data-ttu-id="46366-150">Para obter informações detalhadas sobre a API JavaScript do Word, confira a [Documentação de referência da API JavaScript do Word](/javascript/api/word).</span><span class="sxs-lookup"><span data-stu-id="46366-150">For detailed information about the Word JavaScript API, see the [Word JavaScript API reference documentation](/javascript/api/word).</span></span>

## <a name="see-also"></a><span data-ttu-id="46366-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="46366-151">See also</span></span>

* [<span data-ttu-id="46366-152">Visão geral dos suplementos do Word</span><span class="sxs-lookup"><span data-stu-id="46366-152">Word add-ins overview</span></span>](https://docs.microsoft.com/office/dev/add-ins/word/word-add-ins-programming-overview)
* [<span data-ttu-id="46366-153">Visão geral da plataforma de suplementos do Office</span><span class="sxs-lookup"><span data-stu-id="46366-153">Office Add-ins platform overview</span></span>](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)
* [<span data-ttu-id="46366-154">Exemplos de suplementos do Word no GitHub</span><span class="sxs-lookup"><span data-stu-id="46366-154">Word add-in samples on GitHub</span></span>](https://github.com/OfficeDev?utf8=%E2%9C%93&q=Word)