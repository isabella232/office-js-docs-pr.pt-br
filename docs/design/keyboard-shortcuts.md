---
title: Atalhos de teclado personalizados em suplementos do Office
description: Saiba como adicionar atalhos de teclado personalizados, também conhecidos como combinações de teclas, ao suplemento do Office.
ms.date: 11/09/2020
localization_priority: Normal
ms.openlocfilehash: f95c26067203a4ec2659aa6a632403c96ed81674
ms.sourcegitcommit: ca66ff7462bfdf4ed7ae04f43d1388c24de63bf9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "48996671"
---
# <a name="add-custom-keyboard-shortcuts-to-your-office-add-ins-preview"></a><span data-ttu-id="fce36-103">Adicionar atalhos de teclado personalizados para seus suplementos do Office (visualização)</span><span class="sxs-lookup"><span data-stu-id="fce36-103">Add Custom keyboard shortcuts to your Office Add-ins (preview)</span></span>

<span data-ttu-id="fce36-104">Os atalhos de teclado, também conhecidos como combinações de teclas, permitem que os usuários do seu suplemento trabalhem com mais eficiência e melhoram a acessibilidade do suplemento aos usuários com deficiências, fornecendo uma alternativa ao mouse.</span><span class="sxs-lookup"><span data-stu-id="fce36-104">Keyboard shortcuts, also known as key combinations, enable your add-in's users to work more efficiently and they improve the add-in's accessibility for users with disabilities by providing an alternative to the mouse.</span></span>

[!include[Keyboard shortcut prerequisites](../includes/keyboard-shortcuts-prerequisites.md)]

