# <a name="resources-element"></a><span data-ttu-id="b076c-101">Elemento Resources</span><span class="sxs-lookup"><span data-stu-id="b076c-101">Resources element</span></span>

<span data-ttu-id="b076c-p101">Contém ícones, sequências de caracteres e URLs para o nó [VersionOverrides](versionoverrides.md). Um elemento de manifesto especifica um recurso usando a **id** do recurso. Isso ajuda a manter o tamanho do manifesto gerenciável, especialmente quando os recursos tiverem versões para localidades diferentes. Uma **id** deve ser exclusiva no manifesto e pode ter no máximo 32 caracteres.</span><span class="sxs-lookup"><span data-stu-id="b076c-p101">Contains icons, strings, and URLs for the [VersionOverrides](versionoverrides.md) node. A manifest element specifies a resource by using the **id** of the resource. This helps to keep the size of the manifest manageable, especially when resources have versions for different locales. An **id** must be unique within the manifest and can have a maximum of 32 characters.</span></span>

<span data-ttu-id="b076c-106">Cada recurso pode ter um ou mais elementos filhos **Override** para definir um recurso diferente para uma localidade específica.</span><span class="sxs-lookup"><span data-stu-id="b076c-106">Each resource can have one or more **Override** child elements to define a different resource for a specific locale.</span></span>

## <a name="child-elements"></a><span data-ttu-id="b076c-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b076c-107">Child elements</span></span>

