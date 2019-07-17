---
title: 'Tutorial: Creación de un glifo de margen | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa18b900ca44fbb52c646bfdf021beed6e77f504
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148855"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Tutorial: Crear un glifo de margen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede personalizar la apariencia de los márgenes del editor mediante el uso de extensiones de editor personalizado. En este tutorial se coloca un glifo personalizados en el margen del indicador cada vez que aparece la palabra "todo" en un comentario de código.  
  
## <a name="prerequisites"></a>Requisitos previos  
 A partir de Visual Studio 2015, no instale el SDK de Visual Studio desde el centro de descarga. Se incluye como una característica opcional en el programa de instalación de Visual Studio. También puede instalar el SDK de VS más adelante. Para obtener más información, consulte [instalar el SDK de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creación de un proyecto MEF  
  
1. Cree un proyecto de VSIX de C#. (En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C# / extensibilidad**, a continuación, **proyecto VSIX**.) Asigne a la solución el nombre `TodoGlyphTest`.  
  
2. Agregar un elemento de proyecto de clasificador de Editor. Para obtener más información, consulte [crear una extensión con una plantilla de elementos de Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Elimine los archivos de clase existentes.  
  
## <a name="defining-the-glyph"></a>Definir el glifo  
 Definir un glifo implementando la <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfaz.  
  
#### <a name="to-define-the-glyph"></a>Para definir el glifo  
  
1. Agregue un archivo de clase y asígnele el nombre `TodoGlyphFactory`.  
  
2. Agregue lo siguiente mediante declaraciones.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3. Agregue una clase denominada `TodoGlyphFactory` que implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4. Agregue un campo privado que define las dimensiones del glifo.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5. Implemente `GenerateGlyph` definiendo el elemento de interfaz de usuario de glifo. `TodoTag` se define más adelante en este tutorial.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6. Agregue una clase denominada `TodoGlyphFactoryProvider` que implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Exportar a esta clase con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "TodoGlyph", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de VsTextMarker después, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "código" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7. Implemente el <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> método creando el `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definir una etiqueta de la lista de tareas y un etiquetador  
 Definir la relación entre el elemento de interfaz de usuario que ha definido en los pasos anteriores y el margen del indicador mediante la creación de un tipo de etiqueta y el etiquetador y exportarlo mediante el uso de un proveedor del etiquetador.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Para definir una etiqueta a la lista de tareas y etiquetador  
  
1. Agregue un nuevo archivo de clase al proyecto y asígnele el nombre `TodoTagger`.  
  
2. Agregue las siguientes importaciones.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3. Agregue una clase denominada `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4. Modificar la clase denominada `TodoTagger` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de tipo `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5. Para el `TodoTagger` (clase), agregue los campos privados de un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> y para que el texto Buscar en la clasificación abarca.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6. Agregue un constructor que establece el clasificador.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método mediante la búsqueda de todas la clasificación abarca cuyos nombres incluyen la palabra "comment" y cuyo texto incluye el texto de búsqueda. Cada vez que se encuentra el texto de búsqueda, vuelta producen un nuevo <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> de tipo `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8. Declarar un `TagsChanged` eventos.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Agregue una clase denominada `TodoTaggerProvider` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>y se exporta con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "code" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Importar el <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> método creando el `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Compilar y probar el código  
 Para probar este código, compile la solución TodoGlyphTest y ejecútelo en la instancia experimental.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Para compilar y probar la solución TodoGlyphTest  
  
1. Compile la solución.  
  
2. Ejecute el proyecto presionando F5. Se crea una instancia de una segunda instancia de Visual Studio.  
  
3. Asegúrese de que se muestre el margen del indicador. (En el **herramientas** menú, haga clic en **opciones**. En el **Editor de texto** página, asegúrese de que **margen del indicador** está seleccionada.)  
  
4. Abra un archivo de código con comentarios. Agregue la palabra "todo" para una de las secciones de comentario.  
  
5. Un círculo azul claro que tiene un contorno azul oscuro debe aparecer en el margen del indicador a la izquierda de la ventana de código.
