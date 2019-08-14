---
title: Visão geral da autenticação e autorização nos Suplementos do Office
description: ''
ms.date: 08/07/2019
localization_priority: Priority
ms.openlocfilehash: 2733f8af9f236347e52269c9e73b322b4310e2a9
ms.sourcegitcommit: 1dc1bb0befe06d19b587961da892434bd0512fb5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302925"
---
# <a name="overview-of-authentication-and-authorization-in-office-add-ins"></a><span data-ttu-id="66e61-102">Visão geral da autenticação e autorização nos Suplementos do Office</span><span class="sxs-lookup"><span data-stu-id="66e61-102">Overview of identity, authentication, and authorization in Office 2013</span></span>

<span data-ttu-id="66e61-103">Os aplicativos da Web e, portanto, os Suplementos do Office permitem acesso anônimo por padrão, mas é possível exigir que os usuários se autentiquem com um logon.</span><span class="sxs-lookup"><span data-stu-id="66e61-103">Web applications and, hence, Office Add-ins allow anonymous access by default, but you can require users to authenticate with a login.</span></span> <span data-ttu-id="66e61-104">Em particular, você pode exigir que os usuários se conectem com uma Conta da Microsoft, uma Conta Corporativa ou de Estudante (Office 365).</span><span class="sxs-lookup"><span data-stu-id="66e61-104">In particular, you can require that your users be logged in with either a Microsoft Account or a Work or School (Office 365) account.</span></span> <span data-ttu-id="66e61-105">Essa tarefa é chamada de autenticação do usuário, pois permite que o suplemento saiba quem é o usuário.</span><span class="sxs-lookup"><span data-stu-id="66e61-105">This task is called user authentication because it enables the add-in to know who the user is.</span></span>

<span data-ttu-id="66e61-106">Seu suplemento também pode obter consentimento do usuário para acessar seus dados do Microsoft Graph (como seu perfil do Office 365, arquivos do OneDrive e dados do SharePoint) ou para dados de outras fontes externas, como Google, Facebook, LinkedIn, SalesForce e GitHub.</span><span class="sxs-lookup"><span data-stu-id="66e61-106">Your add-in can also get the user's consent to access their Microsoft Graph data (such as their Office 365 profile, OneDrive files, and SharePoint data) or to data in other external sources such as Google, Facebook, LinkedIn, SalesForce, and GitHub.</span></span> <span data-ttu-id="66e61-107">Essa tarefa é chamada de autorização de suplemento (ou aplicativo), pois é o *suplemento* que está sendo autorizado, não o usuário.</span><span class="sxs-lookup"><span data-stu-id="66e61-107">This task is called add-in (or app) authorization, because it is the *add-in* that is being authorized, not the user.</span></span>

<span data-ttu-id="66e61-108">Há duas maneiras de realizar essas autenticações.</span><span class="sxs-lookup"><span data-stu-id="66e61-108">You have a choice of two ways to accomplish these authentications.</span></span>

- <span data-ttu-id="66e61-109">**Logon único do Office (SSO)**: Um sistema, \* que está atualmente no modo de visualização.\*, permite que o logon do usuário do Office funcione também como um logon no suplemento.</span><span class="sxs-lookup"><span data-stu-id="66e61-109">**Office Single Sign-on (SSO)**: A system, *currently in preview*, that enables the user's login to Office to also function as a login to the add-in.</span></span> <span data-ttu-id="66e61-110">Opcionalmente, o suplemento também pode usar as credenciais do usuário do Office para autorizar o suplemento ao Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="66e61-110">Optionally, the add-in can also use the user's Office credentials to authorize the add-in to Microsoft Graph.</span></span> <span data-ttu-id="66e61-111">(As fontes que não são da Microsoft não podem ser acessadas por este sistema.)</span><span class="sxs-lookup"><span data-stu-id="66e61-111">(Non-Microsoft sources are not accessible through this system.)</span></span>
- <span data-ttu-id="66e61-112">**Autenticação e Autorização de Aplicativos Web com o Azure Active Directory**: Não é algo novo ou especial.</span><span class="sxs-lookup"><span data-stu-id="66e61-112">**Web Application Authentication and Authorization with Azure Active Directory**: This isn't something new or special.</span></span> <span data-ttu-id="66e61-113">É apenas a maneira como o suplemento do Office (e outros aplicativos Web) autenticavam os usuários e aplicativos autorizados antes de haver um sistema de SSO do Office e ainda é usado em situações em que o SSO do Office não pode.</span><span class="sxs-lookup"><span data-stu-id="66e61-113">It's just the way Office add-in (and other web apps) authenticated users and authorized apps before there was an Office SSO system and is still used in scenarios where Office SSO cannot be.</span></span>

