---
title: Procedimiento Agrupar filas en una hoja de cálculo mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6cf553876aaad0a502c89a8b3c91002aed9e66f7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53896791"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Procedimiento Agrupar filas en una hoja de cálculo mediante programación
  Puede agrupar uno o más filas completas. Para crear un grupo en una hoja de cálculo, use un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto nativo de rango de Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="use-a-namedrange-control"></a>Usar un control NamedRange  
 Si agrega un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a un proyecto de nivel de documento en tiempo de diseño, puede utilizar el control para crear mediante programación un grupo. En el siguiente ejemplo se da por supuesto que hay tres <xref:Microsoft.Office.Tools.Excel.NamedRange> controles en la misma hoja de cálculo: `data2001`, `data2002`, y `dataAll`. Cada rango con nombre hace referencia a una fila completa en la hoja de cálculo.  
  
### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Para crear un grupo de controles NamedRange en una hoja de cálculo  
  
1.  Tres rangos con nombre de grupo mediante una llamada a la <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> método de cada rango. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Para desagrupar filas, llame a la <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> método.  
  
## <a name="use-native-excel-ranges"></a>Utilice los rangos de Excel nativos  
 El código supone que tiene tres rangos de Excel denominados `data2001`, `data2002`, y `dataAll` en una hoja de cálculo.  
  
### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Para crear un grupo de rangos de Excel en una hoja de cálculo  
  
1.  Tres rangos con nombre de grupo mediante una llamada a la <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> método de cada rango. En el siguiente ejemplo se da por supuesto que hay tres <xref:Microsoft.Office.Interop.Excel.Range> controles denominados `data2001`, `data2002`, y `dataAll` en la misma hoja de cálculo. Cada rango con nombre hace referencia a una fila completa en la hoja de cálculo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Para desagrupar filas, llame a la <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> método.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [NamedRange (control)](../vsto/namedrange-control.md)   
 [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
