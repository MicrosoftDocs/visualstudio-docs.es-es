---
title: "C&#243;mo: Cambiar el tama&#241;o de los controles ListObject"
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
  - "controles [desarrollo de Office en Visual Studio], cambiar tamaño"
  - "Control ListObject, cambiar tamaño"
ms.assetid: a4c7dceb-7b55-447e-9b88-c3596a2fc361
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# C&#243;mo: Cambiar el tama&#241;o de los controles ListObject
  Aunque se puede establecer el tamaño de un control <xref:Microsoft.Office.Tools.Excel.ListObject> al agregarlo a un libro de Microsoft Office Excel, podrían ser necesarios cambios posteriores. Por ejemplo, conviene cambiar una lista de columnas de dos a tres columnas.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 En proyectos de nivel de documento, el tamaño de los controles <xref:Microsoft.Office.Tools.Excel.ListObject> se puede cambiar en tiempo de diseño o en tiempo de ejecución. Puede cambiar el tamaño de los controles <xref:Microsoft.Office.Tools.Excel.ListObject> en tiempo de ejecución a un proyecto de complemento VSTO.  
  
 En este tema se describen las tareas siguientes:  
  
-   [Cambiar el tamaño de controles ListObject en tiempo de diseño](#designtime)  
  
-   [Cambiar el tamaño de controles ListObject en tiempo de ejecución a un proyecto de nivel de documento](#runtimedoclevel)  
  
-   [Cambiar el tamaño de controles ListObject en tiempo de ejecución a un proyecto de complemento VSTO](#runtimeaddin)  
  
 Para obtener más información sobre los controles <xref:Microsoft.Office.Tools.Excel.ListObject>, consulte [ListObject &#40;Control&#41;](../vsto/listobject-control.md).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Para una demostración en vídeo relacionada, vea [Cómo agregar columnas a un objeto de lista enlazado a datos en tiempo de ejecución](http://go.microsoft.com/fwlink/?LinkID=130318).  
  
##  <a name="designtime"></a> Cambiar el tamaño de un control ListObject en tiempo de diseño  
 Para cambiar el tamaño de una lista, puede hacer clic y arrastrar uno de los controladores de tamaño, o puede volver a definir su tamaño en el cuadro de diálogo **Cambiar el tamaño de la lista**.  
  
#### Para cambiar el tamaño de una lista mediante el cuadro de diálogo Cambiar el tamaño de la lista  
  
1.  Haga clic con el botón secundario en un control <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
2.  Seleccione **Lista** y haga clic en **Cambiar el tamaño de lista** en el menú contextual.  
  
3.  Seleccione las celdas que quiere usar para definir el tamaño de la lista.  
  
4.  Haga clic en **Aceptar**.  
  
##  <a name="runtimedoclevel"></a> Cambiar el tamaño de controles ListObject en tiempo de ejecución a un proyecto de nivel de documento  
 Puede cambiar el tamaño de un control <xref:Microsoft.Office.Tools.Excel.ListObject> en tiempo de ejecución usando el método <xref:Microsoft.Office.Tools.Excel.ListObject.Resize%2A>. No puede usar este método para mover el control <xref:Microsoft.Office.Tools.Excel.ListObject> a una nueva ubicación en la hoja de cálculo. Los encabezados deben permanecer en la misma fila y el cambio de tamaño del control <xref:Microsoft.Office.Tools.Excel.ListObject> debe superponerse sobre el objeto de lista original. El control <xref:Microsoft.Office.Tools.Excel.ListObject> con el tamaño cambiado debe contener una fila de encabezado y al menos una fila de datos.  
  
#### Para cambiar el tamaño de un objeto de lista mediante programación  
  
1.  Cree un control <xref:Microsoft.Office.Tools.Excel.ListObject> que abarque de la celda **A1** a la **B3** en `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreHostControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#6)]  
  
2.  Cambie el tamaño de la lista para incluir las celdas de la **A1** a la **C5**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreHostControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#7)]  
  
##  <a name="runtimeaddin"></a> Cambiar el tamaño de ListObject en tiempo de ejecución a un proyecto de complemento VSTO  
 Se puede cambiar el tamaño de un control <xref:Microsoft.Office.Tools.Excel.ListObject> en tiempo de ejecución en cualquier hoja de cálculo abierta. Para obtener más información sobre cómo agregar un control <xref:Microsoft.Office.Tools.Excel.ListObject> a una hoja de cálculo mediante un complemento de VSTO, consulte [Cómo: Agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
#### Para cambiar el tamaño de un objeto de lista mediante programación  
  
1.  Cree un control <xref:Microsoft.Office.Tools.Excel.ListObject> que abarque de la celda **A1** a la **B3** en `Sheet1`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_Excel_Dynamic_Controls#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#12)]  
  
2.  Cambie el tamaño de la lista para incluir las celdas de la **A1** a la **C5**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#13)]
     [!code-vb[Trin_Excel_Dynamic_Controls#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#13)]  
  
## Vea también  
 [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [ListObject &#40;Control&#41;](../vsto/listobject-control.md)   
 [Cómo: Agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)   
 [Cómo: Cambiar el tamaño de los controles Bookmark](../vsto/how-to-resize-bookmark-controls.md)   
 [Cómo: Cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)  
  
  