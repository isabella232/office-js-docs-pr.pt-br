---
title: Criar um suplemento do Outlook Mobile para um provedor de reunião online
description: Descreve como configurar um suplemento móvel do Outlook para um provedor de serviços de reunião online.
ms.topic: article
ms.date: 06/25/2020
localization_priority: Normal
ms.openlocfilehash: d3dd1f035c69b668c05f80b36ef48108b8a9cecc
ms.sourcegitcommit: 83f9a2fdff81ca421cd23feea103b9b60895cab4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "47431070"
---
# <a name="create-an-outlook-mobile-add-in-for-an-online-meeting-provider"></a>Criar um suplemento do Outlook Mobile para um provedor de reunião online

A configuração de uma reunião online é uma experiência principal para um usuário do Outlook e é fácil [criar uma reunião do teams com o Outlook](/microsoftteams/teams-add-in-for-outlook) Mobile. No entanto, a criação de uma reunião online no Outlook com um serviço que não seja da Microsoft pode ser complicada. Ao implementar esse recurso, os provedores de serviços podem simplificar a experiência de criação de reunião online para os usuários de suplementos do Outlook.

> [!IMPORTANT]
> Este recurso só é suportado no Android com uma assinatura do Microsoft 365.

Neste artigo, você aprenderá como configurar seu suplemento do Outlook Mobile para permitir que os usuários organizem e ingressem em uma reunião usando o serviço de reunião online. Neste artigo, vamos usar um provedor de serviço de reunião online fictício, "contoso".

## <a name="set-up-your-environment"></a>Configurar seu ambiente

Conclua o [início rápido do Outlook](../quickstarts/outlook-quickstart.md?tabs=yeomangenerator) que cria um projeto de suplemento com o gerador Yeoman para suplementos do Office.

## <a name="configure-the-manifest"></a>Configurar o manifesto

Para permitir que os usuários criem reuniões online com seu suplemento, você deve configurar o `MobileOnlineMeetingCommandSurface` ponto de extensão no manifesto no elemento pai `MobileFormFactor` . Não há suporte para outros fatores de formulário.

1. Em seu editor de código, abra o projeto de início rápido.

1. Abra o arquivo **manifest.xml** localizado na raiz do seu projeto.

1. Selecione o `<VersionOverrides>` nó inteiro (incluindo marcas de abertura e fechamento) e substitua-o pelo seguinte XML.

