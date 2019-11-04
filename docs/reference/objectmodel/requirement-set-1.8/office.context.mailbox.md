---
title: Office. Context. Mailbox – conjunto de requisitos 1,8
description: ''
ms.date: 10/31/2019
localization_priority: Normal
ms.openlocfilehash: 3f6d639cdf8bdff6f2df365622f58eba1c4b38e0
ms.sourcegitcommit: e989096f3d19761bf8477c585cde20b3f8e0b90d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "37902124"
---
# <a name="mailbox"></a><span data-ttu-id="f4ff2-102">mailbox</span><span class="sxs-lookup"><span data-stu-id="f4ff2-102">mailbox</span></span>

### <a name="officeofficemdcontextofficecontextmdmailbox"></a><span data-ttu-id="f4ff2-103">[Office](Office.md)[.context](Office.context.md).mailbox</span><span class="sxs-lookup"><span data-stu-id="f4ff2-103">[Office](Office.md)[.context](Office.context.md).mailbox</span></span>

<span data-ttu-id="f4ff2-104">Fornece acesso ao modelo de objeto de suplemento do Outlook para o Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-104">Provides access to the Outlook add-in object model for Microsoft Outlook.</span></span>

##### <a name="requirements"></a><span data-ttu-id="f4ff2-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-105">Requirements</span></span>

