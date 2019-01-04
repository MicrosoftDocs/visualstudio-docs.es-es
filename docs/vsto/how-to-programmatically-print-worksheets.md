---
title: Procedimiento Imprimir mediante programación las hojas de cálculo
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- worksheets, printing
- print preview, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2c5061c7b83173088a4031455f27d1332219b6f7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904557"
---
# <a name="how-to-programmatically-print-worksheets"></a>Procedimiento Imprimir mediante programación las hojas de cálculo
  Puede imprimir cualquier hoja de cálculo de un libro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="print-a-worksheet-in-a-document-level-customization"></a>Imprimir una hoja de cálculo en una personalización de nivel de documento  
  
### <a name="to-print-a-worksheet"></a>Para imprimir una hoja de cálculo  
  
1. Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintOut%2A> de `Sheet1`, solicite dos copias y obtenga una vista previa del documento antes de imprimirlo.  
  
    [!code-csharp[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#22)]
    [!code-vb[Trin_VstcoreExcelAutomation#22](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#22)]  
  
   El <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> método le permite mostrar el objeto especificado en el **vista previa de impresión** ventana. El siguiente código supone que tiene un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> denominado `Sheet1`.  
  
### <a name="to-preview-a-page-before-printing"></a>Para obtener una vista previa de una página antes de imprimirla  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.PrintPreview%2A> de la hoja de cálculo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#23)]
     [!code-vb[Trin_VstcoreExcelAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#23)]  
  
## <a name="print-a-worksheet-in-a-vsto-add-in"></a>Imprimir una hoja de cálculo en un complemento de VSTO  
  
### <a name="to-print-a-worksheet"></a>Para imprimir una hoja de cálculo  
  
1. Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintOut%2A> de la hoja de cálculo activa, solicite dos copias y obtenga una vista previa del documento antes de imprimirlo.  
  
    [!code-csharp[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#14)]
    [!code-vb[Trin_VstcoreExcelAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#14)]  
  
   El <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> método le permite mostrar el objeto especificado en el **vista previa de impresión** ventana.  
  
### <a name="to-preview-a-page-before-printing"></a>Para obtener una vista previa de una página antes de imprimirla  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> de la hoja de cálculo activa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#15)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Revisar la ortografía en hojas de cálculo mediante programación](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
