---
title: Autorrellenar cambiar intervalos de datos incrementalmente mediante programación
description: Obtenga información sobre cómo el método Autorrellenar del objeto Range le permite rellenar un rango en una hoja de cálculo con valores automáticamente.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 64af8ddfa0d3d086b661483e76cb9b2bd82ae5c9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892078"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Cómo: rellenar rangos automáticamente con datos que cambian de forma incremental
  El <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método del <xref:Microsoft.Office.Interop.Excel.Range> objeto le permite rellenar automáticamente un intervalo en una hoja de cálculo con valores. La mayoría de las veces, el <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método se usa para almacenar valores que aumentan o disminuyen de forma incremental en un intervalo. Puede especificar el comportamiento proporcionando una constante opcional de la <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> enumeración.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Debe especificar dos intervalos al usar <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> :

- El intervalo que llama al <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método, que especifica el punto inicial del relleno y contiene un valor inicial.

- El intervalo que desea rellenar, pasado como un parámetro al <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método. Este intervalo de destino debe incluir el intervalo que contiene el valor inicial.

    > [!NOTE]
    > No se puede pasar un <xref:Microsoft.Office.Tools.Excel.NamedRange> control en lugar de <xref:Microsoft.Office.Interop.Excel.Range> . Para obtener más información, vea [limitaciones de programación de elementos y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a>Ejemplo
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]

## <a name="compile-the-code"></a>Compilar el código
 La primera celda del rango que desea rellenar debe contener un valor inicial.

 El ejemplo requiere que se rellenen tres regiones:

- La columna B va a incluir cinco días de la semana. En el valor inicial, escriba **lunes** en la celda B1.

- La columna C va a incluir cinco meses. En el valor inicial, escriba **enero** en la celda C1.

- La columna D consiste en incluir una serie de números, incrementando en dos por cada fila. Para los valores iniciales, escriba **4** en la celda D1 y **6** en la celda D2.

## <a name="see-also"></a>Vea también
- [Trabajar con rangos](../vsto/working-with-ranges.md)
- [Cómo: hacer referencia a rangos de hojas de cálculo en el código mediante programación](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Cómo: aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Cómo: ejecutar cálculos de Excel mediante programación](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Información general sobre elementos y controles host](../vsto/host-items-and-host-controls-overview.md)
- [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
