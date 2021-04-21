---
title: 'Cómo: Aplicar color mediante programación a intervalos de Excel'
description: Aprenda que para aplicar un color al texto dentro de un intervalo de celdas, use un control NamedRange o un objeto de intervalo nativo de Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 081985dbd4b235fe5dd8d3472d0ab574603abe1b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828324"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Cómo: Aplicar color mediante programación a intervalos de Excel
  Para aplicar un color al texto dentro de un intervalo de celdas, use un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto de intervalo nativo de Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Uso de un control NamedRange
 Este ejemplo es para las personalizaciones de nivel de documento.

### <a name="to-apply-color-to-a-namedrange-control"></a>Para aplicar color a un control NamedRange

1. Cree un <xref:Microsoft.Office.Tools.Excel.NamedRange> control en la celda A1.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet65":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet65":::

2. Establezca el color del texto en el <xref:Microsoft.Office.Tools.Excel.NamedRange> control .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet66":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet66":::

## <a name="use-native-excel-ranges"></a>Uso de intervalos nativos de Excel

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Para aplicar color a un objeto de intervalo nativo de Excel

1. Cree un intervalo en la celda A1 y, a continuación, establezca el color del texto.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet67":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet67":::

## <a name="see-also"></a>Consulte también
- [Trabajar con intervalos](../vsto/working-with-ranges.md)
- [Control NamedRange](../vsto/namedrange-control.md)
- [Cómo: Aplicar estilos mediante programación a intervalos de libros](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Cómo: Hacer referencia mediante programación a los intervalos de hojas de cálculo en el código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatización de Excel mediante objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
