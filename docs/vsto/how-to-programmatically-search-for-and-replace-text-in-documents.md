---
title: Buscar y reemplazar texto en documentos mediante programación
description: Obtenga información sobre cómo puede usar Visual Studio para buscar y reemplazar texto en un documento de Microsoft Word mediante programación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0f2fc5bbfabbe2672ae59c55734a5cf57fc84318
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825165"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Cómo: Buscar y reemplazar texto en documentos mediante programación
  El objeto <xref:Microsoft.Office.Interop.Word.Find> es miembro de los objetos <xref:Microsoft.Office.Interop.Word.Selection> y <xref:Microsoft.Office.Interop.Word.Range> y puede usar cualquiera de ellos para buscar texto en documentos de Microsoft Office Word. El comando replace es una extensión del comando find.

 Use un objeto <xref:Microsoft.Office.Interop.Word.Find> para recorrer un documento de Microsoft Office Word y buscar un determinado texto, formato o estilo y use la propiedad <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> para reemplazar cualquiera de los elementos encontrados.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Usar un objeto Selection
 Cuando se usa un objeto <xref:Microsoft.Office.Interop.Word.Selection> para buscar texto, los criterios de búsqueda que especifique se aplicarán únicamente al texto actualmente seleccionado. Si la <xref:Microsoft.Office.Interop.Word.Selection> es un punto de inserción, se buscará en el documento. Cuando se encuentra el elemento que coincide con los criterios de búsqueda, se selecciona automáticamente.

 Es importante tener en cuenta que los criterios <xref:Microsoft.Office.Interop.Word.Find> son acumulativos, lo que significa que se agregan a los criterios de búsqueda anteriores. Borre el formato de las búsquedas anteriores mediante el método <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> antes de hacer la búsqueda.

### <a name="to-find-text-using-a-selection-object"></a>Para buscar texto mediante un objeto de selección

1. Asigne una cadena de búsqueda a una variable.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet68":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet68":::

2. Borre el formato de las búsquedas anteriores.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet69":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet69":::

3. Ejecute la búsqueda y se mostrará un cuadro de mensaje con los resultados.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet70":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet70":::

   En el siguiente ejemplo se muestra el método completo.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet67":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet67":::

## <a name="use-a-range-object"></a>Usar un objeto Range
 Los objetos <xref:Microsoft.Office.Interop.Word.Range> le permiten buscar texto sin mostrar nada en la interfaz de usuario. El objeto devuelve True si se encuentra texto que coincide con los criterios de búsqueda <xref:Microsoft.Office.Interop.Word.Find> y **False** si no lo hace.  También redefine el objeto <xref:Microsoft.Office.Interop.Word.Range> para que coincida con los criterios de búsqueda si se encuentra el texto.

### <a name="to-find-text-using-a-range-object"></a>Para buscar texto con un objeto Range

1. Defina un objeto <xref:Microsoft.Office.Interop.Word.Range> formado por el segundo párrafo del documento.

    El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet72":::

    El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet72":::

2. Con la propiedad del objeto , borre primero las opciones de formato existentes <xref:Microsoft.Office.Interop.Word.Range.Find%2A> <xref:Microsoft.Office.Interop.Word.Range> y, a continuación, busque la cadena **find me**.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet73":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet73":::

3. Se mostrarán los resultados de la búsqueda en un cuadro de mensaje; seleccione <xref:Microsoft.Office.Interop.Word.Range> para que sea visible.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet74":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet74":::

    Si se produce un error en la búsqueda, se seleccionará el segundo párrafo; si se hace correctamente, se mostrarán los criterios de búsqueda.

   En el siguiente ejemplo se muestra el código completo de una personalización de nivel de documento. Para usar este ejemplo, ejecute el código desde la clase `ThisDocument` del proyecto.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet71":::

   En el siguiente ejemplo se muestra el código completo de un complemento de VSTO. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet71":::

## <a name="search-for-and-replace-text-in-documents"></a>Búsqueda y reemplazo de texto en documentos
 El código siguiente busca en la selección actual y reemplaza todas las apariciones de la cadena **find me** por la cadena **Found**.

### <a name="to-search-for-and-replace-text-in-documents"></a>Para buscar y reemplazar texto en documentos

1. Agregue el siguiente código de ejemplo a la clase `ThisDocument` o `ThisAddIn` del proyecto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet75":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet75":::

     La clase <xref:Microsoft.Office.Interop.Word.Find> tiene un método <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> y la clase <xref:Microsoft.Office.Interop.Word.Replacement> también tiene su propio método <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A>. Al realizar operaciones de búsqueda y reemplazo, debe usar el método ClearFormatting de ambos objetos. Si solo lo usa en el objeto <xref:Microsoft.Office.Interop.Word.Find>, podría obtener resultados imprevistos en el texto de reemplazo.

2. Use el método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> del objeto <xref:Microsoft.Office.Interop.Word.Find> para reemplazar los elementos encontrados. Para especificar qué elementos reemplazar, use el *parámetro Replace.* Este parámetro puede ser uno de los siguientes valores <xref:Microsoft.Office.Interop.Word.WdReplace>:

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> reemplaza todos los elementos encontrados.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> no reemplaza ninguno de los elementos encontrados.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> reemplaza el primer elemento encontrado.

## <a name="see-also"></a>Consulte también
- [Cómo: Establecer opciones de búsqueda mediante programación en Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Cómo: Recorrer en bucle los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Cómo: Definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: Restaurar selecciones mediante programación después de las búsquedas](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
