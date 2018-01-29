# <a name="debug-office-add-ins-on-ipad-and-mac"></a>Depurar suplementos do Office no iPad e no Mac

Você pode usar o Visual Studio para desenvolver e depurar suplementos no Windows, mas não pode usá-lo para depurar suplementos no iPad ou no Mac. Como os suplementos são desenvolvidos usando HTML e Javascript, são projetados para funcionar em várias plataformas, mas pode haver diferenças sutis em como cada navegador processa o HTML. Este artigo descreve como depurar suplementos em execução em um iPad ou em um Mac. 

## <a name="debugging-with-vorlonjs"></a>Depuração com Vorlon.JS 

O Vorlon.JS é um depurador para páginas da Web, semelhante às ferramentas F12. Ele é projetado para funcionar remotamente e permite depurar páginas da Web em dispositivos diferentes. Para saber mais, veja o [site do Vorlon](http://www.vorlonjs.com).  

### <a name="install-and-set-up-up-vorlonjs-on-a-mac-or-ipad"></a>Instalar e configurar o Vorlon.JS em um Mac ou iPad 

1.  Faça logon no dispositivo como um administrador.

2.  Instale o [Node.js](https://nodejs.org) se ele ainda não estiver instalado. 

2.  Abra uma janela do **Terminal** e digite o comando `npm i -g vorlon`. A ferramenta está instalada em `/usr/local/lib/node_modules/vorlon`.

### <a name="configure-vorlonjs-to-use-https"></a>Configurar o Vorlon.JS para usar HTTPS

Para depurar um aplicativo usando o Vorlon.JS, adicione uma marca `<script>` à página de abertura do aplicativo que carrega um script Vorlon.JS de um local conhecido (para obter detalhes, veja o procedimento a seguir). Os suplementos exigem o protocolo HTTPS, ou seja, SSL. Por extensão, todos os scripts que eles usarem deverão estar hospedados em um servidor HTTPS, incluindo o script Vorlon.JS. Portanto, você precisará configurar o Vorlon.JS para usar SSL se quiser usar esse script com suplementos. 

4.  No **Localizador**, acesse `/usr/local/lib/node_modules/vorlon`, abra o menu de contexto (clique com o botão direito do mouse) da pasta `/Server` e escolha **Obter Informações**.

5.  Escolha o ícone de cadeado no canto inferior direito da janela **Informações do servidor** para desbloquear a pasta.

6. Na seção **Compartilhamento e Permissões** da janela, defina o **Privilégio** para o grupo **funcionários** como **Leitura/Gravação**.

7. Escolha o ícone de cadeado novamente para ***voltar a bloquear*** a pasta.

8. No **Localizador**, expanda a subpasta `/Server`, clique com botão direito do mouse no arquivo `config.json` e selecione **Obter Informações**.

9. Na janela **informações de config.json**, altere os privilégios do arquivo da mesma forma que você fez para sua pasta `/Server` pai. Não se esqueça de bloquear novamente e de fechar a janela.

10. No **Localizador**, clique com botão direito do mouse no arquivo `config.json`, selecione **Abrir com**e selecione **TextEdit**. O arquivo é aberto em um editor de texto.

11. Altere a propriedade **useSSL** para `true`.

12. Na seção **plug-ins**, localize o plug-in com a **id** de `OFFICE` e o **nome** de `Office Addin`. Se a propriedade **enabled** do plug-in ainda não estiver como `true`, defina-a como `true`.

13. Salve o arquivo e feche o editor.

5.  No **Localizador**, navegue até `/usr/local/lib/node_modules/vorlon`, clique com botão direito do mouse na subpasta `Server` e selecione **Novo terminal na pasta**. 
    
7.  Na janela do **Terminal**, digite `sudo vorlon`. Será solicitado que você digite sua senha de administrador. O servidor Vorlon é iniciado. Deixe aberta a janela do **Terminal**.

6.  Abra uma janela do navegador e vá para `https://localhost:1337`, que é a interface do Vorlon.JS. Quando solicitado, escolha **Sempre** para confiar no certificado de segurança. 

    >**Observação:** Se não for solicitado, talvez seja necessário confiar no certificado manualmente. O arquivo de certificado é `/usr/local/lib/node_modules/vorlon/Server/cert/server.crt`. Experimente as etapas a seguir. Se você tiver problemas, veja a ajuda da Macintosh ou do iPad. 
    >
    >1. Feche a janela do navegador e na janela do **Terminal** que está executando o servidor Vorlon, use Control-C para parar o servidor.
    >2. No **Localizador**, clique com botão direito do mouse no arquivo `server.crt` e escolha **Acesso ao Conjunto de Chaves**. A janela **Acesso ao Conjunto de Chaves** é exibida.
    >2. Na lista **Conjuntos de Chaves** à esquerda, escolha **logon**, caso ainda não estiver marcado, e, em seguida, escolha **Certificados** na seção **Categoria**. Verifique se o **localhost** do certificado está na lista.
    >3. Clique com botão direito do mouse no **localhost** do certificado e escolha **Obter Informações**. Uma janela do **localhost** é exibida.
    >4. Na seção **Confiar**, abra o seletor rotulado como **Ao usar este certificado** e escolha **Sempre Confiar**. 
    >5. Feche a janela do **localhost**. Se a ação for bem-sucedida, o certificado do **localhost** na janela **Acesso ao Conjunto de Chaves** exibirá uma cruz branca em um círculo azul no ícone.

### <a name="configure-the-add-in-for-vorlonjs-debugging"></a>Configurar o suplemento para depuração do Vorlon.JS

1. Adicione a seguinte marca de script à seção `<head>` do arquivo home.html (ou arquivo HTML principal) do seu suplemento:

    ```    
    <script src="https://localhost:1337/vorlon.js"></script>    
    ```  

2. Implante o aplicativo da Web do suplemento em um servidor Web que pode ser acessado do Mac ou iPad, como um site do Azure. 

3. Atualize a URL do suplemento em todos os locais onde a URL aparece no manifesto do suplemento.

4. No Mac ou iPad, copie o manifesto do suplemento na seguinte pasta: `/Users/{your_name_on_the_device}/Library/Containers/com.microsoft.{host_name}/Data/Documents/wef`, onde *{nome_do_host}* é Word, Excel, PowerPoint ou Outlook.

### <a name="inspect-an-add-in-in-vorlonjs"></a>Inspecionar um suplemento no Vorlon.JS

1. Se o servidor Vorlon não estiver sendo executado, no **Localizador**, navegue até `/usr/local/lib/node_modules/vorlon`, clique com botão direito do mouse na subpasta `Server` e selecione **Novo terminal na pasta**. 
    
7.  Na janela do **Terminal**, digite `sudo vorlon`. Será solicitado que você digite sua senha de administrador. O servidor Vorlon é iniciado. Deixe aberta a janela do **Terminal**.

6.  Abra uma janela do navegador e vá para `https://localhost:1337`, que é a interface do Vorlon.JS.

7. Realize o sideload do suplemento. Para o Excel, PowerPoint ou Word, realize o sideload conforme descrito em [Realizar sideload de um suplemento do Office no iPad e no Mac](https://dev.office.com/docs/add-ins/testing/sideload-an-office-add-in-on-ipad-and-mac). Se for um suplemento do Outlook, realize o sideload conforme descrito em [Realizar sideload de suplementos do Outlook para teste](https://dev.office.com/docs/add-ins/testing/sideload-outlook-add-ins-for-testing). Se o suplemento não usar comandos de suplemento, ele será imediatamente aberto. Caso contrário, escolha o botão para abrir o suplemento. Dependendo da compilação do aplicativo host do Office, o botão será exibido em ambas guias **Página Inicial** ou em uma guia **Suplemento**.

O suplemento aparecerá na lista de Clientes no Vorlon.JS (no lado esquerdo da interface do Vorlon.JS) como **{OS} - n**, para um determinado número *n* e em que *{OS}* é o tipo de dispositivo, como "Macintosh". 

![Captura de tela que mostra a interface do Vorlon.js](../images/vorlon_interface.png)

A ferramenta Vorlon tem uma variedade de plug-ins. Os que estiverem habilitados no momento serão exibidos como guias na parte superior da ferramenta. (É possível habilitar mais plug-ins escolhendo o ícone de engrenagem no canto esquerdo). Esses plug-ins são semelhantes às funções nas ferramentas F12. Por exemplo, você pode realçar elementos DOM, executar comandos e muito mais. Para obter mais detalhes, veja [Principais plug-ins da documentação do Vorlon](http://vorlonjs.com/documentation/#console) 

Um plug-in do **Suplemento do Office** adiciona recursos extras ao Office.js, como explorar o modelo de objeto e executar chamadas de Office.js e ler os valores das propriedades de objetos. Para obter instruções, veja [Plug-in do VorlonJS para depuração de suplementos do Office](https://blogs.msdn.microsoft.com/mim/2016/02/18/vorlonjs-plugin-for-debugging-office-addin/).

>**Observação:** Não é possível definir pontos de interrupção no Vorlon.JS.

## <a name="clearing-the-office-applications-cache-on-a-mac-or-ipad"></a>Limpar cache do aplicativo do Office em um Mac ou iPad

Os Suplementos muitas vezes são armazenados em cache no Office para Mac por questão de desempenho. Normalmente, o cache será limpo quando o suplemento for recarregado. Se houver mais de um suplemento no mesmo documento, é provável que o processo de limpeza automática do cache ao recarregar não seja confiável. 

No Mac, o cache pode ser limpo manualmente ao excluir tudo na pasta `/Users/{your_name_on_the_device}/Library/Containers/com.Microsoft.OsfWebHost/Data/`. 

No iPad, você pode chamar `window.location.reload(true)` a partir do JavaScript no suplemento para forçar uma recarrega. Uma outra alternativa é reinstalar o Office.