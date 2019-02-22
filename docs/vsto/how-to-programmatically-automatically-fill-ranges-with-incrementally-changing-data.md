---
title: Filtrar Rellenar rangos automáticamente mediante programación con datos que cambian de forma incremental
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 36a91875d2964bf952f039a699da6ed165afa090
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638535"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Filtrar Rellenar rangos automáticamente mediante programación con datos que cambian de forma incremental
  El <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método de la <xref:Microsoft.Office.Interop.Excel.Range> objeto le permite rellenar un rango en una hoja de cálculo con los valores automáticamente. A menudo, el <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método se utiliza para almacenar incrementalmente valores superiores o inferiores de un intervalo. Puede especificar el comportamiento proporcionando una constante opcional de la <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> enumeración.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Debe especificar dos rangos al usar <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:

-   El rango que llama el <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método, que especifica el punto inicial del relleno y contiene un valor inicial.

-   El intervalo que se va a rellenar, pasado como parámetro a la <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método. El rango de destino debe incluir el rango que contiene el valor inicial.

    > [!NOTE]
    >  No puede pasar un <xref:Microsoft.Office.Tools.Excel.NamedRange> control en lugar de la <xref:Microsoft.Office.Interop.Excel.Range>. Para obtener más información, consulte [limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>Compilar el código
 La primera celda del rango que desea rellenar debe contener un valor inicial.

 El ejemplo requiere que rellene tres regiones:

-   Columna B consiste en incluir cinco días de la semana. Para el valor inicial, escriba **el lunes** en la celda B1.

-   La columna C es incluir cinco meses. Para el valor inicial, escriba **enero** en la celda C1.

-   La columna D es incluir una serie de números, incrementos de dos para cada fila. Para los valores iniciales, escriba **4** en la celda D1 y **6** en la celda D2.

## <a name="see-also"></a>Vea también
- [Trabajar con rangos](../vsto/working-with-ranges.md)
- [Cómo: Mediante programación hacen referencia a rangos de hoja de cálculo en el código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Cómo: Aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Cómo: Ejecutar cálculos de Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Elementos host y la información general sobre controles de host](../vsto/host-items-and-host-controls-overview.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
