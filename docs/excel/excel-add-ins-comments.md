---
title: Trabalhar com comentários usando a API JavaScript do Excel
description: ''
ms.date: 10/22/2019
localization_priority: Normal
ms.openlocfilehash: d79f99d1922def58fe2c8887d01ec5a2b173220a
ms.sourcegitcommit: 5ba325cc88183a3f230cd89d615fd49c695addcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "37681911"
---
# <a name="work-with-comments-using-the-excel-javascript-api"></a><span data-ttu-id="1f648-102">Trabalhar com comentários usando a API JavaScript do Excel</span><span class="sxs-lookup"><span data-stu-id="1f648-102">Work with comments using the Excel JavaScript API</span></span>

<span data-ttu-id="1f648-103">Este artigo descreve como adicionar, ler, modificar e remover comentários em uma pasta de trabalho com a API JavaScript do Excel.</span><span class="sxs-lookup"><span data-stu-id="1f648-103">This article describes how to add, read, modify, and remove comments in a workbook with the Excel JavaScript API.</span></span> <span data-ttu-id="1f648-104">Você pode saber mais sobre o recurso comentário do artigo [inserir comentários e anotações no Excel](https://support.office.com/article/insert-comments-and-notes-in-excel-bdcc9f5d-38e2-45b4-9a92-0b2b5c7bf6f8) .</span><span class="sxs-lookup"><span data-stu-id="1f648-104">You can learn more about the comment feature from the [Insert comments and notes in Excel](https://support.office.com/article/insert-comments-and-notes-in-excel-bdcc9f5d-38e2-45b4-9a92-0b2b5c7bf6f8) article.</span></span>

<span data-ttu-id="1f648-105">Na API JavaScript do Excel, um comentário é a anotação inicial e a discussão encadeada conectada.</span><span class="sxs-lookup"><span data-stu-id="1f648-105">In the Excel JavaScript API, a comment is both the initial note and the connected threaded discussion.</span></span> <span data-ttu-id="1f648-106">Ele está vinculado a uma célula individual.</span><span class="sxs-lookup"><span data-stu-id="1f648-106">It is tied to an individual cell.</span></span> <span data-ttu-id="1f648-107">Qualquer pessoa que exiba a pasta de trabalho com permissões suficientes pode responder a um comentário.</span><span class="sxs-lookup"><span data-stu-id="1f648-107">Anyone viewing the workbook with sufficient permissions can reply to a comment.</span></span> <span data-ttu-id="1f648-108">Um objeto [comment](/javascript/api/excel/excel.comment) armazena as respostas como objetos [CommentReply](/javascript/api/excel/excel.commentreply) .</span><span class="sxs-lookup"><span data-stu-id="1f648-108">A [Comment](/javascript/api/excel/excel.comment) object stores those replies as [CommentReply](/javascript/api/excel/excel.commentreply) objects.</span></span> <span data-ttu-id="1f648-109">Você deve considerar um comentário para ser um thread e que um thread deve ter uma entrada especial como o ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="1f648-109">You should consider a comment to be a thread and that a thread must have a special entry as the starting point.</span></span>

![Um comentário do Excel, rotulado "comentário" com duas respostas, rotuladas "comentário. respostas [0]" e "comentário. respostas [1].](../images/excel-comments.png)

<span data-ttu-id="1f648-111">Os `Workbook.comments` comentários em uma pasta de trabalho são rastreados pela propriedade.</span><span class="sxs-lookup"><span data-stu-id="1f648-111">Comments within a workbook are tracked by the `Workbook.comments` property.</span></span> <span data-ttu-id="1f648-112">Isso inclui comentários criados por usuários e comentários criados por seu suplemento.</span><span class="sxs-lookup"><span data-stu-id="1f648-112">This includes comments created by users and also comments created by your add-in.</span></span> <span data-ttu-id="1f648-113">A propriedade `Workbook.comments` é um objeto [CommentCollection](/javascript/api/excel/excel.commentcollection) que contém um conjunto de objetos [Comentário](/javascript/api/excel/excel.comment).</span><span class="sxs-lookup"><span data-stu-id="1f648-113">The `Workbook.comments` property is a [CommentCollection](/javascript/api/excel/excel.commentcollection) object that contains a collection of [Comment](/javascript/api/excel/excel.comment) objects.</span></span> <span data-ttu-id="1f648-114">Os comentários também podem ser acessados no nível da [planilha](/javascript/api/excel/excel.worksheet) .</span><span class="sxs-lookup"><span data-stu-id="1f648-114">Comments are also accessible at the [Worksheet](/javascript/api/excel/excel.worksheet) level.</span></span> <span data-ttu-id="1f648-115">Os exemplos neste artigo trabalham com comentários no nível da pasta de trabalho, mas eles podem ser facilmente modificados para `Worksheet.comments` usar a propriedade.</span><span class="sxs-lookup"><span data-stu-id="1f648-115">The samples in this article work with comments at the workbook level, but they can be easily modified to use the `Worksheet.comments` property.</span></span>

## <a name="add-comments"></a><span data-ttu-id="1f648-116">Adicionar comentários</span><span class="sxs-lookup"><span data-stu-id="1f648-116">Add comments</span></span>

<span data-ttu-id="1f648-117">Use o `CommentCollection.add` método para adicionar comentários a uma pasta de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1f648-117">Use the `CommentCollection.add` method to add comments to a workbook.</span></span> <span data-ttu-id="1f648-118">Este método utiliza até três parâmetros:</span><span class="sxs-lookup"><span data-stu-id="1f648-118">This method takes up to three parameters:</span></span>

- <span data-ttu-id="1f648-119">`cellAddress`: A célula onde o comentário é adicionado.</span><span class="sxs-lookup"><span data-stu-id="1f648-119">`cellAddress`: The cell where the comment is added.</span></span> <span data-ttu-id="1f648-120">Pode ser um objeto String ou [Range](/javascript/api/excel/excel.range) .</span><span class="sxs-lookup"><span data-stu-id="1f648-120">This can either be a string or [Range](/javascript/api/excel/excel.range) object.</span></span> <span data-ttu-id="1f648-121">O intervalo deve ser uma única célula.</span><span class="sxs-lookup"><span data-stu-id="1f648-121">The range must be a single cell.</span></span>
- <span data-ttu-id="1f648-122">`content`: O conteúdo do comentário.</span><span class="sxs-lookup"><span data-stu-id="1f648-122">`content`: The comment's content.</span></span> <span data-ttu-id="1f648-123">Use uma cadeia de caracteres para comentários de texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="1f648-123">Use a string for plain text comments.</span></span> <span data-ttu-id="1f648-124">Use um objeto [CommentRichContent](/javascript/api/excel/excel.commentrichcontent) para comentários com [menção](#mentions-preview).</span><span class="sxs-lookup"><span data-stu-id="1f648-124">Use a [CommentRichContent](/javascript/api/excel/excel.commentrichcontent) object for comments with [mentions](#mentions-preview).</span></span>
- <span data-ttu-id="1f648-125">`contentType`: Um enum [ContentType](/javascript/api/excel/excel.contenttype) especificando o tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="1f648-125">`contentType`: A [ContentType](/javascript/api/excel/excel.contenttype) enum specifying type of content.</span></span> <span data-ttu-id="1f648-126">O valor padrão é `ContentType.plain`.</span><span class="sxs-lookup"><span data-stu-id="1f648-126">The default value is `ContentType.plain`.</span></span>

<span data-ttu-id="1f648-127">O exemplo a seguir adiciona um comentário à célula **A2**.</span><span class="sxs-lookup"><span data-stu-id="1f648-127">The following code sample adds a comment to cell **A2**.</span></span>

```js
Excel.run(function (context) {
    // Add a comment to A2 on the "MyWorksheet" worksheet.
    var comments = context.workbook.comments;

    // Note that an InvalidArgument error will be thrown if multiple cells passed to `Comment.add`.
    comments.add("MyWorksheet!A2", "TODO: add data.");
    return context.sync();
});
```

> [!NOTE]
> <span data-ttu-id="1f648-128">Os comentários adicionados por um suplemento são atribuídos ao usuário atual desse suplemento.</span><span class="sxs-lookup"><span data-stu-id="1f648-128">Comments added by an add-in are attributed to the current user of that add-in.</span></span>

### <a name="add-comment-replies"></a><span data-ttu-id="1f648-129">Adicionar respostas de comentário</span><span class="sxs-lookup"><span data-stu-id="1f648-129">Add comment replies</span></span>

<span data-ttu-id="1f648-130">Um `Comment` objeto é um thread de comentário que contém zero ou mais respostas.</span><span class="sxs-lookup"><span data-stu-id="1f648-130">A `Comment` object is a comment thread that contains zero or more replies.</span></span> <span data-ttu-id="1f648-131">os objetos `Comment` têm uma propriedade `replies`, que é [CommentReplyCollection](/javascript/api/excel/excel.commentreplycollection) que contém objetos [CommentReply](/javascript/api/excel/excel.commentreply).</span><span class="sxs-lookup"><span data-stu-id="1f648-131">`Comment` objects have a `replies` property, which is a [CommentReplyCollection](/javascript/api/excel/excel.commentreplycollection) that contains [CommentReply](/javascript/api/excel/excel.commentreply) objects.</span></span> <span data-ttu-id="1f648-132">Para adicionar uma resposta a um comentário, use o método `CommentReplyCollection.add`, passando o texto da resposta.</span><span class="sxs-lookup"><span data-stu-id="1f648-132">To add a reply to a comment, use the `CommentReplyCollection.add` method, passing in the text of the reply.</span></span> <span data-ttu-id="1f648-133">As respostas são exibidas na ordem em que são adicionadas.</span><span class="sxs-lookup"><span data-stu-id="1f648-133">Replies are displayed in the order they are added.</span></span> <span data-ttu-id="1f648-134">Eles também são atribuídos ao usuário atual do suplemento.</span><span class="sxs-lookup"><span data-stu-id="1f648-134">They are also attributed to the current user of the add-in.</span></span>

<span data-ttu-id="1f648-135">O exemplo a seguir adiciona uma resposta ao primeiro comentário da pasta de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1f648-135">The following code sample adds a reply to the first comment in the workbook.</span></span>

```js
Excel.run(function (context) {
    // Get the first comment added to the workbook.
    var comment = context.workbook.comments.getItemAt(0);
    comment.replies.add("Thanks for the reminder!");
    return context.sync();
});
```

## <a name="edit-comments"></a><span data-ttu-id="1f648-136">Editar comentários</span><span class="sxs-lookup"><span data-stu-id="1f648-136">Edit comments</span></span>

<span data-ttu-id="1f648-137">Para editar um comentário ou uma resposta de comentário, defina uma propriedade`Comment.content` e uma propriedade`CommentReply.content`.</span><span class="sxs-lookup"><span data-stu-id="1f648-137">To edit a comment or comment reply, set its `Comment.content` property or `CommentReply.content` property.</span></span>

```js
Excel.run(function (context) {
    // Edit the first comment in the workbook.
    var comment = context.workbook.comments.getItemAt(0);
    comment.content = "PLEASE add headers here.";
    return context.sync();
});
```

### <a name="edit-comment-replies"></a><span data-ttu-id="1f648-138">Editar respostas de comentário</span><span class="sxs-lookup"><span data-stu-id="1f648-138">Edit comment replies</span></span>

<span data-ttu-id="1f648-139">Para editar uma resposta de comentário, defina `CommentReply.content` sua propriedade.</span><span class="sxs-lookup"><span data-stu-id="1f648-139">To edit a comment reply, set its `CommentReply.content` property.</span></span>

```js
Excel.run(function (context) {
    // Edit the first comment reply on the first comment in the workbook.
    var comment = context.workbook.comments.getItemAt(0);
    var reply = comment.replies.getItemAt(0);
    reply.content = "Never mind";
    return context.sync();
});
```

## <a name="delete-comments"></a><span data-ttu-id="1f648-140">Excluir comentários</span><span class="sxs-lookup"><span data-stu-id="1f648-140">Delete comments</span></span>

<span data-ttu-id="1f648-141">Para excluir um comentário, use `Comment.delete` o método.</span><span class="sxs-lookup"><span data-stu-id="1f648-141">To delete a comment use the `Comment.delete` method.</span></span> <span data-ttu-id="1f648-142">A exclusão de um comentário também exclui as respostas associadas a esse comentário.</span><span class="sxs-lookup"><span data-stu-id="1f648-142">Deleting a comment also deletes the replies associated with that comment.</span></span>

```js
Excel.run(function (context) {
    // Delete the comment thread at A2 on the "MyWorksheet" worksheet.
    context.workbook.comments.getItemByCell("MyWorksheet!A2").delete();
    return context.sync();
});
```

### <a name="delete-comment-replies"></a><span data-ttu-id="1f648-143">Excluir respostas de comentário</span><span class="sxs-lookup"><span data-stu-id="1f648-143">Delete comment replies</span></span>

<span data-ttu-id="1f648-144">Para excluir uma resposta de comentário, use `CommentReply.delete` o método.</span><span class="sxs-lookup"><span data-stu-id="1f648-144">To delete a comment reply, use the `CommentReply.delete` method.</span></span>

```js
Excel.run(function (context) {
    // Delete the first comment reply from this worksheet's first comment.
    var comment = context.workbook.comments.getItemAt(0);
    comment.replies.getItemAt(0).delete();
    return context.sync();
});
```

## <a name="resolve-comment-threads"></a><span data-ttu-id="1f648-145">Resolver threads de comentário</span><span class="sxs-lookup"><span data-stu-id="1f648-145">Resolve comment threads</span></span>

<span data-ttu-id="1f648-146">Um thread de comentário tem um valor booliano `resolved`configurável, para indicar se ele foi resolvido.</span><span class="sxs-lookup"><span data-stu-id="1f648-146">A comment thread has a configurable boolean value, `resolved`, to indicate if it is resolved.</span></span> <span data-ttu-id="1f648-147">Um valor de `true` significa que o thread de comentários é resolvido.</span><span class="sxs-lookup"><span data-stu-id="1f648-147">A value of `true` means the comment thread is resolved.</span></span> <span data-ttu-id="1f648-148">Um valor de `false` significa que o thread de comentários é novo ou reaberto.</span><span class="sxs-lookup"><span data-stu-id="1f648-148">A value of `false` means the comment thread is either new or reopened.</span></span>

```js
Excel.run(function (context) {
    // Resolve the first comment thread in the workbook.
    context.workbook.comments.getItemAt(0).resolved = true;
    return context.sync();
});
```

<span data-ttu-id="1f648-149">Respostas de comentário têm uma `resolved` propriedade ReadOnly.</span><span class="sxs-lookup"><span data-stu-id="1f648-149">Comment replies have a readonly `resolved` property.</span></span> <span data-ttu-id="1f648-150">Seu valor é sempre igual ao do restante do thread.</span><span class="sxs-lookup"><span data-stu-id="1f648-150">Its value is always equal to that of the rest of the thread.</span></span>

## <a name="comment-metadata"></a><span data-ttu-id="1f648-151">Metadados de comentários</span><span class="sxs-lookup"><span data-stu-id="1f648-151">Comment metadata</span></span>

<span data-ttu-id="1f648-152">Cada comentário contém metadados sobre a criação, como o autor e a data de criação.</span><span class="sxs-lookup"><span data-stu-id="1f648-152">Each comment contains metadata about its creation, such as the author and creation date.</span></span> <span data-ttu-id="1f648-153">Os comentários criados por seu suplemento são considerados criados pelo usuário atual.</span><span class="sxs-lookup"><span data-stu-id="1f648-153">Comments created by your add-in are considered to be authored by the current user.</span></span>

<span data-ttu-id="1f648-154">O exemplo a seguir mostra como exibir o email do autor, o nome do autor e a data de criação de um comentário em **A2**.</span><span class="sxs-lookup"><span data-stu-id="1f648-154">The following sample shows how to display the author's email, author's name, and creation date of a comment at **A2**.</span></span>

```js
Excel.run(function (context) {
    // Get the comment at cell A2 in the "MyWorksheet" worksheet.
    var comment = context.workbook.comments.getItemByCell("MyWorksheet!A2");

    // Load and print the following values.
    comment.load(["authorEmail", "authorName", "creationDate"]);
    return context.sync().then(function () {
        console.log(`${comment.creationDate.toDateString()}: ${comment.authorName} (${comment.authorEmail})`);
    });
});
```

### <a name="comment-reply-metadata"></a><span data-ttu-id="1f648-155">Metadados de resposta de comentário</span><span class="sxs-lookup"><span data-stu-id="1f648-155">Comment reply metadata</span></span>

<span data-ttu-id="1f648-156">Respostas de comentários armazenam os mesmos tipos de metadados que o comentário inicial.</span><span class="sxs-lookup"><span data-stu-id="1f648-156">Comment replies store the same types of metadata as the initial comment.</span></span>

<span data-ttu-id="1f648-157">O exemplo a seguir mostra como exibir o email do autor, o nome do autor e a data de criação da resposta de comentário mais recente em **a2**.</span><span class="sxs-lookup"><span data-stu-id="1f648-157">The following sample shows how to display the author's email, author's name, and creation date of the latest comment reply at **A2**.</span></span>

```js
Excel.run(function (context) {
    // Get the comment at cell A2 in the "MyWorksheet" worksheet.
    var comment = context.workbook.comments.getItemByCell("MyWorksheet!A2");
    var replyCount = comment.replies.getCount();
    // Sync to get the current number of comment replies.
    return context.sync().then(function () {
        // Get the last comment reply in the comment thread.
        var reply = comment.replies.getItemAt(replyCount.value - 1);
        reply.load(["authorEmail", "authorName", "creationDate"]);
        // Sync to load the reply metadata to print.
        return context.sync().then(function () {
            console.log(`Latest reply: ${reply.creationDate.toDateString()}: ${reply.authorName} ${reply.authorEmail})`);
            return context.sync();
        });
    });
});
```

## <a name="mentions-preview"></a><span data-ttu-id="1f648-158">Menciona (versão prévia)</span><span class="sxs-lookup"><span data-stu-id="1f648-158">Mentions (preview)</span></span>

> [!NOTE]
> <span data-ttu-id="1f648-159">O comentário mencionando APIs estão atualmente disponíveis somente na visualização pública.</span><span class="sxs-lookup"><span data-stu-id="1f648-159">The comment mention APIs are currently available only in public preview.</span></span> [!INCLUDE [Information about using preview APIs](../includes/using-excel-preview-apis.md)]

> [!IMPORTANT]
> <span data-ttu-id="1f648-160">As mencionadas de comentários atualmente só têm suporte no Excel na Web.</span><span class="sxs-lookup"><span data-stu-id="1f648-160">Comment mentions are currently only supported for Excel on the web.</span></span>

<span data-ttu-id="1f648-161">As [mencionas](https://support.office.com/article/use-mention-in-comments-to-tag-someone-for-feedback-644bf689-31a0-4977-a4fb-afe01820c1fd) são usadas para marcar colegas em um comentário.</span><span class="sxs-lookup"><span data-stu-id="1f648-161">[Mentions](https://support.office.com/article/use-mention-in-comments-to-tag-someone-for-feedback-644bf689-31a0-4977-a4fb-afe01820c1fd) are used to tag colleagues in a comment.</span></span> <span data-ttu-id="1f648-162">Isso envia notificações com o conteúdo do comentário.</span><span class="sxs-lookup"><span data-stu-id="1f648-162">This sends them notifications with your comment's content.</span></span> <span data-ttu-id="1f648-163">O suplemento pode criar essas menção em seu nome.</span><span class="sxs-lookup"><span data-stu-id="1f648-163">Your add-in can create these mentions on your behalf.</span></span>

<span data-ttu-id="1f648-164">Comentários com menção precisam ser criados com objetos [CommentRichContent](/javascript/api/excel/excel.commentrichcontent) .</span><span class="sxs-lookup"><span data-stu-id="1f648-164">Comments with mentions need to be created with [CommentRichContent](/javascript/api/excel/excel.commentrichcontent) objects.</span></span> <span data-ttu-id="1f648-165">Call `CommentCollection.add` com um `CommentRichContent` contendo um ou mais mencionas e especifique `ContentType.mention` como o `contentType` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1f648-165">Call `CommentCollection.add` with a `CommentRichContent` containing one or more mentions and specify `ContentType.mention` as the `contentType` parameter.</span></span> <span data-ttu-id="1f648-166">A `content` cadeia de caracteres também precisa ser formatada para inserir o menção no texto.</span><span class="sxs-lookup"><span data-stu-id="1f648-166">The `content` string also needs to be formatted to insert the mention into the text.</span></span> <span data-ttu-id="1f648-167">O formato de um menção é: `<at id="{replyIndex}">{mentionName}</at>`.</span><span class="sxs-lookup"><span data-stu-id="1f648-167">The format for a mention is: `<at id="{replyIndex}">{mentionName}</at>`.</span></span>

> <span data-ttu-id="1f648-168">Observação Atualmente, apenas o nome exato de menção pode ser usado como o texto do link de menção.</span><span class="sxs-lookup"><span data-stu-id="1f648-168">[NOTE] Currently, only the mention's exact name can be used as the text of the mention link.</span></span> <span data-ttu-id="1f648-169">O suporte para versões reduzidas de um nome será adicionado posteriormente.</span><span class="sxs-lookup"><span data-stu-id="1f648-169">Support for shortened versions of a name will be added later.</span></span>

<span data-ttu-id="1f648-170">O exemplo a seguir mostra um comentário com uma única menção.</span><span class="sxs-lookup"><span data-stu-id="1f648-170">The following example shows a comment with a single mention.</span></span>

```js
Excel.run(function (context) {
    // Add an "@mention" for "Kate Kristensen" to cell A1 in the "MyWorksheet" worksheet.
    var mention = {
        email: "kakri@contoso.com",
        id: 0,
        name: "Kate Kristensen"
    };

    // This will tag the mention's name using the '@' syntax.
    // They will be notified via email.
    var commentBody = {
        mentions: [mention],
        richContent: '<at id="0">' + mention.name + "</at> -  Can you take a look?"
    };

    // Note that an InvalidArgument error will be thrown if multiple cells passed to `comment.add`.
    context.workbook.comments.add("MyWorksheet!A1", commentBody, Excel.ContentType.mention);
    return context.sync();
});
```

## <a name="see-also"></a><span data-ttu-id="1f648-171">Confira também</span><span class="sxs-lookup"><span data-stu-id="1f648-171">See also</span></span>

- [<span data-ttu-id="1f648-172">Conceitos fundamentais de programação com a API JavaScript do Excel</span><span class="sxs-lookup"><span data-stu-id="1f648-172">Fundamental programming concepts with the Excel JavaScript API</span></span>](excel-add-ins-core-concepts.md)
- [<span data-ttu-id="1f648-173">Trabalhar com pastas de trabalho usando a API JavaScript do Excel</span><span class="sxs-lookup"><span data-stu-id="1f648-173">Work with workbooks using the Excel JavaScript API</span></span>](excel-add-ins-workbooks.md)
- [<span data-ttu-id="1f648-174">Inserir comentários e anotações no Excel</span><span class="sxs-lookup"><span data-stu-id="1f648-174">Insert comments and notes in Excel</span></span>](https://support.office.com/article/insert-comments-and-notes-in-excel-bdcc9f5d-38e2-45b4-9a92-0b2b5c7bf6f8)