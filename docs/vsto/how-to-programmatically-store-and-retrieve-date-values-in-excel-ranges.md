---
title: Almacenar & recuperar valores de fecha en intervalos de Excel mediante programación
description: Obtenga información sobre cómo puede usar Visual Studio almacenar y recuperar valores de fecha en intervalos de Microsoft Excel mediante programación.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6e3115e00147a5dff850f6e0c051ffc3b6733218
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826244"
---
# <a name="how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges"></a>Cómo: Almacenar y recuperar valores de fecha en intervalos de Excel mediante programación
  Puede almacenar y recuperar valores en un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o en un objeto de intervalo de Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Si almacena un valor de fecha que se encuentra en o después del 1/1/1900 en un intervalo mediante las herramientas de desarrollo de Office en Visual Studio, se almacena en formato ole automation (OA). Debe usar el método para recuperar el valor de las fechas de <xref:System.DateTime.FromOADate%2A> OLE Automation (OA). Si la fecha es anterior al 1/1/1900, se almacena como una cadena.

> [!NOTE]
> Las fechas de Excel difieren de las fechas de OLE Automation de los dos primeros meses de 1900. También hay diferencias si la opción del sistema de fecha **1904** está activada. Los ejemplos de código siguientes no abordan estas diferencias.

## <a name="use-a-namedrange-control"></a>Uso de un control NamedRange

- Este ejemplo es para las personalizaciones de nivel de documento. El código siguiente debe colocarse en una clase de hoja, no en la `ThisWorkbook` clase .

### <a name="to-store-a-date-value-in-a-named-range"></a>Para almacenar un valor de fecha en un intervalo con nombre

1. Cree un <xref:Microsoft.Office.Tools.Excel.NamedRange> control en la celda **A1.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet50":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet50":::

2. Establezca la fecha de hoy como el valor de `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet51":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet51":::

### <a name="to-retrieve-a-date-value-from-a-named-range"></a>Para recuperar un valor de fecha de un intervalo con nombre

1. Recupere el valor de fecha de `NamedRange1` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet52":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet52":::

## <a name="use-native-excel-ranges"></a>Uso de intervalos nativos de Excel

### <a name="to-store-a-date-value-in-a-native-excel-range-object"></a>Para almacenar un valor de fecha en un objeto de intervalo nativo de Excel

1. Cree un <xref:Microsoft.Office.Interop.Excel.Range> objeto que represente la **celda A1.**

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet25":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet25":::

2. Establezca la fecha de hoy como el valor de `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet26":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet26":::

### <a name="to-retrieve-a-date-value-from-a-native-excel-range-object"></a>Para recuperar un valor de fecha de un objeto de intervalo nativo de Excel

1. Recupere el valor de fecha de `rng` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet27":::

## <a name="see-also"></a>Consulte también
- [Trabajar con intervalos](../vsto/working-with-ranges.md)
- [Introducción al modelo de objetos de Excel](../vsto/excel-object-model-overview.md)
- [Control NamedRange](../vsto/namedrange-control.md)
- [Cómo: Hacer referencia mediante programación a los intervalos de hojas de cálculo en el código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
