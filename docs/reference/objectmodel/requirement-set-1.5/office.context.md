# <a name="context"></a><span data-ttu-id="ad18e-101">context</span><span class="sxs-lookup"><span data-stu-id="ad18e-101">context</span></span>

### <a name="officeofficemdcontext"></a><span data-ttu-id="ad18e-102">.context do [Office](Office.md)</span><span class="sxs-lookup"><span data-stu-id="ad18e-102">[Office](Office.md).context</span></span>

<span data-ttu-id="ad18e-p101">O namespace do Office.context fornece interfaces compartilhadas que são usadas pelos suplementos em todos os aplicativos do Office. Esta listagem documenta somente as interfaces usadas pelos suplementos do Outlook. Para obter uma listagem completa do namespace Office.context, confira a [Referência sobre o Office.context na API compartilhada](/javascript/api/office/office.context).</span><span class="sxs-lookup"><span data-stu-id="ad18e-p101">The Office.context namespace provides shared interfaces that are used by add-ins in all of the Office apps. This listing documents only those interfaces that are used by Outlook add-ins. For a full listing of the Office.context namespace, see the [Office.context reference in the Shared API](/javascript/api/office/office.context).</span></span>

##### <a name="requirements"></a><span data-ttu-id="ad18e-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad18e-105">Requirements</span></span>

