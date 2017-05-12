---
title: "C&#243;mo: Agregar controles Chart a hojas de c&#225;lculo"
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
  - "Chart (control) [desarrollo de Office en Visual Studio], agregar a hojas de cálculo"
  - "controles [desarrollo de Office en Visual Studio], agregar a hojas de cálculo"
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# C&#243;mo: Agregar controles Chart a hojas de c&#225;lculo
  Puede agregar controles <xref:Microsoft.Office.Tools.Excel.Chart> a una hoja de cálculo de Microsoft Office Excel en tiempo de diseño y en tiempo de ejecución en las personalizaciones de nivel de documento.  También puede agregar controles <xref:Microsoft.Office.Tools.Excel.Chart> en tiempo de ejecución a los complementos de VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 En este tema se describen las tareas siguientes:  
  
-   [Agregar controles Chart en tiempo de diseño](#designtime)  
  
-   [Agregar controles Chart en tiempo de ejecución a un proyecto de nivel de documento](#runtimedoclevel)  
  
-   [Agregar controles Chart en tiempo de ejecución a un proyecto de complemento de VSTO](#runtimeaddin)  
  
 Para obtener más información sobre los controles <xref:Microsoft.Office.Tools.Excel.Chart>, consulte [Chart &#40;Control&#41;](../vsto/chart-control.md).  
  
##  <a name="designtime"></a> Agregar controles Chart en tiempo de diseño  
 Puede agregar el control <xref:Microsoft.Office.Tools.Excel.Chart> a la hoja de cálculo de la misma manera que agregaría un gráfico desde la aplicación.  
  
> [!NOTE]  
>  El control <xref:Microsoft.Office.Tools.Excel.Chart> no está disponible en la ventana **Cuadro de herramientas** ni en **Orígenes de datos**.  
  
#### Para agregar un control host Chart a una hoja de cálculo de Excel  
  
1.  En la pestaña **Insertar**, en el grupo **Gráficos**, haga clic en **Columna**, haga clic en una categoría de gráficos y en el tipo de gráfico que desee.  
  
2.  En el cuadro de diálogo **Insertar gráfico**, haga clic en **Aceptar**.  
  
3.  En la pestaña **Diseño**, en el grupo **Datos**, haga clic en **Seleccionar datos**.  
  
4.  En el cuadro de diálogo **Seleccionar origen de datos**, haga clic en el cuadro **Rango de datos delgráfico** y borre las selecciones predeterminadas.  
  
5.  En la hoja **Datos de gráfico**, seleccione el rango de celdas que contiene los datos del gráfico \(desde la celda **A5** hasta la **D8**\).  
  
6.  En el cuadro de diálogo **Seleccionar origen de datos**, haga clic en **Aceptar**.  
  
##  <a name="runtimedoclevel"></a> Agregar controles Chart en tiempo de ejecución a un proyecto de nivel de documento  
 Puede agregar el control <xref:Microsoft.Office.Tools.Excel.Chart> dinámicamente en tiempo de ejecución.  Los gráficos creados dinámicamente no se conservan en el documento como controles host cuando se cierra.  Para obtener más información, consulte [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Para agregar un control Chart a una hoja de cálculo mediante programación  
  
1.  En el controlador de eventos <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, inserte el siguiente código para agregar el control <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> Agregar controles Chart en tiempo de ejecución a un proyecto de complemento de VSTO  
 Puede agregar un control <xref:Microsoft.Office.Tools.Excel.Chart> mediante programación a cualquier hoja de cálculo abierta de un proyecto de complemento de VSTO.  Para obtener más información, consulte [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Los controles Chart creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando se cierra la hoja de cálculo.  Para obtener más información, consulte [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### Para agregar un control Chart a una hoja de cálculo mediante programación  
  
1.  El siguiente código genera un elemento host de hoja de cálculo que se basa en la hoja de cálculo abierta; luego, agrega un control <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#9)]  
  
## Compilar el código  
 Este ejemplo tiene los siguientes requisitos:  
  
-   Datos que se deben representar gráficamente, almacenados en el rango de celdas A5 a D8 en la hoja de cálculo.  
  
## Vea también  
 [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Chart &#40;Control&#41;](../vsto/chart-control.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  