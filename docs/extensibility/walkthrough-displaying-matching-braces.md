---
title: 'Tutorial: Mostrar llaves coincidentes | Microsoft Docs'
description: Obtenga información sobre cómo definir llaves en el contexto de un idioma y aplicar etiquetas de coincidencia de llaves al tipo de contenido de texto mediante este tutorial.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce40f5673a8aba4ab3f7714a3aafdc3de4697cc4
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877954"
---
# <a name="walkthrough-display-matching-braces"></a>Tutorial: Mostrar llaves coincidentes
Implemente características basadas en el lenguaje, como la coincidencia de llaves mediante la definición de las llaves que desee buscar y la adición de una etiqueta de marcador de texto a las llaves coincidentes cuando el símbolo de intercalación esté en una de las llaves. Puede definir llaves en el contexto de un idioma, definir su propia extensión de nombre de archivo y tipo de contenido, y aplicar las etiquetas solo a ese tipo o aplicar las etiquetas a un tipo de contenido existente (como "texto"). En el siguiente tutorial se muestra cómo aplicar etiquetas de coincidencia de llaves al tipo de contenido de "texto".

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Crear un proyecto Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Para crear un nuevo proyecto de MEF

1. Cree un proyecto de clasificador de editor. Asigne a la solución el nombre `BraceMatchingTest`.

2. Agregue una plantilla de elemento clasificador de editor al proyecto. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Elimine los archivos de clase existentes.

## <a name="implement-a-brace-matching-tagger"></a>Implementar un etiquetador de coincidencia de llaves
 Para obtener un efecto de resaltado de llaves similar al que se usa en Visual Studio, puede implementar un etiquetador de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . En el código siguiente se muestra cómo definir el etiquetador para los pares de llaves en cualquier nivel de anidamiento. En este ejemplo, los pares de llaves de [] y {} se definen en el constructor del etiquetador, pero en una implementación de lenguaje completo, los pares de llaves correspondientes se definirían en la especificación del lenguaje.

### <a name="to-implement-a-brace-matching-tagger"></a>Para implementar un etiquetador de coincidencia de llaves

1. Agregue un archivo de clase y asígnele el nombre BraceMatching.

2. Importe los siguientes espacios de nombres.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Defina una clase `BraceMatchingTagger` que herede de <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Agregar propiedades para la vista de texto, el búfer de origen, el punto de la instantánea actual y también un conjunto de pares de llaves.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. En el constructor del etiquetador, establezca las propiedades y suscríbase a los eventos de cambio de vista <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> y <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . En este ejemplo, para fines ilustrativos, los pares coincidentes también se definen en el constructor.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Como parte de la <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementación de, declare un evento TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. Los controladores de eventos actualizan la posición actual del símbolo de intercalación de la `CurrentChar` propiedad y generan el evento TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método para buscar coincidencias entre llaves cuando el carácter actual es una llave de apertura o cuando el carácter anterior es una llave de cierre, como en Visual Studio. Cuando se encuentra la coincidencia, este método crea una instancia de dos etiquetas, una para la llave de apertura y otra para la llave de cierre.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. Los métodos privados siguientes buscan la llave coincidente en cualquier nivel de anidamiento. El primer método busca el carácter de cierre que coincide con el carácter abierto:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. El siguiente método auxiliar busca el carácter abierto que coincide con un carácter de cierre:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementar un proveedor de etiquetador de coincidencia de llaves
 Además de implementar un etiquetador, también debe implementar y exportar un proveedor de etiquetadores. En este caso, el tipo de contenido del proveedor es "Text". Por lo tanto, la coincidencia de llaves aparecerá en todos los tipos de archivos de texto, pero una implementación más completa aplica la coincidencia de llaves solo a un tipo de contenido específico.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Para implementar un proveedor de etiquetadores de coincidencia de llaves

1. Declare un proveedor de etiquetador que herede de <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , asígnele el nombre BraceMatchingTaggerProvider y expórtelo con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "Text" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> método para crear una instancia de un BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Compilar y probar el código
 Para probar este código, compile la solución BraceMatchingTest y ejecútela en la instancia experimental.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Para compilar y probar la solución BraceMatchingTest

1. Compile la solución.

2. Al ejecutar este proyecto en el depurador, se inicia una segunda instancia de Visual Studio.

3. Cree un archivo de texto y escriba algún texto que incluya llaves coincidentes.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Al colocar el símbolo de intercalación delante de una llave de apertura, se deben resaltar tanto esa llave como la llave de cierre correspondiente. Al colocar el cursor justo después de la llave de cierre, se deben resaltar tanto esa llave como la llave de apertura correspondiente.

## <a name="see-also"></a>Consulte también
- [Tutorial: vincular un tipo de contenido a una extensión de nombre de archivo](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
