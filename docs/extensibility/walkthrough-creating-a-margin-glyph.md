---
title: 'Tutorial: Creación de un glifo de margen ( Margin Glyph) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9588b150dd795fc2bc5e6c55d8f6e2359f609939
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697700"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Tutorial: Crear un glifo de margen
Puede personalizar la apariencia de los márgenes del editor mediante extensiones de editor personalizadas. Este tutorial coloca un glifo personalizado en el margen del indicador cada vez que aparece la palabra "todo" en un comentario de código.

## <a name="prerequisites"></a>Prerrequisitos
 A partir de Visual Studio 2015, no se instala el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en la configuración de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, vea [Instalar el SDK](../extensibility/installing-the-visual-studio-sdk.md)de Visual Studio .

## <a name="create-a-mef-project"></a>Crear un proyecto MEF

1. Cree un proyecto de VSIX de C. (En el cuadro de diálogo **Nuevo proyecto** , seleccione **Visual C/ Extensibilidad**y, a continuación, **Proyecto VSIX**.) Asigne un `TodoGlyphTest`nombre a la solución .

2. Agregue un elemento de proyecto Clasificador de editor. Para obtener más información, consulte Crear una extensión con una plantilla de elemento de [editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Elimine los archivos de clase existentes.

## <a name="define-the-glyph"></a>Definir el glifo
 Defina un glifo <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> ejecutando la interfaz.

### <a name="to-define-the-glyph"></a>Para definir el glifo

1. Agregue un archivo de clase y asígnele el nombre `TodoGlyphFactory`.

2. Agregue el código siguiente mediante declaraciones.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Agregue una `TodoGlyphFactory` clase denominada <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>que implemente .

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Agregue un campo privado que defina las dimensiones del glifo.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implementar `GenerateGlyph` mediante la definición del elemento de interfaz de usuario (UI) glifo. `TodoTag`se define más adelante en este tutorial.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Agregue una `TodoGlyphFactoryProvider` clase denominada <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>que implemente . Exporte esta <xref:Microsoft.VisualStudio.Utilities.NameAttribute> clase con un de <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> "TodoGlyph", <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> un de After VsTextMarker, un de "código" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Implemente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> el método creando una `TodoGlyphFactory`instancia de .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Definir una etiqueta Todo y un tagger
 Defina la relación entre el elemento de interfaz de usuario que definió en los pasos anteriores y el margen del indicador. Cree un tipo de etiqueta y un tagger y expórtelo mediante un proveedor de etiquetas.

### <a name="to-define-a-todo-tag-and-tagger"></a>Para definir una etiqueta de todo y un tagger

1. Agregue un nuevo archivo de clase `TodoTagger`al proyecto y asílo.

2. Agregue las importaciones siguientes.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Agregue una clase denominada `TodoTag`.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Modifique la `TodoTagger` clase denominada <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> que `TodoTag`implementa de tipo .

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. A `TodoTagger` la clase, agregue <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> campos privados para un y para que el texto se encuentre en los intervalos de clasificación.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Agregue un constructor que establezca el clasificador.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> el método buscando todos los intervalos de clasificación cuyos nombres incluyen la palabra "comentario" y cuyo texto incluye el texto de búsqueda. Cada vez que se encuentra el <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> texto `TodoTag`de búsqueda, devolver un nuevo tipo .

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Declarar `TagsChanged` un evento.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Agregue una `TodoTaggerProvider` clase denominada <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>que implemente y <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> expórtela <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> con un "código" y un de TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Importe <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>el archivo .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> el método creando una `TodoTagger`instancia de .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Compile y pruebe el código
 Para probar este código, compile la solución TodoGlyphTest y ejecútela en la instancia experimental.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Para compilar y probar la solución TodoGlyphTest

1. Compile la solución.

2. Ejecute el proyecto presionando **F5**. Se inicia una segunda instancia de Visual Studio.

3. Asegúrese de que se muestra el margen del indicador. (En el menú **Herramientas,** haga clic en **Opciones**. En la página Editor de **texto,** asegúrese de que **el margen del indicador** está seleccionado.)

4. Abra un archivo de código que tenga comentarios. Agregue la palabra "todo" a una de las secciones de comentarios.

5. Un círculo azul claro con un contorno azul oscuro aparece en el margen del indicador a la izquierda de la ventana de código.
