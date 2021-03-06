---
title: Trabalhar com comentários usando a API JavaScript do Excel
description: Informações sobre como usar as APIs para adicionar, remover e editar comentários e encadeamentos de comentários.
ms.date: 10/09/2020
localization_priority: Normal
ms.openlocfilehash: 00f7dd22fb2148902152197521098482071e5284
ms.sourcegitcommit: 4e7c74ad67ea8bf6b47d65b2fde54a967090f65b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2020
ms.locfileid: "48626418"
---
# <a name="work-with-comments-using-the-excel-javascript-api"></a>Trabalhar com comentários usando a API JavaScript do Excel

Este artigo descreve como adicionar, ler, modificar e remover comentários em uma pasta de trabalho com a API JavaScript do Excel. Você pode saber mais sobre o recurso comentário do artigo [inserir comentários e anotações no Excel](https://support.office.com/article/insert-comments-and-notes-in-excel-bdcc9f5d-38e2-45b4-9a92-0b2b5c7bf6f8) .

Na API JavaScript do Excel, um comentário inclui o único comentário inicial e a discussão encadeada conectada. Ele está vinculado a uma célula individual. Qualquer pessoa que exiba a pasta de trabalho com permissões suficientes pode responder a um comentário. Um objeto [comment](/javascript/api/excel/excel.comment) armazena as respostas como objetos [CommentReply](/javascript/api/excel/excel.commentreply) . Você deve considerar um comentário para ser um thread e que um thread deve ter uma entrada especial como o ponto de partida.

![Um comentário do Excel, rotulado "comentário" com duas respostas, rotuladas "comentário. respostas [0]" e "comentário. respostas [1].](../images/excel-comments.png)

Os comentários em uma pasta de trabalho são rastreados pela `Workbook.comments` propriedade. Isso inclui comentários criados por usuários e comentários criados por seu suplemento. A propriedade `Workbook.comments` é um objeto [CommentCollection](/javascript/api/excel/excel.commentcollection) que contém um conjunto de objetos [Comentário](/javascript/api/excel/excel.comment). Os comentários também podem ser acessados no nível da [planilha](/javascript/api/excel/excel.worksheet) . Os exemplos neste artigo trabalham com comentários no nível da pasta de trabalho, mas eles podem ser facilmente modificados para usar a `Worksheet.comments` propriedade.

## <a name="add-comments"></a>Adicionar comentários

Use o `CommentCollection.add` método para adicionar comentários a uma pasta de trabalho. Este método utiliza até três parâmetros:

- `cellAddress`: A célula onde o comentário é adicionado. Pode ser um objeto String ou [Range](/javascript/api/excel/excel.range) . O intervalo deve ser uma única célula.
- `content`: O conteúdo do comentário. Use uma cadeia de caracteres para comentários de texto sem formatação. Use um objeto [CommentRichContent](/javascript/api/excel/excel.commentrichcontent) para comentários com [menção](#mentions).
- `contentType`: Um enum [ContentType](/javascript/api/excel/excel.contenttype) especificando o tipo de conteúdo. O valor padrão é `ContentType.plain`.

O exemplo a seguir adiciona um comentário à célula **A2**.

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
> Os comentários adicionados por um suplemento são atribuídos ao usuário atual desse suplemento.

### <a name="add-comment-replies"></a>Adicionar respostas de comentário

Um `Comment` objeto é um thread de comentário que contém zero ou mais respostas. os objetos `Comment` têm uma propriedade `replies`, que é [CommentReplyCollection](/javascript/api/excel/excel.commentreplycollection) que contém objetos [CommentReply](/javascript/api/excel/excel.commentreply). Para adicionar uma resposta a um comentário, use o método `CommentReplyCollection.add`, passando o texto da resposta. As respostas são exibidas na ordem em que são adicionadas. Eles também são atribuídos ao usuário atual do suplemento.

O exemplo a seguir adiciona uma resposta ao primeiro comentário da pasta de trabalho.

```js
Excel.run(function (context) {
    // Get the first comment added to the workbook.
    var comment = context.workbook.comments.getItemAt(0);
    comment.replies.add("Thanks for the reminder!");
    return context.sync();
});
```

## <a name="edit-comments"></a>Editar comentários

Para editar um comentário ou uma resposta de comentário, defina uma propriedade`Comment.content` e uma propriedade`CommentReply.content`.

```js
Excel.run(function (context) {
    // Edit the first comment in the workbook.
    var comment = context.workbook.comments.getItemAt(0);
    comment.content = "PLEASE add headers here.";
    return context.sync();
});
```

### <a name="edit-comment-replies"></a>Editar respostas de comentário

Para editar uma resposta de comentário, defina sua `CommentReply.content` propriedade.

```js
Excel.run(function (context) {
    // Edit the first comment reply on the first comment in the workbook.
    var comment = context.workbook.comments.getItemAt(0);
    var reply = comment.replies.getItemAt(0);
    reply.content = "Never mind";
    return context.sync();
});
```

## <a name="delete-comments"></a>Excluir comentários

Para excluir um comentário, use o `Comment.delete` método. A exclusão de um comentário também exclui as respostas associadas a esse comentário.

```js
Excel.run(function (context) {
    // Delete the comment thread at A2 on the "MyWorksheet" worksheet.
    context.workbook.comments.getItemByCell("MyWorksheet!A2").delete();
    return context.sync();
});
```

### <a name="delete-comment-replies"></a>Excluir respostas de comentário

Para excluir uma resposta de comentário, use o `CommentReply.delete` método.

```js
Excel.run(function (context) {
    // Delete the first comment reply from this worksheet's first comment.
    var comment = context.workbook.comments.getItemAt(0);
    comment.replies.getItemAt(0).delete();
    return context.sync();
});
```

## <a name="resolve-comment-threads"></a>Resolver threads de comentário

Um thread de comentário tem um valor booliano configurável, `resolved` para indicar se ele foi resolvido. Um valor de `true` significa que o thread de comentários é resolvido. Um valor de `false` significa que o thread de comentários é novo ou reaberto.

```js
Excel.run(function (context) {
    // Resolve the first comment thread in the workbook.
    context.workbook.comments.getItemAt(0).resolved = true;
    return context.sync();
});
```

Respostas de comentário têm uma `resolved` propriedade ReadOnly. Seu valor é sempre igual ao do restante do thread.

## <a name="comment-metadata"></a>Metadados de comentários

Cada comentário contém metadados sobre a criação, como o autor e a data de criação. Os comentários criados por seu suplemento são considerados criados pelo usuário atual.

O exemplo a seguir mostra como exibir o email do autor, o nome do autor e a data de criação de um comentário em **A2**.

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

### <a name="comment-reply-metadata"></a>Metadados de resposta de comentário

Respostas de comentários armazenam os mesmos tipos de metadados que o comentário inicial.

O exemplo a seguir mostra como exibir o email do autor, o nome do autor e a data de criação da resposta de comentário mais recente em **a2**.

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

## <a name="mentions"></a>Menções

As [mencionas](https://support.office.com/article/use-mention-in-comments-to-tag-someone-for-feedback-644bf689-31a0-4977-a4fb-afe01820c1fd) são usadas para marcar colegas em um comentário. Isso envia notificações com o conteúdo do comentário. O suplemento pode criar essas menção em seu nome.

Comentários com menção precisam ser criados com objetos [CommentRichContent](/javascript/api/excel/excel.commentrichcontent) . Call `CommentCollection.add` com um `CommentRichContent` contendo um ou mais mencionas e especifique `ContentType.mention` como o `contentType` parâmetro. A `content` cadeia de caracteres também precisa ser formatada para inserir o menção no texto. O formato de um menção é: `<at id="{replyIndex}">{mentionName}</at>` .

> [!NOTE]
> Atualmente, apenas o nome exato de menção pode ser usado como o texto do link de menção. O suporte para versões reduzidas de um nome será adicionado posteriormente.

O exemplo a seguir mostra um comentário com uma única menção.

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

## <a name="comment-events"></a>Eventos de comentários

O suplemento pode ouvir adições, alterações e exclusões de comentários. [Eventos de comentários](/javascript/api/excel/excel.commentcollection#event-details) ocorrem no `CommentCollection` objeto. Para ouvir eventos de comentários, registre o `onAdded` , `onChanged` ou o `onDeleted` manipulador de eventos comment. Quando um evento Comment é detectado, use este manipulador de eventos para recuperar dados sobre o Comentário adicionado, alterado ou excluído. O `onChanged` evento também trata de adições de comentários, alterações e exclusões. 

Cada evento de comentário é acionado apenas uma vez quando várias adições, alterações ou exclusões são realizadas ao mesmo tempo. Todos os objetos [CommentAddedEventArgs](/javascript/api/excel/excel.commentaddedeventargs), [CommentChangedEventArgs](/javascript/api/excel/excel.commentchangedeventargs)e [CommentDeletedEventArgs](/javascript/api/excel/excel.commentdeletedeventargs) contêm matrizes de IDs de comentários para mapear as ações de evento de volta para as coleções de comentários.

Confira o artigo [trabalhar com eventos usando o Excel JavaScript API](excel-add-ins-events.md) para obter mais informações sobre como registrar manipuladores de eventos, manipular eventos e remover manipuladores de eventos. 

### <a name="comment-addition-events"></a>Eventos de adição de comentários 
O `onAdded` evento é disparado quando um ou mais comentários novos são adicionados à coleção comment. Esse evento *não* é disparado quando as respostas são adicionadas a um thread de comentários (consulte comentários sobre eventos de [alteração](#comment-change-events) para saber mais sobre eventos de resposta de comentários).

O exemplo a seguir mostra como registrar o `onAdded` manipulador de eventos e, em seguida, usar o `CommentAddedEventArgs` objeto para recuperar a `commentDetails` matriz do Comentário adicionado.

> [!NOTE]
> Este exemplo só funciona quando um único comentário é adicionado. 

```js
Excel.run(function (context) {
    var comments = context.workbook.worksheets.getActiveWorksheet().comments;

    // Register the onAdded comment event handler.
    comments.onAdded.add(commentAdded);

    return context.sync();
});

function commentAdded() {
    Excel.run(function (context) {
        // Retrieve the added comment using the comment ID.
        // Note: This method assumes only a single comment is added at a time. 
        var addedComment = context.workbook.comments.getItem(event.commentDetails[0].commentId);

        // Load the added comment's data.
        addedComment.load(["content", "authorName"]);

        return context.sync().then(function () {
            // Print out the added comment's data.
            console.log(`A comment was added. ID: ${event.commentDetails[0].commentId}. Comment content:${addedComment.content}. Comment author:${addedComment.authorName}`);
            return context.sync();
        });            
    });
}
```

### <a name="comment-change-events"></a>Eventos de alteração de comentário 
O `onChanged` evento Comment é disparado nos cenários a seguir.

- O conteúdo de um comentário é atualizado.
- Um thread de comentários é resolvido.
- Um thread de comentários é reaberto.
- Uma resposta é adicionada a um thread de comentários.
- Uma resposta é atualizada em um thread de comentários.
- Uma resposta é excluída em um thread de comentários.

O exemplo a seguir mostra como registrar o `onChanged` manipulador de eventos e, em seguida, usar o `CommentChangedEventArgs` objeto para recuperar a `commentDetails` matriz do comentário alterado.

> [!NOTE]
> Este exemplo só funciona quando um único comentário é alterado. 

```js
Excel.run(function (context) {
    var comments = context.workbook.worksheets.getActiveWorksheet().comments;

    // Register the onChanged comment event handler.
    comments.onChanged.add(commentChanged);

    return context.sync();
});    

function commentChanged() {
    Excel.run(function (context) {
        // Retrieve the changed comment using the comment ID.
        // Note: This method assumes only a single comment is changed at a time. 
        var changedComment = context.workbook.comments.getItem(event.commentDetails[0].commentId);

        // Load the changed comment's data.
        changedComment.load(["content", "authorName"]);

        return context.sync().then(function () {
            // Print out the changed comment's data.
            console.log(`A comment was changed. ID: ${event.commentDetails[0].commentId}`. Updated comment content: ${changedComment.content}`. Comment author: ${changedComment.authorName}`);
            return context.sync();
        });
    });
}
```

### <a name="comment-deletion-events"></a>Eventos de exclusão de comentários
O `onDeleted` evento é disparado quando um comentário é excluído da coleção comment. Após a exclusão de um comentário, seus metadados não estão mais disponíveis. O objeto [CommentDeletedEventArgs](/javascript/api/excel/excel.commentdeletedeventargs) fornece IDs de comentários, caso o suplemento esteja gerenciando Comentários individuais.

O exemplo a seguir mostra como registrar o `onDeleted` manipulador de eventos e, em seguida, usar o `CommentDeletedEventArgs` objeto para recuperar a `commentDetails` matriz do comentário excluído.

> [!NOTE]
> Este exemplo só funciona quando um único comentário é excluído. 

```js
Excel.run(function (context) {
    var comments = context.workbook.worksheets.getActiveWorksheet().comments;

    // Register the onDeleted comment event handler.
    comments.onDeleted.add(commentDeleted);

    return context.sync();
});

function commentDeleted() {
    Excel.run(function (context) {
        // Print out the deleted comment's ID.
        // Note: This method assumes only a single comment is deleted at a time. 
        console.log(`A comment was deleted. ID: ${event.commentDetails[0].commentId}`);
    });
}
```

## <a name="see-also"></a>Confira também

- [Modelo de objeto do JavaScript do Excel em suplementos do Office](excel-add-ins-core-concepts.md)
- [Trabalhar com pastas de trabalho usando a API JavaScript do Excel](excel-add-ins-workbooks.md)
- [Trabalhar com eventos usando a API JavaScript do Excel](excel-add-ins-events.md)
- [Inserir comentários e anotações no Excel](https://support.office.com/article/insert-comments-and-notes-in-excel-bdcc9f5d-38e2-45b4-9a92-0b2b5c7bf6f8)
