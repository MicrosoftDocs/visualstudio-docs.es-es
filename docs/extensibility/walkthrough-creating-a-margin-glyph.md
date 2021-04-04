---
title: 'Tutorial: crear un glifo de margen | Microsoft Docs'
description: Obtenga información acerca de cómo personalizar la apariencia de los márgenes del editor mediante el uso de extensiones de editor personalizadas mediante este tutorial.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec5eecef40220c2cf2d4e3f1ece8eb5eb763bdeb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217416"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Tutorial: crear un glifo de margen
Puede personalizar la apariencia de los márgenes del editor mediante extensiones de editor personalizadas. En este tutorial se coloca un glifo personalizado en el margen del indicador siempre que aparece la palabra "todo" en un Comentario de código.

## <a name="prerequisites"></a>Requisitos previos
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

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet1":::

3. Agregue una clase denominada `TodoGlyphFactory` que implemente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet2":::

4. Agregue un campo privado que defina las dimensiones del glifo.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet3":::

5. Implemente `GenerateGlyph` definiendo el elemento de interfaz de usuario (UI) del glifo. `TodoTag` se define más adelante en este tutorial.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet4":::

6. Agregue una clase denominada `TodoGlyphFactoryProvider` que implemente <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Exporte esta clase con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> de "TodoGlyph", una <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> de después de VsTextMarker, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "Code" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet5":::

7. Implemente el <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> método mediante la creación de instancias de `TodoGlyphFactory` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet6":::

## <a name="define-a-todo-tag-and-tagger"></a>Definir una etiqueta todo y un etiquetador
 Defina la relación entre el elemento de la interfaz de usuario que definió en los pasos anteriores y el margen del indicador. Cree un tipo de etiqueta y un etiquetador y expórtelo mediante un proveedor de etiquetadores.

### <a name="to-define-a-todo-tag-and-tagger"></a>Para definir una etiqueta todo y un etiquetador

1. Agregue un nuevo archivo de clase al proyecto y asígnele el nombre `TodoTagger` .

2. Agregue las importaciones siguientes.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet7":::

3. Agregue una clase denominada `TodoTag`.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet8":::

4. Modifique la clase denominada `TodoTagger` que implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> de tipo `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet9":::

5. En la `TodoTagger` clase, agregue campos privados para un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> y para el texto que se va a buscar en los intervalos de clasificación.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet10":::

6. Agregue un constructor que establezca el clasificador.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet11":::

7. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> método buscando todos los intervalos de clasificación cuyos nombres incluyan la palabra "comment" y cuyo texto incluya el texto de búsqueda. Cada vez que se encuentra el texto de búsqueda, devuelve un nuevo <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> de tipo `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet12":::

8. Declare un `TagsChanged` evento.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet13":::

9. Agregue una clase denominada `TodoTaggerProvider` que implemente <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> y expórtelos con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> de "Code" y un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> de TodoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet14":::

10. Importe el <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet15":::

11. Implemente el <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> método mediante la creación de instancias de `TodoTagger` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet16":::

## <a name="build-and-test-the-code"></a>Compilar y probar el código
 Para probar este código, compile la solución TodoGlyphTest y ejecútela en la instancia experimental.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Para compilar y probar la solución TodoGlyphTest

1. Compile la solución.

2. Ejecute el proyecto presionando **F5**. Se inicia una segunda instancia de Visual Studio.

3. Asegúrese de que se muestra el margen del indicador. (En el menú **herramientas** , haga clic en **Opciones**. En la página **Editor de texto** , asegúrese de que la opción margen del **indicador** está seleccionada).

4. Abra un archivo de código que tenga Comentarios. Agregue la palabra "todo" a una de las secciones de comentario.

5. Aparece un círculo azul claro con un contorno azul oscuro en el margen del indicador situado a la izquierda de la ventana de código.
