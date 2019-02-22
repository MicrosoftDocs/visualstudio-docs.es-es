---
title: Filtrar Cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d039de309e1e9d5ec80d469d4d1329aad7118e71
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56625470"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Filtrar Cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo
  Cuando cambia el tamaño de columnas o filas de una hoja de cálculo, los controles host dentro de las celdas que se ajustan automáticamente el alto o ancho de la celda que se cambió el tamaño. Controles de formularios Windows Forms no cambian de tamaño automáticamente de forma predeterminada.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Si agrega los controles en tiempo de diseño, debe establecer las opciones para cada control de posición.

 Si agregar mediante programación un control de Windows Forms y proporcionar un argumento de intervalo, el control cambia automáticamente de tamaño cuando se cambia el tamaño de una celda dentro del intervalo. Para obtener más información, consulte [agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Cambiar el tamaño de los controles en tiempo de diseño

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Para que los controles de cambio de tamaño con las celdas en tiempo de diseño

1.  Desde el **cuadro de herramientas**, arrastre un control de Windows Forms a una hoja de cálculo.

2.  Haga clic en el control y, a continuación, haga clic en **formato Control**.

3.  En el **formato Control** cuadro de diálogo, haga clic en el **propiedades** ficha.

4.  En **ubicación del objeto**, seleccione el **mover y cambiar el tamaño de las celdas** opción y, a continuación, haga clic en **Aceptar**.

     Cuando cambia el tamaño de la celda que contiene el control, el control cambia de tamaño para ajustarse a la celda.

## <a name="resize-controls-at-runtime"></a>Cambiar el tamaño de los controles en tiempo de ejecución
 Si agrega un control de Windows Forms en tiempo de ejecución y pase un <xref:Microsoft.Office.Interop.Excel.Range> como ubicación para el control, el control cambia de tamaño automáticamente cuando se cambia el tamaño de la celda de la hoja de cálculo que contiene el intervalo.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Para que los controles de cambio de tamaño con las celdas en tiempo de ejecución

1.  Agregue un control al rango A1.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     Cuando cambia el tamaño de la celda que contiene el control, el control cambia de tamaño para ajustarse a la celda.

## <a name="reset-control-placement"></a>Restablecer la posición del control
 Puede restablecer la posición y el tamaño del control estableciendo la `Placement` propiedad en uno de los siguientes <xref:Microsoft.Office.Interop.Excel.XlPlacement> valores:

-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Para cambiar el comportamiento de un control para que no cambie el tamaño o se mueven con la celda

1.  Llame a la propiedad de colocación del control y establezca el valor en <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>Vea también
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Cómo: Agregar controles de formularios Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Cómo: Ocultar controles en hojas de cálculo al imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitaciones de los controles de Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
