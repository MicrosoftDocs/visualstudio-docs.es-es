---
title: "C&#243;mo: Agregar controles NamedRange a hojas de c&#225;lculo"
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
  - "intervalos, agregar a hojas de cálculo"
  - "control NamedRange, agregar a hojas de cálculo"
  - "controles [desarrollo de Office en Visual Studio], agregar a hojas de cálculo"
ms.assetid: da7ec48f-92cb-4fa3-b3e2-447c238d17a8
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# C&#243;mo: Agregar controles NamedRange a hojas de c&#225;lculo
  Puede agregar controles <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo de Microsoft Office Excel en tiempo de diseño y en tiempo de ejecución, en los proyectos de nivel de documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 También puede agregar controles <xref:Microsoft.Office.Tools.Excel.NamedRange> en tiempo de ejecución a los proyectos de complementos VSTO.  
  
 En este tema se describen las tareas siguientes:  
  
-   [Agregar controles NamedRange en tiempo de diseño](#designtime)  
  
-   [Agregar controles NamedRange en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)  
  
-   [Agregar controles NamedRange en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)  
  
 Para obtener más información sobre los controles <xref:Microsoft.Office.Tools.Excel.NamedRange>, consulte [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md).  
  
##  <a name="designtime"></a> Agregar controles NamedRange en tiempo de diseño  
 Existen varias maneras de agregar controles <xref:Microsoft.Office.Tools.Excel.NamedRange> a una hoja de cálculo en un proyecto de nivel de documento en tiempo de diseño: desde Excel, desde el **Cuadro de Herramientas** de Visual Studio y desde la ventana **Orígenes de datos**.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Para agregar un control NamedRange a una hoja de cálculo usando el cuadro de nombre en Excel  
  
1.  Seleccione las celdas que quiere incluir en el rango con nombre.  
  
2.  En el **cuadro de nombres**, escriba un nombre para el rango y presione ENTRAR.  
  
     El **cuadro de nombre**s está situado al lado de la barra de fórmulas, justo sobre la columna **A** de la hoja de cálculo.  
  
#### Para agregar un control NamedRange a una hoja de cálculo con el cuadro de herramientas  
  
1.  Abra el **Cuadro de herramientas** y haga clic en la pestaña **Controles de Excel**.  
  
2.  Haga clic en <xref:Microsoft.Office.Tools.Excel.NamedRange> y arrástrelo a una hoja de cálculo.  
  
     Aparece el cuadro de diálogo **Agregar rango con nombre**.  
  
3.  Seleccione las celdas que quiere incluir en el rango con nombre.  
  
4.  Haga clic en **Aceptar**.  
  
     Si no quiere usar el nombre predeterminado que se le ha dado al control puede cambiarlo en la ventana **Propiedades**.  
  
#### Para agregar un control NamedRange a una hoja de cálculo con la ventana Orígenes de datos  
  
1.  Abra la ventana **Orígenes de datos** y cree un origen de datos para su proyecto. Para obtener más información, consulta [Cómo: Conectarse a los datos de una base de datos](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
2.  Arrastre un único campo desde la ventana **Orígenes de datos** hasta su hoja de cálculo.  
  
     Un control <xref:Microsoft.Office.Tools.Excel.NamedRange> enlazado a los datos se agrega a la hoja de cálculo. Para obtener más información, consulta [Enlace de datos y formularios Windows Forms](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27).  
  
##  <a name="runtimedoclevel"></a> Agregar controles NamedRange en tiempo de ejecución en un proyecto de nivel de documento  
 Puede agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> mediante programación a la hoja de cálculo en tiempo de ejecución. Esto le permite crear los controles host en respuesta a eventos. Los rangos con nombre creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando esta se cierra. Para obtener más información, consulta [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Para agregar un control NamedRange a una hoja de cálculo mediante programación  
  
1.  En el controlador de eventos <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, inserte el siguiente código para agregar el control <xref:Microsoft.Office.Tools.Excel.NamedRange> a la celda **A1** y establezca su propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> en `Hello world!`.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> Agregar controles NamedRange en tiempo de ejecución en un proyecto de complemento de VSTO  
 Puede agregar un control <xref:Microsoft.Office.Tools.Excel.NamedRange> mediante programación a cualquier hoja de cálculo abierta de un proyecto de complemento VSTO. Los rangos con nombre creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando esta se cierra. Para obtener más información, consulta [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Para agregar un control NamedRange a una hoja de cálculo mediante programación  
  
1.  El siguiente código crea un elemento host de hoja de cálculo que se basa en la hoja de cálculo abierta; a continuación, agrega un control <xref:Microsoft.Office.Tools.Excel.NamedRange> a la celda **A1** y establece su propiedad <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> en `Hello world`.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#7)]  
  
## Vea también  
 [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Cómo: Cambiar el tamaño de los controles NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  