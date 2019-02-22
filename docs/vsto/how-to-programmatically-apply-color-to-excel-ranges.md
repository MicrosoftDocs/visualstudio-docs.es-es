---
title: Filtrar Aplicar color a rangos de Excel mediante programación
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- color, Excel ranges
- ranges, applying color
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d85803e478931022e5872ddde2746b5b90feacf
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614134"
---
# <a name="how-to-programmatically-apply-color-to-excel-ranges"></a>Procedimiento Aplicar color a rangos de Excel mediante programación
  Para aplicar un color al texto de un rango de celdas, use un <xref:Microsoft.Office.Tools.Excel.NamedRange> control o un objeto nativo de rango de Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Usar un control NamedRange
 En este ejemplo es para las personalizaciones de nivel de documento.

### <a name="to-apply-color-to-a-namedrange-control"></a>Aplicar color a un control NamedRange

1.  Crear un <xref:Microsoft.Office.Tools.Excel.NamedRange> control en la celda A1.

     [!code-csharp[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#65)]
     [!code-vb[Trin_VstcoreExcelAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#65)]

2.  Establecer el color del texto en el <xref:Microsoft.Office.Tools.Excel.NamedRange> control.

     [!code-csharp[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#66)]
     [!code-vb[Trin_VstcoreExcelAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#66)]

## <a name="use-native-excel-ranges"></a>Utilice los rangos de Excel nativos

### <a name="to-apply-color-to-a-native-excel-range-object"></a>Aplicar color a un objeto nativo de rango de Excel

1.  Cree un rango en la celda A1 y, a continuación, establezca el color del texto.

     [!code-csharp[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#67)]
     [!code-vb[Trin_VstcoreExcelAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#67)]

## <a name="see-also"></a>Vea también
- [Trabajar con rangos](../vsto/working-with-ranges.md)
- [NamedRange (control)](../vsto/namedrange-control.md)
- [Cómo: Aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Cómo: Mediante programación hacen referencia a rangos de hoja de cálculo en el código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
