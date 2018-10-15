# <a name="officeapp-element"></a><span data-ttu-id="83870-101">Elemento OfficeApp</span><span class="sxs-lookup"><span data-stu-id="83870-101">OfficeApp element</span></span>

<span data-ttu-id="83870-102">O elemento raiz no manifesto de um suplemento do Office.</span><span class="sxs-lookup"><span data-stu-id="83870-102">The root element in the manifest of an Office Add-in.</span></span>

<span data-ttu-id="83870-103">**Tipo de suplemento:** Conteúdo, Painel de tarefas, Email</span><span class="sxs-lookup"><span data-stu-id="83870-103">**Add-in type:** Content, Task pane, Mail</span></span>

## <a name="syntax"></a><span data-ttu-id="83870-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83870-104">Syntax</span></span>

```XML
<OfficeApp 
  xmlns="http://schemas.microsoft.com/office/appforoffice/1.1" 
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
  xsi:type= ["ContentApp" |"MailApp"| "TaskPaneApp"]>
  ...
</OfficeApp>
```

## <a name="contained-in"></a><span data-ttu-id="83870-105">Contido em</span><span class="sxs-lookup"><span data-stu-id="83870-105">Contained in:</span></span>

 <span data-ttu-id="83870-106">_nenhum_</span><span class="sxs-lookup"><span data-stu-id="83870-106">_none_</span></span>

## <a name="must-contain"></a><span data-ttu-id="83870-107">Deve conter:</span><span class="sxs-lookup"><span data-stu-id="83870-107">Must contain:</span></span>

