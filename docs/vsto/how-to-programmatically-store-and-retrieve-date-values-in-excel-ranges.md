---
title: Almacenar & recuperar valores de fecha en rangos de Excel mediante programación
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], retrieving date values from ranges
- ranges, retrieving data values
- dates, retrieving from Excel ranges
- Excel [Office development in Visual Studio], storing date values in ranges
- date values, storing in Excel ranges
- dates, storing in Excel ranges
- ranges, storing date values
- date values
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e4cea02af59b6b6a8457d964bdce802e1e2b2b84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546970"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Cómo: almacenar y recuperar valores de fecha en rangos de Excel mediante programación
  Puede almacenar y recuperar valores en un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o en un objeto de intervalo de Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Si almacena un valor de fecha que cae en un intervalo de 1/1/1900, o después de él, con las herramientas de desarrollo de Office en Visual Studio, se almacena en formato de automatización OLE (OA). Debe utilizar el <xref:System.DateTime.FromOADate%2A> método para recuperar el valor de las fechas de automatización OLE (OA). Si la fecha es anterior a 1/1/1900, se almacena como una cadena.

> [!NOTE]
> Las fechas de Excel difieren de las fechas de automatización OLE durante los dos primeros meses de 1900. También hay diferencias si se activa la opción **sistema de fecha 1904** . Los ejemplos de código siguientes no abordan estas diferencias.

## <a name="use-a-namedrange-control"></a>Usar un control NamedRange

- Este ejemplo es para las personalizaciones de nivel de documento. El código siguiente se debe colocar en una clase Sheet, no en la `ThisWorkbook` clase.

### <a name="to-store-a-date-value-in-a-named-range"></a>Para almacenar un valor de fecha en un rango con nombre

1. Cree un <xref:Microsoft.Office.Tools.Excel.NamedRange> control en la celda **a1**.

     [!code-csharp[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#50)]
     [!code-vb[Trin_VstcoreExcelAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#50)]

2. Establezca la fecha de hoy como el valor de `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#51)]
     [!code-vb[Trin_VstcoreExcelAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#51)]

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Para recuperar un valor de fecha de un rango con nombre

1. Recupere el valor de fecha de `NamedRange1` .

     [!code-csharp[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#52)]
     [!code-vb[Trin_VstcoreExcelAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#52)]

## <a name="use-native-excel-ranges"></a>Usar intervalos de Excel nativos

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Para almacenar un valor de fecha en un objeto de intervalo de Excel nativo

1. Cree un <xref:Microsoft.Office.Interop.Excel.Range> que represente la celda **a1**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#25)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#25](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#25)]

2. Establezca la fecha de hoy como el valor de `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#26](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#26)]

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Para recuperar un valor de fecha de un objeto de intervalo de Excel nativo

1. Recupere el valor de fecha de `rng` .

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#27](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#27)]

## <a name="see-also"></a>Vea también
- [Trabajar con rangos](../vsto/working-with-ranges.md)
- [Información general del modelo de objetos de Excel](../vsto/excel-object-model-overview.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Cómo: hacer referencia a rangos de hojas de cálculo en el código mediante programación](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Cómo: agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