```xml
<VersionOverrides xmlns="http://schemas.microsoft.com/office/mailappversionoverrides" xsi:type="VersionOverridesV1_0">
  <VersionOverrides xmlns="http://schemas.microsoft.com/office/mailappversionoverrides/1.1" xsi:type="VersionOverridesV1_1">
    <Description resid="residDescription"></Description>
    <Requirements>
      <bt:Sets>
        <bt:Set Name="Mailbox" MinVersion="1.3"/>
      </bt:Sets>
    </Requirements>
    <Hosts>
      <Host xsi:type="MailHost">
        <DesktopFormFactor>
          <FunctionFile resid="residFunctionFile"/>
          <ExtensionPoint xsi:type="AppointmentOrganizerCommandSurface">
            <OfficeTab id="TabDefault">
              <Group id="apptComposeGroup">
                <Label resid="residDescription"/>
                <Control xsi:type="Button" id="insertMeetingButton">
                  <Label resid="residLabel"/>
                  <Supertip>
                    <Title resid="residLabel"/>
                    <Description resid="residTooltip"/>
                  </Supertip>
                  <Icon>
                    <bt:Image size="16" resid="icon-16"/>
                    <bt:Image size="32" resid="icon-32"/>
                    <bt:Image size="64" resid="icon-64"/>
                    <bt:Image size="80" resid="icon-80"/>
                  </Icon>
                  <Action xsi:type="ExecuteFunction">
                    <FunctionName>insertContosoMeeting</FunctionName>
                  </Action>
                </Control>
              </Group>
            </OfficeTab>
          </ExtensionPoint>
        </DesktopFormFactor>

        <MobileFormFactor>
          <FunctionFile resid="residFunctionFile"/>
          <ExtensionPoint xsi:type="MobileOnlineMeetingCommandSurface">
            <Control xsi:type="MobileButton" id="insertMeetingButton">
              <Label resid="residLabel"/>
              <Icon>
                <bt:Image size="25" scale="1" resid="icon-16"/>
                <bt:Image size="25" scale="2" resid="icon-16"/>
                <bt:Image size="25" scale="3" resid="icon-16"/>

                <bt:Image size="32" scale="1" resid="icon-32"/>
                <bt:Image size="32" scale="2" resid="icon-32"/>
                <bt:Image size="32" scale="3" resid="icon-32"/>

                <bt:Image size="48" scale="1" resid="icon-48"/>
                <bt:Image size="48" scale="2" resid="icon-48"/>
                <bt:Image size="48" scale="3" resid="icon-48"/>
              </Icon>
              <Action xsi:type="ExecuteFunction">
                <FunctionName>insertContosoMeeting</FunctionName>
              </Action>
            </Control>
          </ExtensionPoint>
        </MobileFormFactor>
      </Host>
    </Hosts>
    <Resources>
      <bt:Images>
        <bt:Image id="icon-16" DefaultValue="https://contoso.com/assets/icon-16.png"/>
        <bt:Image id="icon-32" DefaultValue="https://contoso.com/assets/icon-32.png"/>
        <bt:Image id="icon-48" DefaultValue="https://contoso.com/assets/icon-48.png"/>
        <bt:Image id="icon-64" DefaultValue="https://contoso.com/assets/icon-64.png"/>
        <bt:Image id="icon-80" DefaultValue="https://contoso.com/assets/icon-80.png"/>
      </bt:Images>
      <bt:Urls>
        <bt:Url id="residFunctionFile" DefaultValue="https://contoso.com/commands.html"/>
      </bt:Urls>
      <bt:ShortStrings>
        <bt:String id="residDescription" DefaultValue="Contoso meeting"/>
        <bt:String id="residLabel" DefaultValue="Add a contoso meeting"/>
      </bt:ShortStrings>
      <bt:LongStrings>
        <bt:String id="residTooltip" DefaultValue="Add a contoso meeting to this appointment."/>
      </bt:LongStrings>
    </Resources>
  </VersionOverrides>
</VersionOverrides>
```

> [!TIP]
> Para saber mais sobre manifestos para suplementos do Outlook, confira [manifestos de suplemento do Outlook](manifests.md) e [Adicione suporte para comandos de suplemento do Outlook Mobile](add-mobile-support.md).

## <a name="implement-adding-online-meeting-details"></a>Implementar adicionando detalhes da reunião online

Nesta seção, saiba como o script do seu suplemento pode atualizar a reunião de um usuário para incluir detalhes online da reunião.

1. No mesmo projeto de início rápido, abra o arquivo **./src/commands/commands.js** em seu editor de código.

