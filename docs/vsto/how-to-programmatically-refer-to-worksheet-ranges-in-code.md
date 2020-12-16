---
title: 'Cómo: hacer referencia a rangos de hojas de cálculo en el código mediante programación'
description: Obtenga información sobre cómo puede usar Visual Studio para hacer referencia mediante programación al contenido de un control NamedRange o a un objeto de intervalo de Excel nativo en una hoja de cálculo de Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, referring to
- worksheets, referring to ranges
- referring to worksheet ranges
- Excel [Office development in Visual Studio], referring to worksheet ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9756123038de33e8f8e69bd9a824822c26e2dc00
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526678"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Cómo: hacer referencia a rangos de hojas de cálculo en el código mediante programación
  Se usa un proceso similar para hacer referencia al contenido de un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto de intervalo de Excel nativo.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usar un control NamedRange
 En el siguiente ejemplo se agrega un <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo y, a continuación, se agrega texto a la celda del rango.

### <a name="to-refer-to-a-namedrange-control"></a>Para hacer referencia a un control NamedRange

1. Asigne una cadena a la <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propiedad del <xref:Microsoft.Office.Tools.Excel.NamedRange> control. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>Usar intervalos de Excel nativos
 En el siguiente ejemplo se agrega un intervalo de Excel nativo a una hoja de cálculo y, a continuación, se agrega texto a la celda del rango.

### <a name="to-refer-to-a-native-range-object"></a>Para hacer referencia a un objeto de intervalo nativo

1. Asigne una cadena a la <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> propiedad del intervalo.

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>Consulte también
- [Trabajar con rangos](../vsto/working-with-ranges.md)
- [Cómo: comprobar la ortografía en hojas de cálculo mediante programación](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Cómo: aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Cómo: rellenar rangos automáticamente con datos que cambian de forma incremental](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Cómo: buscar texto en rangos de hojas de cálculo mediante programación](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
