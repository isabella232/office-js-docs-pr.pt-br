---
title: Instale a última versão do Office
description: Informações sobre como desativar essa opção para obter as versões mais recentes do Office.
ms.date: 07/07/2020
localization_priority: Normal
ms.openlocfilehash: df10d64d69b64283321bbad79aca7f7f6d482dd1
ms.sourcegitcommit: 7ef14753dce598a5804dad8802df7aaafe046da7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2020
ms.locfileid: "45093613"
---
# <a name="install-the-latest-version-of-office"></a>Instale a última versão do Office

Novos recursos de desenvolvedor, inclusive os que ainda estão na visualização, são fornecidos primeiro aos assinantes que aceitam obter as últimas compilações do Office.

## <a name="opt-in-to-getting-the-latest-builds"></a>Aceitar para receber as versões mais recentes

Aceitar para receber as versões mais recentes do Office:

- Se você for um assinante da família Microsoft 365, pessoal ou universidade, confira [ser um Office Insider](https://insider.office.com).
- Se você for um cliente do Microsoft 365 para clientes de negócios, confira [instalar a versão de primeiro lançamento para os clientes do microsoft 365 aplicativos para empresas](https://support.office.com/article/Install-the-First-Release-build-for-Office-365-for-business-customers-4dd8ba40-73c0-4468-b778-c7b744d03ead).
- Se você estiver executando o Office em um Mac:
  - Abra um aplicativo do Office.
  - Selecione **Verificar Atualizações** no menu Ajuda.
  - Na caixa Microsoft AutoUpdate, marque a caixa para participar do programa Office Insider.

## <a name="get-the-latest-build"></a>Obtenha a versão mais recente:

Para receber as versões mais recentes do Office:

1. Baixar a [Ferramenta de Implantação do Office](https://www.microsoft.com/download/details.aspx?id=49117).
2. Execute a ferramenta. Isso extrai estes dois arquivos: Setup.exe e configuration.xml.
3. Substitua o arquivo configuration.xml pelo [Arquivo de Configuração do Primeiro Lançamento](https://raw.githubusercontent.com/OfficeDev/Office-Add-in-Commands-Samples/master/Tools/FirstReleaseConfig/configuration.xml).
4. Execute o seguinte comando como administrador: `setup.exe /configure configuration.xml`

> [!NOTE]
> O comando pode demorar muito para ser executado sem indicar o progresso.

Quando o processo de instalação for concluído, você terá os últimos aplicativos do Office instalados. Para verificar se você tem a última compilação, vá até **arquivo** > **conta** em qualquer aplicativo do Office. Em Atualizações do Office, você verá o rótulo (Office Insiders) acima do número de versão.

![Uma captura de tela que mostra informações do produto com o rótulo Office Insiders](../images/office-insiders-label.png)

## <a name="minimum-office-builds-for-office-javascript-api-requirement-sets"></a>Builds mínimos do Office para conjuntos de requisitos de API JavaScript para Office

Para saber mais sobre os builds mínimos de produtos para cada plataforma dos conjuntos de requisitos de API, confira o seguinte:

- [Conjuntos de requisitos da API JavaScript do Excel](../reference/requirement-sets/excel-api-requirement-sets.md)
- [Conjuntos de requisitos da API JavaScript do OneNote](../reference/requirement-sets/onenote-api-requirement-sets.md)
- [Conjuntos de requisitos de API JavaScript do Outlook](../reference/requirement-sets/outlook-api-requirement-sets.md)
- [Conjuntos de requisitos de API JavaScript do PowerPoint](../reference/requirement-sets/powerpoint-api-requirement-sets.md)
- [Conjuntos de requisitos da API JavaScript do Word](../reference/requirement-sets/word-api-requirement-sets.md)
- [Conjuntos de requisitos da API de Caixa de Diálogo](../reference/requirement-sets/dialog-api-requirement-sets.md)
- [Conjuntos de requisitos da API comum do Office](../reference/requirement-sets/office-add-in-requirement-sets.md)
