---
title: Limites para ativação e uso da API em suplementos do Outlook
description: Você deve estar ciente das determinadas diretrizes de ativação e de uso da API e implementar seus suplementos dentro desses limites.
ms.date: 10/31/2019
localization_priority: Normal
ms.openlocfilehash: 15fba6d0be2f638bfa4ffd531da5876a4ccbc876
ms.sourcegitcommit: a3ddfdb8a95477850148c4177e20e56a8673517c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "42165807"
---
# <a name="limits-for-activation-and-javascript-api-for-outlook-add-ins"></a>Limites para ativação e API JavaScript para suplementos do Outlook

A fim de fornecer uma experiência satisfatória para os usuários dos suplementos do Outlook, você deve estar ciente das determinadas diretrizes de ativação e de uso da API e implementar seus suplementos dentro desses limites Essas diretrizes existem para que um suplemento individual não possa exigir do Exchange Server ou do Outlook que gastem um tempo excessivamente longo processando suas regras de ativação ou chamadas à API JavaScript para Office, afetando a experiência do usuário geral no Outlook e outros suplementos. Esses limites se aplicam à criação de regras de ativação no manifesto do suplemento e ao uso das propriedades personalizadas, à configuração de roaming, aos destinatários, às solicitações e respostas EWS (serviços Web do Exchange) e chamadas assíncronas.

> [!NOTE]
> Se o suplemento é executado em um cliente avançado do Outlook, você também deve verificar se o suplemento está funcionando dentro de certos limites de uso dos recursos do tempo de execução.

## <a name="limits-on-where-add-ins-activate"></a>Limites em que os suplementos são ativados

Os suplementos foram projetados apenas para serem ativados na caixa de correio principal do usuário. Os suplementos não são ativados em caixas de correio compartilhadas, pastas de caixas de correio do outro usuário abertas com acesso de representante, caixas de correio de arquivo morto ou pastas públicas.

## <a name="limits-for-activation-rules"></a>Limites para regras de ativação

Siga estas diretrizes ao criar regras de ativação para suplementos do Outlook:

- Limite o tamanho do manifesto a 256 KB. Se você exceder esse limite, não poderá instalar o suplemento do Outlook para uma caixa de correio do Exchange.

- Especifique até 15 regras de ativação para o suplemento. Se você exceder esse limite, não poderá instalar o suplemento.

