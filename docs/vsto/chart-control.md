---
title: "Control de gráfico | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VST.ProjectItem.ExcelChart
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Chart control [Office development in Visual Studio], events
- Chart control [Office development in Visual Studio]
- Chart control [Office development in Visual Studio], data binding
ms.assetid: 64f1a7cc-cc66-47da-aaeb-44a62ae53909
caps.latest.revision: "51"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 15583118629a5b75854c87892ccc85db59d49322
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="chart-control"></a>Chart Control
  El control <xref:Microsoft.Office.Tools.Excel.Chart> es un objeto de gráfico que expone eventos. Al agregar un gráfico a una hoja de cálculo, Visual Studio crea un objeto <xref:Microsoft.Office.Tools.Excel.Chart> que se puede programar directamente sin tener que recorrer el modelo de objetos de Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="creating-the-control"></a>Crear el control  
 Puede agregar controles <xref:Microsoft.Office.Tools.Excel.Chart> a una hoja de cálculo de Microsoft Office Excel en tiempo de diseño o en tiempo de ejecución en un proyecto de nivel de documento.  
  
 Puede agregar controles <xref:Microsoft.Office.Tools.Excel.Chart> a una hoja de cálculo en tiempo de ejecución en un complemento de VSTO. Para obtener más información, consulte [Cómo: agregar controles Chart a hojas de cálculo](../vsto/how-to-add-chart-controls-to-worksheets.md).  
  
> [!NOTE]  
>  Los objetos de gráfico creados de forma dinámica no se conservan en la hoja de cálculo como controles host cuando se cierra la hoja de cálculo. Para obtener más información, consulta [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
## <a name="formatting"></a>Formato  
 Todo el formato que se puede aplicar a un control <xref:Microsoft.Office.Interop.Excel.Chart> también puede aplicarse a un control <xref:Microsoft.Office.Tools.Excel.Chart>. Esto incluye bordes, fuentes, tipo de gráfico, líneas de cuadrícula, leyenda y etiquetas de datos.  
  
## <a name="events"></a>Eventos  
 Los eventos siguientes están disponibles para el control <xref:Microsoft.Office.Tools.Excel.Chart>:  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.ActivateEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeDoubleClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BeforeRightClick>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.BindingContextChanged>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Calculate>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Deactivate>  
  
-   <xref:System.ComponentModel.Component.Disposed>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragOver>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.DragPlot>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseDown>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseMove>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.MouseUp>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.Resize>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SelectEvent>  
  
-   <xref:Microsoft.Office.Tools.Excel.Chart.SeriesChange>  
  
## <a name="see-also"></a>Vea también  
 [Tutoriales y ejemplos de desarrollo de office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Extender documentos de Word y libros de Excel en complementos VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Cómo: agregar controles Chart a hojas de cálculo](../vsto/how-to-add-chart-controls-to-worksheets.md)   
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  