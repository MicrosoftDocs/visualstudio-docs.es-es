---
title: 'Cómo: Hacer referencia mediante programación a los intervalos de hojas de cálculo en el código'
description: Obtenga información sobre cómo puede usar Visual Studio para hacer referencia mediante programación al contenido de un control NamedRange o un objeto de intervalo nativo de Excel en una hoja de cálculo de Microsoft Excel.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6ea4e3da3c67d55aedea0d85a0a35b8ed2cf93b6
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827089"
---
# <a name="how-to-programmatically-refer-to-worksheet-ranges-in-code"></a>Cómo: Hacer referencia mediante programación a los intervalos de hojas de cálculo en el código
  Se usa un proceso similar para hacer referencia al contenido de un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto de intervalo nativo de Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Uso de un control NamedRange
 En el ejemplo siguiente se agrega a una hoja de cálculo y, a continuación, se agrega texto a <xref:Microsoft.Office.Tools.Excel.NamedRange> la celda del intervalo.

### <a name="to-refer-to-a-namedrange-control"></a>Para hacer referencia a un control NamedRange

1. Asigne una cadena a la <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> propiedad del <xref:Microsoft.Office.Tools.Excel.NamedRange> control . Este código se debe colocar en una clase Sheet, no en la clase `ThisWorkbook` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet46":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet46":::

## <a name="use-native-excel-ranges"></a>Uso de intervalos nativos de Excel
 En el ejemplo siguiente se agrega un intervalo nativo de Excel a una hoja de cálculo y, a continuación, se agrega texto a la celda del intervalo.

### <a name="to-refer-to-a-native-range-object"></a>Para hacer referencia a un objeto de intervalo nativo

1. Asigne una cadena a <xref:Microsoft.Office.Interop.Excel.Range.Value2%2A> la propiedad del intervalo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet47":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet47":::

## <a name="see-also"></a>Consulte también
- [Trabajar con intervalos](../vsto/working-with-ranges.md)
- [Cómo: Comprobar la ortografía en hojas de cálculo mediante programación](../vsto/how-to-programmatically-check-spelling-in-worksheets.md)
- [Cómo: Aplicar estilos mediante programación a intervalos en libros](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Cómo: Rellenar intervalos automáticamente mediante programación con datos que cambian incrementalmente](../vsto/how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data.md)
- [Cómo: Buscar texto en rangos de hojas de cálculo mediante programación](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)
- [Control NamedRange](../vsto/namedrange-control.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Limitaciones mediante programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
