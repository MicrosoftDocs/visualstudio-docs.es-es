---
title: 'Tutorial: Mostrar la coincidencia de llaves | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 370340246cd75e53580d1ac2b6c591f0854cb23e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-displaying-matching-braces"></a>Tutorial: Mostrar llaves coincidentes
Puede implementar características basadas en lenguaje como relleno de llaves definiendo las llaves que desee buscar y, a continuación, agregar una etiqueta de marcador de texto a las llaves cuando el símbolo de intercalación está en una de las llaves. Puede definir llaves en el contexto de un idioma, o puede definir su propio tipo de contenido y la extensión de nombre de archivo y las etiquetas se aplican a ese tipo, o puede aplicar las etiquetas a un tipo de contenido existente (por ejemplo, "text"). En el siguiente tutorial se muestra cómo aplicar etiquetas para el tipo de contenido "text" la coincidencia de llaves.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF  
  
1.  Cree un proyecto de clasificador de editor. Llame a la solución `BraceMatchingTest`.  
  
2.  Agregar una plantilla de elementos de clasificador de Editor para el proyecto. Para obtener más información, consulte [crear una extensión con una plantilla de elemento de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementar un etiquetador de coincidencia de llaves  
 Para obtener un efecto similar al que se usa en Visual Studio de resaltado de llaves, puede implementar un etiquetador de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. El código siguiente muestra cómo definir el etiquetador para los pares de llave en cualquier nivel de anidamiento. En este ejemplo, la llave de pares []. [] y {} se define en el constructor de etiquetador, pero en una implementación de lenguaje completo se definiría los pares de llave relevante en la especificación del lenguaje.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Para implementar un etiquetador de coincidencia de llaves  
  
1.  Agregue un archivo de clase y asígnele el intercambio.  
  
2.  Importe los siguientes espacios de nombres.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Defina una clase `BraceMatchingTagger` que herede de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Agregar propiedades de la vista de texto, el búfer de origen y el punto de la instantánea actual y un conjunto de pares de llaves.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  En el constructor etiquetador, establezca las propiedades y suscribirse a los eventos de cambio de vista <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> y <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. En este ejemplo, con fines ilustrativos, también se definen los pares coincidentes en el constructor.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Como parte de la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementación, declara un evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Los controladores de eventos actualizan la posición actual del símbolo de intercalación de la `CurrentChar` propiedad y generar el evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método para que coincida con las llaves cualquiera cuando el carácter actual es una llave de apertura o cuando el carácter anterior es una llave de cierre, como en Visual Studio. Cuando se encuentra la coincidencia, este método crea una instancia de dos etiquetas, una para la llave de apertura y otro para la llave de cierre.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Los siguientes métodos privados encuentra la llave correspondiente en cualquier nivel de anidamiento. El primer método busca el carácter de cierre que coincida con el carácter abierto:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. El método auxiliar siguiente busca el carácter abierto que coincide con un carácter de cierre:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementar un proveedor del etiquetador de coincidencia de llaves  
 Además de implementar un etiquetador, también debe implementar y exportar un proveedor del etiquetador. En este caso, el tipo de contenido del proveedor es "text". Esto significa que la coincidencia de llaves aparecerá en todos los tipos de archivos de texto, pero una implementación más completa se aplicaría solo a un tipo de contenido específico de la coincidencia de llaves.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Para implementar un proveedor del etiquetador de coincidencia de llaves  
  
1.  Declarar un proveedor del etiquetador que hereda de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, asígnele el nombre BraceMatchingTaggerProvider y exportarlo a un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "text" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> método para crear instancias de un BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución BraceMatchingTest y ejecútelo en la instancia experimental.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Para compilar y probar soluciones de BraceMatchingTest  
  
1.  Compile la solución.  
  
2.  Al ejecutar este proyecto en el depurador, se crea una segunda instancia de Visual Studio.  
  
3.  Cree un archivo de texto y escriba algún texto que incluye llaves coincidentes.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Al colocar el símbolo de intercalación antes de una llave de apertura, esa llave y la llave de cierre correspondiente debe aparecer resaltada. Al colocar el cursor justo después de la llave de cierre, debe aparecer resaltada esa llave y la llave de apertura correspondiente.  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: vinculación de un tipo de contenido con una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)