<span data-ttu-id="66e61-114">O fluxograma a seguir mostra as decisões que você precisa tomar como desenvolvedor de suplemento.</span><span class="sxs-lookup"><span data-stu-id="66e61-114">The following flowchart shows you the decisions that you need to make as an add-in developer.</span></span> <span data-ttu-id="66e61-115">Os detalhes estão incluídos mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="66e61-115">Those additional steps are described later in this article.</span></span>

![Uma imagem mostrando um fluxograma de decisão para habilitar a autenticação e a autorização nos suplementos do Office](../images/auth-decisions-flowchart.gif)

## <a name="user-authentication-without-sso"></a><span data-ttu-id="66e61-117">Autenticação de usuário sem SSO</span><span class="sxs-lookup"><span data-stu-id="66e61-117">User authentication without SSO</span></span>

<span data-ttu-id="66e61-118">É possível autenticar um usuário em um Suplemento do Office com o Azure Active Directory (AAD) da mesma forma que em qualquer outro aplicativo Web com uma exceção: o AAD não permite que sua página de logon seja aberta em um iframe.</span><span class="sxs-lookup"><span data-stu-id="66e61-118">You can authenticate a user in an Office Add-in with Azure Active Directory (AAD) as you would any in any other web application with one exception: AAD does not allow its login page to open in an iframe.</span></span> <span data-ttu-id="66e61-119">Quando um suplemento do Office está sendo executado no *Office na Web*, o painel de tarefas é um iframe.</span><span class="sxs-lookup"><span data-stu-id="66e61-119">When an Office Add-in is running on *Office on the web*, the task pane is an iframe.</span></span> <span data-ttu-id="66e61-120">Isso significa que você precisará abrir a tela de logon do AAD em uma caixa de diálogo aberta com a API de Diálogo do Office.</span><span class="sxs-lookup"><span data-stu-id="66e61-120">This means that you will need to open the AAD login screen in a dialog opened with the Office Dialog API.</span></span> <span data-ttu-id="66e61-121">Isso afeta o modo como você usa bibliotecas auxiliares de autenticação.</span><span class="sxs-lookup"><span data-stu-id="66e61-121">This affects how you use authentication helper libraries.</span></span> <span data-ttu-id="66e61-122">Para saber mais, confira [Autenticação com a API de Diálogo do Office](auth-with-office-dialog-api.md).</span><span class="sxs-lookup"><span data-stu-id="66e61-122">For more information, see [Authentication with the Office Dialog API](auth-with-office-dialog-api.md).</span></span>

<span data-ttu-id="66e61-123">Para obter informações sobre a autenticação de programação com o AAD, comece com [Visão geral da plataforma de Identidade da Microsoft (v 2.0)](/azure/active-directory/develop/v2-overview).</span><span class="sxs-lookup"><span data-stu-id="66e61-123">For information about programming authentication with AAD, begin with [Microsoft identity platform (v2.0) overview](/azure/active-directory/develop/v2-overview).</span></span> <span data-ttu-id="66e61-124">Há muitos tutoriais e guias nesse conjunto de documentos, bem como links para exemplos e bibliotecas relevantes.</span><span class="sxs-lookup"><span data-stu-id="66e61-124">There are many tutorials and guides in that documentation set, as well as links to relevant samples and libraries.</span></span> <span data-ttu-id="66e61-125">Conforme explicado em [Autenticação com a API de Diálogo do Office](auth-with-office-dialog-api.md), talvez seja necessário ajustar o código nos exemplos para executar o Diálogo no Office.</span><span class="sxs-lookup"><span data-stu-id="66e61-125">As explained in [Authentication with the Office Dialog API](auth-with-office-dialog-api.md), you may need to adjust the code in the samples to run in the Office Dialog.</span></span>

## <a name="access-to-microsoft-graph-without-sso"></a><span data-ttu-id="66e61-126">Acesso ao Microsoft Graph sem SSO</span><span class="sxs-lookup"><span data-stu-id="66e61-126">Access to Microsoft Graph without SSO</span></span>