> [!NOTE]
> <span data-ttu-id="fce36-105">Para começar com uma versão de trabalho de um suplemento com atalhos de teclado já habilitados, clone e execute os [atalhos de teclado do Excel](https://github.com/OfficeDev/PnP-OfficeAddins/tree/master/Samples/excel-keyboard-shortcuts)de exemplo.</span><span class="sxs-lookup"><span data-stu-id="fce36-105">To start with a working version of an add-in with keyboard shortcuts already enabled, clone and run the sample [Excel Keyboard Shortcuts](https://github.com/OfficeDev/PnP-OfficeAddins/tree/master/Samples/excel-keyboard-shortcuts).</span></span> <span data-ttu-id="fce36-106">Quando estiver pronto para adicionar atalhos de teclado ao seu próprio suplemento, continue com este artigo.</span><span class="sxs-lookup"><span data-stu-id="fce36-106">When you are ready to add keyboard shortcuts to your own add-in, continue with this article.</span></span>

<span data-ttu-id="fce36-107">Há três etapas para adicionar atalhos de teclado a um suplemento:</span><span class="sxs-lookup"><span data-stu-id="fce36-107">There are three steps to add keyboard shortcuts to an add-in:</span></span>

1. <span data-ttu-id="fce36-108">[Configure o manifesto do suplemento](#configure-the-manifest).</span><span class="sxs-lookup"><span data-stu-id="fce36-108">[Configure the add-in's manifest](#configure-the-manifest).</span></span>
1. <span data-ttu-id="fce36-109">[Crie ou edite o arquivo JSON de atalhos](#create-or-edit-the-shortcuts-json-file) para definir ações e seus atalhos de teclado.</span><span class="sxs-lookup"><span data-stu-id="fce36-109">[Create or edit the shortcuts JSON file](#create-or-edit-the-shortcuts-json-file) to define actions and their keyboard shortcuts.</span></span>
1. <span data-ttu-id="fce36-110">[Adicione uma ou mais chamadas de tempo de execução](#create-a-mapping-of-actions-to-their-functions) da API [Office. Actions. associa](/javascript/api/office/office.actions#associate) para mapear uma função para cada ação.</span><span class="sxs-lookup"><span data-stu-id="fce36-110">[Add one or more runtime calls](#create-a-mapping-of-actions-to-their-functions) of the [Office.actions.associate](/javascript/api/office/office.actions#associate) API to map a function to each action.</span></span>

## <a name="configure-the-manifest"></a><span data-ttu-id="fce36-111">Configurar o manifesto</span><span class="sxs-lookup"><span data-stu-id="fce36-111">Configure the manifest</span></span>

<span data-ttu-id="fce36-112">Há duas pequenas alterações para o manifesto fazer.</span><span class="sxs-lookup"><span data-stu-id="fce36-112">There are two small changes to the manifest to make.</span></span> <span data-ttu-id="fce36-113">Uma é habilitar o suplemento para usar um tempo de execução compartilhado e o outro é apontar para um arquivo formatado por JSON onde você definiu os atalhos de teclado.</span><span class="sxs-lookup"><span data-stu-id="fce36-113">One is to enable the add-in to use a shared runtime and the other is to point to a JSON-formatted file where you defined the keyboard shortcuts.</span></span>

### <a name="configure-the-add-in-to-use-a-shared-runtime"></a><span data-ttu-id="fce36-114">Configurar o suplemento para usar um tempo de execução compartilhado</span><span class="sxs-lookup"><span data-stu-id="fce36-114">Configure the add-in to use a shared runtime</span></span>

<span data-ttu-id="fce36-115">Adicionar atalhos de teclado personalizados exige que seu suplemento use o tempo de execução compartilhado.</span><span class="sxs-lookup"><span data-stu-id="fce36-115">Adding custom keyboard shortcuts requires your add-in to use the shared runtime.</span></span> <span data-ttu-id="fce36-116">Para obter mais informações, [Configure um suplemento para usar um tempo de execução compartilhado](../excel/configure-your-add-in-to-use-a-shared-runtime.md).</span><span class="sxs-lookup"><span data-stu-id="fce36-116">For more information, [Configure an add-in to use a shared runtime](../excel/configure-your-add-in-to-use-a-shared-runtime.md).</span></span>

### <a name="link-the-mapping-file-to-the-manifest"></a><span data-ttu-id="fce36-117">Vincular o arquivo de mapeamento ao manifesto</span><span class="sxs-lookup"><span data-stu-id="fce36-117">Link the mapping file to the manifest</span></span>

<span data-ttu-id="fce36-118">Imediatamente *abaixo* (não dentro) do `<VersionOverrides>` elemento no manifesto, adicione um elemento [ExtendedOverrides](../reference/manifest/extendedoverrides.md) .</span><span class="sxs-lookup"><span data-stu-id="fce36-118">Immediately *below* (not inside) the `<VersionOverrides>` element in the manifest, add an [ExtendedOverrides](../reference/manifest/extendedoverrides.md) element.</span></span> <span data-ttu-id="fce36-119">Defina o `Url` atributo para a URL completa de um arquivo JSON em seu projeto que você irá criar em uma etapa posterior.</span><span class="sxs-lookup"><span data-stu-id="fce36-119">Set the `Url` attribute to the full URL of a JSON file in your project that you will create in a later step.</span></span>

```xml
    ...
    </VersionOverrides>  
    <ExtendedOverrides Url="https://contoso.com/addin/shortcuts.json"></ExtendedOverrides>
</OfficeApp>
```

## <a name="create-or-edit-the-shortcuts-json-file"></a><span data-ttu-id="fce36-120">Criar ou editar o arquivo JSON de atalhos</span><span class="sxs-lookup"><span data-stu-id="fce36-120">Create or edit the shortcuts JSON file</span></span>

<span data-ttu-id="fce36-121">Crie um arquivo JSON em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="fce36-121">Create a JSON file in your project.</span></span> <span data-ttu-id="fce36-122">Certifique-se de que o caminho do arquivo corresponde ao local especificado para o `Url` atributo do elemento [ExtendedOverrides](../reference/manifest/extendedoverrides.md) .</span><span class="sxs-lookup"><span data-stu-id="fce36-122">Be sure the path of the file matches the location you specified for the `Url` attribute of the [ExtendedOverrides](../reference/manifest/extendedoverrides.md) element.</span></span> <span data-ttu-id="fce36-123">Esse arquivo descreve seus atalhos de teclado e as ações que eles invocarão.</span><span class="sxs-lookup"><span data-stu-id="fce36-123">This file will describe your keyboard shortcuts, and the actions that they will invoke.</span></span>

1. <span data-ttu-id="fce36-124">Dentro do arquivo JSON, há duas matrizes.</span><span class="sxs-lookup"><span data-stu-id="fce36-124">Inside the JSON file, there are two arrays.</span></span> <span data-ttu-id="fce36-125">A matriz de ações conterá objetos que definem as ações a serem invocadas e a matriz de atalhos conterá objetos que mapeiam combinações de teclas para ações.</span><span class="sxs-lookup"><span data-stu-id="fce36-125">The actions array will contain objects that define the actions to be invoked and the shortcuts array will contain objects that map key combinations onto actions.</span></span> <span data-ttu-id="fce36-126">Veja um exemplo:</span><span class="sxs-lookup"><span data-stu-id="fce36-126">Here is an example:</span></span>

    ```json
    {
        "actions": [
            {
                "id": "SHOWTASKPANE",
                "type": "ExecuteFunction",
                "name": "Show task pane for add-in"
            },
            {
                "id": "HIDETASKPANE",
                "type": "ExecuteFunction",
                "name": "Hide task pane for add-in"
            }
        ],
        "shortcuts": [
            {
                "action": "SHOWTASKPANE",
                "key": {
                    "default": "CTRL+SHIFT+UP"
                }
            },
            {
                "action": "HIDETASKPANE",
                "key": {
                    "default": "CTRL+SHIFT+DOWN"
                }
            }
        ]
    }
    ```

    <span data-ttu-id="fce36-127">Para obter mais informações sobre os objetos JSON, consulte [construir os objetos Action](#constructing-the-action-objects) e [criar os objetos de atalho](#constructing-the-shortcut-objects).</span><span class="sxs-lookup"><span data-stu-id="fce36-127">For more information about the JSON objects, see [Constructing the action objects](#constructing-the-action-objects) and [Constructing the shortcut objects](#constructing-the-shortcut-objects).</span></span> <span data-ttu-id="fce36-128">O esquema completo para o JSON de atalhos está em [extended-manifest.schema.js](https://developer.microsoft.com/en-us/json-schemas/office-js/extended-manifest.schema.json).</span><span class="sxs-lookup"><span data-stu-id="fce36-128">The complete schema for the shortcuts JSON is at [extended-manifest.schema.json](https://developer.microsoft.com/en-us/json-schemas/office-js/extended-manifest.schema.json).</span></span>

    > [!NOTE]
    > <span data-ttu-id="fce36-129">Você pode usar o "controle" em vez de "CTRL" neste artigo.</span><span class="sxs-lookup"><span data-stu-id="fce36-129">You can use "CONTROL" in place of "CTRL" throughout this article.</span></span>

    <span data-ttu-id="fce36-130">Em uma etapa posterior, as ações serão mapeadas para as funções que você escrever.</span><span class="sxs-lookup"><span data-stu-id="fce36-130">In a later step, the actions will themselves be mapped to functions that you write.</span></span> <span data-ttu-id="fce36-131">Neste exemplo, posteriormente, você irá mapear SHOWTASKPANE para uma função que chama o `Office.addin.showAsTaskpane` método e HIDETASKPANE para uma função que chama o `Office.addin.hide` método.</span><span class="sxs-lookup"><span data-stu-id="fce36-131">In this example, you will later map SHOWTASKPANE to a function that calls the `Office.addin.showAsTaskpane` method and HIDETASKPANE to a function that calls the `Office.addin.hide` method.</span></span>

## <a name="create-a-mapping-of-actions-to-their-functions"></a><span data-ttu-id="fce36-132">Criar um mapeamento de ações para suas funções</span><span class="sxs-lookup"><span data-stu-id="fce36-132">Create a mapping of actions to their functions</span></span>

1. <span data-ttu-id="fce36-133">Em seu projeto, abra o arquivo JavaScript carregado pela página HTML no `<FunctionFile>` elemento.</span><span class="sxs-lookup"><span data-stu-id="fce36-133">In your project, open the JavaScript file loaded by your HTML page in the `<FunctionFile>` element.</span></span>
1. <span data-ttu-id="fce36-134">No arquivo JavaScript, use a API [Office. Actions. associa](/javascript/api/office/office.actions#associate) para mapear cada ação que você especificou no arquivo JSON para uma função JavaScript.</span><span class="sxs-lookup"><span data-stu-id="fce36-134">In the JavaScript file, use the [Office.actions.associate](/javascript/api/office/office.actions#associate) API to map each action that you specified in the JSON file to a JavaScript function.</span></span> <span data-ttu-id="fce36-135">Adicione o seguinte JavaScript ao arquivo.</span><span class="sxs-lookup"><span data-stu-id="fce36-135">Add the following JavaScript to the file.</span></span> <span data-ttu-id="fce36-136">Observe o seguinte sobre o código:</span><span class="sxs-lookup"><span data-stu-id="fce36-136">Note the following about the code:</span></span>

    - <span data-ttu-id="fce36-137">O primeiro parâmetro é uma das ações do arquivo JSON.</span><span class="sxs-lookup"><span data-stu-id="fce36-137">The first parameter is one of the actions from the JSON file.</span></span>
    - <span data-ttu-id="fce36-138">O segundo parâmetro é a função que é executada quando um usuário pressiona a combinação de teclas que é mapeada para a ação no arquivo JSON.</span><span class="sxs-lookup"><span data-stu-id="fce36-138">The second parameter is the function that runs when a user presses the key combination that is mapped to the action in the JSON file.</span></span>

    ```javascript
    Office.actions.associate('-- action ID goes here--', function () {

    });
    ```

1. <span data-ttu-id="fce36-139">Para continuar o exemplo, use `'SHOWTASKPANE'` como o primeiro parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fce36-139">To continue the example, use `'SHOWTASKPANE'` as the first parameter.</span></span>
1. <span data-ttu-id="fce36-140">Para o corpo da função, use o método [Office. AddIn. showTaskpane](/javascript/api/office/office.addin.md#showastaskpane--) para abrir o painel de tarefas do suplemento.</span><span class="sxs-lookup"><span data-stu-id="fce36-140">For the body of the function, use the [Office.addin.showTaskpane](/javascript/api/office/office.addin.md#showastaskpane--) method to open the add-in's task pane.</span></span> <span data-ttu-id="fce36-141">Quando você terminar, o código deverá ser semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="fce36-141">When you are done, the code should look like the following:</span></span>

    ```javascript
    Office.actions.associate('SHOWTASKPANE', function () {
        return Office.addin.showAsTaskpane()
            .then(function () {
                return;
            })
            .catch(function (error) {
                return error.code;
            });
    });
    ```

1. <span data-ttu-id="fce36-142">Adicione uma segunda chamada de `Office.actions.associate` função para mapear a `HIDETASKPANE` ação para uma função que chama [Office. AddIn. Hide](/javascript/api/office/office.addin.md#hide--).</span><span class="sxs-lookup"><span data-stu-id="fce36-142">Add a second call of `Office.actions.associate` function to map the `HIDETASKPANE` action to a function that calls [Office.addin.hide](/javascript/api/office/office.addin.md#hide--).</span></span> <span data-ttu-id="fce36-143">Este é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="fce36-143">The following is an example:</span></span>

    ```javascript
    Office.actions.associate('HIDETASKPANE', function () {
        return Office.addin.hide()
            .then(function () {
                return;
            })
            .catch(function (error) {
                return error.code;
            });
    });
    ```

<span data-ttu-id="fce36-144">Seguindo as etapas anteriores permite que o suplemento alterne a visibilidade do painel de tarefas pressionando **Ctrl + Shift + tecla de seta para cima** e **Ctrl + Shift + tecla de seta para baixo**.</span><span class="sxs-lookup"><span data-stu-id="fce36-144">Following the previous steps lets your add-in toggle the visibility of the task pane by pressing **Ctrl+Shift+Up arrow key** and **Ctrl+Shift+Down arrow key**.</span></span> <span data-ttu-id="fce36-145">Esse é o mesmo comportamento mostrado no suplemento de [exemplo de atalhos de teclado do Excel](https://github.com/OfficeDev/PnP-OfficeAddins/tree/master/Samples/excel-keyboard-shortcuts).</span><span class="sxs-lookup"><span data-stu-id="fce36-145">This is the same behavior as shown in the [sample excel keyboard shortcuts add-in](https://github.com/OfficeDev/PnP-OfficeAddins/tree/master/Samples/excel-keyboard-shortcuts).</span></span>

## <a name="details-and-restrictions"></a><span data-ttu-id="fce36-146">Detalhes e restrições</span><span class="sxs-lookup"><span data-stu-id="fce36-146">Details and restrictions</span></span>

### <a name="constructing-the-action-objects"></a><span data-ttu-id="fce36-147">Construir os objetos Action</span><span class="sxs-lookup"><span data-stu-id="fce36-147">Constructing the action objects</span></span>

<span data-ttu-id="fce36-148">Use as diretrizes a seguir ao especificar os objetos na `action` matriz de shortcuts.jsem:</span><span class="sxs-lookup"><span data-stu-id="fce36-148">Use the following guidelines when specifying the objects in the `action` array of the shortcuts.json:</span></span>

- <span data-ttu-id="fce36-149">Os nomes das propriedades `id` e `name` são obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="fce36-149">The property names `id` and `name` are mandatory.</span></span>
- <span data-ttu-id="fce36-150">A `id` propriedade é usada para identificar exclusivamente a ação a ser invocada usando um atalho de teclado.</span><span class="sxs-lookup"><span data-stu-id="fce36-150">The `id` property is used to uniquely identify the action to invoke using a keyboard shortcut.</span></span>
- <span data-ttu-id="fce36-151">A `name` propriedade deve ser uma cadeia de caracteres amigável que descreve a ação.</span><span class="sxs-lookup"><span data-stu-id="fce36-151">The `name` property must be a user friendly string describing the action.</span></span> <span data-ttu-id="fce36-152">Deve ser uma combinação dos caracteres A-Z, a-z, 0-9 e das marcas de Pontuação "-", "_" e "+".</span><span class="sxs-lookup"><span data-stu-id="fce36-152">It must be a combination of the characters A - Z, a - z, 0 - 9, and the punctuation marks "-", "_", and "+".</span></span>
- <span data-ttu-id="fce36-153">A propriedade do `type` é opcional.</span><span class="sxs-lookup"><span data-stu-id="fce36-153">The `type` property is optional.</span></span> <span data-ttu-id="fce36-154">No momento, só `ExecuteFunction` há suporte para Type.</span><span class="sxs-lookup"><span data-stu-id="fce36-154">Currently only `ExecuteFunction` type is supported.</span></span>

<span data-ttu-id="fce36-155">Este é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="fce36-155">The following is an example:</span></span>

```json
    "actions": [
        {
            "id": "SHOWTASKPANE",
            "type": "ExecuteFunction",
            "name": "Show task pane for add-in"
        },
        {
            "id": "HIDETASKPANE",
            "type": "ExecuteFunction",
            "name": "Hide task pane for add-in"
        }
    ]
```

<span data-ttu-id="fce36-156">O esquema completo para o JSON de atalhos está em [extended-manifest.schema.js](https://developer.microsoft.com/en-us/json-schemas/office-js/extended-manifest.schema.json).</span><span class="sxs-lookup"><span data-stu-id="fce36-156">The complete schema for the shortcuts JSON is at [extended-manifest.schema.json](https://developer.microsoft.com/en-us/json-schemas/office-js/extended-manifest.schema.json).</span></span>

### <a name="constructing-the-shortcut-objects"></a><span data-ttu-id="fce36-157">Construir os objetos de atalho</span><span class="sxs-lookup"><span data-stu-id="fce36-157">Constructing the shortcut objects</span></span>

<span data-ttu-id="fce36-158">Use as diretrizes a seguir ao especificar os objetos na `shortcuts` matriz de shortcuts.jsem:</span><span class="sxs-lookup"><span data-stu-id="fce36-158">Use the following guidelines when specifying the objects in the `shortcuts` array of the shortcuts.json:</span></span>

- <span data-ttu-id="fce36-159">Os nomes das propriedades `action` , `key` e `default` são obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="fce36-159">The property names `action`, `key`, and `default` are required.</span></span>
- <span data-ttu-id="fce36-160">O valor da `action` propriedade é uma cadeia de caracteres e deve corresponder a uma das `id` Propriedades no objeto Action.</span><span class="sxs-lookup"><span data-stu-id="fce36-160">The value of the `action` property is a string and must match one of the `id` properties in the action object.</span></span>
- <span data-ttu-id="fce36-161">A `default` propriedade pode ser qualquer combinação dos caracteres a-z, a-z, 0-9 e das marcas de Pontuação "-", "_" e "+".</span><span class="sxs-lookup"><span data-stu-id="fce36-161">The `default` property can be any combination of the characters A - Z, a -z, 0 - 9, and the punctuation marks "-", "_", and "+".</span></span> <span data-ttu-id="fce36-162">(Por convenção, letras minúsculas não são usadas nessas propriedades.)</span><span class="sxs-lookup"><span data-stu-id="fce36-162">(By convention, lower case letters are not used in these properties.)</span></span>
- <span data-ttu-id="fce36-163">A `default` propriedade deve conter o nome de pelo menos uma tecla modificadora (Alt, CTRL, Shift) e apenas uma tecla.</span><span class="sxs-lookup"><span data-stu-id="fce36-163">The `default` property must contain the name of at least one modifier key (ALT, CTRL, SHIFT) and only one other key.</span></span>
- <span data-ttu-id="fce36-164">Para Macs, também há suporte para a tecla modificador de comandos.</span><span class="sxs-lookup"><span data-stu-id="fce36-164">For Macs, we also support the COMMAND modifier key.</span></span>
- <span data-ttu-id="fce36-165">Para Macs, ALT é mapeada para a tecla de opção.</span><span class="sxs-lookup"><span data-stu-id="fce36-165">For Macs, ALT is mapped to the OPTION key.</span></span> <span data-ttu-id="fce36-166">Para o Windows, o comando é mapeado para a tecla CTRL.</span><span class="sxs-lookup"><span data-stu-id="fce36-166">For Windows, COMMAND is mapped to the CTRL key.</span></span>
- <span data-ttu-id="fce36-167">Quando dois caracteres são vinculados à mesma chave física em um teclado padrão, eles são sinônimos na `default` Propriedade; por exemplo, ALT + a e Alt + a são o mesmo atalho, portanto, são CTRL + e CTRL + \_ porque "-" e "_" são a mesma chave física.</span><span class="sxs-lookup"><span data-stu-id="fce36-167">When two characters are linked to the same physical key in a standard keyboard, then they are synonyms in the `default` property; for example, ALT+a and ALT+A are the same shortcut, so are CTRL+- and CTRL+\_ because "-" and "_" are the same physical key.</span></span>
- <span data-ttu-id="fce36-168">O caractere "+" indica que as teclas de ambos os lados são pressionadas simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="fce36-168">The "+" character indicates that the keys on either side of it are pressed simultaneously.</span></span>

<span data-ttu-id="fce36-169">Este é um exemplo:</span><span class="sxs-lookup"><span data-stu-id="fce36-169">The following is an example:</span></span>

```json
    "shortcuts": [
        {
            "action": "SHOWTASKPANE",
            "key": {
                "default": "CTRL+SHIFT+UP"
            }
        },
        {
            "action": "HIDETASKPANE",
            "key": {
                "default": "CTRL+SHIFT+DOWN"
            }
        }
    ]
```

<span data-ttu-id="fce36-170">O esquema completo para o JSON de atalhos está em [extended-manifest.schema.js](https://developer.microsoft.com/en-us/json-schemas/office-js/extended-manifest.schema.json).</span><span class="sxs-lookup"><span data-stu-id="fce36-170">The complete schema for the shortcuts JSON is at [extended-manifest.schema.json](https://developer.microsoft.com/en-us/json-schemas/office-js/extended-manifest.schema.json).</span></span>

> [!NOTE]
> <span data-ttu-id="fce36-171">As dicas de teclas, também conhecidas como atalhos de chave sequencial, como o atalho do Excel para escolher uma cor de preenchimento **ALT + H** , não são compatíveis com os suplementos do Office.</span><span class="sxs-lookup"><span data-stu-id="fce36-171">Keytips, also known as sequential key shortcuts, such as the Excel shortcut to choose a fill color **Alt+H, H** , are not supported in Office add-ins.</span></span>

### <a name="using-shortcuts-when-the-focus-is-in-the-task-pane"></a><span data-ttu-id="fce36-172">Usando atalhos quando o foco está no painel de tarefas</span><span class="sxs-lookup"><span data-stu-id="fce36-172">Using shortcuts when the focus is in the task pane</span></span>

<span data-ttu-id="fce36-173">Atualmente, os atalhos de teclado para um suplemento do Office só podem ser invocados quando o foco do usuário está na planilha.</span><span class="sxs-lookup"><span data-stu-id="fce36-173">Currently, the keyboard shortcuts for an Office add-in can only be invoked when the user's focus is in the worksheet.</span></span> <span data-ttu-id="fce36-174">Quando o foco do usuário está dentro da interface do usuário do Office (como o painel de tarefas), nenhum dos atalhos do suplemento é ignorado.</span><span class="sxs-lookup"><span data-stu-id="fce36-174">When the user's focus is inside the Office UI (such as the task pane), none of the add-in's shortcuts are ignored.</span></span> <span data-ttu-id="fce36-175">Como uma solução alternativa, o suplemento pode definir manipuladores de teclado que podem invocar determinadas ações quando o foco do usuário está dentro da interface do usuário do suplemento.</span><span class="sxs-lookup"><span data-stu-id="fce36-175">As a workaround, the add-in can define keyboard handlers that can invoke certain actions when the user's focus is inside of the add-in UI.</span></span>

## <a name="using-key-combinations-that-are-already-used-by-office-or-another-add-in"></a><span data-ttu-id="fce36-176">Usando combinações de teclas já utilizadas pelo Office ou outro suplemento</span><span class="sxs-lookup"><span data-stu-id="fce36-176">Using key combinations that are already used by Office or another add-in</span></span>

<span data-ttu-id="fce36-177">Durante o período de visualização, não há nenhum sistema para determinar o que acontece quando um usuário pressiona uma combinação de teclas que é registrada por um suplemento e também pelo Office ou por outro suplemento.</span><span class="sxs-lookup"><span data-stu-id="fce36-177">During the preview period, there is no system for determining what happens when a user presses a key combination that is registered by an add-in and also by Office or by another add-in.</span></span> <span data-ttu-id="fce36-178">O comportamento é indefinido.</span><span class="sxs-lookup"><span data-stu-id="fce36-178">Behavior is undefined.</span></span>

<span data-ttu-id="fce36-179">No momento, não há solução alternativa quando dois ou mais suplementos registraram o mesmo atalho de teclado, mas você pode minimizar conflitos com o Excel com essas boas práticas:</span><span class="sxs-lookup"><span data-stu-id="fce36-179">Currently, there is no workaround when two or more add-ins have registered the same keyboard shortcut, but you can minimize conflicts with Excel with these good practices:</span></span>

- <span data-ttu-id="fce36-180">Use apenas atalhos de teclado com o seguinte padrão em seu suplemento: \* *Ctrl + Shift + Alt +* x \* \* \*, onde *x* é outra tecla.</span><span class="sxs-lookup"><span data-stu-id="fce36-180">Use only keyboard shortcuts with the following pattern in your add-in: \* *Ctrl+Shift+Alt+* x\*\*\*, where *x* is some other key.</span></span>
- <span data-ttu-id="fce36-181">Se você precisar de mais atalhos de teclado, verifique a [lista de atalhos de teclado do Excel](https://support.microsoft.com/office/keyboard-shortcuts-in-excel-1798d9d5-842a-42b8-9c99-9b7213f0040f)e evite usar qualquer um deles no suplemento.</span><span class="sxs-lookup"><span data-stu-id="fce36-181">If you need more keyboard shortcuts, check the [list of Excel keyboard shortcuts](https://support.microsoft.com/office/keyboard-shortcuts-in-excel-1798d9d5-842a-42b8-9c99-9b7213f0040f), and avoid using any of them in your add-in.</span></span>

## <a name="browser-shortcuts-that-cannot-be-overridden"></a><span data-ttu-id="fce36-182">Atalhos do navegador que não podem ser substituídos</span><span class="sxs-lookup"><span data-stu-id="fce36-182">Browser shortcuts that cannot be overridden</span></span>

<span data-ttu-id="fce36-183">Você não pode usar nenhuma das combinações de teclado a seguir.</span><span class="sxs-lookup"><span data-stu-id="fce36-183">You cannot use any of the following keyboard combinations.</span></span> <span data-ttu-id="fce36-184">Eles são usados pelos navegadores e não podem ser substituídos.</span><span class="sxs-lookup"><span data-stu-id="fce36-184">They are used by browsers and cannot be overridden.</span></span> <span data-ttu-id="fce36-185">Esta lista é um trabalho em andamento.</span><span class="sxs-lookup"><span data-stu-id="fce36-185">This list is a work in progress.</span></span> <span data-ttu-id="fce36-186">Se você descobrir outras combinações que não podem ser substituídas, informe-nos usando a ferramenta de comentários na parte inferior desta página.</span><span class="sxs-lookup"><span data-stu-id="fce36-186">If you discover other combinations that cannot be overridden, please let us know by using the feedback tool at the bottom of this page.</span></span>

- <span data-ttu-id="fce36-187">Ctrl + N</span><span class="sxs-lookup"><span data-stu-id="fce36-187">Ctrl+N</span></span>
- <span data-ttu-id="fce36-188">Ctrl + Shift + N</span><span class="sxs-lookup"><span data-stu-id="fce36-188">Ctrl+Shift+N</span></span>
- <span data-ttu-id="fce36-189">CTRL + T</span><span class="sxs-lookup"><span data-stu-id="fce36-189">Ctrl+T</span></span>
- <span data-ttu-id="fce36-190">CTRL + SHIFT + T</span><span class="sxs-lookup"><span data-stu-id="fce36-190">Ctrl+Shift+T</span></span>
- <span data-ttu-id="fce36-191">CTRL + W</span><span class="sxs-lookup"><span data-stu-id="fce36-191">Ctrl+W</span></span>
- <span data-ttu-id="fce36-192">CTRL + PgUp/PgDn</span><span class="sxs-lookup"><span data-stu-id="fce36-192">Ctrl+PgUp/PgDn</span></span>

## <a name="next-steps"></a><span data-ttu-id="fce36-193">Próximas Etapas</span><span class="sxs-lookup"><span data-stu-id="fce36-193">Next Steps</span></span>

- <span data-ttu-id="fce36-194">Confira o suplemento de exemplo [Excel-teclado-atalhos](https://github.com/OfficeDev/PnP-OfficeAddins/tree/master/Samples/excel-keyboard-shortcuts).</span><span class="sxs-lookup"><span data-stu-id="fce36-194">See the sample add-in [excel-keyboard-shortcuts](https://github.com/OfficeDev/PnP-OfficeAddins/tree/master/Samples/excel-keyboard-shortcuts).</span></span>