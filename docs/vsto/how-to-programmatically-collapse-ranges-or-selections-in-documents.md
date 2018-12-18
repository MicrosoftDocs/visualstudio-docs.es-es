---
title: 'Cómo: contraer intervalos o selecciones en documentos de mediante programación'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fee3c821c0b6a39c8dfb499caa00355aa008d413
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906733"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Cómo: contraer intervalos o selecciones en documentos de mediante programación
  Si está trabajando con un objeto <xref:Microsoft.Office.Interop.Word.Range> o <xref:Microsoft.Office.Interop.Word.Selection> , puede que desee cambiar la selección a un punto de inserción antes de insertar el texto, para no sobrescribir el texto existente. Tanto el <xref:Microsoft.Office.Interop.Word.Range> y <xref:Microsoft.Office.Interop.Word.Selection> objetos tienen un método Collapse, que hace uso de la <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> valores de enumeración:  
  
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
  
4. Seleccione el control <xref:Microsoft.Office.Interop.Word.Range>.  
  
    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]  
  
   Si usa el valor de enumeración <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> , el texto se inserta al principio del párrafo siguiente.  
  
   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]  
  
   Puede que espere que al insertar una nueva frase, se inserte antes del marcador de párrafo, pero esto no ocurre porque el rango original incluye la marca de párrafo. Para obtener más información, consulte [Cómo: excluir marcas de párrafo al crear intervalos mediante programación](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).  
  
## <a name="document-level-customization-example"></a>Ejemplo de personalización de nivel de documento  
  
### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Para contraer un intervalo en una personalización de nivel de documento  
  
1.  En el siguiente ejemplo se muestra el método completo de una personalización de nivel de documento. Para usar este código, ejecútelo desde la clase `ThisDocument` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]  
  
## <a name="vsto-add-in-example"></a>Ejemplo de complemento de VSTO  
  
### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Para contraer un intervalo en un complemento de VSTO  
  
1.  El ejemplo siguiente muestra el método completo para un complemento de VSTO. Para usar este código, ejecútelo desde la clase `ThisAddIn` del proyecto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Cómo: definir y seleccionar rangos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Cómo: recuperar los caracteres inicial y final en los intervalos mediante programación](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Cómo: excluir marcas de párrafo al crear intervalos mediante programación](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)   
 [Cómo: ampliar intervalos en documentos de mediante programación](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Cómo: restablecer intervalos en documentos de Word de mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)  
  