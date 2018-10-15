
# <a name="diagnostics"></a><span data-ttu-id="bc8e8-101">diagnostics</span><span class="sxs-lookup"><span data-stu-id="bc8e8-101">diagnostics</span></span>

### <span data-ttu-id="bc8e8-p101">[Office](Office.md)[.context](Office.context.md)[.mailbox](Office.context.mailbox.md). diagnostics</span><span class="sxs-lookup"><span data-stu-id="bc8e8-p101">[Office](Office.md)[.context](Office.context.md)[.mailbox](Office.context.mailbox.md). diagnostics</span></span>

<span data-ttu-id="bc8e8-104">Fornece informações de diagnóstico para um suplemento do Outlook.</span><span class="sxs-lookup"><span data-stu-id="bc8e8-104">Provides diagnostic information to an Outlook add-in.</span></span>

##### <a name="requirements"></a><span data-ttu-id="bc8e8-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc8e8-105">Requirements</span></span>

|<span data-ttu-id="bc8e8-106">Requisito</span><span class="sxs-lookup"><span data-stu-id="bc8e8-106">Requirement</span></span>| <span data-ttu-id="bc8e8-107">Valor</span><span class="sxs-lookup"><span data-stu-id="bc8e8-107">Value</span></span>|
|---|---|
|[<span data-ttu-id="bc8e8-108">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="bc8e8-108">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="bc8e8-109">1.0</span><span class="sxs-lookup"><span data-stu-id="bc8e8-109">1.0</span></span>|
|[<span data-ttu-id="bc8e8-110">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="bc8e8-110">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="bc8e8-111">ReadItem</span><span class="sxs-lookup"><span data-stu-id="bc8e8-111">ReadItem</span></span>|
|[<span data-ttu-id="bc8e8-112">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="bc8e8-112">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="bc8e8-113">Redação ou leitura</span><span class="sxs-lookup"><span data-stu-id="bc8e8-113">Compose or read</span></span>|

### <a name="members"></a><span data-ttu-id="bc8e8-114">Membros</span><span class="sxs-lookup"><span data-stu-id="bc8e8-114">Members</span></span>

####  <a name="hostname-string"></a><span data-ttu-id="bc8e8-115">hostName :String</span><span class="sxs-lookup"><span data-stu-id="bc8e8-115">hostName :String</span></span>

<span data-ttu-id="bc8e8-116">Obtém uma sequência de caracteres que representa o nome do aplicativo host.</span><span class="sxs-lookup"><span data-stu-id="bc8e8-116">Gets a string that represents the name of the host application.</span></span>

<span data-ttu-id="bc8e8-117">Uma sequência de caracteres que pode ser um dos valores a seguir: `Outlook`, `OutlookIOS` ou `OutlookWebApp`.</span><span class="sxs-lookup"><span data-stu-id="bc8e8-117">A string that can be one of the following values: `Outlook`, `OutlookIOS`, , or `OutlookWebApp`.</span></span>

##### <a name="type"></a><span data-ttu-id="bc8e8-118">Tipo:</span><span class="sxs-lookup"><span data-stu-id="bc8e8-118">Type:</span></span>

*   <span data-ttu-id="bc8e8-119">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="bc8e8-119">String</span></span>

##### <a name="requirements"></a><span data-ttu-id="bc8e8-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc8e8-120">Requirements</span></span>

|<span data-ttu-id="bc8e8-121">Requisito</span><span class="sxs-lookup"><span data-stu-id="bc8e8-121">Requirement</span></span>| <span data-ttu-id="bc8e8-122">Valor</span><span class="sxs-lookup"><span data-stu-id="bc8e8-122">Value</span></span>|
|---|---|
|[<span data-ttu-id="bc8e8-123">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="bc8e8-123">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="bc8e8-124">1.0</span><span class="sxs-lookup"><span data-stu-id="bc8e8-124">1.0</span></span>|
|[<span data-ttu-id="bc8e8-125">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="bc8e8-125">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="bc8e8-126">ReadItem</span><span class="sxs-lookup"><span data-stu-id="bc8e8-126">ReadItem</span></span>|
|[<span data-ttu-id="bc8e8-127">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="bc8e8-127">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="bc8e8-128">Redação ou leitura</span><span class="sxs-lookup"><span data-stu-id="bc8e8-128">Compose or read</span></span>|

####  <a name="hostversion-string"></a><span data-ttu-id="bc8e8-129">hostVersion :String</span><span class="sxs-lookup"><span data-stu-id="bc8e8-129">hostVersion :String</span></span>

<span data-ttu-id="bc8e8-130">Obtém uma sequência de caracteres que representa a versão do aplicativo host ou do Exchange Server.</span><span class="sxs-lookup"><span data-stu-id="bc8e8-130">Gets a string that represents the version of either the host application or the Exchange Server.</span></span>

<span data-ttu-id="bc8e8-p102">Se o suplemento de email estiver em execução no cliente da área de trabalho do Outlook ou no Outlook para iOS, a propriedade `hostVersion` retornará a versão do aplicativo host, o Outlook. No Outlook Web App, a propriedade retorna a versão do Exchange Server. Um exemplo é a sequência de caracteres `15.0.468.0`.</span><span class="sxs-lookup"><span data-stu-id="bc8e8-p102">If the mail add-in is running on the Outlook desktop client or Outlook for iOS, the `hostVersion` property returns the version of the host application, Outlook. In Outlook Web App, the property returns the version of the Exchange Server. An example is the string `15.0.468.0`.</span></span>

##### <a name="type"></a><span data-ttu-id="bc8e8-134">Tipo:</span><span class="sxs-lookup"><span data-stu-id="bc8e8-134">Type:</span></span>

*   <span data-ttu-id="bc8e8-135">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="bc8e8-135">String</span></span>

##### <a name="requirements"></a><span data-ttu-id="bc8e8-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc8e8-136">Requirements</span></span>

|<span data-ttu-id="bc8e8-137">Requisito</span><span class="sxs-lookup"><span data-stu-id="bc8e8-137">Requirement</span></span>| <span data-ttu-id="bc8e8-138">Valor</span><span class="sxs-lookup"><span data-stu-id="bc8e8-138">Value</span></span>|
|---|---|
|[<span data-ttu-id="bc8e8-139">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="bc8e8-139">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="bc8e8-140">1.0</span><span class="sxs-lookup"><span data-stu-id="bc8e8-140">1.0</span></span>|
|[<span data-ttu-id="bc8e8-141">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="bc8e8-141">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="bc8e8-142">ReadItem</span><span class="sxs-lookup"><span data-stu-id="bc8e8-142">ReadItem</span></span>|
|[<span data-ttu-id="bc8e8-143">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="bc8e8-143">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="bc8e8-144">Redação ou leitura</span><span class="sxs-lookup"><span data-stu-id="bc8e8-144">Compose or read</span></span>|

####  <a name="owaview-string"></a><span data-ttu-id="bc8e8-145">OWAView :String</span><span class="sxs-lookup"><span data-stu-id="bc8e8-145">OWAView :String</span></span>

<span data-ttu-id="bc8e8-146">Obtém uma sequência de caracteres que representa o modo de exibição atual do Outlook Web App.</span><span class="sxs-lookup"><span data-stu-id="bc8e8-146">Gets a string that represents the current view of Outlook Web App.</span></span>

<span data-ttu-id="bc8e8-147">A sequência de caracteres retornada pode ser um dos valores a seguir: `OneColumn`, `TwoColumns` ou `ThreeColumns`.</span><span class="sxs-lookup"><span data-stu-id="bc8e8-147">The returned string can be one of the following values: `OneColumn`, `TwoColumns`, or `ThreeColumns`.</span></span>

<span data-ttu-id="bc8e8-148">Se o aplicativo host não for o Outlook Web App, o acesso a essa propriedade resultará em `undefined`.</span><span class="sxs-lookup"><span data-stu-id="bc8e8-148">If the host application is not Outlook Web App, then accessing this property results in `undefined`.</span></span>

<span data-ttu-id="bc8e8-149">O Outlook Web App tem três modos de exibição que correspondem à largura da tela e da janela, e ao número de colunas que pode ser exibido:</span><span class="sxs-lookup"><span data-stu-id="bc8e8-149">Outlook Web App has three views that correspond to the width of the screen and the window, and the number of columns that can be displayed:</span></span>

*   <span data-ttu-id="bc8e8-p103">`OneColumn`, que é exibido quando a tela é estreita. O Outlook Web App usa esse layout de coluna única em toda a tela de um smartphone.</span><span class="sxs-lookup"><span data-stu-id="bc8e8-p103">`OneColumn`, which is displayed when the screen is narrow. Outlook Web App uses this single-column layout on the entire screen of a smartphone.</span></span>
*   <span data-ttu-id="bc8e8-p104">`TwoColumns`, que é exibido quando a tela é mais larga. O Outlook Web App usa esse modo de exibição na maioria dos tablets.</span><span class="sxs-lookup"><span data-stu-id="bc8e8-p104">`TwoColumns`, which is displayed when the screen is wider. Outlook Web App uses this view on most tablets.</span></span>
*   <span data-ttu-id="bc8e8-p105">`ThreeColumns`, que é exibido quando a tela é larga. Por exemplo, o Outlook Web App usa esse modo de exibição em uma janela de tela inteira em um computador.</span><span class="sxs-lookup"><span data-stu-id="bc8e8-p105">`ThreeColumns`, which is displayed when the screen is wide. For example, Outlook Web App uses this view in a full screen window on a desktop computer.</span></span>

##### <a name="type"></a><span data-ttu-id="bc8e8-156">Tipo:</span><span class="sxs-lookup"><span data-stu-id="bc8e8-156">Type:</span></span>

*   <span data-ttu-id="bc8e8-157">Sequência de caracteres</span><span class="sxs-lookup"><span data-stu-id="bc8e8-157">String</span></span>

##### <a name="requirements"></a><span data-ttu-id="bc8e8-158">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc8e8-158">Requirements</span></span>

|<span data-ttu-id="bc8e8-159">Requisito</span><span class="sxs-lookup"><span data-stu-id="bc8e8-159">Requirement</span></span>| <span data-ttu-id="bc8e8-160">Valor</span><span class="sxs-lookup"><span data-stu-id="bc8e8-160">Value</span></span>|
|---|---|
|[<span data-ttu-id="bc8e8-161">Versão mínima do conjunto de requisitos de caixa de correio</span><span class="sxs-lookup"><span data-stu-id="bc8e8-161">Minimum mailbox requirement set version</span></span>](/office/dev/add-ins/reference/requirement-sets/outlook-api-requirement-sets)| <span data-ttu-id="bc8e8-162">1.0</span><span class="sxs-lookup"><span data-stu-id="bc8e8-162">1.0</span></span>|
|[<span data-ttu-id="bc8e8-163">Nível de permissão mínimo</span><span class="sxs-lookup"><span data-stu-id="bc8e8-163">Minimum permission level</span></span>](https://docs.microsoft.com/outlook/add-ins/understanding-outlook-add-in-permissions)| <span data-ttu-id="bc8e8-164">ReadItem</span><span class="sxs-lookup"><span data-stu-id="bc8e8-164">ReadItem</span></span>|
|[<span data-ttu-id="bc8e8-165">Modo do Outlook aplicável</span><span class="sxs-lookup"><span data-stu-id="bc8e8-165">Applicable Outlook mode</span></span>](https://docs.microsoft.com/outlook/add-ins/#extension-points)| <span data-ttu-id="bc8e8-166">Redação ou leitura</span><span class="sxs-lookup"><span data-stu-id="bc8e8-166">Compose or read</span></span>|