|<span data-ttu-id="ad18e-106">Requisito</span><span class="sxs-lookup"><span data-stu-id="ad18e-106">Requirement</span></span>| <span data-ttu-id="ad18e-107">Valor</span><span class="sxs-lookup"><span data-stu-id="ad18e-107">Value</span></span>|
|---|---|
|[<span data-ttu-id="ad18e-108">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="ad18e-108">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="ad18e-109">1.0</span><span class="sxs-lookup"><span data-stu-id="ad18e-109">1.0</span></span>|
|[<span data-ttu-id="ad18e-110">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="ad18e-110">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="ad18e-111">Redigir ou ler</span><span class="sxs-lookup"><span data-stu-id="ad18e-111">Compose or read</span></span>|

##### <a name="members-and-methods"></a><span data-ttu-id="ad18e-112">Membros e métodos</span><span class="sxs-lookup"><span data-stu-id="ad18e-112">Members and methods</span></span>

| <span data-ttu-id="ad18e-113">Membro</span><span class="sxs-lookup"><span data-stu-id="ad18e-113">Member</span></span> | <span data-ttu-id="ad18e-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="ad18e-114">Type</span></span> |
|--------|------|
| [<span data-ttu-id="ad18e-115">displayLanguage</span><span class="sxs-lookup"><span data-stu-id="ad18e-115">displayLanguage</span></span>](#displaylanguage-string) | <span data-ttu-id="ad18e-116">Membro</span><span class="sxs-lookup"><span data-stu-id="ad18e-116">Member</span></span> |
| [<span data-ttu-id="ad18e-117">officeTheme</span><span class="sxs-lookup"><span data-stu-id="ad18e-117">officeTheme</span></span>](#officetheme-object) | <span data-ttu-id="ad18e-118">Membro</span><span class="sxs-lookup"><span data-stu-id="ad18e-118">Member</span></span> |
| [<span data-ttu-id="ad18e-119">roamingSettings</span><span class="sxs-lookup"><span data-stu-id="ad18e-119">roamingSettings</span></span>](#roamingsettings-roamingsettingsjavascriptapioutlook15officeroamingsettings) | <span data-ttu-id="ad18e-120">Membro</span><span class="sxs-lookup"><span data-stu-id="ad18e-120">Member</span></span> |

### <a name="namespaces"></a><span data-ttu-id="ad18e-121">Namespaces</span><span class="sxs-lookup"><span data-stu-id="ad18e-121">Namespaces</span></span>

<span data-ttu-id="ad18e-122">[mailbox](office.context.mailbox.md): fornece acesso ao modelo de objeto de suplemento do Outlook para o Microsoft Outlook e o Microsoft Outlook na Web.</span><span class="sxs-lookup"><span data-stu-id="ad18e-122">[mailbox](office.context.mailbox.md): Provides access to the Outlook Add-in object model for Microsoft Outlook and Microsoft Outlook on the web.</span></span>

### <a name="members"></a><span data-ttu-id="ad18e-123">Membros</span><span class="sxs-lookup"><span data-stu-id="ad18e-123">Members</span></span>

####  <a name="displaylanguage-string"></a><span data-ttu-id="ad18e-124">displayLanguage :String</span><span class="sxs-lookup"><span data-stu-id="ad18e-124">displayLanguage :String</span></span>

<span data-ttu-id="ad18e-125">Obtém a localidade (idioma) no formato de marca de linguagem RFC 1766 especificado pelo usuário para a interface do usuário do aplicativo host do Office.</span><span class="sxs-lookup"><span data-stu-id="ad18e-125">Gets the locale (language) in RFC 1766 Language tag format specified by the user for the UI of the Office host application.</span></span>

<span data-ttu-id="ad18e-126">O valor `displayLanguage` reflete a configuração atual do **Idioma de Exibição** especificada em **Arquivo > Opções > Idioma** no aplicativo host do Office.</span><span class="sxs-lookup"><span data-stu-id="ad18e-126">The `displayLanguage` value reflects the current **Display Language** setting specified with **File > Options > Language** in the Office host application.</span></span>

##### <a name="type"></a><span data-ttu-id="ad18e-127">Tipo:</span><span class="sxs-lookup"><span data-stu-id="ad18e-127">Type:</span></span>

*   <span data-ttu-id="ad18e-128">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="ad18e-128">String</span></span>

##### <a name="requirements"></a><span data-ttu-id="ad18e-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad18e-129">Requirements</span></span>

|<span data-ttu-id="ad18e-130">Requisito</span><span class="sxs-lookup"><span data-stu-id="ad18e-130">Requirement</span></span>| <span data-ttu-id="ad18e-131">Valor</span><span class="sxs-lookup"><span data-stu-id="ad18e-131">Value</span></span>|
|---|---|
|[<span data-ttu-id="ad18e-132">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="ad18e-132">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="ad18e-133">1.0</span><span class="sxs-lookup"><span data-stu-id="ad18e-133">1.0</span></span>|
|[<span data-ttu-id="ad18e-134">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="ad18e-134">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="ad18e-135">Redigir ou ler</span><span class="sxs-lookup"><span data-stu-id="ad18e-135">Compose or read</span></span>|

##### <a name="example"></a><span data-ttu-id="ad18e-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ad18e-136">Example</span></span>

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

####  <a name="officetheme-object"></a><span data-ttu-id="ad18e-137">officeTheme :Object</span><span class="sxs-lookup"><span data-stu-id="ad18e-137">officeTheme :Object</span></span>

<span data-ttu-id="ad18e-138">Fornece acesso às propriedades de cores de temas do Office.</span><span class="sxs-lookup"><span data-stu-id="ad18e-138">Provides access to the properties for Office theme colors.</span></span>

> [!NOTE]
> <span data-ttu-id="ad18e-139">Este membro não é suportado no Outlook para iOS ou no Outlook para Android.</span><span class="sxs-lookup"><span data-stu-id="ad18e-139">Note: This member is not supported in Outlook for iOS or Outlook for Android.</span></span>

<span data-ttu-id="ad18e-p102">Usando as cores de tema do Office, você pode coordenar o esquema de cores do seu suplemento com o tema atual do Office, selecionado pelo usuário em **Arquivo > Conta do Office > Tema da interface de usuário do Office**, que é aplicado a todos os aplicativos host do Office. Usar cores de tema do Office é apropriado para suplementos de painel de tarefas e email.</span><span class="sxs-lookup"><span data-stu-id="ad18e-p102">Using Office theme colors let's you coordinate the color scheme of your add-in with the current Office theme selected by the user with **File > Office Account > Office Theme UI**, which is applied across all Office host applications. Using Office theme colors is appropriate for mail and task pane add-ins.</span></span>

##### <a name="type"></a><span data-ttu-id="ad18e-142">Tipo:</span><span class="sxs-lookup"><span data-stu-id="ad18e-142">Type:</span></span>

*   <span data-ttu-id="ad18e-143">Objeto</span><span class="sxs-lookup"><span data-stu-id="ad18e-143">Object</span></span>

##### <a name="properties"></a><span data-ttu-id="ad18e-144">Propriedades:</span><span class="sxs-lookup"><span data-stu-id="ad18e-144">Properties:</span></span>

|<span data-ttu-id="ad18e-145">Nome</span><span class="sxs-lookup"><span data-stu-id="ad18e-145">Name</span></span>| <span data-ttu-id="ad18e-146">Tipo</span><span class="sxs-lookup"><span data-stu-id="ad18e-146">Type</span></span>| <span data-ttu-id="ad18e-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad18e-147">Description</span></span>|
|---|---|---|
|`bodyBackgroundColor`| <span data-ttu-id="ad18e-148">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="ad18e-148">String</span></span>|<span data-ttu-id="ad18e-149">Obtém a cor do plano de fundo do corpo do tema do Office como um trio de cores hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="ad18e-149">Gets the Office theme body background color as a hexadecimal color triplet.</span></span>|
|`bodyForegroundColor`| <span data-ttu-id="ad18e-150">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="ad18e-150">String</span></span>|<span data-ttu-id="ad18e-151">Obtém a cor de primeiro plano do corpo do tema do Office como um trio de cores hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="ad18e-151">Gets the Office theme body foreground color as a hexadecimal color triplet.</span></span>|
|`controlBackgroundColor`| <span data-ttu-id="ad18e-152">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="ad18e-152">String</span></span>|<span data-ttu-id="ad18e-153">Obtém o tema do Office para controlar a cor do plano de fundo como um trio de cores hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="ad18e-153">Gets the Office theme control background color as a hexadecimal color triplet.</span></span>|
|`controlForegroundColor`| <span data-ttu-id="ad18e-154">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="ad18e-154">String</span></span>|<span data-ttu-id="ad18e-155">Obtém a cor de controle do corpo do tema do Office como um trio de cores hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="ad18e-155">Gets the Office theme body control color as a hexadecimal color triplet.</span></span>|

##### <a name="requirements"></a><span data-ttu-id="ad18e-156">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad18e-156">Requirements</span></span>

|<span data-ttu-id="ad18e-157">Requisito</span><span class="sxs-lookup"><span data-stu-id="ad18e-157">Requirement</span></span>| <span data-ttu-id="ad18e-158">Valor</span><span class="sxs-lookup"><span data-stu-id="ad18e-158">Value</span></span>|
|---|---|
|[<span data-ttu-id="ad18e-159">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="ad18e-159">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="ad18e-160">1.3</span><span class="sxs-lookup"><span data-stu-id="ad18e-160">1.3</span></span>|
|[<span data-ttu-id="ad18e-161">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="ad18e-161">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="ad18e-162">Redigir ou ler</span><span class="sxs-lookup"><span data-stu-id="ad18e-162">Compose or read</span></span>|

##### <a name="example"></a><span data-ttu-id="ad18e-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ad18e-163">Example</span></span>

```js
function applyOfficeTheme(){
  // Get office theme colors.
  var bodyBackgroundColor = Office.context.officeTheme.bodyBackgroundColor;
  var bodyForegroundColor = Office.context.officeTheme.bodyForegroundColor;
  var controlBackgroundColor = Office.context.officeTheme.controlBackgroundColor
  var controlForegroundColor = Office.context.officeTheme.controlForegroundColor;

  // Apply body background color to a CSS class.
  $('.body').css('background-color', bodyBackgroundColor);
}
```

####  <a name="roamingsettings-roamingsettingsjavascriptapioutlook15officeroamingsettings"></a><span data-ttu-id="ad18e-164">roamingSettings:[RoamingSettings](/javascript/api/outlook_1_5/office.RoamingSettings)</span><span class="sxs-lookup"><span data-stu-id="ad18e-164">roamingSettings :[RoamingSettings](/javascript/api/outlook_1_5/office.RoamingSettings)</span></span>

<span data-ttu-id="ad18e-165">Obtém um objeto que representa as configurações personalizadas ou o estado de um suplemento de email salvo na caixa de correio de um usuário.</span><span class="sxs-lookup"><span data-stu-id="ad18e-165">Gets an object that represents the custom settings or state of a mail add-in saved to a user's mailbox.</span></span>

<span data-ttu-id="ad18e-166">O objeto `RoamingSettings` permite armazenar e acessar dados para um suplemento de email armazenado na caixa de correio de um usuário, para que ele esteja disponível para esse complemento quando estiver sendo executado em qualquer aplicativo cliente host usado para acessar essa caixa de correio.</span><span class="sxs-lookup"><span data-stu-id="ad18e-166">The `RoamingSettings` object lets you store and access data for a mail add-in that is stored in a user's mailbox, so that is available to that add-in when it is running from any host client application used to access that mailbox.</span></span>

##### <a name="type"></a><span data-ttu-id="ad18e-167">Tipo:</span><span class="sxs-lookup"><span data-stu-id="ad18e-167">Type:</span></span>

*   [<span data-ttu-id="ad18e-168">RoamingSettings</span><span class="sxs-lookup"><span data-stu-id="ad18e-168">RoamingSettings</span></span>](/javascript/api/outlook_1_5/office.RoamingSettings)

##### <a name="requirements"></a><span data-ttu-id="ad18e-169">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ad18e-169">Requirements</span></span>

|<span data-ttu-id="ad18e-170">Requisito</span><span class="sxs-lookup"><span data-stu-id="ad18e-170">Requirement</span></span>| <span data-ttu-id="ad18e-171">Valor</span><span class="sxs-lookup"><span data-stu-id="ad18e-171">Value</span></span>|
|---|---|
|[<span data-ttu-id="ad18e-172">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="ad18e-172">Minimum mailbox requirement set version</span></span>](/javascript/office/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="ad18e-173">1.0</span><span class="sxs-lookup"><span data-stu-id="ad18e-173">1.0</span></span>|
|[<span data-ttu-id="ad18e-174">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="ad18e-174">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="ad18e-175">Restrito</span><span class="sxs-lookup"><span data-stu-id="ad18e-175">Restricted</span></span>|
|[<span data-ttu-id="ad18e-176">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="ad18e-176">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="ad18e-177">Redigir ou ler</span><span class="sxs-lookup"><span data-stu-id="ad18e-177">Compose or read</span></span>|