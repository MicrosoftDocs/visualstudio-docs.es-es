---
title: 'Cómo: ejecutar cálculos de Excel mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para ejecutar cálculos mediante programación en un libro de Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, running calculations
- calculations, running in Excel
- Excel [Office development in Visual Studio], running calculations programmatically
- workbooks, running calculations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 761f58027171ccaa667aa26569e41c3b4a8b75a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880481"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Cómo: ejecutar cálculos de Excel mediante programación
  Se usa un proceso similar para ejecutar cálculos en un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o en un objeto de intervalo de Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Ejecutar cálculos en un control NamedRange
 En el ejemplo siguiente se crea un <xref:Microsoft.Office.Tools.Excel.NamedRange> en la celda a1 y, a continuación, se calcula la celda. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

### <a name="to-run-calculations-in-a-namedrange-control"></a>Para ejecutar cálculos en un control NamedRange

1. Cree el rango con nombre.

     [!code-csharp[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#75)]
     [!code-vb[Trin_VstcoreExcelAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#75)]

2. Llame al <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> método del intervalo especificado.

     [!code-csharp[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#76)]
     [!code-vb[Trin_VstcoreExcelAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#76)]

## <a name="run-calculations-in-a-native-excel-range"></a>Ejecutar cálculos en un intervalo de Excel nativo

### <a name="to-run-calculations-in-a-native-excel-range"></a>Para ejecutar cálculos en un intervalo de Excel nativo

1. Cree el rango con nombre.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#30)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#30](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#30)]

2. Llame al <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> método del intervalo especificado.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#31](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#31)]

## <a name="see-also"></a>Vea también
- [Trabajar con rangos](../vsto/working-with-ranges.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
