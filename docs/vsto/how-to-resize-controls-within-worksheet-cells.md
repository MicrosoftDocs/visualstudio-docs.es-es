---
title: "C&#243;mo: Cambiar el tama&#241;o de controles en celdas de hojas de c&#225;lculo"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "controles [desarrollo de Office en Visual Studio], cambiar el tamaño"
  - "controles administrados, cambiar el tamaño"
  - "controles de formularios Windows Forms [desarrollo de Office en Visual Studio], cambiar el tamaño"
  - "hojas de cálculo, cambiar el tamaño"
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# C&#243;mo: Cambiar el tama&#241;o de controles en celdas de hojas de c&#225;lculo
  Cuando cambia el tamaño de las columnas o las filas de una hoja de cálculo, cualquier control host contenido en las celdas cambia de tamaño automáticamente para ajustarse al alto o ancho de la celda cuyo tamaño cambió.  Los controles de formularios Windows Forms no cambian el tamaño automáticamente de forma predeterminada.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 Si se agregan en tiempo de diseño, debe establecer las opciones de posición para cada control.  
  
 Si agrega un control de formulario Windows Forms mediante programación y proporciona un argumento de rango, el control cambia automáticamente el tamaño cuando se cambia el tamaño de una celda contenida en el rango.  Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## Cambiar el tamaño de los controles en tiempo de diseño  
  
#### Para hacer que cambie el tamaño de los controles junto con las celdas en tiempo de diseño  
  
1.  Desde el **Cuadro de herramientas** arrastre un control de formulario Windows Forms hasta una hoja de cálculo.  
  
2.  Haga clic con el botón secundario en el control y, a continuación, haga clic en **Formato de control**.  
  
3.  En el cuadro de diálogo **Formato de control**, haga clic en la ficha **Propiedades**.  
  
4.  En **Ubicación del objeto**, seleccione la opción **Mover y cambiar tamaño con celdas** y haga clic en **Aceptar**.  
  
     Cuando se cambia el tamaño de la celda que contiene el control, el control cambia el tamaño para ajustarse a la celda.  
  
## Cambiar el tamaño de los controles en tiempo de ejecución  
 Si agrega un control de formulario Windows Forms en tiempo de ejecución y pasa <xref:Microsoft.Office.Interop.Excel.Range> como la ubicación para el control, el control cambiará automáticamente el tamaño cuando se cambie el tamaño de la celda de hoja de cálculo que contiene el rango.  
  
#### Para hacer que cambie el tamaño de los controles junto con las celdas en tiempo de ejecución  
  
1.  Agregue un control al rango A1.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#5)]  
  
     Cuando se cambia el tamaño de la celda que contiene el control, el control cambia el tamaño para ajustarse a la celda.  
  
## Restablecer la ubicación del control  
 Puede restablecer la ubicación y el tamaño del control estableciendo la propiedad `Placement` en uno de los valores de <xref:Microsoft.Office.Interop.Excel.XlPlacement> siguientes:  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### Para cambiar el comportamiento de un control para que no cambie de tamaño ni se desplace con la celda  
  
1.  Llame a la propiedad de ubicación del control y establezca el valor en <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#6)]  
  
## Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Cómo: Agregar controles de Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Cómo: Ocultar controles en hojas de cálculo al imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Limitaciones de los controles de formularios Windows Forms en los documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  