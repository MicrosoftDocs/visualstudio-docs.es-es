---
title: "Cómo: agregar controles Chart a hojas de cálculo | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], adding to worksheets
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1ba31b5577090c3aef01ad974ba51a72e6f9980e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-chart-controls-to-worksheets"></a>Cómo: Agregar controles Chart a hojas de cálculo
  Puede agregar controles <xref:Microsoft.Office.Tools.Excel.Chart> a una hoja de cálculo de Microsoft Office Excel en tiempo de diseño y en tiempo de ejecución en las personalizaciones de nivel de documento. También puede agregar controles <xref:Microsoft.Office.Tools.Excel.Chart> en tiempo de ejecución a los complementos de VSTO.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 En este tema se describen las tareas siguientes:  
  
-   [Agregar controles Chart en tiempo de diseño](#designtime)  
  
-   [Agregar controles Chart en tiempo de ejecución en un proyecto de nivel de documento](#runtimedoclevel)  
  
-   [Agregar controles Chart en tiempo de ejecución en un proyecto de complemento de VSTO](#runtimeaddin)  
  
 Para obtener más información acerca de <xref:Microsoft.Office.Tools.Excel.Chart> controles, vea [Control Chart](../vsto/chart-control.md).  
  
##  <a name="designtime"></a>Agregar controles Chart en tiempo de diseño  
 Puede agregar el control <xref:Microsoft.Office.Tools.Excel.Chart> a la hoja de cálculo de la misma manera que agregaría un gráfico desde la aplicación.  
  
> [!NOTE]  
>  El <xref:Microsoft.Office.Tools.Excel.Chart> control no está disponible en la **cuadro de herramientas** o **orígenes de datos** ventana.  
  
#### <a name="to-add-a-chart-host-control-to-a-worksheet-in-excel"></a>Para agregar un control host Chart a una hoja de cálculo de Excel  
  
1.  En el **insertar** ficha la **gráficos** grupo, haga clic en **columna**, haga clic en una categoría de gráficos y, a continuación, haga clic en el tipo de gráfico que desee.  
  
2.  En el **Insertar gráfico** cuadro de diálogo, haga clic en **Aceptar**.  
  
3.  En el **diseño** ficha la **datos** grupo, haga clic en **seleccionar datos**.  
  
4.  En el **Seleccionar origen de datos** cuadro de diálogo, haga clic en el **gráfico** **rango de datos** cuadro y borre las selecciones predeterminadas.  
  
5.  En el **datos de gráfico** hoja, seleccione el rango de celdas que contiene los datos para el gráfico (celdas **A5** a través de **D8**).  
  
6.  En el **Seleccionar origen de datos** cuadro de diálogo, haga clic en **Aceptar**.  
  
##  <a name="runtimedoclevel"></a>Agregar controles Chart en tiempo de ejecución en un proyecto de nivel de documento  
 Puede agregar el control <xref:Microsoft.Office.Tools.Excel.Chart> dinámicamente en tiempo de ejecución. Los gráficos creados dinámicamente no se conservan en el documento como controles host cuando se cierra. Para obtener más información, consulta [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Para agregar un control Chart a una hoja de cálculo mediante programación  
  
1.  En el controlador de eventos <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> de `Sheet1`, inserte el siguiente código para agregar el control <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a>Agregar controles Chart en tiempo de ejecución en un proyecto de complemento de VSTO  
 Puede agregar un control <xref:Microsoft.Office.Tools.Excel.Chart> mediante programación a cualquier hoja de cálculo abierta de un proyecto de complemento de VSTO. Para obtener más información, consulta [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
 Los controles Chart creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando se cierra la hoja de cálculo. Para obtener más información, consulta [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-chart-control-to-a-worksheet-programmatically"></a>Para agregar un control Chart a una hoja de cálculo mediante programación  
  
1.  El siguiente código genera un elemento host de hoja de cálculo que se basa en la hoja de cálculo abierta; luego, agrega un control <xref:Microsoft.Office.Tools.Excel.Chart>.  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/CSharp/Trin_Excel_Dynamic_Controls/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../vsto/codesnippet/VisualBasic/Trin_Excel_Dynamic_Controls/ThisAddIn.vb#9)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Este ejemplo tiene los siguientes requisitos:  
  
-   Datos que se deben representar gráficamente, almacenados en el rango de celdas A5 a D8 en la hoja de cálculo.  
  
## <a name="see-also"></a>Vea también  
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Chart (Control)](../vsto/chart-control.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  