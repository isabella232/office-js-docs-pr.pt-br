Ao concluir o assistente, o Visual Studio cria uma solução que contém dois projetos.

|**Projeto**|**Descrição**|
|:-----|:-----|
|Projeto de suplemento|Contém somente um arquivo de manifesto XML, que contém todas as configurações que descrevem o suplemento. As configurações ajudam o host do Office a determinar quando o suplemento deverá ser ativado e onde ele deverá aparecer. O Visual Studio gera o conteúdo desse arquivo para que você possa executar o projeto e usar o suplemento imediatamente . É possível alterar as configurações a qualquer momento modificando o arquivo XML.|
|Projeto de aplicativo Web|Contém as páginas de conteúdo do suplemento, incluindo todos os arquivos e referências de arquivo de que você precisa para desenvolver páginas HTML e JavaScript com reconhecimento do Office. Enquanto você desenvolve o suplemento, o Visual Studio hospeda o aplicativo Web no servidor IIS local. Quando estiver pronto para publicar, você precisará implantar este projeto de aplicativo Web em um servidor Web.|