1. Substitua todo o conteúdo do arquivo de **commands.js** pelo seguinte JavaScript.

    ```js
    // 1. How to construct online meeting details.
    // Not shown: How to get the meeting organizer's ID and other details from your service.
    const newBody = '<br>' +
        '<a href="https://contoso.com/meeting?id=123456789" target="_blank">Join Contoso meeting</a>' +
        '<br><br>' +
        'Phone Dial-in: +1(123)456-7890' +
        '<br><br>' +
        'Meeting ID: 123 456 789' +
        '<br><br>' +
        'Want to test your video connection?' +
        '<br><br>' +
        '<a href="https://contoso.com/testmeeting" target="_blank">Join test meeting</a>' +
        '<br><br>';

    var mailboxItem;

    // Office is ready.
    Office.onReady(function () {
            mailboxItem = Office.context.mailbox.item;
        }
    );

    // 2. How to define a UI-less function named `insertContosoMeeting` (referenced in the manifest)
    //    to update the meeting body with the online meeting details.
    function insertContosoMeeting(event) {
        // Get HTML body from the client.
        mailboxItem.body.getAsync("html",
            { asyncContext: event },
            function (getBodyResult) {
                if (getBodyResult.status === Office.AsyncResultStatus.Succeeded) {
                    updateBody(getBodyResult.asyncContext, getBodyResult.value);
                } else {
                    console.error("Failed to get HTML body.");
                    getBodyResult.asyncContext.completed({ allowEvent: false });
                }
            }
        );
    }

    // 3. How to implement a supporting function `updateBody`
    //    that appends the online meeting details to the current body of the meeting.
    function updateBody(event, existingBody) {
        // Append new body to the existing body.
        mailboxItem.body.setAsync(existingBody + newBody,
            { asyncContext: event, coercionType: "html" },
            function (setBodyResult) {
                if (setBodyResult.status === Office.AsyncResultStatus.Succeeded) {
                    setBodyResult.asyncContext.completed({ allowEvent: true });
                } else {
                    console.error("Failed to set HTML body.");
                    setBodyResult.asyncContext.completed({ allowEvent: false });
                }
            }
        );
    }

    function getGlobal() {
      return typeof self !== "undefined"
        ? self
        : typeof window !== "undefined"
        ? window
        : typeof global !== "undefined"
        ? global
        : undefined;
    }

    const g = getGlobal();

    // The add-in command functions need to be available in global scope.
    g.insertContosoMeeting = insertContosoMeeting;
    ```

## <a name="testing-and-validation"></a>Teste e validação

Siga as orientações usuais para [testar e validar o suplemento](testing-and-tips.md). Após o [Sideload](sideload-outlook-add-ins-for-testing.md) no Outlook na Web, no Windows ou no Mac, reinicie o Outlook no seu dispositivo móvel Android. (Android é o único cliente com suporte para agora.) Em seguida, em uma nova tela de reunião, verifique se o Microsoft Teams ou o alternância do Skype foi substituído por seu próprio.

### <a name="create-meeting-ui"></a>Criar IU de reunião

Como organizador da reunião, você deve ver telas semelhantes às três imagens a seguir ao criar uma reunião.