|<span data-ttu-id="f4ff2-106">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-106">Requirement</span></span>| <span data-ttu-id="f4ff2-107">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-107">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-108">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-108">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-109">1.0</span><span class="sxs-lookup"><span data-stu-id="f4ff2-109">1.0</span></span>|
|[<span data-ttu-id="f4ff2-110">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-110">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-111">Restrito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-111">Restricted</span></span>|
|[<span data-ttu-id="f4ff2-112">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-112">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-113">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-113">Compose or Read</span></span>|

##### <a name="members-and-methods"></a><span data-ttu-id="f4ff2-114">Membros e métodos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-114">Members and methods</span></span>

| <span data-ttu-id="f4ff2-115">Membro</span><span class="sxs-lookup"><span data-stu-id="f4ff2-115">Member</span></span> | <span data-ttu-id="f4ff2-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-116">Type</span></span> |
|--------|------|
| [<span data-ttu-id="f4ff2-117">ewsUrl</span><span class="sxs-lookup"><span data-stu-id="f4ff2-117">ewsUrl</span></span>](#ewsurl-string) | <span data-ttu-id="f4ff2-118">Membro</span><span class="sxs-lookup"><span data-stu-id="f4ff2-118">Member</span></span> |
| [<span data-ttu-id="f4ff2-119">Nova mastercategories</span><span class="sxs-lookup"><span data-stu-id="f4ff2-119">masterCategories</span></span>](#mastercategories-mastercategories) | <span data-ttu-id="f4ff2-120">Membro</span><span class="sxs-lookup"><span data-stu-id="f4ff2-120">Member</span></span> |
| [<span data-ttu-id="f4ff2-121">restUrl</span><span class="sxs-lookup"><span data-stu-id="f4ff2-121">restUrl</span></span>](#resturl-string) | <span data-ttu-id="f4ff2-122">Membro</span><span class="sxs-lookup"><span data-stu-id="f4ff2-122">Member</span></span> |
| [<span data-ttu-id="f4ff2-123">addHandlerAsync</span><span class="sxs-lookup"><span data-stu-id="f4ff2-123">addHandlerAsync</span></span>](#addhandlerasynceventtype-handler-options-callback) | <span data-ttu-id="f4ff2-124">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-124">Method</span></span> |
| [<span data-ttu-id="f4ff2-125">convertToEwsId</span><span class="sxs-lookup"><span data-stu-id="f4ff2-125">convertToEwsId</span></span>](#converttoewsiditemid-restversion--string) | <span data-ttu-id="f4ff2-126">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-126">Method</span></span> |
| [<span data-ttu-id="f4ff2-127">convertToLocalClientTime</span><span class="sxs-lookup"><span data-stu-id="f4ff2-127">convertToLocalClientTime</span></span>](#converttolocalclienttimetimevalue--localclienttime) | <span data-ttu-id="f4ff2-128">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-128">Method</span></span> |
| [<span data-ttu-id="f4ff2-129">convertToRestId</span><span class="sxs-lookup"><span data-stu-id="f4ff2-129">convertToRestId</span></span>](#converttorestiditemid-restversion--string) | <span data-ttu-id="f4ff2-130">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-130">Method</span></span> |
| [<span data-ttu-id="f4ff2-131">convertToUtcClientTime</span><span class="sxs-lookup"><span data-stu-id="f4ff2-131">convertToUtcClientTime</span></span>](#converttoutcclienttimeinput--date) | <span data-ttu-id="f4ff2-132">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-132">Method</span></span> |
| [<span data-ttu-id="f4ff2-133">displayAppointmentForm</span><span class="sxs-lookup"><span data-stu-id="f4ff2-133">displayAppointmentForm</span></span>](#displayappointmentformitemid) | <span data-ttu-id="f4ff2-134">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-134">Method</span></span> |
| [<span data-ttu-id="f4ff2-135">displayMessageForm</span><span class="sxs-lookup"><span data-stu-id="f4ff2-135">displayMessageForm</span></span>](#displaymessageformitemid) | <span data-ttu-id="f4ff2-136">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-136">Method</span></span> |
| [<span data-ttu-id="f4ff2-137">displayNewAppointmentForm</span><span class="sxs-lookup"><span data-stu-id="f4ff2-137">displayNewAppointmentForm</span></span>](#displaynewappointmentformparameters) | <span data-ttu-id="f4ff2-138">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-138">Method</span></span> |
| [<span data-ttu-id="f4ff2-139">displayNewMessageForm</span><span class="sxs-lookup"><span data-stu-id="f4ff2-139">displayNewMessageForm</span></span>](#displaynewmessageformparameters) | <span data-ttu-id="f4ff2-140">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-140">Method</span></span> |
| [<span data-ttu-id="f4ff2-141">getCallbackTokenAsync</span><span class="sxs-lookup"><span data-stu-id="f4ff2-141">getCallbackTokenAsync</span></span>](#getcallbacktokenasyncoptions-callback) | <span data-ttu-id="f4ff2-142">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-142">Method</span></span> |
| [<span data-ttu-id="f4ff2-143">getCallbackTokenAsync</span><span class="sxs-lookup"><span data-stu-id="f4ff2-143">getCallbackTokenAsync</span></span>](#getcallbacktokenasynccallback-usercontext) | <span data-ttu-id="f4ff2-144">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-144">Method</span></span> |
| [<span data-ttu-id="f4ff2-145">getUserIdentityTokenAsync</span><span class="sxs-lookup"><span data-stu-id="f4ff2-145">getUserIdentityTokenAsync</span></span>](#getuseridentitytokenasynccallback-usercontext) | <span data-ttu-id="f4ff2-146">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-146">Method</span></span> |
| [<span data-ttu-id="f4ff2-147">makeEwsRequestAsync</span><span class="sxs-lookup"><span data-stu-id="f4ff2-147">makeEwsRequestAsync</span></span>](#makeewsrequestasyncdata-callback-usercontext) | <span data-ttu-id="f4ff2-148">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-148">Method</span></span> |
| [<span data-ttu-id="f4ff2-149">removeHandlerAsync</span><span class="sxs-lookup"><span data-stu-id="f4ff2-149">removeHandlerAsync</span></span>](#removehandlerasynceventtype-options-callback) | <span data-ttu-id="f4ff2-150">Método</span><span class="sxs-lookup"><span data-stu-id="f4ff2-150">Method</span></span> |

### <a name="namespaces"></a><span data-ttu-id="f4ff2-151">Namespaces</span><span class="sxs-lookup"><span data-stu-id="f4ff2-151">Namespaces</span></span>

<span data-ttu-id="f4ff2-152">[diagnostics](Office.context.mailbox.diagnostics.md): Fornece informações de diagnóstico para um suplemento do Outlook.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-152">[diagnostics](Office.context.mailbox.diagnostics.md): Provides diagnostic information to an Outlook add-in.</span></span>

<span data-ttu-id="f4ff2-153">[item](Office.context.mailbox.item.md): Fornece propriedades e métodos para acessar uma mensagem ou um compromisso em um suplemento do Outlook.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-153">[item](Office.context.mailbox.item.md): Provides methods and properties for accessing a message or appointment in an Outlook add-in.</span></span>

<span data-ttu-id="f4ff2-154">[userProfile](Office.context.mailbox.userProfile.md): Fornece informações sobre o usuário em um suplemento do Outlook.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-154">[userProfile](Office.context.mailbox.userProfile.md): Provides information about the user in an Outlook add-in.</span></span>

### <a name="members"></a><span data-ttu-id="f4ff2-155">Members</span><span class="sxs-lookup"><span data-stu-id="f4ff2-155">Members</span></span>

#### <a name="ewsurl-string"></a><span data-ttu-id="f4ff2-156">ewsUrl: String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-156">ewsUrl: String</span></span>

<span data-ttu-id="f4ff2-p101">Obtém a URL do ponto de extremidade dos EWS (Serviços Web do Exchange) para esta conta de email. Somente modo de Leitura.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p101">Gets the URL of the Exchange Web Services (EWS) endpoint for this email account. Read mode only.</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-159">Não há suporte para esse membro no Outlook no iOS ou no Android.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-159">This member is not supported in Outlook on iOS or Android.</span></span>

<span data-ttu-id="f4ff2-p102">O valor `ewsUrl` pode ser usado por um serviço remoto para fazer chamadas do EWS à caixa de correio do usuário. Por exemplo, você pode criar um serviço remoto para [obter anexos do item selecionado](/outlook/add-ins/get-attachments-of-an-outlook-item).</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p102">The `ewsUrl` value can be used by a remote service to make EWS calls to the user's mailbox. For example, you can create a remote service to [get attachments from the selected item](/outlook/add-ins/get-attachments-of-an-outlook-item).</span></span>

<span data-ttu-id="f4ff2-162">Seu aplicativo deve ter a permissão **ReadItem** especificada em seu manifesto para chamar o membro `ewsUrl` em modo de leitura.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-162">Your app must have the **ReadItem** permission specified in its manifest to call the `ewsUrl` member in read mode.</span></span>

<span data-ttu-id="f4ff2-p103">No modo de composição, é preciso chamar o método [`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) antes de poder usar o membro `ewsUrl`. Seu aplicativo deve ter permissões **ReadWriteItem** para chamar o método `saveAsync`.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p103">In compose mode you must call the [`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) method before you can use the `ewsUrl` member. Your app must have **ReadWriteItem** permissions to call the `saveAsync` method.</span></span>

##### <a name="type"></a><span data-ttu-id="f4ff2-165">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-165">Type</span></span>

*   <span data-ttu-id="f4ff2-166">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-166">String</span></span>

##### <a name="requirements"></a><span data-ttu-id="f4ff2-167">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-167">Requirements</span></span>

|<span data-ttu-id="f4ff2-168">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-168">Requirement</span></span>| <span data-ttu-id="f4ff2-169">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-169">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-170">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-170">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-171">1.0</span><span class="sxs-lookup"><span data-stu-id="f4ff2-171">1.0</span></span>|
|[<span data-ttu-id="f4ff2-172">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-172">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-173">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-173">ReadItem</span></span>|
|[<span data-ttu-id="f4ff2-174">Modo Aplicável do Outlook</span><span class="sxs-lookup"><span data-stu-id="f4ff2-174">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-175">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-175">Compose or Read</span></span>|

<br>

---
---

#### <a name="mastercategories-mastercategoriesjavascriptapioutlookofficemastercategoriesviewoutlook-js-18"></a><span data-ttu-id="f4ff2-176">Nova mastercategories: [nova mastercategories](/javascript/api/outlook/office.mastercategories?view=outlook-js-1.8)</span><span class="sxs-lookup"><span data-stu-id="f4ff2-176">masterCategories: [MasterCategories](/javascript/api/outlook/office.mastercategories?view=outlook-js-1.8)</span></span>

<span data-ttu-id="f4ff2-177">Obtém um objeto que fornece métodos para gerenciar a lista mestra de categorias nesta caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-177">Gets an object that provides methods to manage the categories master list on this mailbox.</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-178">Não há suporte para esse membro no Outlook no iOS ou no Android.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-178">This member is not supported in Outlook on iOS or Android.</span></span>

##### <a name="type"></a><span data-ttu-id="f4ff2-179">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-179">Type</span></span>

*   [<span data-ttu-id="f4ff2-180">MasterCategories</span><span class="sxs-lookup"><span data-stu-id="f4ff2-180">MasterCategories</span></span>](/javascript/api/outlook/office.mastercategories?view=outlook-js-1.8)

##### <a name="requirements"></a><span data-ttu-id="f4ff2-181">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-181">Requirements</span></span>

|<span data-ttu-id="f4ff2-182">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-182">Requirement</span></span>| <span data-ttu-id="f4ff2-183">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-183">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-184">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-184">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-185">1,8</span><span class="sxs-lookup"><span data-stu-id="f4ff2-185">1.8</span></span> |
|[<span data-ttu-id="f4ff2-186">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-186">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-187">ReadWriteMailbox</span><span class="sxs-lookup"><span data-stu-id="f4ff2-187">ReadWriteMailbox</span></span> |
|[<span data-ttu-id="f4ff2-188">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-188">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-189">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-189">Compose or Read</span></span> |

##### <a name="example"></a><span data-ttu-id="f4ff2-190">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-190">Example</span></span>

<span data-ttu-id="f4ff2-191">Este exemplo obtém a lista mestra de categorias para esta caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-191">This example gets the categories master list for this mailbox.</span></span>

```js
Office.context.mailbox.masterCategories.getAsync(function (asyncResult) {
  if (asyncResult.status === Office.AsyncResultStatus.Failed) {
    console.log("Action failed with error: " + asyncResult.error.message);
  } else {
    console.log("Master categories: " + JSON.stringify(asyncResult.value));
  }
});
```

<br>

---
---

#### <a name="resturl-string"></a><span data-ttu-id="f4ff2-192">restUrl: String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-192">restUrl: String</span></span>

<span data-ttu-id="f4ff2-193">Obtém a URL do ponto de extremidade de REST para esta conta de email.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-193">Gets the URL of the REST endpoint for this email account.</span></span>

<span data-ttu-id="f4ff2-194">O valor `restUrl` pode ser usado para fazer chamadas da [API REST](/outlook/rest/) para a caixa de correio do usuário.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-194">The `restUrl` value can be used to make [REST API](/outlook/rest/) calls to the user's mailbox.</span></span>

<span data-ttu-id="f4ff2-195">Seu aplicativo deve ter a permissão **ReadItem** especificada em seu manifesto para chamar o membro `restUrl` em modo de leitura.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-195">Your app must have the **ReadItem** permission specified in its manifest to call the `restUrl` member in read mode.</span></span>

<span data-ttu-id="f4ff2-p104">No modo de composição, é preciso chamar o método [`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) antes de poder usar o membro `restUrl`. Seu aplicativo deve ter permissões **ReadWriteItem** para chamar o método `saveAsync`.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p104">In compose mode you must call the [`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) method before you can use the `restUrl` member. Your app must have **ReadWriteItem** permissions to call the `saveAsync` method.</span></span>

##### <a name="type"></a><span data-ttu-id="f4ff2-198">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-198">Type</span></span>

*   <span data-ttu-id="f4ff2-199">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-199">String</span></span>

##### <a name="requirements"></a><span data-ttu-id="f4ff2-200">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-200">Requirements</span></span>

|<span data-ttu-id="f4ff2-201">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-201">Requirement</span></span>| <span data-ttu-id="f4ff2-202">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-202">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-203">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-203">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-204">1,5</span><span class="sxs-lookup"><span data-stu-id="f4ff2-204">1.5</span></span> |
|[<span data-ttu-id="f4ff2-205">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-205">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-206">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-206">ReadItem</span></span>|
|[<span data-ttu-id="f4ff2-207">Modo Aplicável do Outlook</span><span class="sxs-lookup"><span data-stu-id="f4ff2-207">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-208">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-208">Compose or Read</span></span>|

### <a name="methods"></a><span data-ttu-id="f4ff2-209">Métodos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-209">Methods</span></span>

#### <a name="addhandlerasynceventtype-handler-options-callback"></a><span data-ttu-id="f4ff2-210">addHandlerAsync(eventType, handler, [options], [callback])</span><span class="sxs-lookup"><span data-stu-id="f4ff2-210">addHandlerAsync(eventType, handler, [options], [callback])</span></span>

<span data-ttu-id="f4ff2-211">Adiciona um manipulador de eventos a um evento com suporte.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-211">Adds an event handler for a supported event.</span></span>

<span data-ttu-id="f4ff2-212">Atualmente, os tipos de eventos com `Office.EventType.ItemChanged` suporte `Office.EventType.OfficeThemeChanged`são e.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-212">Currently, the supported event types are `Office.EventType.ItemChanged` and `Office.EventType.OfficeThemeChanged`.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-213">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-213">Parameters</span></span>

| <span data-ttu-id="f4ff2-214">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-214">Name</span></span> | <span data-ttu-id="f4ff2-215">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-215">Type</span></span> | <span data-ttu-id="f4ff2-216">Atributos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-216">Attributes</span></span> | <span data-ttu-id="f4ff2-217">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-217">Description</span></span> |
|---|---|---|---|
| `eventType` | [<span data-ttu-id="f4ff2-218">Office.EventType</span><span class="sxs-lookup"><span data-stu-id="f4ff2-218">Office.EventType</span></span>](office.md#eventtype-string) || <span data-ttu-id="f4ff2-219">O evento que deve invocar o manipulador.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-219">The event that should invoke the handler.</span></span> |
| `handler` | <span data-ttu-id="f4ff2-220">Função</span><span class="sxs-lookup"><span data-stu-id="f4ff2-220">Function</span></span> || <span data-ttu-id="f4ff2-p105">A função para manipular o evento. A função deve aceitar um parâmetro exclusivo, que é um objeto literal. A propriedade `type` no parâmetro corresponderá ao parâmetro `eventType` passado para `addHandlerAsync`.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p105">The function to handle the event. The function must accept a single parameter, which is an object literal. The `type` property on the parameter will match the `eventType` parameter passed to `addHandlerAsync`.</span></span> |
| `options` | <span data-ttu-id="f4ff2-224">Objeto</span><span class="sxs-lookup"><span data-stu-id="f4ff2-224">Object</span></span> | <span data-ttu-id="f4ff2-225">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-225">&lt;optional&gt;</span></span> | <span data-ttu-id="f4ff2-226">Um objeto literal que contém uma ou mais das propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-226">An object literal that contains one or more of the following properties.</span></span> |
| `options.asyncContext` | <span data-ttu-id="f4ff2-227">Objeto</span><span class="sxs-lookup"><span data-stu-id="f4ff2-227">Object</span></span> | <span data-ttu-id="f4ff2-228">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-228">&lt;optional&gt;</span></span> | <span data-ttu-id="f4ff2-229">Os desenvolvedores podem fornecer qualquer objeto que desejarem acessar no método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-229">Developers can provide any object they wish to access in the callback method.</span></span> |
| `callback` | <span data-ttu-id="f4ff2-230">function</span><span class="sxs-lookup"><span data-stu-id="f4ff2-230">function</span></span>| <span data-ttu-id="f4ff2-231">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-231">&lt;optional&gt;</span></span>|<span data-ttu-id="f4ff2-232">Quando o método for concluído, a função passada ao parâmetro `callback` é chamada com um único parâmetro, `asyncResult`, que é um objeto [`AsyncResult`](/javascript/api/office/office.asyncresult).</span><span class="sxs-lookup"><span data-stu-id="f4ff2-232">When the method completes, the function passed in the `callback` parameter is called with a single parameter, `asyncResult`, which is an [`AsyncResult`](/javascript/api/office/office.asyncresult) object.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-233">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-233">Requirements</span></span>

|<span data-ttu-id="f4ff2-234">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-234">Requirement</span></span>| <span data-ttu-id="f4ff2-235">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-235">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-236">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-236">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-237">1,5</span><span class="sxs-lookup"><span data-stu-id="f4ff2-237">1.5</span></span> |
|[<span data-ttu-id="f4ff2-238">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-238">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-239">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-239">ReadItem</span></span> |
|[<span data-ttu-id="f4ff2-240">Modo Aplicável do Outlook</span><span class="sxs-lookup"><span data-stu-id="f4ff2-240">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-241">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-241">Compose or Read</span></span>|

##### <a name="example"></a><span data-ttu-id="f4ff2-242">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-242">Example</span></span>

```js
Office.initialize = function (reason) {
  $(document).ready(function () {
    Office.context.mailbox.addHandlerAsync(Office.EventType.ItemChanged, loadNewItem, function (result) {
      if (result.status === Office.AsyncResultStatus.Failed) {
        // Handle error.
      }
    });
  });
};

function loadNewItem(eventArgs) {
  // Load the properties of the newly selected item.
  loadProps(Office.context.mailbox.item);
}
```

<br>

---
---

#### <a name="converttoewsiditemid-restversion--string"></a><span data-ttu-id="f4ff2-243">convertToEwsId(itemId, restVersion) → {String}</span><span class="sxs-lookup"><span data-stu-id="f4ff2-243">convertToEwsId(itemId, restVersion) → {String}</span></span>

<span data-ttu-id="f4ff2-244">Converte uma ID de item formatada para REST no formato EWS.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-244">Converts an item ID formatted for REST into EWS format.</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-245">Não há suporte para esse método no Outlook no iOS ou no Android.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-245">This method is not supported in Outlook on iOS or Android.</span></span>

<span data-ttu-id="f4ff2-p106">IDs de itens recuperadas por meio de uma API REST (como a [API do Email do Outlook](/previous-versions/office/office-365-api/api/version-2.0/mail-rest-operations) ou o [Microsoft Graph](https://graph.microsoft.io/)) usam um formato diferente daquele usado pelos Serviços Web do Exchange (EWS). O método `convertToEwsId` converte uma ID formatada como REST para o formato adequado para EWS.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p106">Item IDs retrieved via a REST API (such as the [Outlook Mail API](/previous-versions/office/office-365-api/api/version-2.0/mail-rest-operations) or the [Microsoft Graph](https://graph.microsoft.io/)) use a different format than the format used by Exchange Web Services (EWS). The `convertToEwsId` method converts a REST-formatted ID into the proper format for EWS.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-248">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-248">Parameters</span></span>

|<span data-ttu-id="f4ff2-249">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-249">Name</span></span>| <span data-ttu-id="f4ff2-250">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-250">Type</span></span>| <span data-ttu-id="f4ff2-251">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-251">Description</span></span>|
|---|---|---|
|`itemId`| <span data-ttu-id="f4ff2-252">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-252">String</span></span>|<span data-ttu-id="f4ff2-253">Uma ID de item formatada para APIs REST do Outlook</span><span class="sxs-lookup"><span data-stu-id="f4ff2-253">An item ID formatted for the Outlook REST APIs</span></span>|
|`restVersion`| [<span data-ttu-id="f4ff2-254">Office.MailboxEnums.RestVersion</span><span class="sxs-lookup"><span data-stu-id="f4ff2-254">Office.MailboxEnums.RestVersion</span></span>](/javascript/api/outlook/office.mailboxenums.restversion?view=outlook-js-1.8)|<span data-ttu-id="f4ff2-255">Um valor que indica a versão da API REST do Outlook usada para recuperar a ID do item.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-255">A value indicating the version of the Outlook REST API used to retrieve the item ID.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-256">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-256">Requirements</span></span>

|<span data-ttu-id="f4ff2-257">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-257">Requirement</span></span>| <span data-ttu-id="f4ff2-258">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-258">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-259">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-259">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-260">1.3</span><span class="sxs-lookup"><span data-stu-id="f4ff2-260">1.3</span></span>|
|[<span data-ttu-id="f4ff2-261">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-261">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-262">Restrito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-262">Restricted</span></span>|
|[<span data-ttu-id="f4ff2-263">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-263">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-264">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-264">Compose or Read</span></span>|

##### <a name="returns"></a><span data-ttu-id="f4ff2-265">Retorna:</span><span class="sxs-lookup"><span data-stu-id="f4ff2-265">Returns:</span></span>

<span data-ttu-id="f4ff2-266">Tipo: String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-266">Type: String</span></span>

##### <a name="example"></a><span data-ttu-id="f4ff2-267">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-267">Example</span></span>

```js
// Get an item's ID from a REST API.
var restId = 'AAMkAGVlOTZjNTM3LW...';

// Treat restId as coming from the v2.0 version of the Outlook Mail API.
var ewsId = Office.context.mailbox.convertToEwsId(restId, Office.MailboxEnums.RestVersion.v2_0);
```

<br>

---
---

#### <a name="converttolocalclienttimetimevalue--localclienttimejavascriptapioutlookofficelocalclienttimeviewoutlook-js-18"></a><span data-ttu-id="f4ff2-268">convertToLocalClientTime(timeValue) → {[LocalClientTime](/javascript/api/outlook/office.LocalClientTime?view=outlook-js-1.8)}</span><span class="sxs-lookup"><span data-stu-id="f4ff2-268">convertToLocalClientTime(timeValue) → {[LocalClientTime](/javascript/api/outlook/office.LocalClientTime?view=outlook-js-1.8)}</span></span>

<span data-ttu-id="f4ff2-269">Obtém um dicionário contendo informações de hora em tempo local do cliente.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-269">Gets a dictionary containing time information in local client time.</span></span>

<span data-ttu-id="f4ff2-p107">Um aplicativo de email para o Outlook em uma área de trabalho ou na Web pode usar fusos horários diferentes para as datas e horas. O Outlook em uma área de trabalho usa o fuso horário do computador cliente; o Outlook na Web usa o fuso horário definido no Centro de Administração do Exchange (EAC). Você deve lidar com valores de data e hora para que os valores exibidos na interface do usuário sejam sempre consistentes com o fuso horário que o usuário espera.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p107">A mail app for Outlook on a desktop or on the web can use different time zones for the dates and times. Outlook on a desktop uses the client computer time zone; Outlook on the web uses the time zone set on the Exchange Admin Center (EAC). You should handle date and time values so that the values you display on the user interface are always consistent with the time zone that the user expects.</span></span>

<span data-ttu-id="f4ff2-p108">Se o aplicativo de email estiver sendo executado no Outlook em um cliente da área de trabalho, o método `convertToLocalClientTime` retornará um objeto de dicionário com os valores definidos para o fuso horário do computador cliente. Se o aplicativo de email estiver sendo executado no Outlook na Web, o método `convertToLocalClientTime` retornará um objeto de dicionário com os valores definidos para o fuso horário especificado no EAC.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p108">If the mail app is running in Outlook on a desktop client, the `convertToLocalClientTime` method will return a dictionary object with the values set to the client computer time zone. If the mail app is running in Outlook on the web, the `convertToLocalClientTime` method will return a dictionary object with the values set to the time zone specified in the EAC.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-275">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-275">Parameters</span></span>

|<span data-ttu-id="f4ff2-276">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-276">Name</span></span>| <span data-ttu-id="f4ff2-277">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-277">Type</span></span>| <span data-ttu-id="f4ff2-278">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-278">Description</span></span>|
|---|---|---|
|`timeValue`| <span data-ttu-id="f4ff2-279">Date</span><span class="sxs-lookup"><span data-stu-id="f4ff2-279">Date</span></span>|<span data-ttu-id="f4ff2-280">Um objeto Date</span><span class="sxs-lookup"><span data-stu-id="f4ff2-280">A Date object</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-281">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-281">Requirements</span></span>

|<span data-ttu-id="f4ff2-282">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-282">Requirement</span></span>| <span data-ttu-id="f4ff2-283">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-283">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-284">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-284">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-285">1.0</span><span class="sxs-lookup"><span data-stu-id="f4ff2-285">1.0</span></span>|
|[<span data-ttu-id="f4ff2-286">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-286">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-287">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-287">ReadItem</span></span>|
|[<span data-ttu-id="f4ff2-288">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-288">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-289">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-289">Compose or Read</span></span>|

##### <a name="returns"></a><span data-ttu-id="f4ff2-290">Retorna:</span><span class="sxs-lookup"><span data-stu-id="f4ff2-290">Returns:</span></span>

<span data-ttu-id="f4ff2-291">Tipo: [LocalClientTime](/javascript/api/outlook/office.LocalClientTime?view=outlook-js-1.8)</span><span class="sxs-lookup"><span data-stu-id="f4ff2-291">Type: [LocalClientTime](/javascript/api/outlook/office.LocalClientTime?view=outlook-js-1.8)</span></span>

<br>

---
---

#### <a name="converttorestiditemid-restversion--string"></a><span data-ttu-id="f4ff2-292">convertToRestId(itemId, restVersion) → {String}</span><span class="sxs-lookup"><span data-stu-id="f4ff2-292">convertToRestId(itemId, restVersion) → {String}</span></span>

<span data-ttu-id="f4ff2-293">Converte uma ID de item formatada para EWS no formato REST.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-293">Converts an item ID formatted for EWS into REST format.</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-294">Não há suporte para esse método no Outlook no iOS ou no Android.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-294">This method is not supported in Outlook on iOS or Android.</span></span>

<span data-ttu-id="f4ff2-p109">IDs de itens recuperadas por EWS ou pela propriedade `itemId` usam um formato diferente daquele usado por APIs REST (como a [API do Email do Outlook](/previous-versions/office/office-365-api/api/version-2.0/mail-rest-operations) ou o [Microsoft Graph](https://graph.microsoft.io/)). O método `convertToRestId` converte uma ID formatada como EWS para o formato adequado para REST.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p109">Item IDs retrieved via EWS or via the `itemId` property use a different format than the format used by REST APIs (such as the [Outlook Mail API](/previous-versions/office/office-365-api/api/version-2.0/mail-rest-operations) or the [Microsoft Graph](https://graph.microsoft.io/)). The `convertToRestId` method converts an EWS-formatted ID into the proper format for REST.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-297">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-297">Parameters</span></span>

|<span data-ttu-id="f4ff2-298">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-298">Name</span></span>| <span data-ttu-id="f4ff2-299">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-299">Type</span></span>| <span data-ttu-id="f4ff2-300">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-300">Description</span></span>|
|---|---|---|
|`itemId`| <span data-ttu-id="f4ff2-301">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-301">String</span></span>|<span data-ttu-id="f4ff2-302">Uma ID de item formatada para os Serviços Web do Exchange (EWS)</span><span class="sxs-lookup"><span data-stu-id="f4ff2-302">An item ID formatted for Exchange Web Services (EWS)</span></span>|
|`restVersion`| [<span data-ttu-id="f4ff2-303">Office.MailboxEnums.RestVersion</span><span class="sxs-lookup"><span data-stu-id="f4ff2-303">Office.MailboxEnums.RestVersion</span></span>](/javascript/api/outlook/office.mailboxenums.restversion?view=outlook-js-1.8)|<span data-ttu-id="f4ff2-304">Um valor que indica a versão da API REST do Outlook com a qual a ID convertida será usada.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-304">A value indicating the version of the Outlook REST API that the converted ID will be used with.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-305">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-305">Requirements</span></span>

|<span data-ttu-id="f4ff2-306">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-306">Requirement</span></span>| <span data-ttu-id="f4ff2-307">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-307">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-308">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-308">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-309">1.3</span><span class="sxs-lookup"><span data-stu-id="f4ff2-309">1.3</span></span>|
|[<span data-ttu-id="f4ff2-310">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-310">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-311">Restrito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-311">Restricted</span></span>|
|[<span data-ttu-id="f4ff2-312">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-312">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-313">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-313">Compose or Read</span></span>|

##### <a name="returns"></a><span data-ttu-id="f4ff2-314">Retorna:</span><span class="sxs-lookup"><span data-stu-id="f4ff2-314">Returns:</span></span>

<span data-ttu-id="f4ff2-315">Tipo: String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-315">Type: String</span></span>

##### <a name="example"></a><span data-ttu-id="f4ff2-316">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-316">Example</span></span>

```js
// Get the currently selected item's ID.
var ewsId = Office.context.mailbox.item.itemId;

// Convert to a REST ID for the v2.0 version of the Outlook Mail API.
var restId = Office.context.mailbox.convertToRestId(ewsId, Office.MailboxEnums.RestVersion.v2_0);
```

<br>

---
---

#### <a name="converttoutcclienttimeinput--date"></a><span data-ttu-id="f4ff2-317">convertToUtcClientTime(input) → {Date}</span><span class="sxs-lookup"><span data-stu-id="f4ff2-317">convertToUtcClientTime(input) → {Date}</span></span>

<span data-ttu-id="f4ff2-318">Obtém um objeto Date de um dicionário contendo as informações de hora.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-318">Gets a Date object from a dictionary containing time information.</span></span>

<span data-ttu-id="f4ff2-319">O método `convertToUtcClientTime` converte um dicionário que contém uma data e hora locais para um objeto Date com os valores corretos para a data e hora locais.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-319">The `convertToUtcClientTime` method converts a dictionary containing a local date and time to a Date object with the correct values for the local date and time.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-320">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-320">Parameters</span></span>

|<span data-ttu-id="f4ff2-321">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-321">Name</span></span>| <span data-ttu-id="f4ff2-322">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-322">Type</span></span>| <span data-ttu-id="f4ff2-323">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-323">Description</span></span>|
|---|---|---|
|`input`| [<span data-ttu-id="f4ff2-324">LocalClientTime</span><span class="sxs-lookup"><span data-stu-id="f4ff2-324">LocalClientTime</span></span>](/javascript/api/outlook/office.LocalClientTime?view=outlook-js-1.8)|<span data-ttu-id="f4ff2-325">O valor de hora local a converter.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-325">The local time value to convert.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-326">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-326">Requirements</span></span>

|<span data-ttu-id="f4ff2-327">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-327">Requirement</span></span>| <span data-ttu-id="f4ff2-328">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-328">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-329">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-329">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-330">1.0</span><span class="sxs-lookup"><span data-stu-id="f4ff2-330">1.0</span></span>|
|[<span data-ttu-id="f4ff2-331">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-331">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-332">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-332">ReadItem</span></span>|
|[<span data-ttu-id="f4ff2-333">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-333">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-334">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-334">Compose or Read</span></span>|

##### <a name="returns"></a><span data-ttu-id="f4ff2-335">Retorna:</span><span class="sxs-lookup"><span data-stu-id="f4ff2-335">Returns:</span></span>

<span data-ttu-id="f4ff2-336">Um objeto Date com a hora expressa em UTC.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-336">A Date object with the time expressed in UTC.</span></span>

<span data-ttu-id="f4ff2-337">Tipo: Data</span><span class="sxs-lookup"><span data-stu-id="f4ff2-337">Type: Date</span></span>

##### <a name="example"></a><span data-ttu-id="f4ff2-338">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-338">Example</span></span>

```js
// Represents 3:37 PM PDT on Monday, August 26, 2019.
var input = {
  date: 26,
  hours: 15,
  milliseconds: 2,
  minutes: 37,
  month: 7,
  seconds: 2,
  timezoneOffset: -420,
  year: 2019
};

// result should be a Date object.
var result = Office.context.mailbox.convertToUtcClientTime(input);

// Output should be "2019-08-26T22:37:02.002Z".
console.log(result.toISOString());
```

<br>

---
---

#### <a name="displayappointmentformitemid"></a><span data-ttu-id="f4ff2-339">displayAppointmentForm(itemId)</span><span class="sxs-lookup"><span data-stu-id="f4ff2-339">displayAppointmentForm(itemId)</span></span>

<span data-ttu-id="f4ff2-340">Exibe um compromisso de calendário existente.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-340">Displays an existing calendar appointment.</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-341">Não há suporte para esse método no Outlook no iOS ou no Android.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-341">This method is not supported in Outlook on iOS or Android.</span></span>

<span data-ttu-id="f4ff2-342">O método `displayAppointmentForm` abre um compromisso de calendário existente em uma nova janela na área de trabalho ou em uma caixa de diálogo em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-342">The `displayAppointmentForm` method opens an existing calendar appointment in a new window on the desktop or in a dialog box on mobile devices.</span></span>

<span data-ttu-id="f4ff2-p110">No Outlook no Mac, você pode usar esse método para exibir um único compromisso que não faz parte de uma série recorrente, ou o compromisso mestre de uma série recorrente, mas não pode exibir um instância da série. Isso ocorre porque no Outlook no Mac você não pode acessar as propriedades (incluindo a ID do item) das instâncias de uma série recorrente.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p110">In Outlook on Mac, you can use this method to display a single appointment that is not part of a recurring series, or the master appointment of a recurring series, but you cannot display an instance of the series. This is because in Outlook on Mac, you cannot access the properties (including the item ID) of instances of a recurring series.</span></span>

<span data-ttu-id="f4ff2-345">No Outlook na Web, este método abre o formulário especificado somente se o corpo do formulário for menor ou igual ao número de caracteres de 32KB.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-345">In Outlook on the web, this method opens the specified form only if the body of the form is less than or equal to 32KB number of characters.</span></span>

<span data-ttu-id="f4ff2-346">Se o identificador do item especificado não identificar um compromisso existente, um painel em branco abre no dispositivo ou no computador cliente e nenhuma mensagem de erro será exibida.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-346">If the specified item identifier does not identify an existing appointment, a blank pane opens on the client computer or device, and no error message will be returned.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-347">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-347">Parameters</span></span>

|<span data-ttu-id="f4ff2-348">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-348">Name</span></span>| <span data-ttu-id="f4ff2-349">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-349">Type</span></span>| <span data-ttu-id="f4ff2-350">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-350">Description</span></span>|
|---|---|---|
|`itemId`| <span data-ttu-id="f4ff2-351">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-351">String</span></span>|<span data-ttu-id="f4ff2-352">O identificador dos Serviços Web do Exchange (EWS) para um compromisso de calendário existente.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-352">The Exchange Web Services (EWS) identifier for an existing calendar appointment.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-353">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-353">Requirements</span></span>

|<span data-ttu-id="f4ff2-354">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-354">Requirement</span></span>| <span data-ttu-id="f4ff2-355">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-355">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-356">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-356">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-357">1.0</span><span class="sxs-lookup"><span data-stu-id="f4ff2-357">1.0</span></span>|
|[<span data-ttu-id="f4ff2-358">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-358">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-359">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-359">ReadItem</span></span>|
|[<span data-ttu-id="f4ff2-360">Modo Aplicável do Outlook</span><span class="sxs-lookup"><span data-stu-id="f4ff2-360">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-361">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-361">Compose or Read</span></span>|

##### <a name="example"></a><span data-ttu-id="f4ff2-362">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-362">Example</span></span>

```js
Office.context.mailbox.displayAppointmentForm(appointmentId);
```

<br>

---
---

#### <a name="displaymessageformitemid"></a><span data-ttu-id="f4ff2-363">displayMessageForm(itemId)</span><span class="sxs-lookup"><span data-stu-id="f4ff2-363">displayMessageForm(itemId)</span></span>

<span data-ttu-id="f4ff2-364">Exibe uma mensagem existente.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-364">Displays an existing message.</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-365">Não há suporte para esse método no Outlook no iOS ou no Android.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-365">This method is not supported in Outlook on iOS or Android.</span></span>

<span data-ttu-id="f4ff2-366">O método `displayMessageForm` abre uma mensagem existente em uma nova janela na área de trabalho ou em uma caixa de diálogo em dispositivos móveis.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-366">The `displayMessageForm` method opens an existing message in a new window on the desktop or in a dialog box on mobile devices.</span></span>

<span data-ttu-id="f4ff2-367">No Outlook na Web, este método abre o formulário especificado somente se o corpo do formulário for menor ou igual ao número de caracteres de 32 KB.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-367">In Outlook on the web, this method opens the specified form only if the body of the form is less than or equal to 32 KB number of characters.</span></span>

<span data-ttu-id="f4ff2-368">Se o identificador do item especificado não identificar uma mensagem existente, não será exibida mensagem no computador cliente e nenhuma mensagem de erro será retornada.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-368">If the specified item identifier does not identify an existing message, no message will be displayed on the client computer, and no error message will be returned.</span></span>

<span data-ttu-id="f4ff2-p111">Não use o método `displayMessageForm` com um `itemId` que representa um compromisso. Use o método `displayAppointmentForm` para exibir um compromisso existente e `displayNewAppointmentForm` para exibir um formulário e criar um novo compromisso.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p111">Do not use the `displayMessageForm` with an `itemId` that represents an appointment. Use the `displayAppointmentForm` method to display an existing appointment, and `displayNewAppointmentForm` to display a form to create a new appointment.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-371">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-371">Parameters</span></span>

|<span data-ttu-id="f4ff2-372">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-372">Name</span></span>| <span data-ttu-id="f4ff2-373">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-373">Type</span></span>| <span data-ttu-id="f4ff2-374">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-374">Description</span></span>|
|---|---|---|
|`itemId`| <span data-ttu-id="f4ff2-375">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-375">String</span></span>|<span data-ttu-id="f4ff2-376">O identificador dos Serviços Web do Exchange (EWS) para uma mensagem existente.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-376">The Exchange Web Services (EWS) identifier for an existing message.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-377">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-377">Requirements</span></span>

|<span data-ttu-id="f4ff2-378">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-378">Requirement</span></span>| <span data-ttu-id="f4ff2-379">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-379">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-380">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-380">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-381">1.0</span><span class="sxs-lookup"><span data-stu-id="f4ff2-381">1.0</span></span>|
|[<span data-ttu-id="f4ff2-382">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-382">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-383">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-383">ReadItem</span></span>|
|[<span data-ttu-id="f4ff2-384">Modo Aplicável do Outlook</span><span class="sxs-lookup"><span data-stu-id="f4ff2-384">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-385">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-385">Compose or Read</span></span>|

##### <a name="example"></a><span data-ttu-id="f4ff2-386">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-386">Example</span></span>

```js
Office.context.mailbox.displayMessageForm(messageId);
```

<br>

---
---

#### <a name="displaynewappointmentformparameters"></a><span data-ttu-id="f4ff2-387">displayNewAppointmentForm(parameters)</span><span class="sxs-lookup"><span data-stu-id="f4ff2-387">displayNewAppointmentForm(parameters)</span></span>

<span data-ttu-id="f4ff2-388">Exibe um formulário para criar um compromisso no calendário.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-388">Displays a form for creating a new calendar appointment.</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-389">Não há suporte para esse método no Outlook no iOS ou no Android.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-389">This method is not supported in Outlook on iOS or Android.</span></span>

<span data-ttu-id="f4ff2-p112">O método `displayNewAppointmentForm` abre um formulário que permite ao usuário criar um novo compromisso ou reunião. Se os parâmetros forem especificados, os campos de formulário do compromisso serão preenchidos automaticamente com o conteúdo dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p112">The `displayNewAppointmentForm` method opens a form that enables the user to create a new appointment or meeting. If parameters are specified, the appointment form fields are automatically populated with the contents of the parameters.</span></span>

<span data-ttu-id="f4ff2-p113">No Outlook na Web e em dispositivos móveis, este método sempre exibe um formulário com um campo de participantes. Se você não especificar quaisquer participantes como argumentos de entrada, o método exibe um formulário com um botão **Salvar**. Se você especificar participantes, o formulário inclui os participantes e um botão **Enviar**.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p113">In Outlook on the web and mobile devices, this method always displays a form with an attendees field. If you do not specify any attendees as input arguments, the method displays a form with a **Save** button. If you have specified attendees, the form would include the attendees and a **Send** button.</span></span>

<span data-ttu-id="f4ff2-p114">No cliente avançado do Outlook e no Outlook RT, se você especificar quaisquer participantes ou recursos nos parâmetros `requiredAttendees`, `optionalAttendees`ou `resources`, este método exibirá um formulário de reunião com um botão **Enviar**. Se você não especificar destinatários, este método exibirá um formulário de compromisso com um botão **Salvar e Fechar**.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p114">In the Outlook rich client and Outlook RT, if you specify any attendees or resources in the `requiredAttendees`, `optionalAttendees`, or `resources` parameter, this method displays a meeting form with a **Send** button. If you don't specify any recipients, this method displays an appointment form with a **Save & Close** button.</span></span>

<span data-ttu-id="f4ff2-397">Se qualquer dos parâmetros exceder os limites de tamanho especificados, ou se um nome de parâmetro desconhecido for especificado, ocorre uma exceção.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-397">If any of the parameters exceed the specified size limits, or if an unknown parameter name is specified, an exception is thrown.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-398">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-398">Parameters</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-399">Todos os parâmetros são opcionais.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-399">All parameters are optional.</span></span>

|<span data-ttu-id="f4ff2-400">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-400">Name</span></span>| <span data-ttu-id="f4ff2-401">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-401">Type</span></span>| <span data-ttu-id="f4ff2-402">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-402">Description</span></span>|
|---|---|---|
| `parameters` | <span data-ttu-id="f4ff2-403">Object</span><span class="sxs-lookup"><span data-stu-id="f4ff2-403">Object</span></span> | <span data-ttu-id="f4ff2-404">Um dicionário de parâmetros que descreve o novo compromisso.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-404">A dictionary of parameters describing the new appointment.</span></span> |
| `parameters.requiredAttendees` | <span data-ttu-id="f4ff2-405">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-405">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt;</span></span> | <span data-ttu-id="f4ff2-p115">Uma matriz de cadeias de caracteres que contém os endereços de email ou uma matriz contendo um objeto `EmailAddressDetails` para cada um dos participantes obrigatórios do compromisso. A matriz está limitada a um máximo de 100 entradas.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p115">An array of strings containing the email addresses or an array containing an `EmailAddressDetails` object for each of the required attendees for the appointment. The array is limited to a maximum of 100 entries.</span></span> |
| `parameters.optionalAttendees` | <span data-ttu-id="f4ff2-408">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-408">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt;</span></span> | <span data-ttu-id="f4ff2-p116">Uma matriz de cadeias de caracteres que contém os endereços de email ou uma matriz contendo um objeto `EmailAddressDetails` para cada um dos participantes opcionais do compromisso. A matriz está limitada a um máximo de 100 entradas.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p116">An array of strings containing the email addresses or an array containing an `EmailAddressDetails` object for each of the optional attendees for the appointment. The array is limited to a maximum of 100 entries.</span></span> |
| `parameters.start` | <span data-ttu-id="f4ff2-411">Data</span><span class="sxs-lookup"><span data-stu-id="f4ff2-411">Date</span></span> | <span data-ttu-id="f4ff2-412">Um objeto `Date` que especifica a data e a hora de início do compromisso.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-412">A `Date` object specifying the start date and time of the appointment.</span></span> |
| `parameters.end` | <span data-ttu-id="f4ff2-413">Data</span><span class="sxs-lookup"><span data-stu-id="f4ff2-413">Date</span></span> | <span data-ttu-id="f4ff2-414">Um objeto `Date` que especifica a data e a hora de término do compromisso.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-414">A `Date` object specifying the end date and time of the appointment.</span></span> |
| `parameters.location` | <span data-ttu-id="f4ff2-415">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-415">String</span></span> | <span data-ttu-id="f4ff2-p117">Uma cadeia de caracteres que contém o local do compromisso. A cadeia de caracteres está limitada a um máximo de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p117">A string containing the location of the appointment. The string is limited to a maximum of 255 characters.</span></span> |
| `parameters.resources` | <span data-ttu-id="f4ff2-418">Array.&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-418">Array.&lt;String&gt;</span></span> | <span data-ttu-id="f4ff2-p118">Uma matriz de cadeias de caracteres que contém os recursos necessários para o compromisso. A matriz está limitada a um máximo de 100 entradas.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p118">An array of strings containing the resources required for the appointment. The array is limited to a maximum of 100 entries.</span></span> |
| `parameters.subject` | <span data-ttu-id="f4ff2-421">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-421">String</span></span> | <span data-ttu-id="f4ff2-p119">Uma cadeia de caracteres que contém o assunto do compromisso. A cadeia de caracteres está limitada a um máximo de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p119">A string containing the subject of the appointment. The string is limited to a maximum of 255 characters.</span></span> |
| `parameters.body` | <span data-ttu-id="f4ff2-424">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-424">String</span></span> | <span data-ttu-id="f4ff2-p120">O corpo do compromisso. O conteúdo do corpo está limitado a um tamanho máximo de 32 KB.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p120">The body of the appointment. The body content is limited to a maximum size of 32 KB.</span></span> |

##### <a name="requirements"></a><span data-ttu-id="f4ff2-427">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-427">Requirements</span></span>

|<span data-ttu-id="f4ff2-428">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-428">Requirement</span></span>| <span data-ttu-id="f4ff2-429">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-429">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-430">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-430">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-431">1.0</span><span class="sxs-lookup"><span data-stu-id="f4ff2-431">1.0</span></span>|
|[<span data-ttu-id="f4ff2-432">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-432">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-433">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-433">ReadItem</span></span>|
|[<span data-ttu-id="f4ff2-434">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-434">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-435">Read</span><span class="sxs-lookup"><span data-stu-id="f4ff2-435">Read</span></span>|

##### <a name="example"></a><span data-ttu-id="f4ff2-436">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-436">Example</span></span>

```js
var start = new Date();
var end = new Date();
end.setHours(start.getHours() + 1);

Office.context.mailbox.displayNewAppointmentForm(
  {
    requiredAttendees: ['bob@contoso.com'],
    optionalAttendees: ['sam@contoso.com'],
    start: start,
    end: end,
    location: 'Home',
    resources: ['projector@contoso.com'],
    subject: 'meeting',
    body: 'Hello World!'
  });
```

<br>

---
---

#### <a name="displaynewmessageformparameters"></a><span data-ttu-id="f4ff2-437">displayNewMessageForm (parâmetros)</span><span class="sxs-lookup"><span data-stu-id="f4ff2-437">displayNewMessageForm(parameters)</span></span>

<span data-ttu-id="f4ff2-438">Exibe um formulário para criar uma nova mensagem.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-438">Displays a form for creating a new message.</span></span>

<span data-ttu-id="f4ff2-439">O `displayNewMessageForm` método abre um formulário que permite ao usuário criar uma nova mensagem.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-439">The `displayNewMessageForm` method opens a form that enables the user to create a new message.</span></span> <span data-ttu-id="f4ff2-440">Se os parâmetros forem especificados, os campos de formulário da mensagem serão preenchidos automaticamente com o conteúdo dos parâmetros.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-440">If parameters are specified, the message form fields are automatically populated with the contents of the parameters.</span></span>

<span data-ttu-id="f4ff2-441">Se qualquer dos parâmetros exceder os limites de tamanho especificados, ou se um nome de parâmetro desconhecido for especificado, ocorre uma exceção.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-441">If any of the parameters exceed the specified size limits, or if an unknown parameter name is specified, an exception is thrown.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-442">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-442">Parameters</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-443">Todos os parâmetros são opcionais.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-443">All parameters are optional.</span></span>

|<span data-ttu-id="f4ff2-444">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-444">Name</span></span>| <span data-ttu-id="f4ff2-445">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-445">Type</span></span>| <span data-ttu-id="f4ff2-446">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-446">Description</span></span>|
|---|---|---|
| `parameters` | <span data-ttu-id="f4ff2-447">Objeto</span><span class="sxs-lookup"><span data-stu-id="f4ff2-447">Object</span></span> | <span data-ttu-id="f4ff2-448">Um dicionário de parâmetros que descreve a nova mensagem.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-448">A dictionary of parameters describing the new message.</span></span> |
| `parameters.toRecipients` | <span data-ttu-id="f4ff2-449">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-449">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt;</span></span> | <span data-ttu-id="f4ff2-450">Uma matriz de cadeias de caracteres que contém os endereços de email `EmailAddressDetails` ou uma matriz que contém um objeto para cada um dos destinatários na linha para.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-450">An array of strings containing the email addresses or an array containing an `EmailAddressDetails` object for each of the recipients on the To line.</span></span> <span data-ttu-id="f4ff2-451">A matriz está limitada a um máximo de 100 entradas.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-451">The array is limited to a maximum of 100 entries.</span></span> |
| `parameters.ccRecipients` | <span data-ttu-id="f4ff2-452">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-452">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt;</span></span> | <span data-ttu-id="f4ff2-453">Uma matriz de cadeias de caracteres que contém os endereços de email `EmailAddressDetails` ou uma matriz que contém um objeto para cada um dos destinatários na linha CC.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-453">An array of strings containing the email addresses or an array containing an `EmailAddressDetails` object for each of the recipients on the Cc line.</span></span> <span data-ttu-id="f4ff2-454">A matriz está limitada a um máximo de 100 entradas.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-454">The array is limited to a maximum of 100 entries.</span></span> |
| `parameters.bccRecipients` | <span data-ttu-id="f4ff2-455">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-455">Array.&lt;String&gt; &#124; Array.&lt;[EmailAddressDetails](/javascript/api/outlook/office.emailaddressdetails?view=outlook-js-1.8)&gt;</span></span> | <span data-ttu-id="f4ff2-456">Uma matriz de cadeias de caracteres que contém os endereços de email `EmailAddressDetails` ou uma matriz que contém um objeto para cada um dos destinatários na linha Cco.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-456">An array of strings containing the email addresses or an array containing an `EmailAddressDetails` object for each of the recipients on the Bcc line.</span></span> <span data-ttu-id="f4ff2-457">A matriz está limitada a um máximo de 100 entradas.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-457">The array is limited to a maximum of 100 entries.</span></span> |
| `parameters.subject` | <span data-ttu-id="f4ff2-458">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-458">String</span></span> | <span data-ttu-id="f4ff2-459">Uma cadeia de caracteres que contém o assunto da mensagem.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-459">A string containing the subject of the message.</span></span> <span data-ttu-id="f4ff2-460">A cadeia de caracteres está limitada a um máximo de 255 caracteres.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-460">The string is limited to a maximum of 255 characters.</span></span> |
| `parameters.htmlBody` | <span data-ttu-id="f4ff2-461">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-461">String</span></span> | <span data-ttu-id="f4ff2-462">O corpo HTML da mensagem.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-462">The HTML body of the message.</span></span> <span data-ttu-id="f4ff2-463">O conteúdo do corpo está limitado a um tamanho máximo de 32 KB.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-463">The body content is limited to a maximum size of 32 KB.</span></span> |
| `parameters.attachments` | <span data-ttu-id="f4ff2-464">Array.&lt;Object&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-464">Array.&lt;Object&gt;</span></span> | <span data-ttu-id="f4ff2-465">Uma matriz de objetos JSON que são anexos de arquivo ou item.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-465">An array of JSON objects that are either file or item attachments.</span></span> |
| `parameters.attachments.type` | <span data-ttu-id="f4ff2-466">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-466">String</span></span> | <span data-ttu-id="f4ff2-p127">Indica o tipo de anexo. Deve ser `file` para um anexo de arquivo ou `item` para um anexo de item.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p127">Indicates the type of attachment. Must be `file` for a file attachment or `item` for an item attachment.</span></span> |
| `parameters.attachments.name` | <span data-ttu-id="f4ff2-469">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-469">String</span></span> | <span data-ttu-id="f4ff2-470">Uma cadeia de caracteres que contém o nome do anexo, até 255 caracteres de comprimento.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-470">A string that contains the name of the attachment, up to 255 characters in length.</span></span>|
| `parameters.attachments.url` | <span data-ttu-id="f4ff2-471">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-471">String</span></span> | <span data-ttu-id="f4ff2-p128">Usado somente se `type` estiver definido como `file`. O URI do local para o arquivo.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p128">Only used if `type` is set to `file`. The URI of the location for the file.</span></span> |
| `parameters.attachments.isInline` | <span data-ttu-id="f4ff2-474">Booliano</span><span class="sxs-lookup"><span data-stu-id="f4ff2-474">Boolean</span></span> | <span data-ttu-id="f4ff2-p129">Usado somente se `type` estiver definido como `file`. Se for `true`, indicará que o anexo será mostrado embutido no corpo da mensagem e não deverá ser exibido na lista de anexos.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p129">Only used if `type` is set to `file`. If `true`, indicates that the attachment will be shown inline in the message body, and should not be displayed in the attachment list.</span></span> |
| `parameters.attachments.itemId` | <span data-ttu-id="f4ff2-477">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="f4ff2-477">String</span></span> | <span data-ttu-id="f4ff2-478">Usado somente se `type` estiver definido como `item`.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-478">Only used if `type` is set to `item`.</span></span> <span data-ttu-id="f4ff2-479">A ID do item do EWS do email existente que você deseja anexar à nova mensagem.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-479">The EWS item id of the existing e-mail you want to attach to the new message.</span></span> <span data-ttu-id="f4ff2-480">Isso é uma cadeia de até 100 caracteres.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-480">This is a string up to 100 characters.</span></span> |


##### <a name="requirements"></a><span data-ttu-id="f4ff2-481">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-481">Requirements</span></span>

|<span data-ttu-id="f4ff2-482">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-482">Requirement</span></span>| <span data-ttu-id="f4ff2-483">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-483">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-484">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-484">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-485">1.6</span><span class="sxs-lookup"><span data-stu-id="f4ff2-485">1.6</span></span> |
|[<span data-ttu-id="f4ff2-486">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-486">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-487">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-487">ReadItem</span></span>|
|[<span data-ttu-id="f4ff2-488">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-488">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-489">Read</span><span class="sxs-lookup"><span data-stu-id="f4ff2-489">Read</span></span>|

##### <a name="example"></a><span data-ttu-id="f4ff2-490">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-490">Example</span></span>

```js
Office.context.mailbox.displayNewMessageForm(
  {
    // Copy the To line from current item.
    toRecipients: Office.context.mailbox.item.to,
    ccRecipients: ['sam@contoso.com'],
    subject: 'Outlook add-ins are cool!',
    htmlBody: 'Hello <b>World</b>!<br/><img src="cid:image.png"></i>',
    attachments: [
      {
        type: 'file',
        name: 'image.png',
        url: 'http://contoso.com/image.png',
        isInline: true
      }
    ]
  });
```

<br>

---
---

#### <a name="getcallbacktokenasyncoptions-callback"></a><span data-ttu-id="f4ff2-491">getCallbackTokenAsync([options], callback)</span><span class="sxs-lookup"><span data-stu-id="f4ff2-491">getCallbackTokenAsync([options], callback)</span></span>

<span data-ttu-id="f4ff2-492">Obtém uma cadeia de caracteres que contém um token usado para chamar APIs REST ou Serviços Web do Exchange.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-492">Gets a string that contains a token used to call REST APIs or Exchange Web Services.</span></span>

<span data-ttu-id="f4ff2-p131">O método `getCallbackTokenAsync` faz uma chamada assíncrona para obter um token opaco do Exchange Server que hospeda a caixa de correio do usuário. A vida útil do token de retorno de chamada é de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p131">The `getCallbackTokenAsync` method makes an asynchronous call to get an opaque token from the Exchange Server that hosts the user's mailbox. The lifetime of the callback token is 5 minutes.</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-495">É recomendável que suplementos usem as APIs REST em vez dos Serviços Web do Exchange sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-495">It is recommended that add-ins use the REST APIs instead of Exchange Web Services whenever possible.</span></span>

<span data-ttu-id="f4ff2-496">Chamar o método `getCallbackTokenAsync` no modo de leitura requer um nível de permissão mínimo de **ReadItem**.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-496">Calling the `getCallbackTokenAsync` method in read mode requires a minimum permission level of **ReadItem**.</span></span>

<span data-ttu-id="f4ff2-497">Chamar `getCallbackTokenAsync` no modo redigir exige que você tenha salvo o item.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-497">Calling `getCallbackTokenAsync` in compose mode requires you to have saved the item.</span></span> <span data-ttu-id="f4ff2-498">O método [`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) requer um nível de permissão mínimo de **ReadWriteItem**.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-498">The [`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) method requires a minimum permission level of **ReadWriteItem**.</span></span>

<span data-ttu-id="f4ff2-499">**Tokens REST**</span><span class="sxs-lookup"><span data-stu-id="f4ff2-499">**REST Tokens**</span></span>

<span data-ttu-id="f4ff2-p133">Quando um token REST é solicitado (`options.isRest = true`), o token resultante não funcionará para autenticar as chamadas dos Serviços Web do Exchange. O token será limitado em escopo para acesso somente leitura no item atual e seus anexos, a menos que o suplemento tenha especificado a permissão [`ReadWriteMailbox`](/outlook/add-ins/understanding-outlook-add-in-permissions#readwritemailbox-permission) em seu manifesto. Se a permissão `ReadWriteMailbox` tiver sido especificada, o token resultante concederá acesso de leitura/gravação a email, calendário e contatos, incluindo a capacidade de enviar emails.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p133">When a REST token is requested (`options.isRest = true`), the resulting token will not work to authenticate Exchange Web Services calls. The token will be limited in scope to read-only access to the current item and its attachments, unless the add-in has specified the [`ReadWriteMailbox`](/outlook/add-ins/understanding-outlook-add-in-permissions#readwritemailbox-permission) permission in its manifest. If the `ReadWriteMailbox` permission is specified, the resulting token will grant read/write access to mail, calendar, and contacts, including the ability to send mail.</span></span>

<span data-ttu-id="f4ff2-503">O suplemento deve usar a propriedade `restUrl` para determinar a URL correta a ser usada ao fazer chamadas da API REST.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-503">The add-in should use the `restUrl` property to determine the correct URL to use when making REST API calls.</span></span>

<span data-ttu-id="f4ff2-504">**Tokens EWS**</span><span class="sxs-lookup"><span data-stu-id="f4ff2-504">**EWS Tokens**</span></span>

<span data-ttu-id="f4ff2-p134">Quando um token EWS é solicitado (`options.isRest = false`), o token resultante não funcionará para autenticar as chamadas de API REST. O token será limitado em escopo para acessar o item atual.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p134">When an EWS token is requested (`options.isRest = false`), the resulting token will not work to authenticate REST API calls. The token will be limited in scope to accessing the current item.</span></span>

<span data-ttu-id="f4ff2-507">O suplemento deve usar a propriedade `ewsUrl` para determinar a URL correta a ser usada ao fazer chamadas de EWS.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-507">The add-in should use the `ewsUrl` property to determine the correct URL to use when making EWS calls.</span></span>

<span data-ttu-id="f4ff2-508">Você pode passar o token e também um identificador de anexo ou um identificador de item a um sistema de terceiros.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-508">You can pass both the token and either an attachment identifier or item identifier to a third-party system.</span></span> <span data-ttu-id="f4ff2-509">O sistema de terceiros usa o token como um token de autorização de portador para chamar a operação [GetAttachment](/exchange/client-developer/web-service-reference/getattachment-operation) dos serviços Web do Exchange (EWS) ou a operação [GetItem](/exchange/client-developer/web-service-reference/getitem-operation) para recuperar um anexo ou item.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-509">The third-party system uses the token as a bearer authorization token to call the Exchange Web Services (EWS) [GetAttachment](/exchange/client-developer/web-service-reference/getattachment-operation) operation or [GetItem](/exchange/client-developer/web-service-reference/getitem-operation) operation to retrieve an attachment or item.</span></span> <span data-ttu-id="f4ff2-510">Por exemplo, você pode criar um serviço remoto para [obter anexos do item selecionado](/outlook/add-ins/get-attachments-of-an-outlook-item).</span><span class="sxs-lookup"><span data-stu-id="f4ff2-510">For example, you can create a remote service to [get attachments from the selected item](/outlook/add-ins/get-attachments-of-an-outlook-item).</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-511">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-511">Parameters</span></span>

|<span data-ttu-id="f4ff2-512">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-512">Name</span></span>| <span data-ttu-id="f4ff2-513">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-513">Type</span></span>| <span data-ttu-id="f4ff2-514">Atributos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-514">Attributes</span></span>| <span data-ttu-id="f4ff2-515">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-515">Description</span></span>|
|---|---|---|---|
| `options` | <span data-ttu-id="f4ff2-516">Object</span><span class="sxs-lookup"><span data-stu-id="f4ff2-516">Object</span></span> | <span data-ttu-id="f4ff2-517">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-517">&lt;optional&gt;</span></span> | <span data-ttu-id="f4ff2-518">Um objeto literal que contém uma ou mais das propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-518">An object literal that contains one or more of the following properties.</span></span> |
| `options.isRest` | <span data-ttu-id="f4ff2-519">Booliano</span><span class="sxs-lookup"><span data-stu-id="f4ff2-519">Boolean</span></span> |  <span data-ttu-id="f4ff2-520">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-520">&lt;optional&gt;</span></span> | <span data-ttu-id="f4ff2-p136">Determina se o token fornecido será usado para as APIs REST do Outlook ou Serviços Web do Exchange. O valor padrão é `false`.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p136">Determines if the token provided will be used for the Outlook REST APIs or Exchange Web Services. Default value is `false`.</span></span> |
| `options.asyncContext` | <span data-ttu-id="f4ff2-523">Objeto</span><span class="sxs-lookup"><span data-stu-id="f4ff2-523">Object</span></span> |  <span data-ttu-id="f4ff2-524">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-524">&lt;optional&gt;</span></span> | <span data-ttu-id="f4ff2-525">Quaisquer dados de estado que são passados ao método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-525">Any state data that is passed to the asynchronous method.</span></span> |
|`callback`| <span data-ttu-id="f4ff2-526">function</span><span class="sxs-lookup"><span data-stu-id="f4ff2-526">function</span></span>||<span data-ttu-id="f4ff2-527">Quando o método for concluído, a função passada ao parâmetro `callback` é chamada com um único parâmetro, `asyncResult`, que é um objeto [`AsyncResult`](/javascript/api/office/office.asyncresult).</span><span class="sxs-lookup"><span data-stu-id="f4ff2-527">When the method completes, the function passed in the `callback` parameter is called with a single parameter, `asyncResult`, which is an [`AsyncResult`](/javascript/api/office/office.asyncresult) object.</span></span><br/><br/><span data-ttu-id="f4ff2-528">O token é fornecido como uma cadeia de caracteres na propriedade `asyncResult.value`.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-528">The token is provided as a string in the `asyncResult.value` property.</span></span><br><br><span data-ttu-id="f4ff2-529">Se ocorreu um erro, as propriedades`asyncResult.error` e `asyncResult.diagnostics` podem fornecer informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-529">If there was an error, the `asyncResult.error` and `asyncResult.diagnostics` properties may provide additional information.</span></span>|

##### <a name="errors"></a><span data-ttu-id="f4ff2-530">Erros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-530">Errors</span></span>

|<span data-ttu-id="f4ff2-531">Código de erro</span><span class="sxs-lookup"><span data-stu-id="f4ff2-531">Error code</span></span>|<span data-ttu-id="f4ff2-532">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-532">Description</span></span>|
|------------|-------------|
|`HTTPRequestFailure`|<span data-ttu-id="f4ff2-533">A solicitação falhou.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-533">The request has failed.</span></span> <span data-ttu-id="f4ff2-534">Examine o objeto de diagnóstico para o código de erro HTTP.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-534">Please look at the diagnostics object for the HTTP error code.</span></span>|
|`InternalServerError`|<span data-ttu-id="f4ff2-535">O servidor do Exchange retornou um erro.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-535">The Exchange server returned an error.</span></span> <span data-ttu-id="f4ff2-536">Para saber mais, confira o objeto de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-536">Please look at the diagnostics object for more information.</span></span>|
|`NetworkError`|<span data-ttu-id="f4ff2-537">O usuário não está mais conectado à rede.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-537">The user is no longer connected to the network.</span></span> <span data-ttu-id="f4ff2-538">Verifique sua conexão de rede e tente novamente.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-538">Please check your network connection and try again.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-539">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-539">Requirements</span></span>

|<span data-ttu-id="f4ff2-540">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-540">Requirement</span></span>| <span data-ttu-id="f4ff2-541">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-541">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-542">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-542">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-543">1,5</span><span class="sxs-lookup"><span data-stu-id="f4ff2-543">1.5</span></span> |
|[<span data-ttu-id="f4ff2-544">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-544">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-545">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-545">ReadItem</span></span>|
|[<span data-ttu-id="f4ff2-546">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-546">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-547">Redação e leitura</span><span class="sxs-lookup"><span data-stu-id="f4ff2-547">Compose and read</span></span>|

##### <a name="example"></a><span data-ttu-id="f4ff2-548">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-548">Example</span></span>

```js
function getCallbackToken() {
  var options = {
    isRest: true,
    asyncContext: { message: 'Hello World!' }
  };

  Office.context.mailbox.getCallbackTokenAsync(options, cb);
}

function cb(asyncResult) {
  var token = asyncResult.value;
}
```

<br>

---
---

#### <a name="getcallbacktokenasynccallback-usercontext"></a><span data-ttu-id="f4ff2-549">getCallbackTokenAsync(callback, [userContext])</span><span class="sxs-lookup"><span data-stu-id="f4ff2-549">getCallbackTokenAsync(callback, [userContext])</span></span>

<span data-ttu-id="f4ff2-550">Obtém uma cadeia de caracteres que contém um token usado para obter um anexo ou um item de um Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-550">Gets a string that contains a token used to get an attachment or item from an Exchange Server.</span></span>

<span data-ttu-id="f4ff2-p140">O método `getCallbackTokenAsync` faz uma chamada assíncrona para obter um token opaco do Exchange Server que hospeda a caixa de correio do usuário. A vida útil do token de retorno de chamada é de 5 minutos.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p140">The `getCallbackTokenAsync` method makes an asynchronous call to get an opaque token from the Exchange Server that hosts the user's mailbox. The lifetime of the callback token is 5 minutes.</span></span>

<span data-ttu-id="f4ff2-553">Você pode passar o token e também um identificador de anexo ou um identificador de item a um sistema de terceiros.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-553">You can pass both the token and either an attachment identifier or item identifier to a third-party system.</span></span> <span data-ttu-id="f4ff2-554">O sistema de terceiros usa o token como portador da autorização para chamar as operações [GetAttachment](/exchange/client-developer/web-service-reference/getattachment-operation) ou [GetItem](/exchange/client-developer/web-service-reference/getitem-operation) dos Serviços Web do Exchange (EWS) para retornar um anexo ou item.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-554">The third-party system uses the token as a bearer authorization token to call the Exchange Web Services (EWS) [GetAttachment](/exchange/client-developer/web-service-reference/getattachment-operation) operation or [GetItem](/exchange/client-developer/web-service-reference/getitem-operation) operation to return an attachment or item.</span></span> <span data-ttu-id="f4ff2-555">Por exemplo, você pode criar um serviço remoto para [obter anexos do item selecionado](/outlook/add-ins/get-attachments-of-an-outlook-item).</span><span class="sxs-lookup"><span data-stu-id="f4ff2-555">For example, you can create a remote service to [get attachments from the selected item](/outlook/add-ins/get-attachments-of-an-outlook-item).</span></span>

<span data-ttu-id="f4ff2-556">Chamar o método `getCallbackTokenAsync` no modo de leitura requer um nível de permissão mínimo de **ReadItem**.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-556">Calling the `getCallbackTokenAsync` method in read mode requires a minimum permission level of **ReadItem**.</span></span>

<span data-ttu-id="f4ff2-557">Chamar `getCallbackTokenAsync` no modo redigir exige que você tenha salvo o item.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-557">Calling `getCallbackTokenAsync` in compose mode requires you to have saved the item.</span></span> <span data-ttu-id="f4ff2-558">O método [`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) requer um nível de permissão mínimo de **ReadWriteItem**.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-558">The [`saveAsync`](Office.context.mailbox.item.md#saveasyncoptions-callback) method requires a minimum permission level of **ReadWriteItem**.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-559">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-559">Parameters</span></span>

|<span data-ttu-id="f4ff2-560">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-560">Name</span></span>| <span data-ttu-id="f4ff2-561">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-561">Type</span></span>| <span data-ttu-id="f4ff2-562">Atributos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-562">Attributes</span></span>| <span data-ttu-id="f4ff2-563">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-563">Description</span></span>|
|---|---|---|---|
|`callback`| <span data-ttu-id="f4ff2-564">function</span><span class="sxs-lookup"><span data-stu-id="f4ff2-564">function</span></span>||<span data-ttu-id="f4ff2-565">Quando o método for concluído, a função passada ao parâmetro `callback` é chamada com um único parâmetro, `asyncResult`, que é um objeto [`AsyncResult`](/javascript/api/office/office.asyncresult).</span><span class="sxs-lookup"><span data-stu-id="f4ff2-565">When the method completes, the function passed in the `callback` parameter is called with a single parameter, `asyncResult`, which is an [`AsyncResult`](/javascript/api/office/office.asyncresult) object.</span></span><br/><br/><span data-ttu-id="f4ff2-566">O token é fornecido como uma cadeia de caracteres na propriedade `asyncResult.value`.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-566">The token is provided as a string in the `asyncResult.value` property.</span></span><br><br><span data-ttu-id="f4ff2-567">Se ocorreu um erro, as propriedades`asyncResult.error` e `asyncResult.diagnostics` podem fornecer informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-567">If there was an error, the `asyncResult.error` and `asyncResult.diagnostics` properties may provide additional information.</span></span>|
|`userContext`| <span data-ttu-id="f4ff2-568">Objeto</span><span class="sxs-lookup"><span data-stu-id="f4ff2-568">Object</span></span>| <span data-ttu-id="f4ff2-569">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-569">&lt;optional&gt;</span></span>|<span data-ttu-id="f4ff2-570">Quaisquer dados de estado que são passados ao método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-570">Any state data that is passed to the asynchronous method.</span></span>|

##### <a name="errors"></a><span data-ttu-id="f4ff2-571">Erros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-571">Errors</span></span>

|<span data-ttu-id="f4ff2-572">Código de erro</span><span class="sxs-lookup"><span data-stu-id="f4ff2-572">Error code</span></span>|<span data-ttu-id="f4ff2-573">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-573">Description</span></span>|
|------------|-------------|
|`HTTPRequestFailure`|<span data-ttu-id="f4ff2-574">A solicitação falhou.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-574">The request has failed.</span></span> <span data-ttu-id="f4ff2-575">Examine o objeto de diagnóstico para o código de erro HTTP.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-575">Please look at the diagnostics object for the HTTP error code.</span></span>|
|`InternalServerError`|<span data-ttu-id="f4ff2-576">O servidor do Exchange retornou um erro.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-576">The Exchange server returned an error.</span></span> <span data-ttu-id="f4ff2-577">Para saber mais, confira o objeto de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-577">Please look at the diagnostics object for more information.</span></span>|
|`NetworkError`|<span data-ttu-id="f4ff2-578">O usuário não está mais conectado à rede.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-578">The user is no longer connected to the network.</span></span> <span data-ttu-id="f4ff2-579">Verifique sua conexão de rede e tente novamente.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-579">Please check your network connection and try again.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-580">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-580">Requirements</span></span>

|<span data-ttu-id="f4ff2-581">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-581">Requirement</span></span>|||
|---|---|---|
|[<span data-ttu-id="f4ff2-582">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-582">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-583">1.0</span><span class="sxs-lookup"><span data-stu-id="f4ff2-583">1.0</span></span> | <span data-ttu-id="f4ff2-584">1.3</span><span class="sxs-lookup"><span data-stu-id="f4ff2-584">1.3</span></span> |
|[<span data-ttu-id="f4ff2-585">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-585">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-586">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-586">ReadItem</span></span> | <span data-ttu-id="f4ff2-587">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-587">ReadItem</span></span> |
|[<span data-ttu-id="f4ff2-588">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-588">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-589">Read</span><span class="sxs-lookup"><span data-stu-id="f4ff2-589">Read</span></span> | <span data-ttu-id="f4ff2-590">Escrever</span><span class="sxs-lookup"><span data-stu-id="f4ff2-590">Compose</span></span> |

##### <a name="example"></a><span data-ttu-id="f4ff2-591">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-591">Example</span></span>

```js
function getCallbackToken() {
  Office.context.mailbox.getCallbackTokenAsync(cb);
}

function cb(asyncResult) {
  var token = asyncResult.value;
}
```

<br>

---
---

#### <a name="getuseridentitytokenasynccallback-usercontext"></a><span data-ttu-id="f4ff2-592">getUserIdentityTokenAsync(callback, [userContext])</span><span class="sxs-lookup"><span data-stu-id="f4ff2-592">getUserIdentityTokenAsync(callback, [userContext])</span></span>

<span data-ttu-id="f4ff2-593">Obtém um símbolo que identifica o usuário e o suplemento do Office.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-593">Gets a token identifying the user and the Office Add-in.</span></span>

<span data-ttu-id="f4ff2-594">O método `getUserIdentityTokenAsync` retorna um token que pode ser utilizado para identificar e [autenticar o suplemento e o usuário com um sistema de terceiros](/outlook/add-ins/authentication).</span><span class="sxs-lookup"><span data-stu-id="f4ff2-594">The `getUserIdentityTokenAsync` method returns a token that you can use to identify and [authenticate the add-in and user with a third-party system](/outlook/add-ins/authentication).</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-595">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-595">Parameters</span></span>

|<span data-ttu-id="f4ff2-596">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-596">Name</span></span>| <span data-ttu-id="f4ff2-597">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-597">Type</span></span>| <span data-ttu-id="f4ff2-598">Atributos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-598">Attributes</span></span>| <span data-ttu-id="f4ff2-599">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-599">Description</span></span>|
|---|---|---|---|
|`callback`| <span data-ttu-id="f4ff2-600">function</span><span class="sxs-lookup"><span data-stu-id="f4ff2-600">function</span></span>||<span data-ttu-id="f4ff2-601">Quando o método for concluído, a função passada ao parâmetro `callback` é chamada com um único parâmetro, `asyncResult`, que é um objeto [`AsyncResult`](/javascript/api/office/office.asyncresult).</span><span class="sxs-lookup"><span data-stu-id="f4ff2-601">When the method completes, the function passed in the `callback` parameter is called with a single parameter, `asyncResult`, which is an [`AsyncResult`](/javascript/api/office/office.asyncresult) object.</span></span><br/><br/><span data-ttu-id="f4ff2-602">O token é fornecido como uma cadeia de caracteres na propriedade `asyncResult.value`.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-602">The token is provided as a string in the `asyncResult.value` property.</span></span><br><br><span data-ttu-id="f4ff2-603">Se ocorreu um erro, as propriedades`asyncResult.error` e `asyncResult.diagnostics` podem fornecer informações adicionais.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-603">If there was an error, the `asyncResult.error` and `asyncResult.diagnostics` properties may provide additional information.</span></span>|
|`userContext`| <span data-ttu-id="f4ff2-604">Objeto</span><span class="sxs-lookup"><span data-stu-id="f4ff2-604">Object</span></span>| <span data-ttu-id="f4ff2-605">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-605">&lt;optional&gt;</span></span>|<span data-ttu-id="f4ff2-606">Quaisquer dados de estado que são passados ao método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-606">Any state data that is passed to the asynchronous method.</span></span>|

##### <a name="errors"></a><span data-ttu-id="f4ff2-607">Erros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-607">Errors</span></span>

|<span data-ttu-id="f4ff2-608">Código de erro</span><span class="sxs-lookup"><span data-stu-id="f4ff2-608">Error code</span></span>|<span data-ttu-id="f4ff2-609">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-609">Description</span></span>|
|------------|-------------|
|`HTTPRequestFailure`|<span data-ttu-id="f4ff2-610">A solicitação falhou.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-610">The request has failed.</span></span> <span data-ttu-id="f4ff2-611">Examine o objeto de diagnóstico para o código de erro HTTP.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-611">Please look at the diagnostics object for the HTTP error code.</span></span>|
|`InternalServerError`|<span data-ttu-id="f4ff2-612">O servidor do Exchange retornou um erro.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-612">The Exchange server returned an error.</span></span> <span data-ttu-id="f4ff2-613">Para saber mais, confira o objeto de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-613">Please look at the diagnostics object for more information.</span></span>|
|`NetworkError`|<span data-ttu-id="f4ff2-614">O usuário não está mais conectado à rede.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-614">The user is no longer connected to the network.</span></span> <span data-ttu-id="f4ff2-615">Verifique sua conexão de rede e tente novamente.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-615">Please check your network connection and try again.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-616">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-616">Requirements</span></span>

|<span data-ttu-id="f4ff2-617">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-617">Requirement</span></span>| <span data-ttu-id="f4ff2-618">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-618">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-619">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-619">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-620">1.0</span><span class="sxs-lookup"><span data-stu-id="f4ff2-620">1.0</span></span>|
|[<span data-ttu-id="f4ff2-621">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-621">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-622">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-622">ReadItem</span></span>|
|[<span data-ttu-id="f4ff2-623">Modo Aplicável do Outlook</span><span class="sxs-lookup"><span data-stu-id="f4ff2-623">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-624">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-624">Compose or Read</span></span>|

##### <a name="example"></a><span data-ttu-id="f4ff2-625">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-625">Example</span></span>

```js
function getIdentityToken() {
  Office.context.mailbox.getUserIdentityTokenAsync(cb);
}

function cb(asyncResult) {
  var token = asyncResult.value;
}
```

<br>

---
---

#### <a name="makeewsrequestasyncdata-callback-usercontext"></a><span data-ttu-id="f4ff2-626">makeEwsRequestAsync(data, callback, [userContext])</span><span class="sxs-lookup"><span data-stu-id="f4ff2-626">makeEwsRequestAsync(data, callback, [userContext])</span></span>

<span data-ttu-id="f4ff2-627">Faz uma solicitação assíncrona em um serviço dos EWS (Serviços Web do Exchange) no servidor Exchange que hospeda a caixa de correio do usuário.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-627">Makes an asynchronous request to an Exchange Web Services (EWS) service on the Exchange server that hosts the user’s mailbox.</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-628">Esse método não tem suporte nas seguintes situações.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-628">This method is not supported in the following scenarios.</span></span>
> - <span data-ttu-id="f4ff2-629">No Outlook no iOS ou no Android</span><span class="sxs-lookup"><span data-stu-id="f4ff2-629">In Outlook on iOS or Android</span></span>
> - <span data-ttu-id="f4ff2-630">Quando o suplemento é carregado em uma caixa de correio do Gmail</span><span class="sxs-lookup"><span data-stu-id="f4ff2-630">When the add-in is loaded in a Gmail mailbox</span></span>
> 
> <span data-ttu-id="f4ff2-631">Nesses casos, os suplementos devem [usar as APIs REST](/outlook/add-ins/use-rest-api) para acessar a caixa de correio do usuário.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-631">In these cases, add-ins should [use REST APIs](/outlook/add-ins/use-rest-api) to access the user's mailbox instead.</span></span>

<span data-ttu-id="f4ff2-632">O método `makeEwsRequestAsync` envia uma solicitação do EWS em nome do suplemento ao Exchange.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-632">The `makeEwsRequestAsync` method sends an EWS request on behalf of the add-in to Exchange.</span></span> <span data-ttu-id="f4ff2-633">Consulte [Chamar serviços Web de um suplemento do Outlook](/outlook/add-ins/web-services#ews-operations-that-add-ins-support) para obter uma lista das operações de EWS compatíveis.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-633">See [Call web services from an Outlook add-in](/outlook/add-ins/web-services#ews-operations-that-add-ins-support) for a list of the supported EWS operations.</span></span>

<span data-ttu-id="f4ff2-634">Não é possível solicitar os itens associados da pasta com o método `makeEwsRequestAsync`.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-634">You cannot request Folder Associated Items with the `makeEwsRequestAsync` method.</span></span>

<span data-ttu-id="f4ff2-635">A solicitação XML deve especificar a codificação UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-635">The XML request must specify UTF-8 encoding.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
```

<span data-ttu-id="f4ff2-p150">O suplemento deve ter a permissão **ReadWriteMailbox** para usar o método `makeEwsRequestAsync`. Para saber mais sobre como usar a permissão **ReadWriteMailbox** e as operações do EWS que você pode chamar com o método `makeEwsRequestAsync`, confira [Especificar permissões para acesso de suplemento de email na caixa de correio do usuário](/outlook/add-ins/understanding-outlook-add-in-permissions).</span><span class="sxs-lookup"><span data-stu-id="f4ff2-p150">Your add-in must have the **ReadWriteMailbox** permission to use the `makeEwsRequestAsync` method. For information about using the **ReadWriteMailbox** permission and the EWS operations that you can call with the `makeEwsRequestAsync` method, see [Specify permissions for mail add-in access to the user's mailbox](/outlook/add-ins/understanding-outlook-add-in-permissions).</span></span>

> [!NOTE]
> <span data-ttu-id="f4ff2-638">O administrador do servidor deve definir `OAuthAuthentication` como true no diretório do EWS para o Servidor de Acesso para Cliente a fim de habilitar o método `makeEwsRequestAsync` a realizar solicitações do EWS.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-638">The server administrator must set `OAuthAuthentication` to true on the Client Access Server EWS directory to enable the `makeEwsRequestAsync` method to make EWS requests.</span></span>

##### <a name="version-differences"></a><span data-ttu-id="f4ff2-639">Diferenças de versão</span><span class="sxs-lookup"><span data-stu-id="f4ff2-639">Version differences</span></span>

<span data-ttu-id="f4ff2-640">Ao usar o método `makeEwsRequestAsync` nos aplicativos de email em execução em versões do Outlook anteriores à 15.0.4535.1004, é preciso definir o valor de codificação como `ISO-8859-1`.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-640">When you use the `makeEwsRequestAsync` method in mail apps running in Outlook versions earlier than version 15.0.4535.1004, you should set the encoding value to `ISO-8859-1`.</span></span>

```xml
<?xml version="1.0" encoding="iso-8859-1"?>
```

<span data-ttu-id="f4ff2-641">Não é necessário definir o valor de codificação quando o aplicativo de email estiver em execução no Outlook na Web.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-641">You do not need to set the encoding value when your mail app is running in Outlook on the web.</span></span> <span data-ttu-id="f4ff2-642">Você pode determinar se o seu aplicativo de email está em execução no Outlook na Web ou em um cliente de desktop usando a propriedade Mailbox. Diagnostics. hostName.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-642">You can determine whether your mail app is running in Outlook on the web or a desktop client by using the mailbox.diagnostics.hostName property.</span></span> <span data-ttu-id="f4ff2-643">Você pode determinar que versão do Outlook está em execução usando a propriedade mailbox.diagnostics.hostVersion.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-643">You can determine what version of Outlook is running by using the mailbox.diagnostics.hostVersion property.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-644">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-644">Parameters</span></span>

|<span data-ttu-id="f4ff2-645">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-645">Name</span></span>| <span data-ttu-id="f4ff2-646">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-646">Type</span></span>| <span data-ttu-id="f4ff2-647">Atributos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-647">Attributes</span></span>| <span data-ttu-id="f4ff2-648">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-648">Description</span></span>|
|---|---|---|---|
|`data`| <span data-ttu-id="f4ff2-649">String</span><span class="sxs-lookup"><span data-stu-id="f4ff2-649">String</span></span>||<span data-ttu-id="f4ff2-650">A solicitação do EWS.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-650">The EWS request.</span></span>|
|`callback`| <span data-ttu-id="f4ff2-651">function</span><span class="sxs-lookup"><span data-stu-id="f4ff2-651">function</span></span>||<span data-ttu-id="f4ff2-652">Quando o método for concluído, a função passada ao parâmetro `callback` é chamada com um único parâmetro, `asyncResult`, que é um objeto [`AsyncResult`](/javascript/api/office/office.asyncresult).</span><span class="sxs-lookup"><span data-stu-id="f4ff2-652">When the method completes, the function passed in the `callback` parameter is called with a single parameter, `asyncResult`, which is an [`AsyncResult`](/javascript/api/office/office.asyncresult) object.</span></span><br/><br/><span data-ttu-id="f4ff2-653">O resultado XML da chamada do EWS é fornecido como uma cadeia de caracteres na propriedade `asyncResult.value`.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-653">The XML result of the EWS call is provided as a string in the `asyncResult.value` property.</span></span> <span data-ttu-id="f4ff2-654">Se o resultado exceder 1 MB de tamanho, será exibida uma mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-654">If the result exceeds 1 MB in size, an error message is returned instead.</span></span>|
|`userContext`| <span data-ttu-id="f4ff2-655">Objeto</span><span class="sxs-lookup"><span data-stu-id="f4ff2-655">Object</span></span>| <span data-ttu-id="f4ff2-656">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-656">&lt;optional&gt;</span></span>|<span data-ttu-id="f4ff2-657">Quaisquer dados de estado que são passados ao método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-657">Any state data that is passed to the asynchronous method.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-658">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-658">Requirements</span></span>

|<span data-ttu-id="f4ff2-659">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-659">Requirement</span></span>| <span data-ttu-id="f4ff2-660">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-660">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-661">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-661">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-662">1.0</span><span class="sxs-lookup"><span data-stu-id="f4ff2-662">1.0</span></span>|
|[<span data-ttu-id="f4ff2-663">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-663">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-664">ReadWriteMailbox</span><span class="sxs-lookup"><span data-stu-id="f4ff2-664">ReadWriteMailbox</span></span>|
|[<span data-ttu-id="f4ff2-665">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-665">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-666">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-666">Compose or Read</span></span>|

##### <a name="example"></a><span data-ttu-id="f4ff2-667">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-667">Example</span></span>

<span data-ttu-id="f4ff2-668">O exemplo a seguir chama `makeEwsRequestAsync` para usar a operação `GetItem` para obter o assunto de um item.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-668">The following example calls `makeEwsRequestAsync` to use the `GetItem` operation to get the subject of an item.</span></span>

```js
function getSubjectRequest(id) {
  // Return a GetItem operation request for the subject of the specified item.
  var request =
    '<?xml version="1.0" encoding="utf-8"?>' +
    '<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"' +
    '               xmlns:xsd="http://www.w3.org/2001/XMLSchema"' +
    '               xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"' +
    '               xmlns:t="http://schemas.microsoft.com/exchange/services/2006/types">' +
    '  <soap:Header>' +
    '    <RequestServerVersion Version="Exchange2013" xmlns="http://schemas.microsoft.com/exchange/services/2006/types" soap:mustUnderstand="0" />' +
    '  </soap:Header>' +
    '  <soap:Body>' +
    '    <GetItem xmlns="http://schemas.microsoft.com/exchange/services/2006/messages">' +
    '      <ItemShape>' +
    '        <t:BaseShape>IdOnly</t:BaseShape>' +
    '        <t:AdditionalProperties>' +
    '            <t:FieldURI FieldURI="item:Subject"/>' +
    '        </t:AdditionalProperties>' +
    '      </ItemShape>' +
    '      <ItemIds><t:ItemId Id="' + id + '"/></ItemIds>' +
    '    </GetItem>' +
    '  </soap:Body>' +
    '</soap:Envelope>';

  return request;
}

function sendRequest() {
  // Create a local variable that contains the mailbox.
  Office.context.mailbox.makeEwsRequestAsync(
    getSubjectRequest(mailbox.item.itemId), callback);
}

function callback(asyncResult)  {
  var result = asyncResult.value;
  var context = asyncResult.asyncContext;

  // Process the returned response here.
}
```

<br>

---
---

#### <a name="removehandlerasynceventtype-options-callback"></a><span data-ttu-id="f4ff2-669">removeHandlerAsync(eventType, handler, [options], [callback])</span><span class="sxs-lookup"><span data-stu-id="f4ff2-669">removeHandlerAsync(eventType, [options], [callback])</span></span>

<span data-ttu-id="f4ff2-670">Remove um manipulador de eventos para um tipo de evento com suporte.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-670">Removes the event handlers for a supported event type.</span></span>

<span data-ttu-id="f4ff2-671">Atualmente, os tipos de eventos com `Office.EventType.ItemChanged` suporte `Office.EventType.OfficeThemeChanged`são e.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-671">Currently, the supported event types are `Office.EventType.ItemChanged` and `Office.EventType.OfficeThemeChanged`.</span></span>

##### <a name="parameters"></a><span data-ttu-id="f4ff2-672">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4ff2-672">Parameters</span></span>

| <span data-ttu-id="f4ff2-673">Nome</span><span class="sxs-lookup"><span data-stu-id="f4ff2-673">Name</span></span> | <span data-ttu-id="f4ff2-674">Tipo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-674">Type</span></span> | <span data-ttu-id="f4ff2-675">Atributos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-675">Attributes</span></span> | <span data-ttu-id="f4ff2-676">Descrição</span><span class="sxs-lookup"><span data-stu-id="f4ff2-676">Description</span></span> |
|---|---|---|---|
| `eventType` | [<span data-ttu-id="f4ff2-677">Office.EventType</span><span class="sxs-lookup"><span data-stu-id="f4ff2-677">Office.EventType</span></span>](office.md#eventtype-string) || <span data-ttu-id="f4ff2-678">O evento que deve revogar o manipulador.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-678">The event that should revoke the handler.</span></span> |
| `options` | <span data-ttu-id="f4ff2-679">Objeto</span><span class="sxs-lookup"><span data-stu-id="f4ff2-679">Object</span></span> | <span data-ttu-id="f4ff2-680">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-680">&lt;optional&gt;</span></span> | <span data-ttu-id="f4ff2-681">Um objeto literal que contém uma ou mais das propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-681">An object literal that contains one or more of the following properties.</span></span> |
| `options.asyncContext` | <span data-ttu-id="f4ff2-682">Objeto</span><span class="sxs-lookup"><span data-stu-id="f4ff2-682">Object</span></span> | <span data-ttu-id="f4ff2-683">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-683">&lt;optional&gt;</span></span> | <span data-ttu-id="f4ff2-684">Os desenvolvedores podem fornecer qualquer objeto que desejarem acessar no método de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="f4ff2-684">Developers can provide any object they wish to access in the callback method.</span></span> |
| `callback` | <span data-ttu-id="f4ff2-685">function</span><span class="sxs-lookup"><span data-stu-id="f4ff2-685">function</span></span>| <span data-ttu-id="f4ff2-686">&lt;opcional&gt;</span><span class="sxs-lookup"><span data-stu-id="f4ff2-686">&lt;optional&gt;</span></span>|<span data-ttu-id="f4ff2-687">Quando o método for concluído, a função passada ao parâmetro `callback` é chamada com um único parâmetro, `asyncResult`, que é um objeto [`AsyncResult`](/javascript/api/office/office.asyncresult).</span><span class="sxs-lookup"><span data-stu-id="f4ff2-687">When the method completes, the function passed in the `callback` parameter is called with a single parameter, `asyncResult`, which is an [`AsyncResult`](/javascript/api/office/office.asyncresult) object.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="f4ff2-688">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4ff2-688">Requirements</span></span>

|<span data-ttu-id="f4ff2-689">Requisito</span><span class="sxs-lookup"><span data-stu-id="f4ff2-689">Requirement</span></span>| <span data-ttu-id="f4ff2-690">Valor</span><span class="sxs-lookup"><span data-stu-id="f4ff2-690">Value</span></span>|
|---|---|
|[<span data-ttu-id="f4ff2-691">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="f4ff2-691">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="f4ff2-692">1,5</span><span class="sxs-lookup"><span data-stu-id="f4ff2-692">1.5</span></span> |
|[<span data-ttu-id="f4ff2-693">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="f4ff2-693">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="f4ff2-694">ReadItem</span><span class="sxs-lookup"><span data-stu-id="f4ff2-694">ReadItem</span></span> |
|[<span data-ttu-id="f4ff2-695">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="f4ff2-695">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="f4ff2-696">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="f4ff2-696">Compose or Read</span></span>|