---
title: 'Cómo: Ejecutar cálculos de Excel mediante programación'
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
ms.openlocfilehash: 9fdc9cbc1966ac0fd862b795d66c7004f5089499
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823969"
---
# <a name="how-to-programmatically-run-excel-calculations"></a>Cómo: Ejecutar cálculos de Excel mediante programación
  Se usa un proceso similar para ejecutar cálculos en un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto de intervalo de Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="run-calculations-in-a-namedrange-control"></a>Ejecutar cálculos en un control NamedRange
 En el ejemplo siguiente se crea <xref:Microsoft.Office.Tools.Excel.NamedRange> un en la celda A1 y, a continuación, se calcula la celda. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

### <a name="to-run-calculations-in-a-namedrange-control"></a>Para ejecutar cálculos en un control NamedRange

1. Cree el intervalo con nombre.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet75":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet75":::

2. Llame al <xref:Microsoft.Office.Tools.Excel.NamedRange.Calculate%2A> método del intervalo especificado.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet76":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet76":::

## <a name="run-calculations-in-a-native-excel-range"></a>Ejecutar cálculos en un intervalo nativo de Excel

### <a name="to-run-calculations-in-a-native-excel-range"></a>Para ejecutar cálculos en un intervalo nativo de Excel

1. Cree el intervalo con nombre.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet30":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet30":::

2. Llame al <xref:Microsoft.Office.Interop.Excel.Range.Calculate%2A> método del intervalo especificado.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet31":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet31":::

## <a name="see-also"></a>Consulte también
- [Trabajar con intervalos](../vsto/working-with-ranges.md)
- [Control NamedRange](../vsto/namedrange-control.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
