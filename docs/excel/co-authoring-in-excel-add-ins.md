# <a name="coauthoring-in-excel-add-ins"></a>Coautoria em suplementos do Excel  

Com a [coautoria](https://support.office.com/pt-br/article/Collaborate-on-Excel-workbooks-at-the-same-time-with-co-authoring-7152aa8b-b791-414c-a3bb-3024e46fb104), várias pessoas podem trabalhar juntas e editar simultaneamente a mesma pasta de trabalho do Excel. Todos os coautores de uma pasta de trabalho podem ver as alterações de outros coautores assim que o coautor salva a pasta de trabalho. Para ser coautor de uma pasta de trabalho do Excel, esta deve ser armazenada no OneDrive, OneDrive for Business ou SharePoint Online.

> **Importante:** no Excel 2016 para Office 365, você verá o Salvamento Automático no canto superior esquerdo. Quando o Salvamento Automático estiver ativado, os coautores verão as respectivas alterações em tempo real. Considere o impacto desse comportamento no design do seu suplemento do Excel. Os usuários podem desativar o Salvamento Automático pelo botão no canto superior esquerdo da janela do Excel.

A coautoria está disponível nas seguintes plataformas:

- Excel Online
- Excel for Android
- Excel for iOS
- Excel Mobile para Windows 10
- Excel para Windows Desktop para clientes do Office 365 (compilação 16.0.8326.2076 ou posterior do Windows Desktop, que está disponível para clientes do canal atual em vigor desde agosto de 2017)

## <a name="coauthoring-overview"></a>Visão geral da coautoria
 
Quando você altera o conteúdo de uma pasta de trabalho, o Excel sincroniza automaticamente essas alterações entre todos os coautores. Os coautores podem alterar o conteúdo de uma pasta de trabalho, assim como o código em execução em um suplemento do Excel. Por exemplo, quando o seguinte código JavaScript é executado em um suplemento do Office, o valor de um intervalo é definido como Contoso:


    range.values = [[‘Contoso’]];

Depois que "Contoso" é sincronizado entre todos os coautores, qualquer usuário ou suplemento em execução na mesma pasta de trabalho verá o novo valor do intervalo. 

A coautoria sincroniza apenas o conteúdo dentro da pasta de trabalho compartilhada. Os valores copiados da pasta de trabalho em variáveis de JavaScript em um suplemento do Excel não são sincronizados. Por exemplo, se seu suplemento armazenar o valor de uma célula (como "Contoso") em uma variável de JavaScript e um coautor alterar o valor da célula para "Exemplo", após a sincronização todos os coautores verão "Exemplo" na célula. No entanto, o valor da variável de JavaScript continuará definido como "Contoso". Além disso, quando vários autores usarem o mesmo suplemento, cada coautor terá sua própria cópia da variável, que não é sincronizada. Quando você usar variáveis que usam o conteúdo da pasta de trabalho, não se esqueça de verificar se há valores atualizados na pasta de trabalho antes de usar a variável. 

## <a name="use-events-to-manage-the-in-memory-state-of-your-add-in"></a>Usar eventos para gerenciar o estado na memória do suplemento
 
Os suplementos do Excel podem ler conteúdo da pasta de trabalho (de planilhas ocultas e um objeto de configuração) e armazená-lo em estruturas de dados, como variáveis. Depois que os valores originais são copiados em qualquer uma dessas estruturas de dados, os coautores podem atualizar o conteúdo da pasta de trabalho original. Isso significa que os valores copiados nas estruturas de dados agora estão fora de sincronia com o conteúdo da pasta de trabalho. Ao criar seus suplementos, lembre-se dessa separação do conteúdo da pasta de trabalho e dos valores armazenados em estruturas de dados.

Por exemplo, você pode criar um suplemento de conteúdo que exibe visualizações personalizadas. O estado de suas visualizações personalizadas pode ser salvo em uma planilha oculta. Quando coautores usarem a mesma pasta de trabalho, o seguinte cenário poderá ocorrer:

- O Usuário A abre o documento e as visualizações personalizadas são mostradas na pasta de trabalho. As visualizações personalizadas leem dados de uma planilha oculta (por exemplo, a cor das visualizações é definida como azul).
- O usuário B abre o mesmo documento e começa a modificar as visualizações personalizadas. O usuário B define a cor das visualizações personalizadas para laranja. A cor laranja é salva para a planilha oculta.
- A planilha oculta do Usuário A é atualizada com o novo valor de laranja.
- As visualizações personalizadas do Usuário A continuam azuis. 

Se quiser que as visualizações personalizadas do Usuário A respondam às alterações feitas pelos coautores na planilha oculta, use o evento [BindingDataChanged](http://dev.office.com/reference/add-ins/shared/binding.bindingdatachangedevent). Isso garante que as alterações no conteúdo da pasta de trabalho feitas pelos coautores sejam refletidas no estado do seu suplemento.

## <a name="caveats-to-using-events-with-co-authoring"></a>Advertências para usar eventos com coautoria 

Conforme descrito anteriormente, em alguns cenários, acionar eventos para todos os coautores proporciona uma experiência do usuários aprimorada. No entanto, lembre-se de que, em alguns cenários, esse comportamento pode resultar em uma má experiência do usuário. 

Por exemplo, em cenários de validação de dados, é comum exibir a interface do usuário em resposta a eventos. O evento [BindingDataChanged](http://dev.office.com/reference/add-ins/shared/binding.bindingdatachangedevent) descrito na seção anterior é executado quando um usuário local ou coautor (remoto) altera o conteúdo da pasta de trabalho na associação. Se o manipulador de eventos do evento **BindingDataChanged** exibir a interface do usuário, os usuários verão a interface do usuário que não está relacionada às alterações em que eles estavam trabalhando na pasta de trabalho, levando a uma má experiência do usuário. Evite a exibição da interface do usuário ao usar eventos no suplemento.

## <a name="see-also"></a>Veja também 

- [Sobre a coautoria no Excel (VBA)](https://msdn.microsoft.com/pt-br/vba/excel-vba/articles/about-coauthoring-in-excel) 
- [Como o Salvamento Automático afeta suplementos e macros (VBA)](https://msdn.microsoft.com/pt-br/vba/office-shared-vba/articles/how-autosave-impacts-addins-and-macros) 