---
title: Office. Context. Mailbox – conjunto de requisitos 1,1
description: Conjunto de requisitos da API de caixa de correio do Outlook versão 1,1 do modelo de objeto Mailbox.
ms.date: 03/18/2020
localization_priority: Normal
ms.openlocfilehash: dde5f7e40b408dca5506ceddf1b9f076d713a939
ms.sourcegitcommit: 83f9a2fdff81ca421cd23feea103b9b60895cab4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "47430503"
---
# <a name="mailbox-requirement-set-11"></a>caixa de correio (conjunto de requisitos 1,1)

### <a name="officecontextmailbox"></a>[Office](office.md)[.context](office.context.md).mailbox

Fornece acesso ao modelo de objeto de suplemento do Outlook para o Microsoft Outlook.

##### <a name="requirements"></a>Requisitos

|Requisito| Valor|
|---|---|
|[Versão do conjunto de requisitos mínimos da caixa de correio](../../requirement-sets/outlook-api-requirement-sets.md)| 1.1|
|[Nível de permissão mínimo](../../../outlook/understanding-outlook-add-in-permissions.md)| Restrito|
|[Modo do Outlook aplicável](../../../outlook/outlook-add-ins-overview.md#extension-points)| Escrever ou Ler|

## <a name="properties"></a>Propriedades

| Propriedade | Minimum<br>nível de permissão | Modelos | Tipo de retorno | Minimum<br>conjunto de requisitos |
|---|---|---|---|:---:|
| [la](/javascript/api/outlook/office.mailbox?view=outlook-js-1.1&preserve-view=true#diagnostics) | ReadItem | Escrever<br>Ler | [Diagnostics](/javascript/api/outlook/office.diagnostics?view=outlook-js-1.1&preserve-view=true) | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [ewsUrl](/javascript/api/outlook/office.mailbox?view=outlook-js-1.1&preserve-view=true#ewsurl) | ReadItem | Escrever<br>Ler | String | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [item](office.context.mailbox.item.md) | Restricted | Escrever<br>Ler | [Item](/javascript/api/outlook/office.item?view=outlook-js-1.1&preserve-view=true) | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [userProfile](/javascript/api/outlook/office.mailbox?view=outlook-js-1.1&preserve-view=true#userprofile) | ReadItem | Escrever<br>Ler | [UserProfile](/javascript/api/outlook/office.userprofile?view=outlook-js-1.1&preserve-view=true) | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |

## <a name="methods"></a>Methods

| Método | Minimum<br>nível de permissão | Modelos | Minimum<br>conjunto de requisitos |
|---|---|---|:---:|
| [convertToLocalClientTime (TimeValue)](/javascript/api/outlook/office.mailbox?view=outlook-js-1.1&preserve-view=true#converttolocalclienttime-timevalue-) | ReadItem | Escrever<br>Ler | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [convertToUtcClientTime (entrada)](/javascript/api/outlook/office.mailbox?view=outlook-js-1.1&preserve-view=true#converttoutcclienttime-input-) | ReadItem | Escrever<br>Ler | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [displayAppointmentForm(itemId)](/javascript/api/outlook/office.mailbox?view=outlook-js-1.1&preserve-view=true#displayappointmentform-itemid-) | ReadItem | Escrever<br>Ler | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [displayMessageForm(itemId)](/javascript/api/outlook/office.mailbox?view=outlook-js-1.1&preserve-view=true#displaymessageform-itemid-) | ReadItem | Escrever<br>Ler | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [displayNewAppointmentForm(parameters)](/javascript/api/outlook/office.mailbox?view=outlook-js-1.1&preserve-view=true#displaynewappointmentform-parameters-) | ReadItem | Ler | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [getCallbackTokenAsync(callback, [userContext])](/javascript/api/outlook/office.mailbox?view=outlook-js-1.1&preserve-view=true#getcallbacktokenasync-callback--usercontext-) | ReadItem | Escrever<br>Ler | [1.3](../requirement-set-1.3/outlook-requirement-set-1.3.md)<br>[1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [getUserIdentityTokenAsync(callback, [userContext])](/javascript/api/outlook/office.mailbox?view=outlook-js-1.1&preserve-view=true#getuseridentitytokenasync-callback--usercontext-) | ReadItem | Escrever<br>Ler | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
| [makeEwsRequestAsync(data, callback, [userContext])](/javascript/api/outlook/office.mailbox?view=outlook-js-1.1&preserve-view=true#makeewsrequestasync-data--callback--usercontext-) | ReadWriteMailbox | Escrever<br>Ler | [1.1](../requirement-set-1.1/outlook-requirement-set-1.1.md) |
