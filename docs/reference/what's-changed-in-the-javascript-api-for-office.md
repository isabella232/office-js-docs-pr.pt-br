# <a name="whats-changed-in-the-javascript-api-for-office"></a><span data-ttu-id="f28d2-101">O que mudou na API JavaScript para Office</span><span class="sxs-lookup"><span data-stu-id="f28d2-101">What's changed in the JavaScript API for Office</span></span>

<span data-ttu-id="f28d2-102">A API JavaScript para Office é atualizada periodicamente com objetos, métodos, propriedades, eventos e enumerações novos e atualizados para estender a funcionalidade dos seus suplementos do Office. Use os links abaixo para ver os membros da API novos e atualizados.</span><span class="sxs-lookup"><span data-stu-id="f28d2-102">The JavaScript API for Office is periodically updated with new and updated objects, methods, properties, events and enumerations to extend the functionality of your Office Add-ins. Use the links below to see the new and updated API members.</span></span>

<span data-ttu-id="f28d2-103">Para desenvolver suplementos usando novos membros da API, você precisa [atualizar os arquivos da API JavaScript para Office em seu projeto](https://docs.microsoft.com/office/dev/add-ins/develop/update-your-javascript-api-for-office-and-manifest-schema-version).</span><span class="sxs-lookup"><span data-stu-id="f28d2-103">To develop add-ins using new API members, you need to [update the JavaScript API for Office files in your project](https://docs.microsoft.com/office/dev/add-ins/develop/update-your-javascript-api-for-office-and-manifest-schema-version).</span></span>

<span data-ttu-id="f28d2-104">Para ver todos os membros da API, incluindo aqueles que não sofreram alterações nas atualizações anteriores, confira [API JavaScript para Office](javascript-api-for-office.md).</span><span class="sxs-lookup"><span data-stu-id="f28d2-104">To view all API members including those that are unchanged from previous updates, see [JavaScript API for Office](javascript-api-for-office.md).</span></span>

## <a name="new-and-updated-apis"></a><span data-ttu-id="f28d2-105">APIs novas e atualizadas</span><span class="sxs-lookup"><span data-stu-id="f28d2-105">New and updated APIs</span></span>

### <a name="new-and-updated-objects"></a><span data-ttu-id="f28d2-106">Objetos novos e atualizados</span><span class="sxs-lookup"><span data-stu-id="f28d2-106">New and updated objects</span></span>

|<span data-ttu-id="f28d2-107">**Objeto**</span><span class="sxs-lookup"><span data-stu-id="f28d2-107">**Object**</span></span>|<span data-ttu-id="f28d2-108">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="f28d2-108">**Description**</span></span>|<span data-ttu-id="f28d2-109">**Versão adicionada ou atualizada**</span><span class="sxs-lookup"><span data-stu-id="f28d2-109">**Version added or updated**</span></span>|
|:-----|:-----|:-----|
|`Item`|<span data-ttu-id="f28d2-110">Atualizações e adições para:</span><span class="sxs-lookup"><span data-stu-id="f28d2-110">Updates and additions to:</span></span><br><ul><li><p><span data-ttu-id="f28d2-111">Os métodos `getSelectedDataAsync` e `setSelectedDataAsync` para dar suporte à seleção do usuário e substituí-lo no assunto e no corpo de uma mensagem ou um compromisso.</span><span class="sxs-lookup"><span data-stu-id="f28d2-111">The getSelectedDataAsync`getSelectedDataAsync` and setSelectedDataAsync`setSelectedDataAsync` methods to support getting the user's selection and overwriting it in the subject and body  of a message or appointment.</span></span></p></li><li><p><span data-ttu-id="f28d2-112">Os métodos `displayReplyAllForm` e `displayReplyForm` para dar suporte à adição de um anexo ao formulário de resposta de um compromisso.</span><span class="sxs-lookup"><span data-stu-id="f28d2-112">The displayReplyAllForm`displayReplyAllForm` and displayReplyForm`displayReplyForm` methods to support adding an attachment to the reply form of an appointment.</span></span></p></li></ul>|<span data-ttu-id="f28d2-113">Mailbox 1.2</span><span class="sxs-lookup"><span data-stu-id="f28d2-113">Mailbox 1.2</span></span>|
|`Item`|<span data-ttu-id="f28d2-114">Atualizado para incluir campos e métodos para criação de suplementos do Outlook no modo de composição.</span><span class="sxs-lookup"><span data-stu-id="f28d2-114">Updated to include methods and fields for creating compose mode Outlook add-ins.</span></span> |<span data-ttu-id="f28d2-115">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-115">1.1</span></span>|
|`Binding`|<span data-ttu-id="f28d2-116">Atualizado para dar suporte à associação de tabela em suplementos de conteúdo para o Access.</span><span class="sxs-lookup"><span data-stu-id="f28d2-116">Updated to support table binding in content add-ins for Access.</span></span>|<span data-ttu-id="f28d2-117">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-117">1.1</span></span>|
|`Bindings`|<span data-ttu-id="f28d2-118">Atualizado para dar suporte à associação de tabela em suplementos de conteúdo para o Access.</span><span class="sxs-lookup"><span data-stu-id="f28d2-118">Updated to support table binding in content add-ins for Access.</span></span>|<span data-ttu-id="f28d2-119">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-119">1.1</span></span>|
|`Body`|<span data-ttu-id="f28d2-120">Adicionado para permitir a criação e a edição do corpo de uma mensagem ou compromisso em suplementos do Outlook no modo de composição.</span><span class="sxs-lookup"><span data-stu-id="f28d2-120">Added to enable creating and editing the body of a message or appointment in compose mode Outlook add-ins.</span></span>|<span data-ttu-id="f28d2-121">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-121">1.1</span></span>|
|`Document`|<span data-ttu-id="f28d2-122">Atualizações e adições para:</span><span class="sxs-lookup"><span data-stu-id="f28d2-122">Updates and additions to:</span></span> <ul><li><p><span data-ttu-id="f28d2-123">Suporte às propriedades <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js" target="_blank">mode</a>, <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js#settings" target="_blank">settings</a> e <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js" target="_blank">url</a> em suplementos de conteúdo para o Access.</span><span class="sxs-lookup"><span data-stu-id="f28d2-123">Support <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js" target="_blank">mode</a>, <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js#settings" target="_blank">settings</a>, and <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js" target="_blank">url</a> properties in content add-ins for Access.</span></span></p></li><li><p><span data-ttu-id="f28d2-124">Receba o documento como PDF com o método <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js#getfileasync-filetype--options--callback-" target="_blank">getFileAsync</a> em suplementos para Word e PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="f28d2-124">Get the document as PDF with the <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js#getfileasync-filetype--options--callback-" target="_blank">getFileAsync</a> method in add-ins for PowerPoint and Word.</span></span></p></li><li><p><span data-ttu-id="f28d2-125">Obtenha as propriedades de arquivo com o método <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js#getfilepropertiesasync-options--callback-" target="_blank">getFileProperties</a> em suplementos para Excel, PowerPoint e Word.</span><span class="sxs-lookup"><span data-stu-id="f28d2-125">Get file properties with the <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js#getfilepropertiesasync-options--callback-" target="_blank">getFileProperties</a> method in add-ins for Excel, PowerPoint, and Word.</span></span></p></li><li><p><span data-ttu-id="f28d2-126">Navegue até locais e objetos dentro do documento com o método <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js#gotobyidasync-id--gototype--options--callback-" target="_blank">goToByIdAsync</a> em suplementos para Excel e PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="f28d2-126">Navigate to locations and objects within the document with the <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js#gotobyidasync-id--gototype--options--callback-" target="_blank">goToByIdAsync</a> method in add-ins for Excel and PowerPoint.</span></span></p></li><li><p><span data-ttu-id="f28d2-127">Obtenha a identificação, o título e o índice dos slides selecionados com o método <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js#getselecteddataasync-coerciontype--options--callback-" target="_blank">getSelectedDataAsync</a> (ao especificar a nova enumeração <span class="keyword">Office.CoercionType.SlideRange</span><a href="https://docs.microsoft.com/javascript/api/office/office.coerciontype?view=office-js" target="_blank">coercionType</a> enum) em suplementos do PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="f28d2-127">Get the id, title, and index for selected slides with the <a href="https://docs.microsoft.com/javascript/api/office/office.document?view=office-js#getselecteddataasync-coerciontype--options--callback-" target="_blank">getSelectedDataAsync</a> method (when you specify the new <span class="keyword">Office.CoercionType.SlideRange</span><a href="https://docs.microsoft.com/javascript/api/office/office.coerciontype?view=office-js" target="_blank">coercionType</a> enum) in add-ins for PowerPoint.</span></span></p></li></ul>|<span data-ttu-id="f28d2-128">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-128">1.1</span></span>|
|`Location`|<span data-ttu-id="f28d2-129">Adicionado a fim de permitir a configuração do local de um compromisso em suplementos do Outlook no modo de composição.</span><span class="sxs-lookup"><span data-stu-id="f28d2-129">Added to enable setting the location of an appointment in compose mode Outlook add-ins.</span></span>|<span data-ttu-id="f28d2-130">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-130">1.1</span></span>|
|`Office`|<span data-ttu-id="f28d2-131">Método de seleção atualizado para oferecer suporte à obtenção de associações em suplementos de conteúdo para Access.</span><span class="sxs-lookup"><span data-stu-id="f28d2-131">Updated the select method to support getting bindings in content add-ins for Access.</span></span>|<span data-ttu-id="f28d2-132">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-132">1.1</span></span>|
|`Recipients`|<span data-ttu-id="f28d2-133">Adicionado para permitir a obtenção e a configuração dos destinatários de uma mensagem ou de um compromisso no modo de composição.</span><span class="sxs-lookup"><span data-stu-id="f28d2-133">Added to enable getting and setting the recipients of a message or appointment in compose mode.</span></span>|<span data-ttu-id="f28d2-134">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-134">1.1</span></span>|
|`Settings`|<span data-ttu-id="f28d2-135">Atualizado para oferecer suporte à criação de configurações personalizadas em suplementos de conteúdo para o Access.</span><span class="sxs-lookup"><span data-stu-id="f28d2-135">Updated to support creating custom settings in content add-ins for Access.</span></span>|<span data-ttu-id="f28d2-136">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-136">1.1</span></span>|
|`Subject`|<span data-ttu-id="f28d2-137">Adicionado para permitir a obtenção e a configuração do assunto de uma mensagem ou de um compromisso em suplementos do Outlook no modo de composição.</span><span class="sxs-lookup"><span data-stu-id="f28d2-137">Added to enable getting and setting the subject of a message or appointment in compose mode Outlook add-ins.</span></span>|<span data-ttu-id="f28d2-138">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-138">1.1</span></span>|
|`Time`|<span data-ttu-id="f28d2-139">Adicionado para permitir a obtenção e a configuração das horas de início e de término de um compromisso em suplementos do Outlook no modo de composição.</span><span class="sxs-lookup"><span data-stu-id="f28d2-139">Added to enable getting and setting the start and end time of an appointment in compose mode Outlook add-ins.</span></span>|<span data-ttu-id="f28d2-140">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-140">1.1</span></span>|

### <a name="new-and-updated-enumerations"></a><span data-ttu-id="f28d2-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="f28d2-141">New and updated enumerations</span></span>

|<span data-ttu-id="f28d2-142">**Objeto**</span><span class="sxs-lookup"><span data-stu-id="f28d2-142">**Object**</span></span>|<span data-ttu-id="f28d2-143">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="f28d2-143">**Description**</span></span>|<span data-ttu-id="f28d2-144">**Versão**</span><span class="sxs-lookup"><span data-stu-id="f28d2-144">**Version**</span></span>|
|:-----|:-----|:-----|
|`ActiveView`|<span data-ttu-id="f28d2-145">Adicionado para que os suplementos do PowerPoint possam determinar se os usuários estão exibindo a apresentação (**Apresentação de Slides**) ou editando slides.</span><span class="sxs-lookup"><span data-stu-id="f28d2-145">Specifies the state of the active view of the document, for example, whether the user can edit the document.Added so that add-ins for PowerPoint can determine if the users is viewing the presentation ( **Slide Show**) or editing slides.</span></span> |<span data-ttu-id="f28d2-146">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-146">1.1</span></span>|
|`CoercionType`|<span data-ttu-id="f28d2-147">Atualizado com **Office.CoercionType.SlideRange** para oferecer suporte à obtenção do intervalo de slides selecionado com o método **getSelectedDataAsync** em suplementos para PowerPoint.</span><span class="sxs-lookup"><span data-stu-id="f28d2-147">Updated with  **Office.CoercionType.SlideRange** to support getting the selected slide range with the **getSelectedDataAsync** method in add-ins for PowerPoint.</span></span>|<span data-ttu-id="f28d2-148">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-148">1.1</span></span>|
|`EventType`|<span data-ttu-id="f28d2-149">Atualizado para incluir o novo evento ActiveViewChanged.</span><span class="sxs-lookup"><span data-stu-id="f28d2-149">Updated to include the new ActiveViewChanged event.</span></span>|<span data-ttu-id="f28d2-150">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-150">1.1</span></span>|
|`FileType`|<span data-ttu-id="f28d2-151">Atualizado para especificar a saída no formato PDF.</span><span class="sxs-lookup"><span data-stu-id="f28d2-151">Updated to specify output in PDF format.</span></span>|<span data-ttu-id="f28d2-152">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-152">1.1</span></span>|
|`GoToType`|<span data-ttu-id="f28d2-153">Adicionado para especificar o local ou o objeto a ser acessado no documento.</span><span class="sxs-lookup"><span data-stu-id="f28d2-153">Added to specify the place or object in the document to go to.</span></span>|<span data-ttu-id="f28d2-154">1.1</span><span class="sxs-lookup"><span data-stu-id="f28d2-154">1.1</span></span>|