<span data-ttu-id="66e61-127">Você pode obter autorização para os dados do Microsoft Graph para seu suplemento obtendo um token de acesso ao Graph a partir do Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="66e61-127">You can get authorization to Microsoft Graph data for your add-in by obtaining an access token to Graph from Azure Active Directory (AAD).</span></span> <span data-ttu-id="66e61-128">Você pode fazer isso sem depender do SSO do Office.</span><span class="sxs-lookup"><span data-stu-id="66e61-128">You can do this without relying on Office SSO.</span></span> <span data-ttu-id="66e61-129">Para saber mais sobre como fazer isso, confira [Acesse o Microsoft Graph sem o SSO](authorize-to-microsoft-graph-without-sso.md) que tem mais detalhes e links para os exemplos.</span><span class="sxs-lookup"><span data-stu-id="66e61-129">For more information about how, see [Access to Microsoft Graph without SSO](authorize-to-microsoft-graph-without-sso.md) which has more details and links to samples.</span></span>

## <a name="user-authentication-with-sso"></a><span data-ttu-id="66e61-130">Autenticação do usuário com o SSO</span><span class="sxs-lookup"><span data-stu-id="66e61-130">User authentication with SSO</span></span>

<span data-ttu-id="66e61-131">Para usar o SSO para autenticar o usuário, seu código em um arquivo de função ou painel de tarefas chama o método [getAccessTokenAsync](/javascript/api/office/office.auth#getaccesstokenasync-options--callback-).</span><span class="sxs-lookup"><span data-stu-id="66e61-131">To use SSO to authenticate the user, your code in a task pane or function file calls the [getAccessTokenAsync](/javascript/api/office/office.auth#getaccesstokenasync-options--callback-) method.</span></span> <span data-ttu-id="66e61-132">Se o usuário não estiver conectado ao Office, o Office abrirá uma caixa de diálogo e o navegará para a página de logon do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="66e61-132">If the user is not signed into Office, Office will open a dialog and navigate it to the Azure Active Directory login page.</span></span> <span data-ttu-id="66e61-133">Depois que o usuário estiver conectado ou se o usuário já tiver entrado, o método retorna um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="66e61-133">After the user is signed in, or if the user is already signed in, the method returns an access token.</span></span> <span data-ttu-id="66e61-134">O token é um token de Bootstrap no fluxo **On Behalf Of**.</span><span class="sxs-lookup"><span data-stu-id="66e61-134">The token is a bootstrap token in the **On Behalf Of** flow.</span></span> <span data-ttu-id="66e61-135">(Confira [Acessar o Microsoft Graph com o SSO](#access-to-microsoft-graph-with-sso).) No entanto, ele também pode ser usado como um token de ID, pois inclui várias declarações exclusivas para o usuário atual, incluindo `preferred_username`, `name`, `sub` e `oid`.</span><span class="sxs-lookup"><span data-stu-id="66e61-135">(See [Access to Microsoft Graph with SSO](#access-to-microsoft-graph-with-sso).) However, it can be used as an ID token as well, because it contains several claims that are unique to the current user, including `preferred_username`, `name`, `sub`, and `oid`.</span></span> <span data-ttu-id="66e61-136">Para obter orientação sobre qual propriedade usar como a ID de usuário final, consulte [Tokensde acesso da plataforma de identidade da Microsoft](https://docs.microsoft.com/pt-BR/azure/active-directory/develop/access-tokens#payload-claims).</span><span class="sxs-lookup"><span data-stu-id="66e61-136">For guidance on which property to use as the ultimate user ID, see [Microsoft identity platform access tokens](https://docs.microsoft.com/en-us/azure/active-directory/develop/access-tokens#payload-claims).</span></span> <span data-ttu-id="66e61-137">Para obter um exemplo de um desses tokens, consulte o [Exemplo de token de acesso](sso-in-office-add-ins.md#example-access-token).</span><span class="sxs-lookup"><span data-stu-id="66e61-137">For an example of a one of these tokens, see the [Example access token](sso-in-office-add-ins.md#example-access-token).</span></span>

<span data-ttu-id="66e61-138">Após o seu código ter extraído a declaração desejada no token, ele usará esse valor para pesquisar o usuário em uma tabela de usuário ou banco de dados de usuário que você mantém.</span><span class="sxs-lookup"><span data-stu-id="66e61-138">After your code has extracted the desired claim from the token, it uses that value to look up the user in a user table or user database that you maintain.</span></span> <span data-ttu-id="66e61-139">Use o banco de dados para armazenar informações relativas ao usuário, como as preferências do usuário ou o estado da conta do usuário.</span><span class="sxs-lookup"><span data-stu-id="66e61-139">Use the database to store user-relative information such as the user's preferences or the state of the user's account.</span></span> <span data-ttu-id="66e61-140">Uma vez que você está usando o SSO, os usuários não entram separadamente no seu suplemento, assim você não precisa armazenar uma senha para o usuário.</span><span class="sxs-lookup"><span data-stu-id="66e61-140">Since you are using SSO, your users don't sign-in separately to your add-in, so you do not need to store a password for the user.</span></span>

<span data-ttu-id="66e61-141">Antes de começar a implementar a autenticação do usuário com o SSO, certifique-se de que você está totalmente familiarizado com o artigo [Habilitar o logon único para Suplementos do Office](sso-in-office-add-ins.md). Observe também estes exemplos:</span><span class="sxs-lookup"><span data-stu-id="66e61-141">Before you begin implementing user authentication with SSO, be sure that you are thoroughly familiar with the article [Enable single sign-on for Office Add-ins](sso-in-office-add-ins.md). Note also these samples:</span></span>

- <span data-ttu-id="66e61-142">[Suplemento do Office NodeJS SSO](https://github.com/OfficeDev/Office-Add-in-NodeJS-SSO), especialmente o arquivo [auth.ts](https://github.com/OfficeDev/Office-Add-in-NodeJS-SSO/blob/master/Completed/src/auth.ts), que usa a biblioteca [jswebtoken](https://github.com/auth0/node-jsonwebtoken) para decodificar e analisar o token.</span><span class="sxs-lookup"><span data-stu-id="66e61-142">[Office Add-in NodeJS SSO](https://github.com/OfficeDev/Office-Add-in-NodeJS-SSO), especially the file [auth.ts](https://github.com/OfficeDev/Office-Add-in-NodeJS-SSO/blob/master/Completed/src/auth.ts) which uses the library [jswebtoken](https://github.com/auth0/node-jsonwebtoken) to decode and parse the token.</span></span> <span data-ttu-id="66e61-143">(Esse exemplo, no entanto, não usa o token como um token de ID.</span><span class="sxs-lookup"><span data-stu-id="66e61-143">(This sample, however, does not use the token as an ID token.</span></span> <span data-ttu-id="66e61-144">Ele a usa para obter acesso ao Microsoft Graph com o fluxo **On Behalf Of**.)</span><span class="sxs-lookup"><span data-stu-id="66e61-144">It uses it to get access to Microsoft Graph with the **On Behalf Of** flow.)</span></span>
- <span data-ttu-id="66e61-145">[O suplemento do Office ASP.NET SSO](https://github.com/OfficeDev/Office-Add-in-ASPNET-SSO), especialmente o arquivo [ValuesController.ts](https://github.com/OfficeDev/Office-Add-in-ASPNET-SSO/blob/master/Complete/Office-Add-in-ASPNET-SSO-WebAPI/Controllers/ValuesController.cs), que usa a biblioteca [System.Security.Claims.ClaimsPrincipal](https://docs.microsoft.com/dotnet/api/system.security.claims.claimsprincipal) para extrair declarações do token.</span><span class="sxs-lookup"><span data-stu-id="66e61-145">[Office Add-in ASP.NET SSO](https://github.com/OfficeDev/Office-Add-in-ASPNET-SSO), especially the file [ValuesController.ts](https://github.com/OfficeDev/Office-Add-in-ASPNET-SSO/blob/master/Complete/Office-Add-in-ASPNET-SSO-WebAPI/Controllers/ValuesController.cs) which uses the library [System.Security.Claims.ClaimsPrincipal](https://docs.microsoft.com/dotnet/api/system.security.claims.claimsprincipal) class to extract claims from the token.</span></span> <span data-ttu-id="66e61-146">(Esse exemplo, no entanto, não usa o token como um token de ID.</span><span class="sxs-lookup"><span data-stu-id="66e61-146">(This sample, however, does not use the token as an ID token.</span></span> <span data-ttu-id="66e61-147">Ele extrai uma `scope`declaração do token e a usa para obter acesso ao Microsoft Graph com o fluxo **On Behalf Of**).</span><span class="sxs-lookup"><span data-stu-id="66e61-147">It extracts a `scope` claim from the token and uses it to get access to Microsoft Graph with the **On Behalf Of** flow.)</span></span>

## <a name="access-to-microsoft-graph-with-sso"></a><span data-ttu-id="66e61-148">Acesso ao Microsoft Graph com oSSO</span><span class="sxs-lookup"><span data-stu-id="66e61-148">Access to Microsoft Graph with SSO</span></span>

<span data-ttu-id="66e61-149">Para usar o SSO para acessar o Microsoft Graph, seu suplemento em um arquivo de função ou painel de tarefas chama o método [getAccessTokenAsync](/javascript/api/office/office.auth#getaccesstokenasync-options--callback-).</span><span class="sxs-lookup"><span data-stu-id="66e61-149">To use SSO to get access to Microsoft Graph, your add-in in a task pane or function file calls the [getAccessTokenAsync](/javascript/api/office/office.auth#getaccesstokenasync-options--callback-) method.</span></span> <span data-ttu-id="66e61-150">Se o usuário não estiver conectado ao Office, o Office abrirá uma caixa de diálogo e o navegará para a página de logon do Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="66e61-150">If the user is not signed into Office, Office will open a dialog and navigate it to the Azure Active Directory login page.</span></span> <span data-ttu-id="66e61-151">Depois que o usuário estiver conectado ou se o usuário já tiver entrado, o método retorna um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="66e61-151">After the user is signed in, or if the user is already signed in, the method returns an access token.</span></span> <span data-ttu-id="66e61-152">O token é um token de Bootstrap no fluxo **On Behalf Of**.</span><span class="sxs-lookup"><span data-stu-id="66e61-152">The token is a bootstrap token in the **On Behalf Of** flow.</span></span> <span data-ttu-id="66e61-153">Especificamente, ele tem uma `scope` Declaração com o valor `access_as_user`.</span><span class="sxs-lookup"><span data-stu-id="66e61-153">Specifically, it has a `scope` claim with the value `access_as_user`.</span></span> <span data-ttu-id="66e61-154">Para mais instruções sobre as declarações no token, consulte [Tokens de acesso à plataforma de identidade da Microsoft](https://docs.microsoft.com/pt-BR/azure/active-directory/develop/access-tokens#payload-claims).</span><span class="sxs-lookup"><span data-stu-id="66e61-154">For guidance about the claims in the token, see [Microsoft identity platform access tokens](https://docs.microsoft.com/en-us/azure/active-directory/develop/access-tokens#payload-claims).</span></span> <span data-ttu-id="66e61-155">Para obter um exemplo de um desses tokens, consulte o [Exemplo de token de acesso](sso-in-office-add-ins.md#example-access-token).</span><span class="sxs-lookup"><span data-stu-id="66e61-155">For an example of a one of these tokens, see the [Example access token](sso-in-office-add-ins.md#example-access-token).</span></span>

<span data-ttu-id="66e61-156">Após o código obter o token, ele o usará o fluxo **On Behalf Of** para obter um segundo token: um token de acesso ao Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="66e61-156">After your code obtains the token, it uses it in the **On Behalf Of** flow to obtain a second token: an access token to Microsoft Graph.</span></span>

<span data-ttu-id="66e61-157">Antes de começar a implementar o SSO do Office, certifique-se de que você está totalmente familiarizado com esses dois artigos:</span><span class="sxs-lookup"><span data-stu-id="66e61-157">Before you begin implementing Office SSO, be sure that you are thoroughly familiar with these two articles:</span></span>

- [<span data-ttu-id="66e61-158">Habilitar o logon único para Suplementos do Office</span><span class="sxs-lookup"><span data-stu-id="66e61-158">Enable single sign-on for Office Add-ins</span></span>](sso-in-office-add-ins.md)
- [<span data-ttu-id="66e61-159">Autorizar o Microsoft Graph com SSO</span><span class="sxs-lookup"><span data-stu-id="66e61-159">Authorize to Microsoft Graph with SSO</span></span>](authorize-to-microsoft-graph.md)

<span data-ttu-id="66e61-160">Você também deve ler pelo menos um dos artigos descritos aqui.</span><span class="sxs-lookup"><span data-stu-id="66e61-160">You should also read at least one of the walkthrough articles listed here.</span></span> <span data-ttu-id="66e61-161">Mesmo que você não execute as etapas, elas contêm informações valiosas sobre a implementação do SSO do Office e o fluxo **On Behalf Of**.</span><span class="sxs-lookup"><span data-stu-id="66e61-161">Even if you don't carry out the steps, these contain valuable information about how you implement Office SSO and the **On Behalf Of** flow.</span></span> 

- [<span data-ttu-id="66e61-162">Criar um Suplemento do Office com ASP.NET que usa logon único</span><span class="sxs-lookup"><span data-stu-id="66e61-162">Create an ASP.NET Office Add-in that uses single sign-on</span></span>](create-sso-office-add-ins-aspnet.md)
- [<span data-ttu-id="66e61-163">Crie um Suplemento do Office com Node.js que use logon único</span><span class="sxs-lookup"><span data-stu-id="66e61-163">Create a Node.js Office Add-in that uses single sign-on</span></span>](create-sso-office-add-ins-nodejs.md)

<span data-ttu-id="66e61-164">Observe também estes exemplos:</span><span class="sxs-lookup"><span data-stu-id="66e61-164">Note also these samples:</span></span>

- [<span data-ttu-id="66e61-165">SSO do NodeJS do Suplemento do Office</span><span class="sxs-lookup"><span data-stu-id="66e61-165">Office Add-in NodeJS SSO</span></span>](https://github.com/OfficeDev/Office-Add-in-NodeJS-SSO)
- [<span data-ttu-id="66e61-166">SSO do ASP.NET do Suplemento do Office</span><span class="sxs-lookup"><span data-stu-id="66e61-166">Office Add-in ASP.NET SSO</span></span>](https://github.com/OfficeDev/Office-Add-in-ASPNET-SSO)

## <a name="access-to-non-microsoft-data-sources"></a><span data-ttu-id="66e61-167">Acesso a fontes de dados que não são da Microsoft:</span><span class="sxs-lookup"><span data-stu-id="66e61-167">Access to non-Microsoft data sources</span></span>

<span data-ttu-id="66e61-168">Serviços online populares, incluindo o Google, o Facebook, o LinkedIn, o SalesForce e o GitHub, permitem que os desenvolvedores forneçam acesso para os usuários a suas contas em outros aplicativos.</span><span class="sxs-lookup"><span data-stu-id="66e61-168">Popular online services, including Office 365, Google, Facebook, LinkedIn, SalesForce, and GitHub, enable developers to give users access to their accounts in other applications.</span></span> <span data-ttu-id="66e61-169">Isso dá a você a capacidade de incluir esses serviços no seu Suplemento do Office.</span><span class="sxs-lookup"><span data-stu-id="66e61-169">This gives you the ability to include these services in your Office Add-in.</span></span> <span data-ttu-id="66e61-170">Para obter uma visão geral das maneiras como seu suplemento pode fazer isso, confira [Autorizar serviços externos em seu Suplemento do Office](auth-external-add-ins.md).</span><span class="sxs-lookup"><span data-stu-id="66e61-170">For an overview of the ways that your add-in can do this, see [Authorize external services in your Office Add-in](auth-external-add-ins.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="66e61-171">Antes de começar a codificar, descubra se a fonte de dados permite que o logon na tela seja aberto em um iFrame.</span><span class="sxs-lookup"><span data-stu-id="66e61-171">Before you begin coding, find out if the data source allows its login in screen to be opened in an iFrame.</span></span> <span data-ttu-id="66e61-172">Quando um suplemento do Office está sendo executado no *Office na Web*, o painel de tarefas é um iFrame.</span><span class="sxs-lookup"><span data-stu-id="66e61-172">When an Office Add-in is running on *Office on the web*, the task pane is an iFrame.</span></span> <span data-ttu-id="66e61-173">Se a fonte de dados não permitir que sua tela de logon seja aberta em um iFrame, você precisará abrir a tela de logon em uma caixa de diálogo aberta com a API de Diálogo do Office.</span><span class="sxs-lookup"><span data-stu-id="66e61-173">If the data source does not allow its login screen to be opened in an iFrame, then you will need to open the login screen in a dialog opened with the Office Dialog API.</span></span> <span data-ttu-id="66e61-174">Para saber mais, confira [Autenticação com a API de Diálogo do Office](auth-with-office-dialog-api.md).</span><span class="sxs-lookup"><span data-stu-id="66e61-174">For more information, see [Authentication with the Office Dialog API](auth-with-office-dialog-api.md).</span></span>
