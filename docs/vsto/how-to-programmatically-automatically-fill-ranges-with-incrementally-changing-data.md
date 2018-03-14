---
title: "Cómo: rellenar rangos automáticamente mediante programación con datos que cambian gradualmente | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: d6634fea629358368d3b61c5b505e5eec7ec0186
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Cómo: Rellenar rangos automáticamente con datos que cambian de forma incremental mediante programación
  El <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método de la <xref:Microsoft.Office.Interop.Excel.Range> objeto permite rellenar automáticamente un rango en una hoja de cálculo con los valores. A menudo, el <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método se usa para almacenar de forma incremental valores superiores o inferiores de un intervalo. Puede especificar el comportamiento proporcionando una constante opcional de la <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> enumeración.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Debe especificar dos rangos al utilizar <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   El rango que llama el <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método, que especifica el punto inicial del relleno y contiene un valor inicial.  
  
-   El rango que desea rellenar, pasado como un parámetro a la <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> método. Este intervalo de destino debe incluir el rango que contiene el valor inicial.  
  
    > [!NOTE]  
    >  No se puede pasar un <xref:Microsoft.Office.Tools.Excel.NamedRange> controlar en lugar de la <xref:Microsoft.Office.Interop.Excel.Range>. Para obtener más información, consulta [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="example"></a>Ejemplo  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 La primera celda del rango que desea rellenar debe contener un valor inicial.  
  
 El ejemplo requiere que rellene tres regiones:  
  
-   Columna B consiste en incluir cinco días de la semana. Para el valor inicial, escriba **el lunes** en la celda B1.  
  
-   Columna C es incluir cinco meses. Para el valor inicial, escriba **enero** en la celda C1.  
  
-   La columna D consiste en incluir una serie de números, en incrementos por dos para cada fila. Para los valores iniciales, escriba **4** en la celda D1 y **6** en la celda D2.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con rangos](../vsto/working-with-ranges.md)   
 [Cómo: hacer referencia mediante programación a los rangos de hoja de cálculo en el código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Cómo: aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Cómo: ejecutar cálculos de Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Parámetros opcionales en las soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  