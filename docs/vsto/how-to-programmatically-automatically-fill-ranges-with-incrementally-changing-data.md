---
title: Relleno automático de intervalos de datos que cambian incrementalmente mediante programación
description: Obtenga información sobre cómo el método AutoFill del objeto Range le permite rellenar un intervalo en una hoja de cálculo con valores automáticamente.
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
ms.openlocfilehash: 615331181b9402e0d2062142ad266bdd41dca4eb
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824944"
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Cómo: Rellenar intervalos automáticamente mediante programación con datos que cambian incrementalmente
  El <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método del objeto permite rellenar automáticamente un intervalo de una hoja de cálculo con <xref:Microsoft.Office.Interop.Excel.Range> valores. A menudo, el método se usa para almacenar valores que aumentan o <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> disminuyen incrementalmente en un intervalo. Puede especificar el comportamiento si proporciona una constante opcional de la <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> enumeración .

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Debe especificar dos intervalos al usar <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> :

- Intervalo que llama al <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método , que especifica el punto inicial del relleno y contiene un valor inicial.

- Intervalo que desea rellenar, que se pasa como parámetro al <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método . Este intervalo de destino debe incluir el intervalo que contiene el valor inicial.

    > [!NOTE]
    > No se puede pasar <xref:Microsoft.Office.Tools.Excel.NamedRange> un control en lugar de <xref:Microsoft.Office.Interop.Excel.Range> . Para obtener más información, vea [Limitaciones de programación de elementos host y controles host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

## <a name="example"></a>Ejemplo
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet49":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet49":::

## <a name="compile-the-code"></a>Compilar el código
 La primera celda del intervalo que desea rellenar debe contener un valor inicial.

 El ejemplo requiere que se rellenen tres regiones:

- La columna B debe incluir cinco días laborables. Para el valor inicial, escriba **Monday en** la celda B1.

- La columna C debe incluir cinco meses. Para el valor inicial, escriba **January en** la celda C1.

- La columna D debe incluir una serie de números, que se incrementan en dos para cada fila. Para los valores iniciales, escriba **4 en** la celda D1 y **6** en la celda D2.

## <a name="see-also"></a>Consulte también
- [Trabajar con intervalos](../vsto/working-with-ranges.md)
- [Cómo: Hacer referencia mediante programación a los intervalos de hojas de cálculo en el código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)
- [Cómo: Aplicar estilos mediante programación a intervalos en libros](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)
- [Cómo: Ejecutar cálculos de Excel mediante programación](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
