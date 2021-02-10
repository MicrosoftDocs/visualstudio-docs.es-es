---
title: Contraer intervalos o selecciones en documentos mediante programación
description: Sepa que si está trabajando con un objeto de intervalo o selección, es posible que desee cambiar la selección a un punto de inserción antes de insertar texto.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9b063244c8ac611d3a864b9cc3753b5cd8460474
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964295"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Cómo: contraer intervalos o selecciones en documentos mediante programación
  Si está trabajando con un objeto <xref:Microsoft.Office.Interop.Word.Range> o <xref:Microsoft.Office.Interop.Word.Selection> , puede que desee cambiar la selección a un punto de inserción antes de insertar el texto, para no sobrescribir el texto existente. Los <xref:Microsoft.Office.Interop.Word.Range> objetos y <xref:Microsoft.Office.Interop.Word.Selection> tienen un método de contracción, que hace uso de los <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> valores de enumeración:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> contrae la selección hasta el principio de la selección. Esta es la opción predeterminada si no especifica un valor de enumeración.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> contrae la selección hasta el final de la selección.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Para contraer un rango e insertar texto nuevo

1. Cree un objeto <xref:Microsoft.Office.Interop.Word.Range> formado por el primer párrafo del documento.

    El siguiente ejemplo de código se puede usar en una personalización de nivel de documento.

    [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]

    El siguiente ejemplo de código se puede usar en un complemento de VSTO. Este código usa el documento activo.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]

2. Utilice el valor de enumeración <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> para contraer el rango.

    [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
    [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]

3. Inserte el texto nuevo.

    [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
    [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]

4. Seleccione <xref:Microsoft.Office.Interop.Word.Range>.

    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]

   Si usa el valor de enumeración <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> , el texto se inserta al principio del párrafo siguiente.

   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]

   Puede que espere que al insertar una nueva frase, se inserte antes del marcador de párrafo, pero esto no ocurre porque el rango original incluye la marca de párrafo. Para obtener más información, consulte [Cómo: excluir marcas de párrafo al crear intervalos mediante programación](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).

## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Para contraer un intervalo en una personalización de nivel de documento

1. En el siguiente ejemplo se muestra el método completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]

## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Para contraer un intervalo en un complemento de VSTO

1. En el ejemplo siguiente se muestra el método completo de un complemento de VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]

## <a name="see-also"></a>Vea también
- [Cómo: insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Cómo: definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Cómo: recuperar los caracteres inicial y final de los intervalos mediante programación](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Cómo: excluir marcas de párrafo al crear intervalos mediante programación](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Cómo: ampliar intervalos en documentos mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Cómo: restablecer intervalos en documentos de Word mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
