---
title: "Tutorial: Mostrar la coincidencia de llaves | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] nuevos - coincidencia de llaves"
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Tutorial: Mostrar la coincidencia de llaves
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede implementar características basadas en lenguaje como llaves definiendo las llaves que desea hacer coincidir y, a continuación, agregar una etiqueta de marcador de texto a las llaves cuando el símbolo de intercalación está en una de las llaves. Puede definir las llaves en el contexto de un idioma, puede definir su propio tipo de contenido y la extensión de nombre de archivo y las etiquetas se aplican a ese tipo o puede aplicar las etiquetas a un tipo de contenido existente \(por ejemplo, "text"\). El siguiente tutorial muestra cómo aplicar etiquetas para el tipo de contenido "text" de coincidencia de llaves.  
  
## Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional de la instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulta [Instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Crear un proyecto de Managed Extensibility Framework \(MEF\)  
  
#### Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto de clasificador de editor. El nombre de la solución `BraceMatchingTest`.  
  
2.  Agregar una plantilla de elemento de clasificador de Editor para el proyecto. Para obtener más información, consulta [Crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## Implementar un etiquetador de coincidencia de llaves  
 Para obtener un efecto similar al que se utiliza en Visual Studio de resalte de llaves, se puede implementar un etiquetador de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. El código siguiente muestra cómo definir el etiquetador de pares de llave en cualquier nivel de anidamiento. En este ejemplo, la llave pares \[\]. \[\], {} se define en el constructor de etiquetador y en una implementación del lenguaje completo se definiría los pares de la llave correspondiente en la especificación del lenguaje.  
  
#### Para implementar un etiquetador de coincidencia de llaves  
  
1.  Agregue un archivo de clase y denomínelo intercambio.  
  
2.  Importe los siguientes espacios de nombres.  
  
     [!code-cs[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Defina una clase `BraceMatchingTagger` que hereda de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-cs[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Agregar propiedades para la vista de texto, el búfer de origen y el punto de la instantánea actual y un conjunto de pares de llaves.  
  
     [!code-cs[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  En el constructor etiquetador, establezca las propiedades y suscribirse a los eventos de cambio de vista <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> y <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. En este ejemplo, con fines ilustrativos, también se definen los pares coincidentes en el constructor.  
  
     [!code-cs[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Como parte de la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementación, declara un evento TagsChanged.  
  
     [!code-cs[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  La posición del símbolo de intercalación actual de actualización de los controladores de eventos del `CurrentChar` propiedad y generar el evento TagsChanged.  
  
     [!code-cs[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método coincida con llaves bien cuando el carácter actual es una llave de apertura o cuando el carácter anterior es una llave de cierre, como en Visual Studio. Cuando se encuentra la coincidencia, este método crea una instancia de dos etiquetas, una para la llave de apertura y otro para la llave de cierre.  
  
     [!code-cs[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Los siguientes métodos privados encuentra la llave correspondiente en cualquier nivel de anidamiento. El primer método busca el carácter de cierre que coincide con el carácter abierto:  
  
     [!code-cs[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. El siguiente método auxiliar busca el carácter abierto que coincide con un carácter de cierre:  
  
     [!code-cs[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## Implementar un proveedor de etiquetador de coincidencia de llaves  
 Además de implementar un etiquetador, también debe implementar y exportar un proveedor del etiquetador. En este caso, el tipo de contenido del proveedor es "text". Esto significa que la coincidencia de llaves aparecerá en todos los tipos de archivos de texto, pero se aplicaría una implementación más completa de llaves sólo a un tipo de contenido específico.  
  
#### Para implementar un proveedor de etiquetador de coincidencia de llaves  
  
1.  Declarar un proveedor del etiquetador que hereda de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, asígnele el nombre BraceMatchingTaggerProvider y exportarlo a un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "texto" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-cs[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> método para crear una instancia de un BraceMatchingTagger.  
  
     [!code-cs[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## Compilar y probar el código  
 Para probar este código, compile la solución BraceMatchingTest y ejecútelo en la instancia experimental.  
  
#### Para compilar y probar la solución BraceMatchingTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Cree un archivo de texto y escriba el texto que incluye llaves.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Al colocar el símbolo de intercalación antes de una llave de apertura, esa llave y la llave de cierre correspondiente debe aparecer resaltada. Cuando se coloca el cursor justo después de la llave de cierre, esa llave y la llave de apertura correspondiente debe aparecer resaltada.  
  
## Vea también  
 [Tutorial: Vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)