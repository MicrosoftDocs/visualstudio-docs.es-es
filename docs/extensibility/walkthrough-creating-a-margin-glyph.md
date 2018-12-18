---
title: 'Tutorial: Crear un glifo de margen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1ac8d70c401d543afe73ac14d6f8617e5f375482
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497822"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Tutorial: Crear un glifo de margen
Puede personalizar la apariencia de los márgenes del editor mediante el uso de extensiones de editor personalizado. En este tutorial se coloca un glifo personalizados en el margen del indicador cada vez que aparece la palabra "todo" en un comentario de código.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Ha incluido como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Crear un proyecto MEF  
  
1.  Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Nombre de la solución `TodoGlyphTest`.  
  
2.  Agregar un elemento de proyecto de clasificador de Editor. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Elimine los archivos de clase existentes.  
  
## <a name="define-the-glyph"></a>Definir el glifo  
 Definir un glifo mediante la ejecución de la <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfaz.  
  
### <a name="to-define-the-glyph"></a>Para definir el glifo  
  
1.  Agregue un archivo de clase y asígnele el nombre `TodoGlyphFactory`.  
  
2.  Agregar el código siguiente mediante declaraciones.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Agregue una clase denominada `TodoGlyphFactory` que implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Agregue un campo privado que define las dimensiones del glifo.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implemente `GenerateGlyph` definiendo el elemento de interfaz de usuario de glifo. `TodoTag` se define más adelante en este tutorial.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Agregue una clase denominada `TodoGlyphFactoryProvider` que implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Exportar a esta clase con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "TodoGlyph", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de VsTextMarker después, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "código" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implemente el <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> método creando el `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## <a name="define-a-todo-tag-and-tagger"></a>Definir una etiqueta de la lista de tareas y un etiquetador  
 Definir la relación entre el elemento de interfaz de usuario que ha definido en los pasos anteriores y el margen del indicador. Crear un tipo de etiqueta y un etiquetador y exportarlo mediante un proveedor del etiquetador.  
  
### <a name="to-define-a-todo-tag-and-tagger"></a>Para definir una etiqueta a la lista de tareas y etiquetador  
  
1.  Agregue un nuevo archivo de clase al proyecto y asígnele el nombre `TodoTagger`.  
  
2.  Agregue las siguientes importaciones.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Agregue una clase denominada `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Modificar la clase denominada `TodoTagger` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de tipo `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Para el `TodoTagger` (clase), agregue los campos privados de un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> y para que el texto Buscar en la clasificación abarca.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Agregue un constructor que establece el clasificador.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método mediante la búsqueda de todas la clasificación abarca cuyos nombres incluyen la palabra "comment" y cuyo texto incluye el texto de búsqueda. Cada vez que se encuentra el texto de búsqueda, vuelta producen un nuevo <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> de tipo `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Declarar un `TagsChanged` eventos.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Agregue una clase denominada `TodoTaggerProvider` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>y se exporta con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "code" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importar el <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> método creando el `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## <a name="build-and-test-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución TodoGlyphTest y ejecútelo en la instancia experimental.  
  
### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Para compilar y probar la solución TodoGlyphTest  
  
1.  Compile la solución.  
  
2.  Ejecute el proyecto presionando **F5**. Se inicia una segunda instancia de Visual Studio.  
  
3.  Asegúrese de que se muestre el margen del indicador. (En el **herramientas** menú, haga clic en **opciones**. En el **Editor de texto** página, asegúrese de que **margen del indicador** está seleccionada.)  
  
4.  Abra un archivo de código con comentarios. Agregue la palabra "todo" para una de las secciones de comentario.  
  
5.  Aparece un círculo azul claro con un contorno azul oscuro en el margen del indicador a la izquierda de la ventana de código.