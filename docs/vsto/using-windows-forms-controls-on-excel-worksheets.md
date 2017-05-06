---
title: "Usar controles de formularios Windows Forms en hojas de c&#225;lculo de Excel"
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
  - "controles [desarrollo de Office en Visual Studio], controles de formularios Windows Forms"
  - "Excel [desarrollo de Office en Visual Studio], controles de Windows Forms"
  - "controles de formularios Windows Forms [desarrollo de Office en Visual Studio], Excel"
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Usar controles de formularios Windows Forms en hojas de c&#225;lculo de Excel
  Se pueden agregar controles de formularios Windows Forms a los libros de Microsoft Office Excel del mismo modo que se agregan a formularios Windows Forms.  Para obtener información general sobre cómo trabajar con los controles en los documentos, vea [Información general sobre controles de formularios Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Consideraciones sobre controles para Excel  
 Existen algunas consideraciones específicas de Excel.  
  
### Hacer coincidir el tamaño del control con el tamaño de la celda  
 Puede establecer que el control se cambie de tamaño automáticamente cuando se cambie el tamaño de la celda primaria.  Para obtener más información, vea [Cómo: Cambiar el tamaño de controles en celdas de hojas de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md).  
  
### Agregar componentes compartidos por todas las hojas de cálculo  
 Para agregar componentes que desee compartir entre todas las hojas de cálculo, como <xref:System.Data.DataSet>, puede agregarlos al diseñador del libro en lugar de a las hojas de cálculo.  El componente aparecerá en la bandeja de componentes.  
  
### Fórmula para incrustar controles  
 Cuando seleccione un control en Excel, verá **\=EMBED\("WinForms.Control.Host",""\)** en la **Barra de fórmulas**.  Este texto es necesario y no debe eliminarse.  
  
## Vea también  
 [Cómo: Cambiar el tamaño de controles en celdas de hojas de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [Cómo: Ocultar controles en hojas de cálculo al imprimir](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [Tutorial: Cambiar el formato de una hoja de cálculo utilizando controles CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [Tutorial: Mostrar texto en un cuadro de texto en una hoja de cálculo utilizando un botón](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [Tutorial: Actualizar un gráfico en una hoja de cálculo utilizando botones de radio](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  