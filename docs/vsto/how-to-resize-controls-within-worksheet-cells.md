---
title: 'Cómo: cambiar el tamaño de controles dentro de las celdas de la hoja de cálculo | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b145d4435cdb295c94897424b318d328f995c340
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Cómo: Cambiar el tamaño de controles en celdas de hojas de cálculo
  Cuando cambia el tamaño de las columnas o filas en una hoja de cálculo, cambiar el tamaño de los controles de host contenidos en las celdas automáticamente para el alto o el ancho de la celda que se cambió de tamaño. Controles de formularios Windows Forms no cambian de tamaño automáticamente de forma predeterminada.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Si agrega los controles en tiempo de diseño, debe establecer opciones de posición para cada control.  
  
 Si agrega un control de formularios Windows Forms mediante programación y proporcionar un argumento de intervalo, el control cambia automáticamente de tamaño cuando se cambia el tamaño de una celda dentro del intervalo. Para obtener más información, consulta [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="resizing-controls-at-design-time"></a>Cambiar el tamaño de los controles en tiempo de diseño  
  
#### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Para que los controles cambiar el tamaño con las celdas en tiempo de diseño  
  
1.  Desde el **cuadro de herramientas**, arrastre un control de formularios Windows Forms a una hoja de cálculo.  
  
2.  Haga clic en el control y, a continuación, haga clic en **formato de Control**.  
  
3.  En el **Control de formato** cuadro de diálogo, haga clic en el **propiedades** ficha.  
  
4.  En **Object Positioning**, seleccione la **mover y cambiar tamaño con celdas** opción y, a continuación, haga clic en **Aceptar**.  
  
     Cuando cambia el tamaño de la celda que contiene el control, el control cambia de tamaño para ajustarse a la celda.  
  
## <a name="resizing-controls-at-run-time"></a>Cambiar el tamaño de los controles en tiempo de ejecución  
 Si agrega un control de formularios Windows Forms en tiempo de ejecución y pase un <xref:Microsoft.Office.Interop.Excel.Range> como ubicación para el control, el control cambia de tamaño automáticamente cuando se cambia el tamaño de la celda de la hoja de cálculo que contiene el intervalo.  
  
#### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Para que los controles cambiar el tamaño con las celdas en tiempo de ejecución  
  
1.  Agregar un control al rango A1.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]  
  
     Cuando cambia el tamaño de la celda que contiene el control, el control cambia de tamaño para ajustarse a la celda.  
  
## <a name="resetting-control-placement"></a>Restablecer la colocación del Control  
 Puede restablecer la posición y el tamaño del control estableciendo la `Placement` propiedad en uno de los siguientes <xref:Microsoft.Office.Interop.Excel.XlPlacement> valores:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Para cambiar el comportamiento de un control para que no cambie el tamaño o mover a la celda  
  
1.  Llame a la propiedad de colocación del control y establezca el valor en <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]  
  
## <a name="see-also"></a>Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Cómo: agregar controles a documentos de Office de Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Cómo: ocultar controles en hojas de cálculo al imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitaciones de los controles de Windows Forms en los documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  