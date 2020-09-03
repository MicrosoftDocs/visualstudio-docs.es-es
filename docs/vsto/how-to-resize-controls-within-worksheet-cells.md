---
title: 'Cómo: cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: f2d22973e13ee77b66de303041f8b6a765b4b93a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545878"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Cómo: cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo
  Al cambiar el tamaño de las columnas o filas de una hoja de cálculo, los controles host de las celdas se ajustan automáticamente al alto o ancho de la celda cuyo tamaño se cambió. Los controles Windows Forms no se ajustan automáticamente de forma predeterminada.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Si agrega los controles en tiempo de diseño, debe establecer las opciones de posición de cada control.

 Si agrega un control de Windows Forms mediante programación y proporciona un argumento de intervalo, el control cambia de tamaño automáticamente cuando se cambia el tamaño de una celda del intervalo. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Cambiar el tamaño de los controles en tiempo de diseño

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Para hacer que los controles cambien de tamaño con celdas en tiempo de diseño

1. En el **cuadro de herramientas**, arrastre un control Windows Forms a una hoja de cálculo.

2. Haga clic con el botón secundario en el control y, a continuación, haga clic en **formato de control**.

3. En el cuadro de diálogo **control de formato** , haga clic en la pestaña **propiedades** .

4. En **posición del objeto**, seleccione la opción **subir y cambiar el tamaño con celdas** y, a continuación, haga clic en **Aceptar**.

     Al cambiar el tamaño de la celda que contiene el control, el control cambia de tamaño para ajustarse a la celda.

## <a name="resize-controls-at-run-time"></a>Cambiar el tamaño de los controles en tiempo de ejecución
 Si agrega un control Windows Forms en tiempo de ejecución y pasa <xref:Microsoft.Office.Interop.Excel.Range> como la ubicación del control, el control cambiará de tamaño automáticamente cuando se cambie el tamaño de la celda de la hoja de cálculo que contiene el intervalo.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Para hacer que los controles cambien de tamaño con celdas en tiempo de ejecución

1. Agregue un control al rango a1.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     Al cambiar el tamaño de la celda que contiene el control, el control cambia de tamaño para ajustarse a la celda.

## <a name="reset-control-placement"></a>Restablecer la ubicación del control
 Puede restablecer la ubicación y el cambio de tamaño del control si establece la `Placement` propiedad en uno de los <xref:Microsoft.Office.Interop.Excel.XlPlacement> valores siguientes:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Cambiar el comportamiento de un control para que no cambie de tamaño ni se mueva con la celda

1. Llame a la propiedad Placement del control y establezca el valor en <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>Consulte también
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Cómo: agregar controles Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Cómo: ocultar controles en hojas de cálculo al imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitaciones de los controles de Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
