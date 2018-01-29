# <a name="content-office-add-ins"></a>Suplementos de conteúdo do Office

Suplementos de conteúdo são superfícies que podem ser incorporadas diretamente em documentos do Word, Excel ou PowerPoint. Os suplementos de conteúdo concedem aos usuários acesso a controles de interface que executam códigos para modificar documentos ou exibir dados de uma fonte de dados. Use suplementos de conteúdo quando quiser inserir a funcionalidade diretamente no documento.  

**Exemplo: Suplemento de conteúdo**

![Imagem de exemplo exibindo um layout típico de suplementos de conteúdo.](../images/overview_withApp_content.png)

## <a name="best-practices"></a>Práticas recomendadas

- Inclua alguns elementos de navegação ou comando, como CommandBar ou Pivot, na parte superior do suplemento.
- Inclua um elemento da marca, como BrandBar, na parte inferior do suplemento (aplica-se apenas a suplementos do Word, Excel e PowerPoint).

## <a name="variants"></a>Variantes

Os tamanhos dos suplementos de conteúdo para Word, Excel e PowerPoint na área de trabalho do Office 2016 e do Office 365 são especificados pelo usuário.

## <a name="personality-menu"></a>Menu de personalidade

Menus de personalidade podem obstruir elementos de navegação e comando localizados perto da parte superior direita do suplemento. Veja a seguir as dimensões atuais do menu personalidade no Windows e Mac.

**Menu de personalidade no Windows** 

No Windows, o menu de personalidade mede 12 x 32 pixels, conforme mostrado.

![Imagem mostrando o menu do personalidade na área de trabalho do Windows](../images/personalityMenu_Win.png)

**Menu de personalidade no Mac**

No Mac, o menu de personalidade mede 26 x 26 pixels, mas flutua 8 pixels a partir da direita e 6 pixels a partir do topo, o que aumenta o espaço ocupado para 34 x 32 pixels, como mostrado.

![Imagem mostrando o menu de personalidade na área de trabalho do Mac](../images/personalityMenu_Mac.png)

## <a name="implementation"></a>Implementação

Para ver um exemplo que implementa um suplemento de conteúdo, confira [Suplemento de conteúdo do Excel Humongous Insurance](https://github.com/OfficeDev/Excel-Content-Add-in-Humongous-Insurance) no GitHub.

## <a name="additional-resources"></a>Recursos adicionais

- [Office UI Fabric em suplementos do Office](office-ui-fabric.md) 
- [Padrões de design da experiência do usuário para suplementos do Office](ux-design-patterns.md)