---
title: "Cómo: agregar nuevas hojas de cálculo a libros mediante programación | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, adding worksheets
- workbooks, creating worksheets
- worksheets, creating
- worksheets, adding to workbooks
ms.assetid: 19f0d815-51b2-406c-9f36-34aa0ec16b4a
caps.latest.revision: "52"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e6e0864baa39a8865701f28243c516ace3e5882
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-add-new-worksheets-to-workbooks"></a>Cómo: Agregar nuevas hojas de cálculo a libros mediante programación
  Puede crear una hoja de cálculo mediante programación y, a continuación, agregarla a la colección de hojas de cálculo del libro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-document-level-customization"></a>Para agregar una nueva hoja de cálculo a un libro en una personalización de nivel de documento  
  
1.  Use el método <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#15)]
     [!code-vb[Trin_VstcoreExcelAutomation#15](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#15)]  
  
     La nueva hoja de cálculo es un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo y no un elemento host. Si desea agregar un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> , debe agregar la hoja de cálculo en tiempo de diseño.  
  
### <a name="to-add-a-new-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Para agregar una nueva hoja de cálculo a un libro en un complemento de VSTO  
  
1.  Use el método <xref:Microsoft.Office.Interop.Excel.Worksheets.Add%2A> de la colección <xref:Microsoft.Office.Interop.Excel.Sheets> .  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#11)]  
  
     La nueva hoja de cálculo es un objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo y no un elemento host. También puede generar un elemento host <xref:Microsoft.Office.Tools.Excel.Worksheet> desde el objeto <xref:Microsoft.Office.Interop.Excel.Worksheet> nativo. Para obtener más información, consulta [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Cómo: eliminar hojas de cálculo mediante programación de los libros](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Cómo: seleccionar hojas de cálculo de mediante programación](../vsto/how-to-programmatically-select-worksheets.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  