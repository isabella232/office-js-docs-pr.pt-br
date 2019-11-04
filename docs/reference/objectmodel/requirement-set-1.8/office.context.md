---
title: Office. Context – conjunto de requisitos 1,8
description: ''
ms.date: 10/31/2019
localization_priority: Normal
ms.openlocfilehash: 791c88b3b6bc69834ca5635fe1021b9d11029629
ms.sourcegitcommit: e989096f3d19761bf8477c585cde20b3f8e0b90d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "37902122"
---
# <a name="context"></a><span data-ttu-id="b50f5-102">context</span><span class="sxs-lookup"><span data-stu-id="b50f5-102">context</span></span>

### <a name="officeofficemdcontext"></a><span data-ttu-id="b50f5-103">[Office](Office.md).context</span><span class="sxs-lookup"><span data-stu-id="b50f5-103">[Office](Office.md).context</span></span>

<span data-ttu-id="b50f5-104">O namespace Office.context fornece interfaces compartilhadas que são usadas pelos suplementos em todos os aplicativos do Office.</span><span class="sxs-lookup"><span data-stu-id="b50f5-104">The Office.context namespace provides shared interfaces that are used by add-ins in all of the Office apps.</span></span> <span data-ttu-id="b50f5-105">Esta listagem documenta apenas as interfaces usados pelos suplementos do Outlook. Para uma listagem completa do namespace Office.context, veja a referência [Office.context na API Comum](/javascript/api/office/office.context).</span><span class="sxs-lookup"><span data-stu-id="b50f5-105">This listing documents only those interfaces that are used by Outlook add-ins. For a full listing of the Office.context namespace, see the [Office.context reference in the Common API](/javascript/api/office/office.context).</span></span>

##### <a name="requirements"></a><span data-ttu-id="b50f5-106">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b50f5-106">Requirements</span></span>

