---
title: 'Cómo: ejecutar cálculos de Excel mediante programación'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a02e86864065d2c626de2f6e7fea7528554f1391
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547386"
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

## <a name="see-also"></a>Consulte también
- [Trabajar con rangos](../vsto/working-with-ranges.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