- Se você usar uma regra [ItemHasKnownEntity](../reference/manifest/rule.md#itemhasknownentity-rule) no corpo do item selecionado, assuma que um cliente avançado do Outlook aplicará a regra somente ao primeiro MB do corpo e não ao restante do corpo acima desse limite. Seu suplemento não seria ativado se só houvessem correspondências após o primeiro MB do corpo. Se você acha que esse é um cenário provável, recrie suas condições para ativação.

- Se você usa expressões regulares nas regras **ItemHasKnownEntity** ou [ItemHasRegularExpressionMatch](../reference/manifest/rule.md#itemhasregularexpressionmatch-rule), esteja ciente dos seguintes limites e diretrizes que geralmente se aplicam a hosts do Outlook e àqueles descritos nas tabelas 1, 2 e 3 que diferem dependendo do host:
   - Especifique no máximo cinco expressões regulares em regras de ativação em um suplemento. Se você exceder esse limite, não poderá instalar um suplemento.
   - Especifique expressões regulares para que os resultados que você espera sejam retornados pela chamada do método **getRegExMatches** nas primeiras 50 correspondências.
   - Pode especificar declarações look-ahead em expressões regulares, mas não look-behind, `(?<=text)` e negative look-behind `(?<!text)`.

A tabela 1 lista os limites e descreve as diferenças no suporte a expressões regulares entre um cliente avançado do Outlook e o Outlook na Web ou dispositivos móveis. O suporte independe de qualquer tipo específico de dispositivo e de corpo de item.

**Tabela 1. Diferenças gerais no suporte para expressões regulares**

|Cliente avançado do Outlook|Outlook na Web ou em dispositivos móveis|
|:-----|:-----|
|Usa o mecanismo de expressões regulares C++ fornecido como parte da biblioteca de modelo padrão do Visual Studio. Esse mecanismo é compatível com as normas ECMAScript 5. |Usa a avaliação da expressão regular que faz parte do JavaScript, é fornecida pelo navegador e dá suporte a um subconjunto dos ECMAScript 5.|
|Devido aos diferentes mecanismos de Regex, espera-se que um Regex que inclua uma classe de caracteres personalizada com base em classes de caracteres predefinidas possa retornar resultados diferentes em um cliente avançado do Outlook do que no Outlook na Web ou em dispositivos móveis.<br/><br/>Por exemplo, a regex `[\s\S]{0,100}` corresponde a qualquer número, entre 0 e 100, de caracteres únicos que sejam um espaço em branco ou um espaço não em branco. Essa Regex retorna resultados diferentes em um cliente avançado do Outlook do que o Outlook na Web e dispositivos móveis.<br/><br/>Você deve reescrever a regex como `(\s\|\S){0,100}` como solução alternativa. Essa solução alternativa para a regex corresponde a qualquer número, entre 0 e 100, de espaço em branco ou não espaço em branco.<br/><br/>Você deve testar cada regex exaustivamente em cada host do Outlook e, se uma regex retornar resultados diferentes, reescreva-a. |Você deve testar cada regex exaustivamente em cada host do Outlook e se uma regex retornar resultados diferentes, reescreva-a.|
|Por padrão, limita a avaliação de todas as expressões regulares de um suplemento para um segundo. Ultrapassar esse limite pode causar a reavaliação por até três vezes. Além do limite de reavaliação, um cliente avançado do Outlook desabilita o suplemento para não buscar a mesma caixa de correio em outros hosts do Outlook.<br/><br/>Os administradores podem substituir esses limites de avaliação usando as chaves de registro **OutlookActivationAlertThreshold** e **OutlookActivationManagerRetryLimit**.|Não dão suporte às mesmas configurações de registro ou monitoramento de recursos de um cliente avançado do Outlook. Mas suplementos com expressões regulares que exigem muito tempo de avaliação em um cliente avançado do Outlook estão desabilitados para a mesma caixa de correio em todos os hosts do Outlook.|

A Tabela 2 lista os limites e descreve as diferenças na parte do corpo do item a que cada Outlook aplica uma expressão regular. Alguns desses limites dependem do tipo de dispositivo e do corpo do item se a expressão regular é aplicada no corpo do item.

**Tabela 2. Limita o tamanho do corpo do item avaliado**

||Cliente avançado do Outlook|Outlook em dispositivos móveis|Outlook na Web|
|:-----|:-----|:-----|:-----|
|Fator forma|Qualquer dispositivo compatível|Smartphones Android, iPad ou iPhone|Qualquer dispositivo com suporte diferente dos smartphones Android, iPad e iPhone|
|Corpo do item de texto sem formatação|Aplica a regex no primeiro 1 MB de dados do corpo, mas não no restante do corpo acima desse limite.|Ativa o suplemento somente se o corpo ficar com menos de 16 mil caracteres.|Ativa o suplemento somente se o corpo ficar com menos de 500 mil caracteres.|
|Corpo do item HTML|Aplica a regex nos primeiros 512 KB de dados do corpo, mas não no restante do corpo acima desse limite. (O número real de caracteres depende da codificação, que pode variar de 1 a 4 bytes por caractere.)|Aplica a regex nos primeiros 64.000 KB de dados do corpo (incluindo caracteres de marca HTML), mas não no restante do corpo acima desse limite.|Ativa o suplemento somente se o corpo ficar com menos de 500 mil caracteres.|

A Tabela 3 lista os limites e descreve as diferenças entre as correspondências que cada um dos hosts do Outlook retorna depois de avaliar uma expressão regular. O suporte independe de um tipo de dispositivo específico, mas pode depender do tipo do corpo do item se a expressão regular é aplicada ao corpo do item.

**Tabela 3. Limites sobre as correspondências retornadas**

||Cliente avançado do Outlook|Outlook na Web ou em dispositivos móveis|
|:-----|:-----|:-----|
|Ordem das correspondências retornadas|Pressuponha que **getRegExMatches** retorna correspondências para a mesma expressão regular aplicada no mesmo item é diferente em um cliente avançado do Outlook do que no Outlook na Web ou em dispositivos móveis.|Pressuponha que **getRegExMatches** retorna correspondências em ordem diferente em um cliente avançado do Outlook e no Outlook na Web ou em dispositivos móveis.|
|Corpo do item de texto sem formatação|**getRegExMatches** retorna correspondências até 1536 caracteres (1,5 KB), no máximo de 50 correspondências.<br/><br/>**Nota**: **getRegExMatches** não retorna correspondências em nenhuma ordem específica na matriz retornada. Em geral, suponha que a ordem de correspondências em um cliente avançado do Outlook para a mesma expressão regular aplicada no mesmo item seja diferente da do Outlook na Web e dispositivos móveis.|**getRegExMatches** retorna qualquer correspondência com até 3072 caracteres (3 KB), com o máximo de 50 correspondências.|
|Corpo do item HTML|**getRegExMatches** retorna qualquer correspondência com até 3072 caracteres (3 KB), com o máximo de 50 correspondências.<br/> <br/> **Observação**: **getRegExMatches** não retorna correspondências em qualquer ordem específica na matriz retornada. Em geral, suponha que a ordem de correspondências em um cliente avançado do Outlook para a mesma expressão regular aplicada no mesmo item seja diferente da do Outlook na Web e dispositivos móveis.|**getRegExMatches** retorna qualquer correspondência com até 3072 caracteres (3 KB), com o máximo de 50 correspondências.|

## <a name="limits-for-javascript-api"></a>Limites para a API JavaScript

Além das diretrizes anteriores para regras de ativação, cada host do Outlook impõe determinados limites ao modelo de objeto do JavaScript, conforme descrito na Tabela 4.

**Tabela 4. Limites para obter ou definir certos dados usando a API JavaScript para Office**

|Recurso|Limite|API relacionada|Descrição|
|:-----|:-----|:-----|:-----|
|Propriedades personalizadas|2.500 caracteres|Objeto [CustomProperties](/javascript/api/outlook/office.CustomProperties) método<br/> <br/>Método [item.loadCustomPropertiesAsync](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#methods)|Limite de todas as propriedades personalizadas para um item de compromisso ou mensagem. Todos os hosts do Outlook retornarão um erro se o tamanho total de todas as propriedades personalizadas de um suplemento exceder esse limite.|
|Configurações de roaming|32 KB número de caracteres|Objeto [RoamingSettings](/javascript/api/outlook/office.RoamingSettings) propriedade<br/><br/> Propriedade [context.roamingSettings](../reference/objectmodel/preview-requirement-set/office.context.md#properties)|Limite para todas as configurações de roaming do suplemento. Todos os hosts do Outlook retornarão um erro se suas configurações ultrapassarem esse limite.|
|Extrair entidades conhecidas|2000 número de caracteres|Método [item.getEntities](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#methods) método<br/> <br/>[item.getEntitiesByType](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#methods) método<br/> <br/>Método [item.getFilteredEntitiesByName](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#methods)|Limite para o Exchange Server extrair entidades conhecidas no corpo do item. O Exchange Server ignora entidades além desse limite. Observe que esse limite independe de o suplemento usar uma regra **ItemHasKnownEntity**.|
|Serviços Web do Exchange|1 MB número de caracteres|Método [mailbox.makeEwsRequestAsync](../reference/objectmodel/preview-requirement-set/office.context.mailbox.md#methods)|Limite para uma solicitação ou resposta a uma chamada **Mailbox.makeEwsRequestAsync**.|
|Destinatários|100 destinatários|Propriedade [item.requiredAttendees](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#properties) propriedade<br/> <br/>Propriedade [item.optionalAttendees](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#properties)<br/> <br/>Propriedade [item.to](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#properties)<br/> <br/>[item.cc](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#properties) método<br/> <br/>[Recipients.addAsync](/javascript/api/outlook/office.Recipients#addasync-recipients--options--callback-) método<br/> <br/>[Recipient.getAsync](/javascript/api/outlook/office.Recipients#getasync-options--callback-) método<br/> <br/>Método [Recipient.setAsync](/javascript/api/outlook/office.Recipients#setasync-recipients--options--callback-)|Limite para os destinatários especificados em cada propriedade.|
|Nome para exibição|255 caracteres|Propriedade [EmailAddressDetails.displayName](/javascript/api/outlook/office.emailaddressdetails#displayname) objeto<br/><br/> [Recipients](/javascript/api/outlook/office.Recipients) propriedade<br/><br/> **item.requiredAttendees** propriedade<br/><br/> Propriedade **item.optionalAttendees** <br/><br/>Propriedade **item.to** <br/><br/>Propriedade **item.cc**|Limite de tamanho de um nome de exibição em um compromisso ou uma mensagem.|
|Definir o assunto|255 caracteres|Método [mailbox.displayNewAppointmentForm](../reference/objectmodel/preview-requirement-set/office.context.mailbox.md#methods) método<br/><br/> [Subject.setAsync](/javascript/api/outlook/office.Subject#setasync-subject--options--callback-) method|Limite para o assunto no formulário do novo compromisso ou para definir o assunto de um compromisso ou uma mensagem.|
|Definir o local|255 caracteres|[Location.setAsync](/javascript/api/outlook/office.Location#setasync-location--options--callback-) método|Limite para definir o local de um compromisso ou solicitação de reunião.|
|Corpo em um novo formulário de compromisso|32 KB número de caracteres|Método **Mailbox.displayNewAppointmentForm**|Limite do corpo em um formulário de novo compromisso.|
|Exibir o corpo de um item existente|32 KB número de caracteres|Método[mailbox.displayAppointmentForm](../reference/objectmodel/preview-requirement-set/office.context.mailbox.md#methods) método<br/><br/> Método [mailbox.displayMessageForm](../reference/objectmodel/preview-requirement-set/office.context.mailbox.md#methods)|Para o Outlook na Web e dispositivos móveis: limite para o corpo em um formulário de compromisso ou mensagem existente.|
|Definir o corpo|1 MB número de caracteres|Método [Body.prependAsync](/javascript/api/outlook/office.Body#prependasync-data--options--callback-) método<br/> <br/>[Body.setAsync](/javascript/api/outlook/office.Body#setasync-data--options--callback-)<br/><br/>[Body.setSelectedDataAsync](/javascript/api/outlook/office.Body#setselecteddataasync-data--options--callback-) method|Limite para configurar o corpo de um item de compromisso ou de mensagem.|
|Número de anexos|499 arquivos no Outlook na Web e dispositivos móveis|Método [item.addFileAttachmentAsync](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#methods) método|Limite do número de arquivos que podem ser anexados a um item para envio. O Outlook na Web e dispositivos móveis geralmente limitam a conexão de até 499 arquivos, por meio da interface do usuário e do **addFileAttachmentAsync**. Um cliente avançado do Outlook não limita especificamente o número de anexos de arquivo. No entanto, todos os hosts do Outlook observam o limite de tamanho dos anexos configurado para o usuário do Exchange Server Confira o "Tamanho dos anexos" na próxima linha.|
|Tamanho dos anexos|Depende do Exchange Server|Método **item.addFileAttachmentAsync**|Há um limite no tamanho de todos os anexos de um item que um administrador pode configurar no Exchange Server da caixa de correio do usuário. Para um cliente avançado do Outlook, isso limita a quantidade de anexos de um item. Para o Outlook na Web e dispositivos móveis, o menor dos dois limites-o número de anexos e o tamanho de todos os anexos-restringe os anexos reais de um item.|
|Nome do arquivo anexo|255 caracteres|Método **item.addFileAttachmentAsync** método|Limite para o comprimento do nome de arquivo de um anexo a ser adicionado a um item.|
|URI do anexo|2048 caracteres|Método **item.addFileAttachmentAsync** método|Limite do URI do nome de arquivo a ser adicionado como um anexo a um item.|
|ID do anexo|100 caracteres|Método [item.addItemAttachmentAsync](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#methods) método<br/><br/> [item.removeAttachmentAsync](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#methods) method|Limite para o tamanho da ID do anexo a ser adicionado ou removido de um item.|
|Chamadas assíncronas|3 chamadas|Método **item.addFileAttachmentAsync** método<br/><br/>**item.addItemAttachmentAsync** método<br/><br/><br/>**item.removeAttachmentAsync** método<br/><br/> [Body.getTypeAsync](/javascript/api/outlook/office.Body#gettypeasync-options--callback-) método<br/><br/>**Body.prependAsync** método<br/><br/>**Body.setSelectedDataAsync** método<br/><br/> [CustomProperties.saveAsync](/javascript/api/outlook/office.CustomProperties#saveasync-callback--asynccontext-) método<br/><br/><br/> [item. LoadCustomPropertiesAysnc](../reference/objectmodel/preview-requirement-set/office.context.mailbox.item.md#methods) método<br/><br/><br/> [Location.getAsync](/javascript/api/outlook/office.Location#getasync-options--callback-) método<br/><br/>**Location.setAsync** método<br/><br/> [mailbox.getCallbackTokenAsync](../reference/objectmodel/preview-requirement-set/office.context.mailbox.md#methods) método<br/><br/> [mailbox.getUserIdentityTokenAsync](../reference/objectmodel/preview-requirement-set/office.context.mailbox.md#methods) método<br/><br/> [mailbox.makeEwsRequestAsync](../reference/objectmodel/preview-requirement-set/office.context.mailbox.md#methods) método<br/><br/>**Recipients.addAsync** método<br/><br/> [Recipients.getAsync](/javascript/api/outlook/office.Recipients#getasync-options--callback-) método<br/><br/>**Recipients.setAsync** método<br/><br/> [RoamingSettings.saveAsync](/javascript/api/outlook/office.RoamingSettings#saveasync-callback-) método<br/><br/> [Subject.getAsync](/javascript/api/outlook/office.Subject#getasync-options--callback-) método<br/><br/>**Subject.setAsync** método<br/><br/> [Time.getAsync](/javascript/api/outlook/office.Time#getasync-options--callback-) método<br/><br/> Método [Time.setAsync](/javascript/api/outlook/office.Time#setasync-datetime--options--callback-)|Para o Outlook na Web ou dispositivos móveis: o limite do número de chamadas assíncronas simultâneas a qualquer momento, à medida que os navegadores permitem apenas um número limitado de chamadas assíncronas para os servidores. |

## <a name="see-also"></a>Confira também

- [Implantar e instalar suplementos do Outlook para teste](testing-and-tips.md)
- [Privacidade, permissões e segurança para suplementos do Outlook](../develop/privacy-and-security.md)