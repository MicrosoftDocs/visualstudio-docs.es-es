---
title: 'Tutorial: crear un glifo de margen | Microsoft Docs'
description: Obtenga información acerca de cómo personalizar la apariencia de los márgenes del editor mediante el uso de extensiones de editor personalizadas mediante este tutorial.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8a2ac481ebf76fc2b34be841cd20d15b97fcfa9
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863084"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Tutorial: crear un glifo de margen
Puede personalizar la apariencia de los márgenes del editor mediante extensiones de editor personalizadas. En este tutorial se coloca un glifo personalizado en el margen del indicador siempre que aparece la palabra "todo" en un Comentario de código.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS después. Para obtener más información, vea [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creación de un proyecto MEF

1. Cree un proyecto VSIX en C#. (En el cuadro de diálogo **nuevo proyecto** , seleccione **Visual C#/extensibilidad** y, a continuación, **Proyecto VSIX**). Asigne a la solución el nombre `TodoGlyphTest` .

2. Agregue un elemento de proyecto clasificador de editor. Para obtener más información, vea [crear una extensión con una plantilla de elemento de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Elimine los archivos de clase existentes.

## <a name="define-the-glyph"></a>Definir el glifo
 Defina un glifo ejecutando la <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfaz.

### <a name="to-define-the-glyph"></a>Para definir el glifo

1. Agregue un archivo de clase y asígnele el nombre `TodoGlyphFactory`.

2. Agregue el código siguiente mediante declaraciones.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Agregue una clase denominada `TodoGlyphFactory` que implemente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Agregue un campo privado que defina las dimensiones del glifo.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implemente `GenerateGlyph` definiendo el elemento de interfaz de usuario (UI) del glifo. `TodoTag` se define más adelante en este tutorial.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Agregue una clase denominada `TodoGlyphFactoryProvider` que implemente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Exporte esta clase con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "TodoGlyph", una <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de después de VsTextMarker, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "Code" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Implemente el <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> método mediante la creación de instancias de `TodoGlyphFactory` .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Definir una etiqueta todo y un etiquetador
 Defina la relación entre el elemento de la interfaz de usuario que definió en los pasos anteriores y el margen del indicador. Cree un tipo de etiqueta y un etiquetador y expórtelo mediante un proveedor de etiquetadores.

### <a name="to-define-a-todo-tag-and-tagger"></a>Para definir una etiqueta todo y un etiquetador

1. Agregue un nuevo archivo de clase al proyecto y asígnele el nombre `TodoTagger` .

2. Agregue las importaciones siguientes.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Agregue una clase denominada `TodoTag`.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Modifique la clase denominada `TodoTagger` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de tipo `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. En la `TodoTagger` clase, agregue campos privados para un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> y para el texto que se va a buscar en los intervalos de clasificación.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Agregue un constructor que establezca el clasificador.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método buscando todos los intervalos de clasificación cuyos nombres incluyan la palabra "comment" y cuyo texto incluya el texto de búsqueda. Cada vez que se encuentra el texto de búsqueda, devuelve un nuevo <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> de tipo `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Declare un `TagsChanged` evento.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Agregue una clase denominada `TodoTaggerProvider` que implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> y expórtelos con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "Code" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Importe el <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> método mediante la creación de instancias de `TodoTagger` .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Compilar y probar el código
 Para probar este código, compile la solución TodoGlyphTest y ejecútela en la instancia experimental.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Para compilar y probar la solución TodoGlyphTest

1. Compile la solución.

2. Ejecute el proyecto presionando **F5**. Se inicia una segunda instancia de Visual Studio.

3. Asegúrese de que se muestra el margen del indicador. (En el menú **herramientas** , haga clic en **Opciones**. En la página **Editor de texto** , asegúrese de que la opción margen del **indicador** está seleccionada).

4. Abra un archivo de código que tenga Comentarios. Agregue la palabra "todo" a una de las secciones de comentario.

5. Aparece un círculo azul claro con un contorno azul oscuro en el margen del indicador situado a la izquierda de la ventana de código.
