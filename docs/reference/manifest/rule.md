---
title: Elemento Rule no arquivo de manifesto
description: O elemento Rule especifica as regras de ativação que devem ser avaliadas para esse suplemento de email contextual.
ms.date: 05/14/2020
localization_priority: Normal
ms.openlocfilehash: 79b97f2e442e9d8ce59d17467161b5b9b7a7252d
ms.sourcegitcommit: cc6886b47c84ac37a3c957ff85dd0ed526ca5e43
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/12/2020
ms.locfileid: "46641428"
---
# <a name="rule-element"></a>Elemento Rule

Especifica as regras de ativação que devem ser avaliadas para esse suplemento de email contextual.

**Tipo de suplemento:** Email (contextual)

## <a name="contained-in"></a>Contido em

- [OfficeApp](officeapp.md)
- [ExtensionPoint](extensionpoint.md) ([**CustomPane** (preterido)](https://developer.microsoft.com/outlook/blogs/make-your-add-ins-available-in-the-office-ribbon/), [**DetectedEntity**](extensionpoint.md#detectedentity))

## <a name="attributes"></a>Atributos

| Atributo | Obrigatório | Descrição |
|:-----|:-----|:-----|
| **xsi:type** | Sim | O tipo de regra que está sendo definida. |

O tipo de regra pode ser um dos seguintes:

- [ItemIs](#itemis-rule)
- [ItemHasAttachment](#itemhasattachment-rule)
- [ItemHasKnownEntity](#itemhasknownentity-rule)
- [ItemHasRegularExpressionMatch](#itemhasregularexpressionmatch-rule)
- [RuleCollection](#rulecollection)

## <a name="itemis-rule"></a>Regra ItemIs

Define uma regra que é avaliada como true se o item selecionado for do tipo especificado.

### <a name="attributes"></a>Atributos

| Atributo | Obrigatório | Descrição |
|:-----|:-----|:-----|
| **ItemType** | Sim | Especifica o tipo de item para fazer a correspondência. Pode ser `Message` ou `Appointment`. O tipo de item `Message` inclui email, solicitações de reunião, respostas de reunião e cancelamentos de reunião. |
| **FormType** | Não (dentro de [ExtensionPoint](extensionpoint.md)), Sim (dentro de [OfficeApp](officeapp.md)) | Especifica se o aplicativo deve aparecer no formulário de leitura ou edição do item. Pode ser um dos seguintes: `Read`, `Edit`, `ReadOrEdit`. Se não for especificado em um `Rule` dentro de um `ExtensionPoint`, esse valor DEVERÁ ser `Read`. |
| **ItemClass** | Não | Especifica a classe de mensagens personalizada para fazer a correspondência. Para saber mais, confira o artigo [Ativar um suplemento de email no Outlook para uma classe de mensagens específica](../../outlook/activation-rules.md). |
| **IncludeSubClasses** | Não | Especifica se a regra deve ser avaliada como true se o item pertencer a uma subclasse da classe de mensagens especificada. O padrão é `false`. |

### <a name="example"></a>Exemplo

```XML
<Rule xsi:type="ItemIs" ItemType= "Message" />
```

## <a name="itemhasattachment-rule"></a>Regra ItemHasAttachment

Define uma regra que é avaliada como true se o item contiver um anexo.

### <a name="example"></a>Exemplo

```XML
<Rule xsi:type="ItemHasAttachment" />
```

## <a name="itemhasknownentity-rule"></a>Regra ItemHasKnownEntity

Define uma regra que é avaliada como true se o item contiver texto do tipo de entidade especificada em seu assunto ou corpo.

### <a name="attributes"></a>Atributos

| Atributo | Obrigatório | Descrição |
|:-----|:-----|:-----|
| **EntityType** | Sim | Especifica o tipo de entidade que deve ser encontrado para que a regra para que ela seja avaliada como true. Pode ser um dos seguintes: `MeetingSuggestion`, `TaskSuggestion`, `Address`, `Url`, `PhoneNumber`, `EmailAddress`, ou `Contact`. |
| **RegExFilter** | Não | Especifica uma expressão regular para executar esta entidade para ativação. |
| **FilterName** | Não | Especifica o nome do filtro de expressões regulares para que seja possível consultá-lo posteriormente no código do seu suplemento. |
| **IgnoreCase** | Não | Especifica se deve ignorar maiúsculas e minúsculas ao fazer a correspondência da expressão regular especificada por **RegExFilter**. |
| **Realce** | Não | **Observação:** isso se aplica somente aos elementos **Rule** dentro dos elementos **ExtensionPoint**. Especifica como o cliente deve realçar entidades correspondentes. Pode ser um dos seguintes: `all` ou `none`. Se não for especificado, o valor padrão será `all`. |

### <a name="example"></a>Exemplo

```XML
<Rule xsi:type="ItemHasKnownEntity" EntityType="EmailAddress" />
```

## <a name="itemhasregularexpressionmatch-rule"></a>Regra ItemHasRegularExpressionMatch

Define uma regra que é avaliada como true se uma correspondência para a expressão regular especificada pode ser encontrada na propriedade especificada do item.

### <a name="attributes"></a>Atributos

| Atributo | Obrigatório | Descrição |
|:-----|:-----|:-----|
| **RegExName** | Sim | Especifica o nome da expressão regular para que você possa fazer referência à expressão no código de seu suplemento. |
| **RegExValue** | Sim | Especifica a expressão regular que será avaliada para determinar se o suplemento de email deve ser mostrado. |
| **PropertyName** | Sim | Especifica o nome da propriedade em relação a qual expressão regular será avaliada. Pode ser um dos seguintes: `Subject`, `BodyAsPlaintext`, `BodyAsHTML` ou `SenderSMTPAddress`.<br/><br/>Se você especificar `BodyAsHTML`, o Outlook só aplicará a expressão regular se o corpo do item for HTML. Caso contrário, o Outlook não retornará nenhuma correspondência para essa expressão regular.<br/><br/>Se você especificar `BodyAsPlaintext`, o Outlook sempre aplicará a expressão regular no corpo do item.<br/><br/>**Observação:** você deve configurar o atributo **PropertyName** para `BodyAsPlaintext` se você especificar o atributo **realçar** para o elemento **regra**.|
| **IgnoreCase** | Não | Especifica se deve ignorar maiúsculas e minúsculas ao fazer a correspondência da expressão regular especificada pelo atributo **RegExName**. |
| **Realce** | Não | Especifica como o cliente deve realçar texto correspondente. Esse atributo pode ser aplicado apenas à elementos **regra** dentro dos elementos **ExtensionPoint**. Pode ser um dos seguintes: `all` ou `none`. Se não for especificado, o valor padrão será `all`.<br/><br/>**Observação:** você deve configurar o atributo **PropertyName** para `BodyAsPlaintext` se você especificar o atributo **realçar** para o elemento **regra**.
|

### <a name="example"></a>Exemplo

```XML
<Rule xsi:type="ItemHasRegularExpressionMatch" RegExName="SupportArticleNumber" RegExValue="(\W|^)kb\d{6}(\W|$)" PropertyName="BodyAsHTML" IgnoreCase="true" />
```

## <a name="rulecollection"></a>RuleCollection

Define uma coleção de regras e o operador lógico a ser usado ao avaliá-las.

### <a name="attributes"></a>Atributos

| Atributo | Obrigatório | Descrição |
|:-----|:-----|:-----|
| **Mode** | Sim | Especifica o operador lógico a ser usado quando estiver avaliando essa coleção de regras. Pode ser: `And` ou `Or`. |

### <a name="example"></a>Exemplo

```XML
<Rule xsi:type="RuleCollection" Mode="And">
  <Rule xsi:type="ItemIs" ItemType="Message" />
  <Rule xsi:type="ItemHasKnownEntity" EntityType="MeetingSuggestion" />
  <Rule xsi:type="ItemHasKnownEntity" EntityType="Address" Highlight="none" />
</Rule>
```

## <a name="see-also"></a>Confira também

- [Regras de ativação para suplementos do Outlook](../../outlook/activation-rules.md)
- [Corresponder cadeias de caracteres em um item do Outlook como entidades conhecidas](../../outlook/match-strings-in-an-item-as-well-known-entities.md)
- [Usar regras de ativação de expressões regulares para mostrar um suplemento do Outlook](../../outlook/use-regular-expressions-to-show-an-outlook-add-in.md)