|  <span data-ttu-id="b076c-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="b076c-108">Element</span></span> |  <span data-ttu-id="b076c-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="b076c-109">Type</span></span>  |  <span data-ttu-id="b076c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b076c-110">Description</span></span>  |
|:-----|:-----|:-----|
|  [<span data-ttu-id="b076c-111">Images</span><span class="sxs-lookup"><span data-stu-id="b076c-111">Images</span></span>](#images)            |  <span data-ttu-id="b076c-112">image</span><span class="sxs-lookup"><span data-stu-id="b076c-112">image</span></span>   |  <span data-ttu-id="b076c-113">Fornece a URL HTTPS de uma imagem para um ícone.</span><span class="sxs-lookup"><span data-stu-id="b076c-113">Provides the HTTPS URL to an image for an icon.</span></span> |
|  <span data-ttu-id="b076c-114">**Urls**</span><span class="sxs-lookup"><span data-stu-id="b076c-114">**Urls**</span></span>                |  <span data-ttu-id="b076c-115">url</span><span class="sxs-lookup"><span data-stu-id="b076c-115">url</span></span>     |  <span data-ttu-id="b076c-p102">Fornece um local para a URL HTTPS. A URL pode ter 2.048 caracteres no máximo.</span><span class="sxs-lookup"><span data-stu-id="b076c-p102">Provides an HTTPS URL location. A URL can have a maximum of 2048 characters.</span></span> |
|  <span data-ttu-id="b076c-118">**ShortStrings**</span><span class="sxs-lookup"><span data-stu-id="b076c-118">**ShortStrings**</span></span> |  <span data-ttu-id="b076c-119">string</span><span class="sxs-lookup"><span data-stu-id="b076c-119">string</span></span>  |  <span data-ttu-id="b076c-p103">O texto para os elementos **Label** e **Title**. Cada **String** contém no máximo 125 caracteres.</span><span class="sxs-lookup"><span data-stu-id="b076c-p103">The text for **Label** and **Title** elements. Each **String** contains a maximum of 125 characters.</span></span>|
|  <span data-ttu-id="b076c-122">**LongStrings**</span><span class="sxs-lookup"><span data-stu-id="b076c-122">**LongStrings**</span></span>  |  <span data-ttu-id="b076c-123">string</span><span class="sxs-lookup"><span data-stu-id="b076c-123">string</span></span>  | <span data-ttu-id="b076c-p104">O texto para atributos **Description** . Cada **String** contém no máximo 250 caracteres.</span><span class="sxs-lookup"><span data-stu-id="b076c-p104">The text for **Description** attributes. Each **String** contains a maximum of 250 characters.</span></span>|

> [!NOTE]
> <span data-ttu-id="b076c-126">Use o protocolo SSL (Secure Sockets Layer) para todas as URLs nos elementos **Image** e **Url**.</span><span class="sxs-lookup"><span data-stu-id="b076c-126">You must use Secure Sockets Layer (SSL) for all URLs in the **Image** and **Url** elements.</span></span>

### <a name="images"></a><span data-ttu-id="b076c-127">Images</span><span class="sxs-lookup"><span data-stu-id="b076c-127">Images</span></span>
<span data-ttu-id="b076c-128">Cada ícone deve ter três elementos **Images**, um para cada um dos três tamanhos obrigatórios:</span><span class="sxs-lookup"><span data-stu-id="b076c-128">Each icon must have three  **Images** elements, one for each of the three mandatory sizes:</span></span>

- <span data-ttu-id="b076c-129">16x16</span><span class="sxs-lookup"><span data-stu-id="b076c-129">16x16</span></span>
- <span data-ttu-id="b076c-130">32x32</span><span class="sxs-lookup"><span data-stu-id="b076c-130">32x32</span></span>
- <span data-ttu-id="b076c-131">80x80</span><span class="sxs-lookup"><span data-stu-id="b076c-131">80x80</span></span>

<span data-ttu-id="b076c-132">Os seguintes tamanhos adicionais também têm suporte, mas não são obrigatórios:</span><span class="sxs-lookup"><span data-stu-id="b076c-132">The following additional sizes are also supported, but not required:</span></span>

- <span data-ttu-id="b076c-133">20x20</span><span class="sxs-lookup"><span data-stu-id="b076c-133">20x20</span></span>
- <span data-ttu-id="b076c-134">24x24</span><span class="sxs-lookup"><span data-stu-id="b076c-134">24x24</span></span>
- <span data-ttu-id="b076c-135">40x40</span><span class="sxs-lookup"><span data-stu-id="b076c-135">40x40</span></span>
- <span data-ttu-id="b076c-136">48x48</span><span class="sxs-lookup"><span data-stu-id="b076c-136">48x48</span></span>
- <span data-ttu-id="b076c-137">64x64</span><span class="sxs-lookup"><span data-stu-id="b076c-137">64x64</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="b076c-138">O Outlook requer a capacidade de armazenar em cache os recursos de imagem para fins de desempenho.</span><span class="sxs-lookup"><span data-stu-id="b076c-138">Important:  Outlook requires the ability to cache image resources for performance purposes.</span></span> <span data-ttu-id="b076c-139">Por esse motivo, o servidor que hospeda um recurso de imagem não deve adicionar nenhuma diretriz CACHE-CONTROL ao cabeçalho da resposta.</span><span class="sxs-lookup"><span data-stu-id="b076c-139">For this reason, the server hosting an image resource must not add any CACHE-CONTROL directives to the response header.</span></span> <span data-ttu-id="b076c-140">Isso fará com que o Outlook substitua automaticamente uma imagem padrão ou genérica.</span><span class="sxs-lookup"><span data-stu-id="b076c-140">This will result in Outlook automatically substituting a generic or default image.</span></span>    

## <a name="resources-examples"></a><span data-ttu-id="b076c-141">Exemplos de recursos</span><span class="sxs-lookup"><span data-stu-id="b076c-141">Resources examples</span></span> 

```XML
<Resources>
      <bt:Images>
        <bt:Image id="icon1_16x16" DefaultValue="https://www.contoso.com/icon_default.png">
          <bt:Override Locale="ja-jp" Value="https://www.contoso.com/ja-jp16-icon_default.png" />
        </bt:Image>
        <bt:Image id="icon1_32x32" DefaultValue="https://www.contoso.com/icon_default.png">
          <bt:Override Locale="ja-jp" Value="https://www.contoso.com/ja-jp32-icon_default.png" />
        </bt:Image>
        <bt:Image id="icon1_80x80" DefaultValue="https://www.contoso.com/icon_default.png">
          <bt:Override Locale="ja-jp" Value="https://www.contoso.com/ja-jp80-icon_default.png" />
        </bt:Image>
      </bt:Images>
      <bt:Urls>
        <bt:Url id="residDesktopFuncUrl" DefaultValue="https://www.contoso.com/Pages/Home.aspx">
          <bt:Override Locale="ja-jp" Value="https://www.contoso.com/Pages/Home.aspx" />
        </bt:Url>
      </bt:Urls>
      <bt:ShortStrings>
        <bt:String id="residLabel" DefaultValue="GetData">
          <bt:Override Locale="ja-jp" Value="JA-JP-GetData" />
        </bt:String>
      </bt:ShortStrings>
      <bt:LongStrings>
        <bt:String id="residToolTip" DefaultValue="Get data for your document.">
          <bt:Override Locale="ja-jp" Value="JA-JP - Get data for your document." />
        </bt:String>
      </bt:LongStrings>
    </Resources>
```

```xml
<Resources>
  <bt:Images>
    <!-- Blue icon -->
    <bt:Image id="blue-icon-16" DefaultValue="YOUR_WEB_SERVER/blue-16.png"/>
    <bt:Image id="blue-icon-32" DefaultValue="YOUR_WEB_SERVER//blue-32.png"/>
    <bt:Image id="blue-icon-80" DefaultValue="YOUR_WEB_SERVER/blue-80.png"/>
  </bt:Images>
  <bt:Urls>
    <bt:Url id="functionFile" DefaultValue="YOUR_WEB_SERVER/FunctionFile/Functions.html"/>
    <!-- other URLs -->
  </bt:Urls>
  <bt:ShortStrings>
    <bt:String id="groupLabel" DefaultValue="Add-in Demo">
      <bt:Override Locale="ar-sa" Value="<Localized text>" />
    </bt:String>
    <!-- Other short strings -->
  </bt:ShortStrings>
  <bt:LongStrings>
    <bt:String id="funcReadSuperTipDescription" DefaultValue="Gets the subject of the message or appointment.">
      <bt:Override Locale="ar-sa" Value="<Localized text>." />
    </bt:String>
    <!-- Other long strings -->
  </bt:LongStrings>
</Resources>
```