---
title: Modelo de objeto de JavaScript do Word em Suplementos do Office
description: Aprenda as classes mais importantes no modelo de objeto de JavaScript específico do Word.
ms.date: 10/14/2020
localization_priority: Priority
ms.openlocfilehash: c85c56987ef5de7c087064ac668f137326089642
ms.sourcegitcommit: 42e6cfe51d99d4f3f05a3245829d764b28c46bbb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2020
ms.locfileid: "48740865"
---
# <a name="word-javascript-object-model-in-office-add-ins"></a>Modelo de objeto de JavaScript do Word em Suplementos do Office

Este artigo descreve conceitos fundamentais para o uso da [API JavaScript do Word](../reference/overview/word-add-ins-reference-overview.md) para criar suplementos. Ele introduz os principais conceitos fundamentais para o sua da API.

> [!IMPORTANT]
> Confira [Usar o modelo da API específica do aplicativo](../develop/application-specific-api-model.md) para saber mais sobre a natureza assíncrona das APIs do Word e como elas funcionam com o documento.

## <a name="officejs-apis-for-word"></a>APIs Office.js para Word

Um suplemento do Word interage com objetos no Excel usando a API JavaScript do Office, que inclui dois modelos de objetos JavaScript:

* **API JavaScript do Word**: a [API JavaScript do Word](../reference/overview/word-add-ins-reference-overview.md) fornece objetos fortemente tipados que você pode usar para acessar documentos, intervalos, tabelas, listas, formatação e mais.

* **As APIs Comuns**: a [API Comum](/javascript/api/office) pode ser usada para acessar recursos como interface de usuário, caixas de diálogo e configurações de cliente, que são comuns entre vários tipos de aplicativos do Office.

Embora você provavelmente usará a API JavaScript do Word para desenvolver a maioria das funcionalidades em suplementos que visam o Word, você também usará objetos na API comum. Por exemplo:

* [Context](/javascript/api/office/office.context): O `Context`objeto representa o ambiente de tempo de execução do suplemento e fornece acesso a objetos principais da API. Ele consiste em configuração do documento, como `contentLanguage` e `officeTheme`, além de fornecer informações sobre o ambiente de tempo de execução do suplemento, como `host` e `platform`. Além disso, ele fornece o método `requirements.isSetSupported()`, que você pode usar para verificar se um conjunto de requisitos especificado é suportado pelo aplicativo Excel onde o suplemento está sendo executado.
* [Documento](/javascript/api/office/office.document): o `Document` objeto fornece o método `getFileAsync()`, que você pode usar para baixar o arquivo do Word em que o suplemento está sendo executado.

![Imagem das diferentes entre a API JS do Word e as APIs comuns](../images/word-js-api-common-api.png)

## <a name="word-specific-object-model"></a>Modelo de objeto específico do Word

Para entender as APIs do Word, você deve entender como os componentes de um documento estão relacionados entre si.

* O **documento** contém as **seções**, e entidades no nível de documento, como as configurações e partes XML Personalizadas.
* Uma **seção** contém um**corpo**.
* Um **corpo** dá acesso a **parágrafo**s, **ContentControl**s e aos objetos do **intervalo**, entre outros.
* Um **intervalo** representa uma área contínua de conteúdo, incluindo texto, espaço em branco, **tabela**s e imagens. Ele também contém a maioria dos métodos de manipulação de texto.
* Uma **Lista** representa o texto em uma lista numerada ou em lista com marcadores.

## <a name="see-also"></a>Confira também

- [Visão geral da API JavaScript do Word](../reference/overview/word-add-ins-reference-overview.md)
- [Criar seu primeiro suplemento do Word](../quickstarts/word-quickstart.md)
- [Tutorial de suplemento do Word](../tutorials/word-tutorial.md)
- [Referências da API JavaScript do Word](/javascript/api/word)
- [Saiba mais sobre o Programa de Desenvolvedores do Microsoft 365](https://developer.microsoft.com/microsoft-365/dev-program)