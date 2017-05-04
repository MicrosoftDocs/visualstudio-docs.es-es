---
title: "C&#243;mo: Agregar controles ListObject a hojas de c&#225;lculo | Microsoft Docs"
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
  - "control ListObject, agregar a hojas de cálculo"
  - "controles [desarrollo de Office en Visual Studio], agregar a hojas de cálculo"
ms.assetid: 40788ecb-937f-4d2a-90ba-9c938e495b74
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# C&#243;mo: Agregar controles ListObject a hojas de c&#225;lculo
  Puede agregar controles <xref:Microsoft.Office.Tools.Excel.ListObject> a una hoja de cálculo de Microsoft Office Excel en tiempo de diseño y en tiempo de ejecución, en los proyectos de nivel de documento.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 También puede agregar controles <xref:Microsoft.Office.Tools.Excel.ListObject> en tiempo de ejecución a los proyectos de complementos VSTO.  
  
 En este tema se describen las tareas siguientes:  
  
-   [Agregar controles ListObject en tiempo de diseño](#designtime)  
  
-   [Agregar controles ListObject en tiempo de ejecución a un proyecto de nivel de documento](#runtimedoclevel)  
  
-   [Agregar controles ListObject en tiempo de ejecución a un proyecto de complemento VSTO](#runtimeaddin)  
  
 Para obtener más información sobre los controles <xref:Microsoft.Office.Tools.Excel.ListObject>, consulte [ListObject &#40;Control&#41;](../vsto/listobject-control.md).  
  
##  <a name="designtime"></a> Agregar controles ListObject en tiempo de diseño  
 Existen varias maneras de agregar controles <xref:Microsoft.Office.Tools.Excel.ListObject> a una hoja de cálculo en un proyecto de nivel de documento en tiempo de diseño: desde Excel, desde el **Cuadro de Herramientas** de Visual Studio y desde la ventana **Orígenes de datos**.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### Usar la cinta de opciones en Excel  
  
1.  En la ficha **Insertar**, del grupo **Tablas**, haga clic en **Tabla**.  
  
2.  Seleccione las celdas que desea incluir en la lista y haga clic en **Aceptar**.  
  
#### Usar el cuadro de herramientas  
  
1.  Desde la ficha **Controles de Excel** del **Cuadro de herramientas**, arrastre <xref:Microsoft.Office.Tools.Excel.ListObject> hacia la hoja de cálculo.  
  
     Aparecerá el cuadro de diálogo **Agregar control ListObject**.  
  
2.  Seleccione las celdas que desea incluir en la lista y haga clic en **Aceptar**.  
  
     Si no desea conservar el nombre predeterminado, puede cambiarlo en la ventana **Propiedades**.  
  
#### Usar la ventana Orígenes de datos  
  
1.  Abra la ventana **Orígenes de datos** y cree un origen de datos para su proyecto. Para obtener más información, consulta [Cómo: Conectarse a los datos de una base de datos](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
2.  Arrastre una tabla desde la ventana **Orígenes de datos** hasta la hoja de cálculo.  
  
     Un control <xref:Microsoft.Office.Tools.Excel.ListObject> enlazado a los datos se agrega a la hoja de cálculo. Para obtener más información, consulta [Enlace de datos y formularios Windows Forms](../Topic/Data%20Binding%20and%20Windows%20Forms.md).  
  
##  <a name="runtimedoclevel"></a> Agregar controles ListObject en tiempo de ejecución a un proyecto de nivel de documento  
 Puede agregar el control <xref:Microsoft.Office.Tools.Excel.ListObject> dinámicamente en tiempo de ejecución. Esto le permite crear los controles host en respuesta a eventos. Los objetos de lista creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando se cierra la hoja de cálculo. Para obtener más información, consulta [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Agregar un control ListObject a una hoja de cálculo mediante programación  
  
1.  En el controlador de eventos <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, escriba el código siguiente para agregar un control <xref:Microsoft.Office.Tools.Excel.ListObject> de las celdas **A1** hasta la **A4**.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsExcel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#2)]  
  
##  <a name="runtimeaddin"></a> Agregar controles ListObject en tiempo de ejecución a un proyecto de complemento VSTO  
 Puede agregar un control <xref:Microsoft.Office.Tools.Excel.ListObject> mediante programación a cualquier hoja de cálculo abierta de un proyecto de complemento VSTO. Los objetos de lista creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando esta se guarda y, a continuación, se cierra. Para obtener más información, consulta [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### Agregar un control ListObject a una hoja de cálculo mediante programación  
  
1.  El siguiente código crea un elemento host de hoja de cálculo que se basa en la hoja de cálculo abierta; a continuación, agrega un control <xref:Microsoft.Office.Tools.Excel.ListObject> de las celdas **A1** hasta la **A4**.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#8)]
     [!code-vb[Trin_Excel_Dynamic_Controls#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#8)]  
  
## Vea también  
 [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [ListObject &#40;Control&#41;](../vsto/listobject-control.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Cómo: Cambiar el tamaño de los controles ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  