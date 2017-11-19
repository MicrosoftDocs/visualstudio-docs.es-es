---
title: "Cómo: agrupar las filas en una hoja de cálculo mediante programación | Documentos de Microsoft"
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
- worksheets, creating groups
- groups, creating in worksheets
- ranges, creating groups
- worksheets, clearing groups
- groups
- groups [Office development in Visual Studio], clearing in worksheets
- worksheets, ungrouping rows and columns
- rows [Office development in Visual Studio], ungrouping
- columns [Office development in Visual Studio], ungrouping
ms.assetid: 48037dca-35a2-4df2-918b-6a9f568fae91
caps.latest.revision: "46"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c11911d6d9e7b92b7a86b21723c8788afe15a57b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Cómo: Agrupar filas de una hoja de cálculo mediante programación
  Puede agrupar uno o más filas enteras. Para crear un grupo en una hoja de cálculo, use un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto de rango de Excel nativo.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="using-a-namedrange-control"></a>Uso de un Control NamedRange  
 Si agrega un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a un proyecto de nivel de documento en tiempo de diseño, puede utilizar el control para crear mediante programación un grupo. En el siguiente ejemplo se da por supuesto que hay tres <xref:Microsoft.Office.Tools.Excel.NamedRange> controles en la misma hoja de cálculo: `data2001`, `data2002`, y `dataAll`. Cada rango con nombre hace referencia a una fila completa en la hoja de cálculo.  
  
#### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Para crear un grupo de controles NamedRange en una hoja de cálculo  
  
1.  Grupo tres rangos con nombre mediante una llamada a la <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> método de cada rango. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]  
  
    > [!NOTE]  
    >  Para desagrupar filas, llame a la <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> método.  
  
## <a name="using-native-excel-ranges"></a>Uso de rangos de Excel nativo  
 El código supone que tiene tres rangos de Excel denominados `data2001`, `data2002`, y `dataAll` en una hoja de cálculo.  
  
#### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Para crear un grupo de rangos de Excel en una hoja de cálculo  
  
1.  Grupo tres rangos con nombre mediante una llamada a la <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> método de cada rango. En el siguiente ejemplo se da por supuesto que hay tres <xref:Microsoft.Office.Interop.Excel.Range> controles denominados `data2001`, `data2002`, y `dataAll` en la misma hoja de cálculo. Cada rango con nombre hace referencia a una fila completa en la hoja de cálculo.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]  
  
    > [!NOTE]  
    >  Para desagrupar filas, llame a la <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> método.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)   
 [NamedRange (Control)](../vsto/namedrange-control.md)   
 [Cómo: agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  