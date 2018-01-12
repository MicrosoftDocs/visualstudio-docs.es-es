---
title: "Cómo: revisar la ortografía en hojas de cálculo mediante programación | Documentos de Microsoft"
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
- spellchecking
- spelling checker, worksheets
- worksheets, checking spelling
- spelling, checking in worksheets
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ed71e56c72a35f891e797b4c930e5ade9e83e332
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-check-spelling-in-worksheets"></a>Cómo: Revisar la ortografía en hojas de cálculo mediante programación
  Puede comprobar la ortografía en una hoja de cálculo mediante programación. El cuadro de diálogo **Ortografía** aparece automáticamente si hay palabras mal escritas en la hoja de cálculo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-check-spelling-in-a-worksheet-in-a-document-level-customization"></a>Para revisar la ortografía en una hoja de cálculo en una personalización de nivel de documento  
  
1.  Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> de la hoja de cálculo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#45)]
     [!code-vb[Trin_VstcoreExcelAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#45)]  
  
### <a name="to-check-spelling-in-a-worksheet-in-an-vsto-add-in"></a>Para revisar la ortografía en una hoja de cálculo en un complemento VSTO  
  
1.  Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.CheckSpelling%2A> de la hoja de cálculo activa.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#22)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#22](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#22)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: ejecutar cálculos de Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [NamedRange (Control)](../vsto/namedrange-control.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  