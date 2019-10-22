---
title: Procedimiento Mediante programación hacen referencia a rangos de hoja de cálculo en el código
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 2e82b884965c5c7362951c7d94199f90c93fbfc3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955968"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Procedimiento Mediante programación hacen referencia a rangos de hoja de cálculo en el código
  Usar un proceso similar para hacer referencia al contenido de un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto nativo de rango de Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usar un control NamedRange
 En el ejemplo siguiente se agrega un <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo y, a continuación, agrega texto a la celda del rango.

### <a name="to-refer-to-a-namedrange-control"></a>Para hacer referencia a un control NamedRange

1. Asignar una cadena a la <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propiedad de la <xref:Microsoft.Office.Tools.Excel.NamedRange> control. Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#46)]
     [!code-vb[Trin_VstcoreExcelAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#46)]

## <a name="use-native-excel-ranges"></a>Utilice los rangos de Excel nativos
 El ejemplo siguiente agrega un rango de Excel nativo a una hoja de cálculo y, a continuación, agrega texto a la celda del rango.

### <a name="to-refer-to-a-native-range-object"></a>Para hacer referencia a un objeto de rango nativo

1. Asignar una cadena a la <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> propiedad del intervalo.

     [!code-csharp[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#47)]
     [!code-vb[Trin_VstcoreExcelAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#47)]

## <a name="see-also"></a>Vea también
- [Trabajar con rangos](../vsto/working-with-ranges.md)
- [Cómo: Revisar la ortografía en hojas de cálculo mediante programación](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Cómo: Aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Cómo: Rellenar rangos automáticamente mediante programación con datos que cambian de forma incremental](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Cómo: Buscar texto en rangos de hoja de cálculo mediante programación](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
