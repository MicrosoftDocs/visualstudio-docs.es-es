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
ms.openlocfilehash: f3ef1a32d145169db815915ee93d03893943e71f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877907"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Cómo: buscar y reemplazar texto en documentos mediante programación
  El objeto <xref:Microsoft.Office.Interop.Word.Find> es miembro de los objetos <xref:Microsoft.Office.Interop.Word.Selection> y <xref:Microsoft.Office.Interop.Word.Range> y puede usar cualquiera de ellos para buscar texto en documentos de Microsoft Office Word. El comando replace es una extensión del comando find.

 Use un objeto <xref:Microsoft.Office.Interop.Word.Find> para recorrer un documento de Microsoft Office Word y buscar un determinado texto, formato o estilo y use la propiedad <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> para reemplazar cualquiera de los elementos encontrados.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Usar un objeto de selección
 Cuando se usa un objeto <xref:Microsoft.Office.Interop.Word.Selection> para buscar texto, los criterios de búsqueda que especifique se aplicarán únicamente al texto actualmente seleccionado. Si la <xref:Microsoft.Office.Interop.Word.Selection> es un punto de inserción, se buscará en el documento. Cuando se encuentra el elemento que coincide con los criterios de búsqueda, se selecciona automáticamente.

 Es importante tener en cuenta que los criterios <xref:Microsoft.Office.Interop.Word.Find> son acumulativos, lo que significa que se agregan a los criterios de búsqueda anteriores. Borre el formato de las búsquedas anteriores mediante el método <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> antes de hacer la búsqueda.

### <a name="to-find-text-using-a-selection-object"></a>Para buscar texto mediante un objeto de selección

1. Asigne una cadena de búsqueda a una variable.

    [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
    [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]

2. Borre el formato de las búsquedas anteriores.

    [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
    [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]

3. Ejecute la búsqueda y se mostrará un cuadro de mensaje con los resultados.

    [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
    [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]

   En el siguiente ejemplo se muestra el método completo.

   [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
   [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]

## <a name="use-a-range-object"></a>Usar un objeto Range
 Los objetos <xref:Microsoft.Office.Interop.Word.Range> le permiten buscar texto sin mostrar nada en la interfaz de usuario. El <xref:Microsoft.Office.Interop.Word.Find> objeto devuelve **true** si se encuentra texto que coincide con los criterios de búsqueda y **false** en caso contrario. También redefine el objeto <xref:Microsoft.Office.Interop.Word.Range> para que coincida con los criterios de búsqueda si se encuentra el texto.

### <a name="to-find-text-using-a-range-object"></a>Para buscar texto con un objeto Range

1. Defina un objeto <xref:Microsoft.Office.Interop.Word.Range> formado por el segundo párrafo del documento.

    El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

    [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]

    El siguiente ejemplo de código se puede usar en un complemento de VSTO. En este ejemplo se usa el documento activo.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]

2. Con la <xref:Microsoft.Office.Interop.Word.Range.Find%2A> propiedad del <xref:Microsoft.Office.Interop.Word.Range> objeto, borre primero las opciones de formato existentes y busque la cadena **Find me**.

    [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
    [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]

3. Se mostrarán los resultados de la búsqueda en un cuadro de mensaje; seleccione <xref:Microsoft.Office.Interop.Word.Range> para que sea visible.

    [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
    [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]

    Si se produce un error en la búsqueda, se seleccionará el segundo párrafo; si se hace correctamente, se mostrarán los criterios de búsqueda.

   En el siguiente ejemplo se muestra el código completo de una personalización de nivel de documento. Para usar este ejemplo, ejecute el código desde la clase `ThisDocument` del proyecto.

   [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]

   En el siguiente ejemplo se muestra el código completo de un complemento de VSTO. Para usar este ejemplo, ejecute el código desde la clase `ThisAddIn` del proyecto.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]

## <a name="search-for-and-replace-text-in-documents"></a>Buscar y reemplazar texto en documentos
 El código siguiente busca la selección actual y reemplaza todas las apariciones de la cadena **Find me** por la cadena **encontrada**.

### <a name="to-search-for-and-replace-text-in-documents"></a>Para buscar y reemplazar texto en documentos

1. Agregue el siguiente código de ejemplo a la clase `ThisDocument` o `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]

     La clase <xref:Microsoft.Office.Interop.Word.Find> tiene un método <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> y la clase <xref:Microsoft.Office.Interop.Word.Replacement> también tiene su propio método <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A>. Al realizar operaciones de búsqueda y reemplazo, debe utilizar el método ClearFormatting de ambos objetos. Si solo lo usa en el objeto <xref:Microsoft.Office.Interop.Word.Find>, podría obtener resultados imprevistos en el texto de reemplazo.

2. Use el método <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> del objeto <xref:Microsoft.Office.Interop.Word.Find> para reemplazar los elementos encontrados. Para especificar los elementos que se van a reemplazar, use el parámetro *Replace* . Este parámetro puede ser uno de los siguientes valores <xref:Microsoft.Office.Interop.Word.WdReplace>:

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> reemplaza todos los elementos encontrados.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> no reemplaza ninguno de los elementos encontrados.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> reemplaza el primer elemento encontrado.

## <a name="see-also"></a>Vea también
- [Cómo: establecer opciones de búsqueda en Word mediante programación](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Cómo: recorrer los elementos encontrados en documentos mediante programación](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Cómo: definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: restaurar selecciones después de realizar búsquedas mediante programación](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
