---
title: 'Tutorial: Visualización de llaves coincidentes ( Matching Braces) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 107610733ab9b5c8085b3f987fa999250b453d63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697448"
---
# <a name="walkthrough-display-matching-braces"></a>Tutorial: Mostrar llaves coincidentes
Implemente características basadas en lenguaje, como la coincidencia de llaves definiendo las llaves que desea que coincidan y agregando una etiqueta de marcador de texto a las llaves coincidentes cuando el intercalador está en una de las llaves. Puede definir llaves en el contexto de un idioma, definir su propia extensión de nombre de archivo y tipo de contenido, y aplicar las etiquetas solo a ese tipo o aplicar las etiquetas a un tipo de contenido existente (por ejemplo, "texto"). En el siguiente tutorial se muestra cómo aplicar etiquetas de coincidencia de llaves al tipo de contenido "text".

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto de Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1. Cree un proyecto de clasificador de editor. Asigne a la solución el nombre `BraceMatchingTest`.

2. Agregue una plantilla de elemento Clasificador de editor al proyecto. Para obtener más información, consulte Crear una extensión con una plantilla de elemento de [editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Elimine los archivos de clase existentes.

## <a name="implement-a-brace-matching-tagger"></a>Implementar un tagger de coincidencia de llaves
 Para obtener un efecto de resaltado de llaves similar al que se usa en <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>Visual Studio, puede implementar un etiquetador de tipo . El código siguiente muestra cómo definir el etiquetador para pares de llaves en cualquier nivel de anidamiento. En este ejemplo, los pares {} de llaves de [] y se definen en el constructor de etiqueta, pero en una implementación de lenguaje completo, los pares de llaves relevantes se definirían en la especificación de lenguaje.

### <a name="to-implement-a-brace-matching-tagger"></a>Para implementar un tagger de coincidencia de llaves

1. Agregue un archivo de clase y asímócelo BraceMatching.

2. Importe los siguientes espacios de nombres.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Defina una `BraceMatchingTagger` clase que <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> herede de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Agregue propiedades para la vista de texto, el búfer de origen, el punto de instantánea actual y también un conjunto de pares de llaves.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. En el constructor de etiqueta, establezca las propiedades <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>y suscríbase a los eventos de cambio de vista y . En este ejemplo, para fines ilustrativos, los pares coincidentes también se definen en el constructor.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Como parte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de la implementación, declare un TagsChanged eventos.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Los controladores de eventos actualizan la `CurrentChar` posición actual del intercalador de la propiedad y generan el TagsChanged eventos.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> el método para que coincida con las llaves cuando el carácter actual es una llave abierta o cuando el carácter anterior es una llave estrecha, como en Visual Studio. Cuando se encuentra la coincidencia, este método crea dos etiquetas, una para la llave abierta y otra para la llave de cierre.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Los siguientes métodos privados encuentran la llave coincidente en cualquier nivel de anidamiento. El primer método busca el carácter close que coincide con el carácter abierto:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. El siguiente método auxiliar busca el carácter abierto que coincide con un carácter cercano:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementar un proveedor de etiquetado de coincidencia de llaves
 Además de implementar un tagger, también debe implementar y exportar un proveedor de etiquetas. En este caso, el tipo de contenido del proveedor es "texto". Por lo tanto, la coincidencia de llaves aparecerá en todos los tipos de archivos de texto, pero una implementación más completa aplica la coincidencia de llaves solo a un tipo de contenido específico.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Para implementar un proveedor de etiquetado de coincidencia de llaves

1. Declare un proveedor de etiqueta <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>que herede de , asílo sea <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> BraceMatchingTaggerProvider <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>y expórtelo con un de "texto" y un archivo de .

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Implemente <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> el método para crear una instancia de un BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Compile y pruebe el código
 Para probar este código, compile la solución BraceMatchingTest y ejecútela en la instancia experimental.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Para crear y probar la solución BraceMatchingTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba texto que incluya llaves coincidentes.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Al colocar el intercalador antes de una llave abierta, se deben resaltar tanto esa llave como la llave de cierre correspondiente. Al colocar el cursor justo después de la llave de cierre, se deben resaltar tanto esa llave como la llave abierta coincidente.

## <a name="see-also"></a>Vea también
- [Tutorial: Vincule un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