|<span data-ttu-id="83870-108">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="83870-108">**Element**</span></span>|<span data-ttu-id="83870-109">**Content**</span><span class="sxs-lookup"><span data-stu-id="83870-109">**Content**</span></span>|<span data-ttu-id="83870-110">**Mail**</span><span class="sxs-lookup"><span data-stu-id="83870-110">**Mail**</span></span>|<span data-ttu-id="83870-111">**TaskPane**</span><span class="sxs-lookup"><span data-stu-id="83870-111">\*\*\*\* Taskpane</span></span>|
|:-----|:-----|:-----|:-----|
|[<span data-ttu-id="83870-112">Id</span><span class="sxs-lookup"><span data-stu-id="83870-112">Id</span></span>](id.md)|<span data-ttu-id="83870-113">x</span><span class="sxs-lookup"><span data-stu-id="83870-113">x</span></span>|<span data-ttu-id="83870-114">x</span><span class="sxs-lookup"><span data-stu-id="83870-114">x</span></span>|<span data-ttu-id="83870-115">x</span><span class="sxs-lookup"><span data-stu-id="83870-115">x</span></span>|
|[<span data-ttu-id="83870-116">Versão</span><span class="sxs-lookup"><span data-stu-id="83870-116">Version</span></span>](version.md)|<span data-ttu-id="83870-117">x</span><span class="sxs-lookup"><span data-stu-id="83870-117">x</span></span>|<span data-ttu-id="83870-118">x</span><span class="sxs-lookup"><span data-stu-id="83870-118">x</span></span>|<span data-ttu-id="83870-119">x</span><span class="sxs-lookup"><span data-stu-id="83870-119">x</span></span>|
|[<span data-ttu-id="83870-120">ProviderName</span><span class="sxs-lookup"><span data-stu-id="83870-120">ProviderName</span></span>](providername.md)|<span data-ttu-id="83870-121">x</span><span class="sxs-lookup"><span data-stu-id="83870-121">x</span></span>|<span data-ttu-id="83870-122">x</span><span class="sxs-lookup"><span data-stu-id="83870-122">x</span></span>|<span data-ttu-id="83870-123">x</span><span class="sxs-lookup"><span data-stu-id="83870-123">x</span></span>|
|[<span data-ttu-id="83870-124">DefaultLocale</span><span class="sxs-lookup"><span data-stu-id="83870-124">DefaultLocale</span></span>](defaultlocale.md)|<span data-ttu-id="83870-125">x</span><span class="sxs-lookup"><span data-stu-id="83870-125">x</span></span>|<span data-ttu-id="83870-126">x</span><span class="sxs-lookup"><span data-stu-id="83870-126">x</span></span>|<span data-ttu-id="83870-127">x</span><span class="sxs-lookup"><span data-stu-id="83870-127">x</span></span>|
|[<span data-ttu-id="83870-128">DefaultSettings</span><span class="sxs-lookup"><span data-stu-id="83870-128">DefaultSettings</span></span>](defaultsettings.md)|<span data-ttu-id="83870-129">x</span><span class="sxs-lookup"><span data-stu-id="83870-129">x</span></span>||<span data-ttu-id="83870-130">x</span><span class="sxs-lookup"><span data-stu-id="83870-130">x</span></span>|
|[<span data-ttu-id="83870-131">DisplayName</span><span class="sxs-lookup"><span data-stu-id="83870-131">DisplayName</span></span>](displayname.md)|<span data-ttu-id="83870-132">x</span><span class="sxs-lookup"><span data-stu-id="83870-132">x</span></span>|<span data-ttu-id="83870-133">x</span><span class="sxs-lookup"><span data-stu-id="83870-133">x</span></span>|<span data-ttu-id="83870-134">x</span><span class="sxs-lookup"><span data-stu-id="83870-134">x</span></span>|
|[<span data-ttu-id="83870-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="83870-135">Description</span></span>](description.md)|<span data-ttu-id="83870-136">x</span><span class="sxs-lookup"><span data-stu-id="83870-136">x</span></span>|<span data-ttu-id="83870-137">x</span><span class="sxs-lookup"><span data-stu-id="83870-137">x</span></span>|<span data-ttu-id="83870-138">x</span><span class="sxs-lookup"><span data-stu-id="83870-138">x</span></span>|
|[<span data-ttu-id="83870-139">FormSettings</span><span class="sxs-lookup"><span data-stu-id="83870-139">formsettings\*</span></span>](formsettings.md)||<span data-ttu-id="83870-140">x</span><span class="sxs-lookup"><span data-stu-id="83870-140">x</span></span>||
|[<span data-ttu-id="83870-141">Permissões</span><span class="sxs-lookup"><span data-stu-id="83870-141">Permissions</span></span>](permissions.md)|<span data-ttu-id="83870-142">x</span><span class="sxs-lookup"><span data-stu-id="83870-142">x</span></span>||<span data-ttu-id="83870-143">x</span><span class="sxs-lookup"><span data-stu-id="83870-143">x</span></span>|
|[<span data-ttu-id="83870-144">Rule</span><span class="sxs-lookup"><span data-stu-id="83870-144">Rule</span></span>](rule.md)||<span data-ttu-id="83870-145">x</span><span class="sxs-lookup"><span data-stu-id="83870-145">x</span></span>||

## <a name="can-contain"></a><span data-ttu-id="83870-146">Pode conter</span><span class="sxs-lookup"><span data-stu-id="83870-146">Can contain:</span></span>

|<span data-ttu-id="83870-147">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="83870-147">**Element**</span></span>|<span data-ttu-id="83870-148">**Content**</span><span class="sxs-lookup"><span data-stu-id="83870-148">**Content**</span></span>|<span data-ttu-id="83870-149">**Mail**</span><span class="sxs-lookup"><span data-stu-id="83870-149">**Mail**</span></span>|<span data-ttu-id="83870-150">**TaskPane**</span><span class="sxs-lookup"><span data-stu-id="83870-150">\*\*\*\* Taskpane</span></span>|
|:-----|:-----|:-----|:-----|
|[<span data-ttu-id="83870-151">AlternateId</span><span class="sxs-lookup"><span data-stu-id="83870-151">AlternateId</span></span>](alternateid.md)|<span data-ttu-id="83870-152">x</span><span class="sxs-lookup"><span data-stu-id="83870-152">x</span></span>|<span data-ttu-id="83870-153">x</span><span class="sxs-lookup"><span data-stu-id="83870-153">x</span></span>|<span data-ttu-id="83870-154">x</span><span class="sxs-lookup"><span data-stu-id="83870-154">x</span></span>|
|[<span data-ttu-id="83870-155">IconUrl</span><span class="sxs-lookup"><span data-stu-id="83870-155">IconUrl</span></span>](iconurl.md)|<span data-ttu-id="83870-156">x</span><span class="sxs-lookup"><span data-stu-id="83870-156">x</span></span>|<span data-ttu-id="83870-157">x</span><span class="sxs-lookup"><span data-stu-id="83870-157">x</span></span>|<span data-ttu-id="83870-158">x</span><span class="sxs-lookup"><span data-stu-id="83870-158">x</span></span>|
|[<span data-ttu-id="83870-159">HighResolutionIconUrl</span><span class="sxs-lookup"><span data-stu-id="83870-159">HighResolutionIconUrl</span></span>](highresolutioniconurl.md)|<span data-ttu-id="83870-160">x</span><span class="sxs-lookup"><span data-stu-id="83870-160">x</span></span>|<span data-ttu-id="83870-161">x</span><span class="sxs-lookup"><span data-stu-id="83870-161">x</span></span>|<span data-ttu-id="83870-162">x</span><span class="sxs-lookup"><span data-stu-id="83870-162">x</span></span>|
|[<span data-ttu-id="83870-163">SupportUrl</span><span class="sxs-lookup"><span data-stu-id="83870-163">SupportUrl</span></span>](supporturl.md)|<span data-ttu-id="83870-164">x</span><span class="sxs-lookup"><span data-stu-id="83870-164">x</span></span>|<span data-ttu-id="83870-165">x</span><span class="sxs-lookup"><span data-stu-id="83870-165">x</span></span>|<span data-ttu-id="83870-166">x</span><span class="sxs-lookup"><span data-stu-id="83870-166">x</span></span>|
|[<span data-ttu-id="83870-167">AppDomains</span><span class="sxs-lookup"><span data-stu-id="83870-167">AppDomains</span></span>](appdomains.md)|<span data-ttu-id="83870-168">x</span><span class="sxs-lookup"><span data-stu-id="83870-168">x</span></span>|<span data-ttu-id="83870-169">x</span><span class="sxs-lookup"><span data-stu-id="83870-169">x</span></span>|<span data-ttu-id="83870-170">x</span><span class="sxs-lookup"><span data-stu-id="83870-170">x</span></span>|
|[<span data-ttu-id="83870-171">Hosts</span><span class="sxs-lookup"><span data-stu-id="83870-171">Hosts</span></span>](hosts.md)|<span data-ttu-id="83870-172">x</span><span class="sxs-lookup"><span data-stu-id="83870-172">x</span></span>|<span data-ttu-id="83870-173">x</span><span class="sxs-lookup"><span data-stu-id="83870-173">x</span></span>|<span data-ttu-id="83870-174">x</span><span class="sxs-lookup"><span data-stu-id="83870-174">x</span></span>|
|[<span data-ttu-id="83870-175">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83870-175">Requirements</span></span>](requirements.md)|<span data-ttu-id="83870-176">x</span><span class="sxs-lookup"><span data-stu-id="83870-176">x</span></span>|<span data-ttu-id="83870-177">x</span><span class="sxs-lookup"><span data-stu-id="83870-177">x</span></span>|<span data-ttu-id="83870-178">x</span><span class="sxs-lookup"><span data-stu-id="83870-178">x</span></span>|
|[<span data-ttu-id="83870-179">AllowSnapshot</span><span class="sxs-lookup"><span data-stu-id="83870-179">AllowSnapshot</span></span>](allowsnapshot.md)|<span data-ttu-id="83870-180">x</span><span class="sxs-lookup"><span data-stu-id="83870-180">x</span></span>|||
|[<span data-ttu-id="83870-181">Permissões</span><span class="sxs-lookup"><span data-stu-id="83870-181">Permissions</span></span>](permissions.md)||<span data-ttu-id="83870-182">x</span><span class="sxs-lookup"><span data-stu-id="83870-182">x</span></span>||
|[<span data-ttu-id="83870-183">DisableEntityHighlighting</span><span class="sxs-lookup"><span data-stu-id="83870-183">DisableEntityHighlighting</span></span>](disableentityhighlighting.md)||<span data-ttu-id="83870-184">x</span><span class="sxs-lookup"><span data-stu-id="83870-184">x</span></span>||
|[<span data-ttu-id="83870-185">Dicionário</span><span class="sxs-lookup"><span data-stu-id="83870-185">Dictionary</span></span>](dictionary.md)|||<span data-ttu-id="83870-186">x</span><span class="sxs-lookup"><span data-stu-id="83870-186">x</span></span>|
|[<span data-ttu-id="83870-187">VersionOverrides</span><span class="sxs-lookup"><span data-stu-id="83870-187">VersionOverrides</span></span>](versionoverrides.md)|<span data-ttu-id="83870-188">X</span><span class="sxs-lookup"><span data-stu-id="83870-188">X</span></span>|<span data-ttu-id="83870-189">X</span><span class="sxs-lookup"><span data-stu-id="83870-189">X</span></span>|<span data-ttu-id="83870-190">X</span><span class="sxs-lookup"><span data-stu-id="83870-190">X</span></span>|

## <a name="attributes"></a><span data-ttu-id="83870-191">Atributos</span><span class="sxs-lookup"><span data-stu-id="83870-191">Attributes</span></span>

|||
|:-----|:-----|
|<span data-ttu-id="83870-192">xmlns</span><span class="sxs-lookup"><span data-stu-id="83870-192">xmlns</span></span>|<span data-ttu-id="83870-p101">Define a versão do namespace e esquema do manisfesto do suplemento do Office. Esse atributo deve ser sempre definido como  `"http://schemas.microsoft.com/office/appforoffice/1.1"`</span><span class="sxs-lookup"><span data-stu-id="83870-p101">Defines the Office Add-in manifest namespace and schema version. This attribute should always be set to  `"http://schemas.microsoft.com/office/appforoffice/1.1"`</span></span>|
|<span data-ttu-id="83870-195">xmlns: xsi</span><span class="sxs-lookup"><span data-stu-id="83870-195">xmlns:xsi</span></span>|<span data-ttu-id="83870-p102">Define a instância XMLSchema. Esse atributo deve ser sempre definido como  `"http://www.w3.org/2001/XMLSchema-instance"`</span><span class="sxs-lookup"><span data-stu-id="83870-p102">Defines the XMLSchema instance. This attribute should always be set to  `"http://www.w3.org/2001/XMLSchema-instance"`</span></span>|
|<span data-ttu-id="83870-198">xsi:type</span><span class="sxs-lookup"><span data-stu-id="83870-198">xsi:type</span></span>|<span data-ttu-id="83870-p103">Define o tipo de suplemento do Office. Esse atributo deve ser definido como um destes: `"ContentApp"`, `"MailApp"` ou  `"TaskPaneApp"`</span><span class="sxs-lookup"><span data-stu-id="83870-p103">Defines the kind of Office Add-in. This attribute should be set to one of:  `"ContentApp"`,  `"MailApp"`, or  `"TaskPaneApp"`</span></span>|