---
title: Procedimiento Mostrar todas las hojas de cálculo en un libro de mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2cab3547bb23aa563e2c6b5bfe6a82a93fd5e29e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928729"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Procedimiento Mostrar todas las hojas de cálculo en un libro de mediante programación
  La clase <xref:Microsoft.Office.Interop.Excel.Workbook> proporciona un objeto <xref:Microsoft.Office.Interop.Excel.Worksheets>. Este objeto contiene una colección de todos los objetos <xref:Microsoft.Office.Interop.Excel.Worksheet> del libro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Para hacer una lista de todas las hojas de cálculo existentes en un libro en una personalización en el nivel del documento  
  
1.  Recorra en iteración la colección <xref:Microsoft.Office.Interop.Excel.Worksheets> y envíe el nombre de cada una de las hojas a un desplazamiento de celda desde un control <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#21)]  
  
## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Para hacer una lista de todas las hojas de cálculo existentes en un libro en un complemento de VSTO  
  
1.  Recorra en iteración la colección <xref:Microsoft.Office.Interop.Excel.Worksheets> y envíe el nombre de cada una de las hojas a un desplazamiento de celda desde un objeto <xref:Microsoft.Office.Interop.Excel.Range>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#13)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#13](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#13)]  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [Cómo: Agregar nuevas hojas de cálculo a libros mediante programación](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Cómo: Mover hojas de cálculo dentro de los libros de programación](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)  