[ ![ captura de tela da tela criar reunião no Android-ativar/desativar](../images/outlook-android-create-online-meeting-off.png)](../images/outlook-android-create-online-meeting-off-expanded.png#lightbox) [ ![ captura de tela da tela criar reunião no Android-carregando a](../images/outlook-android-create-online-meeting-load.png)](../images/outlook-android-create-online-meeting-load-expanded.png#lightbox) [ ![ captura de tela da Contoso Toggle Screen do botão criar reunião no Android-ativar/desativar](../images/outlook-android-create-online-meeting-on.png)](../images/outlook-android-create-online-meeting-on-expanded.png#lightbox)

### <a name="join-meeting-ui"></a>Ingressar na IU da reunião

Como participante da reunião, você verá uma tela semelhante à seguinte imagem ao exibir a reunião.

[![captura de tela da tela ingressar na reunião no Android](../images/outlook-android-join-online-meeting-view-1.png)](../images/outlook-android-join-online-meeting-view-1-expanded.png#lightbox)

> [!IMPORTANT]
> Se você não vir o link de **ingresso** , pode ser que o modelo de reunião online do seu serviço não esteja registrado nos nossos servidores. Confira a seção [registrar seu modelo de reunião online](#register-your-online-meeting-template) para obter detalhes.

## <a name="register-your-online-meeting-template"></a>Registrar seu modelo de reunião online

Se quiser registrar o modelo de reunião online para o seu serviço, você pode criar um problema do GitHub com os detalhes. Depois, entraremos em contato com você para coordenar a linha do tempo de registro.

1. Vá para a seção de **comentários** no final deste artigo.
1. Pressione o link **esta página** .
1. Defina o **título** do novo problema como "registrar o modelo de reunião online para meu serviço", substituindo `my-service` com o nome do serviço.
1. No corpo da questão, substitua a cadeia de caracteres "[Insira comentários aqui]" com a cadeia de caracteres que você definiu na `newBody` seção ou variável semelhante da seção [implementar detalhes da reunião online](#implement-adding-online-meeting-details) , anteriormente neste artigo.
1. Clique em **Enviar novo problema**.

![captura de tela da nova tela de saída do GitHub com o conteúdo de amostra da contoso](../images/outlook-request-to-register-online-meeting-template.png)

## <a name="available-apis"></a>APIs disponíveis

As seguintes APIs estão disponíveis para este recurso.

- APIs do organizador de compromissos
  - [Office. Context. Mailbox. Item. Subject](/javascript/api/outlook/office.appointmentcompose?view=outlook-js-preview&preserve-view=true#subject) ([assunto](/javascript/api/outlook/office.subject?view=outlook-js-preview&preserve-view=true))
  - [Office. Context. Mailbox. Item. Start](/javascript/api/outlook/office.appointmentcompose?view=outlook-js-preview&preserve-view=true#start) ([time](/javascript/api/outlook/office.time?view=outlook-js-preview&preserve-view=true))
  - [Office. Context. Mailbox. Item. end](/javascript/api/outlook/office.appointmentcompose?view=outlook-js-preview&preserve-view=true#end) ([time](/javascript/api/outlook/office.time?view=outlook-js-preview&preserve-view=true))
  - [Office. Context. Mailbox. Item. Location](/javascript/api/outlook/office.appointmentcompose?view=outlook-js-preview&preserve-view=true#location) ([local](/javascript/api/outlook/office.location?view=outlook-js-preview&preserve-view=true))
  - [Office. Context. Mailbox. Item. optionalAttendees](/javascript/api/outlook/office.appointmentcompose?view=outlook-js-preview&preserve-view=true#optionalattendees) ([destinatários](/javascript/api/outlook/office.recipients?view=outlook-js-preview&preserve-view=true))
  - [Office. Context. Mailbox. Item. requiredAttendees](/javascript/api/outlook/office.appointmentcompose?view=outlook-js-preview&preserve-view=true#requiredattendees) ([destinatários](/javascript/api/outlook/office.recipients?view=outlook-js-preview&preserve-view=true))
  - [Office. Context. Mailbox. Item. Body](/javascript/api/outlook/office.appointmentcompose?view=outlook-js-preview&preserve-view=true#body) ([Body. getasync](/javascript/api/outlook/office.body?view=outlook-js-preview&preserve-view=true#getasync-coerciontype--options--callback-), [Body. setasync](/javascript/api/outlook/office.body?view=outlook-js-preview&preserve-view=true#setasync-data--options--callback-))
  - [Office. Context. Mailbox. Item. loadCustomPropertiesAsync](/javascript/api/outlook/office.appointmentcompose?view=outlook-js-preview&preserve-view=true#loadcustompropertiesasync-callback--usercontext-) ([CustomProperties](/javascript/api/outlook/office.customproperties?view=outlook-js-preview&preserve-view=true))
  - [Office. Context. roamingSettings](../reference/objectmodel/preview-requirement-set/office.context.md?view=outlook-js-preview&preserve-view=true#roamingsettings-roamingsettings) ([roamingSettings](/javascript/api/outlook/office.roamingsettings?view=outlook-js-preview&preserve-view=true))
- Gerenciar fluxo de autenticação
  - [APIs de caixa de diálogo](../develop/dialog-api-in-office-add-ins.md)

## <a name="restrictions"></a>Restriction

Várias restrições se aplicam.

- Aplicável somente aos provedores de serviço de reunião online.
- No momento, o Android é o único cliente com suporte. O suporte ao iOS estará disponível em breve.
- Somente os suplementos instalados pelo administrador serão exibidos na tela de redação da reunião, substituindo a opção Teams ou Skype padrão. Os suplementos instalados pelo usuário não serão ativados.
- O ícone do suplemento deve estar em escala de cinza usando o código hex `#919191` ou seu equivalente em [outros formatos de cor](https://convertingcolors.com/hex-color-919191.html).
- Só há suporte para um comando sem interface do usuário no modo de organizador de compromisso (compor).

## <a name="see-also"></a>Confira também

- [Suplementos do Outlook Mobile](outlook-mobile-addins.md)
- [Adicionar suporte para comandos de suplementos para Outlook Mobile](add-mobile-support.md)
