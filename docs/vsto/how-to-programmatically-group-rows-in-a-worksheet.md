---
title: 'Cómo: agrupar filas en una hoja de cálculo mediante programación'
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 759ba8c6e0796b25a87e8bf0b08795aed5bade05
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537883"
---
# <a name="how-to-programmatically-group-rows-in-a-worksheet"></a>Cómo: agrupar filas en una hoja de cálculo mediante programación
  Puede agrupar una o varias filas enteras. Para crear un grupo en una hoja de cálculo, use un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto de intervalo de Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usar un control NamedRange
 Si agrega un <xref:Microsoft.Office.Tools.Excel.NamedRange> control a un proyecto de nivel de documento en tiempo de diseño, puede usar el control para crear mediante programación un grupo. En el ejemplo siguiente se da por supuesto que hay tres <xref:Microsoft.Office.Tools.Excel.NamedRange> controles en la misma hoja de cálculo: `data2001` , `data2002` y `dataAll` . Cada rango con nombre hace referencia a una fila completa de la hoja de cálculo.

### <a name="to-create-a-group-of-namedrange-controls-on-a-worksheet"></a>Para crear un grupo de controles NamedRange en una hoja de cálculo

1. Agrupe tres rangos con nombre llamando al <xref:Microsoft.Office.Tools.Excel.NamedRange.Group%2A> método de cada intervalo. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#32)]
     [!code-vb[Trin_VstcoreExcelAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#32)]

    > [!NOTE]
    > Para desagrupar filas, llame al <xref:Microsoft.Office.Tools.Excel.NamedRange.Ungroup%2A> método.

## <a name="use-native-excel-ranges"></a>Usar intervalos de Excel nativos
 En el código se supone que tiene tres intervalos de Excel denominados `data2001` , `data2002` y `dataAll` en una hoja de cálculo.

### <a name="to-create-a-group-of-excel-ranges-in-a-worksheet"></a>Para crear un grupo de intervalos de Excel en una hoja de cálculo

1. Agrupe tres rangos con nombre llamando al <xref:Microsoft.Office.Interop.Excel.Range.Group%2A> método de cada intervalo. En el ejemplo siguiente se da por supuesto que hay tres <xref:Microsoft.Office.Interop.Excel.Range> controles denominados `data2001` , `data2002` y `dataAll` en la misma hoja de cálculo. Cada rango con nombre hace referencia a una fila completa de la hoja de cálculo.

     [!code-csharp[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#33)]
     [!code-vb[Trin_VstcoreExcelAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#33)]

    > [!NOTE]
    > Para desagrupar filas, llame al <xref:Microsoft.Office.Interop.Excel.Range.Ungroup%2A> método.

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Cómo: agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