|<span data-ttu-id="b50f5-107">Requisito</span><span class="sxs-lookup"><span data-stu-id="b50f5-107">Requirement</span></span>| <span data-ttu-id="b50f5-108">Valor</span><span class="sxs-lookup"><span data-stu-id="b50f5-108">Value</span></span>|
|---|---|
|[<span data-ttu-id="b50f5-109">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="b50f5-109">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="b50f5-110">1.0</span><span class="sxs-lookup"><span data-stu-id="b50f5-110">1.0</span></span>|
|[<span data-ttu-id="b50f5-111">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="b50f5-111">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="b50f5-112">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="b50f5-112">Compose or Read</span></span>|

##### <a name="members-and-methods"></a><span data-ttu-id="b50f5-113">Membros e métodos</span><span class="sxs-lookup"><span data-stu-id="b50f5-113">Members and methods</span></span>

| <span data-ttu-id="b50f5-114">Membro</span><span class="sxs-lookup"><span data-stu-id="b50f5-114">Member</span></span> | <span data-ttu-id="b50f5-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="b50f5-115">Type</span></span> |
|--------|------|
| [<span data-ttu-id="b50f5-116">displayLanguage</span><span class="sxs-lookup"><span data-stu-id="b50f5-116">displayLanguage</span></span>](#displaylanguage-string) | <span data-ttu-id="b50f5-117">Member</span><span class="sxs-lookup"><span data-stu-id="b50f5-117">Member</span></span> |
| [<span data-ttu-id="b50f5-118">roamingSettings</span><span class="sxs-lookup"><span data-stu-id="b50f5-118">roamingSettings</span></span>](#roamingsettings-roamingsettings) | <span data-ttu-id="b50f5-119">Membro</span><span class="sxs-lookup"><span data-stu-id="b50f5-119">Member</span></span> |

### <a name="namespaces"></a><span data-ttu-id="b50f5-120">Namespaces</span><span class="sxs-lookup"><span data-stu-id="b50f5-120">Namespaces</span></span>

<span data-ttu-id="b50f5-121">[Mailbox](office.context.mailbox.md): fornece acesso ao modelo de objeto do suplemento do Outlook para o Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="b50f5-121">[mailbox](office.context.mailbox.md): Provides access to the Outlook add-in object model for Microsoft Outlook.</span></span>

### <a name="members"></a><span data-ttu-id="b50f5-122">Members</span><span class="sxs-lookup"><span data-stu-id="b50f5-122">Members</span></span>

#### <a name="displaylanguage-string"></a><span data-ttu-id="b50f5-123">displayLanguage: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="b50f5-123">displayLanguage: String</span></span>

<span data-ttu-id="b50f5-124">Obtém a localidade (idioma) no formato de marca de idioma RFC 1766 especificado pelo usuário para a interface do usuário do aplicativo host do Office.</span><span class="sxs-lookup"><span data-stu-id="b50f5-124">Gets the locale (language) in RFC 1766 Language tag format specified by the user for the UI of the Office host application.</span></span>

<span data-ttu-id="b50f5-125">O valor `displayLanguage` reflete a configuração atual de **Display Language** especificada com **Arquivo > Opções > Idioma** no aplicativo host do Office.</span><span class="sxs-lookup"><span data-stu-id="b50f5-125">The `displayLanguage` value reflects the current **Display Language** setting specified with **File > Options > Language** in the Office host application.</span></span>

##### <a name="type"></a><span data-ttu-id="b50f5-126">Tipo</span><span class="sxs-lookup"><span data-stu-id="b50f5-126">Type</span></span>

*   <span data-ttu-id="b50f5-127">String</span><span class="sxs-lookup"><span data-stu-id="b50f5-127">String</span></span>

##### <a name="requirements"></a><span data-ttu-id="b50f5-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b50f5-128">Requirements</span></span>

|<span data-ttu-id="b50f5-129">Requisito</span><span class="sxs-lookup"><span data-stu-id="b50f5-129">Requirement</span></span>| <span data-ttu-id="b50f5-130">Valor</span><span class="sxs-lookup"><span data-stu-id="b50f5-130">Value</span></span>|
|---|---|
|[<span data-ttu-id="b50f5-131">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="b50f5-131">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="b50f5-132">1.0</span><span class="sxs-lookup"><span data-stu-id="b50f5-132">1.0</span></span>|
|[<span data-ttu-id="b50f5-133">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="b50f5-133">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="b50f5-134">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="b50f5-134">Compose or Read</span></span>|

##### <a name="example"></a><span data-ttu-id="b50f5-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b50f5-135">Example</span></span>

```js
function sayHelloWithDisplayLanguage() {
  var myDisplayLanguage = Office.context.displayLanguage;
  switch (myDisplayLanguage) {
    case 'en-US':
      write('Hello!');
      break;
    case 'en-NZ':
      write('G\'day mate!');
      break;
  }
}

// Function that writes to a div with id='message' on the page.
function write(message){
  document.getElementById('message').innerText += message;
}
```

<br>

---
---

#### <a name="roamingsettings-roamingsettingsjavascriptapioutlookofficeroamingsettingsviewoutlook-js-18"></a><span data-ttu-id="b50f5-136">roamingSettings: [roamingSettings](/javascript/api/outlook/office.RoamingSettings?view=outlook-js-1.8)</span><span class="sxs-lookup"><span data-stu-id="b50f5-136">roamingSettings: [RoamingSettings](/javascript/api/outlook/office.RoamingSettings?view=outlook-js-1.8)</span></span>

<span data-ttu-id="b50f5-137">Obtém um objeto que representa as configurações personalizadas ou o estado de um suplemento de email do Outlook salvos na caixa de correio do usuário.</span><span class="sxs-lookup"><span data-stu-id="b50f5-137">Gets an object that represents the custom settings or state of a mail add-in saved to a user's mailbox.</span></span>

<span data-ttu-id="b50f5-138">O objeto `RoamingSettings` permite armazenar e acessar os dados de um suplemento de email que está armazenado na caixa de correio do usuário, para que fiquem disponíveis para esse suplemento quando ele for executado em qualquer aplicativo host de cliente usado para acessar essa caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="b50f5-138">The `RoamingSettings` object lets you store and access data for a mail add-in that is stored in a user's mailbox, so that is available to that add-in when it is running from any host client application used to access that mailbox.</span></span>

##### <a name="type"></a><span data-ttu-id="b50f5-139">Tipo</span><span class="sxs-lookup"><span data-stu-id="b50f5-139">Type</span></span>

*   [<span data-ttu-id="b50f5-140">RoamingSettings</span><span class="sxs-lookup"><span data-stu-id="b50f5-140">RoamingSettings</span></span>](/javascript/api/outlook/office.RoamingSettings?view=outlook-js-1.8)

##### <a name="requirements"></a><span data-ttu-id="b50f5-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b50f5-141">Requirements</span></span>

|<span data-ttu-id="b50f5-142">Requisito</span><span class="sxs-lookup"><span data-stu-id="b50f5-142">Requirement</span></span>| <span data-ttu-id="b50f5-143">Valor</span><span class="sxs-lookup"><span data-stu-id="b50f5-143">Value</span></span>|
|---|---|
|[<span data-ttu-id="b50f5-144">Versão do conjunto de requisitos mínimos da caixa de correio</span><span class="sxs-lookup"><span data-stu-id="b50f5-144">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="b50f5-145">1.0</span><span class="sxs-lookup"><span data-stu-id="b50f5-145">1.0</span></span>|
|[<span data-ttu-id="b50f5-146">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="b50f5-146">Minimum permission level</span></span>](/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="b50f5-147">Restrito</span><span class="sxs-lookup"><span data-stu-id="b50f5-147">Restricted</span></span>|
|[<span data-ttu-id="b50f5-148">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="b50f5-148">Applicable Outlook mode</span></span>](/outlook/add-ins/#extension-points)| <span data-ttu-id="b50f5-149">Escrever ou Ler</span><span class="sxs-lookup"><span data-stu-id="b50f5-149">Compose or Read</span></span>|