---
title: 'Cómo: Cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo'
description: Obtenga información sobre cómo puede usar Visual Studio para cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo de Microsoft Excel tanto en tiempo de diseño como en tiempo de ejecución.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7b42c10fd82ec077b295a8bc683fa138c2eb095b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825750"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Cómo: Cambiar el tamaño de los controles dentro de las celdas de la hoja de cálculo
  Al cambiar el tamaño de las columnas o filas de una hoja de cálculo, cualquier control host dentro de las celdas cambia automáticamente de tamaño al alto o ancho de la celda a la que se ha cambiado el tamaño. Windows Forms controles no cambian de tamaño automáticamente de forma predeterminada.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Si agrega los controles en tiempo de diseño, debe establecer opciones de posicionamiento para cada control.

 Si agrega un control Windows Forms mediante programación y proporciona un argumento de intervalo, el control cambia automáticamente de tamaño cuando se cambia el tamaño de una celda dentro del intervalo. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución.](../vsto/adding-controls-to-office-documents-at-run-time.md)

## <a name="resize-controls-at-design-time"></a>Cambiar el tamaño de los controles en tiempo de diseño

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Para hacer que los controles cambien de tamaño con celdas en tiempo de diseño

1. Desde el **Cuadro de herramientas**, arrastre un control Windows Forms a una hoja de cálculo.

2. Haga clic con el botón derecho en el control y, a continuación, haga clic **en Control de formato**.

3. En el cuadro **de diálogo Control** de formato , haga clic en la **pestaña** Propiedades .

4. En **Posición de objetos**, seleccione la opción Mover y tamaño **con** celdas y, a continuación, haga clic **en Aceptar.**

     Al cambiar el tamaño de la celda que contiene el control, el control cambia de tamaño para ajustarse a la celda.

## <a name="resize-controls-at-run-time"></a>Cambiar el tamaño de los controles en tiempo de ejecución
 Si agrega un control Windows Forms en tiempo de ejecución y pasa como la ubicación del control, el control cambia automáticamente de tamaño cuando se cambia el tamaño de la celda de la hoja de cálculo que contiene el <xref:Microsoft.Office.Interop.Excel.Range> intervalo.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Para hacer que los controles cambien de tamaño con celdas en tiempo de ejecución

1. Agregue un control al intervalo A1.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet5":::

     Al cambiar el tamaño de la celda que contiene el control, el control cambia de tamaño para ajustarse a la celda.

## <a name="reset-control-placement"></a>Restablecimiento de la ubicación del control
 Puede restablecer la ubicación y el tamaño del control estableciendo la `Placement` propiedad en uno de los valores <xref:Microsoft.Office.Interop.Excel.XlPlacement> siguientes:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Para cambiar el comportamiento de un control para que no cambie el tamaño ni se mueva con la celda

1. Llame a la propiedad placement del control y establezca el valor en <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet6":::

## <a name="see-also"></a>Consulte también
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Cómo: Agregar controles Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Cómo: Ocultar controles en hojas de cálculo al imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitaciones de Windows Forms controles en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
