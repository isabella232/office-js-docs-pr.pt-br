---
title: Fazendo referência à biblioteca da API JavaScript do Office
description: Saiba como fazer referência à biblioteca da API JavaScript do Office e definições de tipo no suplemento.
ms.date: 06/23/2020
localization_priority: Normal
ms.openlocfilehash: 64dd08329b7bbc8c249bd270a431b6cbe93ec52c
ms.sourcegitcommit: 9609bd5b4982cdaa2ea7637709a78a45835ffb19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2020
ms.locfileid: "47293181"
---
# <a name="referencing-the-office-javascript-api-library"></a>Fazendo referência à biblioteca da API JavaScript do Office

A biblioteca da [API JavaScript do Office](../reference/javascript-api-for-office.md) fornece as APIs que o suplemento pode usar para interagir com o aplicativo do Office. A maneira mais simples de fazer referência à biblioteca é usar a CDN (rede de distribuição de conteúdo) adicionando a seguinte `<script>` marca dentro da `<head>` seção da página HTML:  

```html
<head>
    ...
    <script src="https://appsforoffice.microsoft.com/lib/1/hosted/office.js" type="text/javascript"></script>
</head>
```

Isso baixará e armazenará em cache os arquivos da API JavaScript do Office na primeira vez em que seu suplemento for carregado para garantir que ele esteja usando a implementação mais atualizada de Office.js e seus arquivos associados para a versão especificada.

> [!IMPORTANT]
> Você deve fazer referência à API JavaScript do Office de dentro da `<head>` seção da página para garantir que a API seja totalmente inicializada antes de qualquer elemento body. Os aplicativos do Office exigem que os suplementos inicializem dentro de 5 segundos de ativação. Se seu suplemento não ativar dentro deste limite, ele será declarado sem resposta e uma mensagem de erro será exibida ao usuário.

## <a name="api-versioning-and-backward-compatibility"></a>Versão da API e compatibilidade com versões anteriores

No trecho de código HTML anterior, o `/1/` na frente da `office.js` URL de CDN especifica a versão incremental mais recente na versão 1 de Office.js. Como a API JavaScript do Office mantém a compatibilidade com versões anteriores, a versão mais recente continuará a dar suporte a membros da API que foram introduzidos anteriormente na versão 1. Se você precisar atualizar um projeto existente, confira [atualizar a versão da API JavaScript do Office e dos arquivos de esquema de manifesto](update-your-javascript-api-for-office-and-manifest-schema-version.md). 

Caso planeje publicar seu Suplemento do Office no AppSource, você deve usar esta referência da CDN. As referências locais são adequadas somente para cenários internos, de depuração e de desenvolvimento.

> [!NOTE]
> Para usar APIs de visualização, faça referência à versão de visualização da biblioteca da API JavaScript do Office na CDN: `https://appsforoffice.microsoft.com/lib/beta/hosted/office.js`.

## <a name="enabling-intellisense-for-a-typescript-project"></a>Habilitando o IntelliSense para um projeto TypeScript

Além de fazer referência à API JavaScript do Office, conforme descrito anteriormente, você também pode habilitar o IntelliSense para o projeto de suplemento do TypeScript usando as definições de tipo do [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/office-js). Para fazer isso, execute o seguinte comando em um prompt do sistema habilitado para nós (ou janela do git bash) da raiz da pasta do seu projeto. Você deve ter o [Node.js](https://nodejs.org) instalado (que inclui o npm).

```command&nbsp;line
npm install --save-dev @types/office-js
```

## <a name="preview-apis"></a>APIs de visualização

As novas APIs JavaScript são primeiro introduzidas em "Preview" e, posteriormente, se tornam parte de um conjunto de requisitos específico, após o teste suficiente e o feedback do usuário é necessário.

[!INCLUDE [Information about using preview APIs](../includes/using-preview-apis-host.md)]

## <a name="see-also"></a>Confira também

- [Entendendo a API JavaScript do Office](understanding-the-javascript-api-for-office.md)
- [API JavaScript para Office](../reference/javascript-api-for-office.md)
