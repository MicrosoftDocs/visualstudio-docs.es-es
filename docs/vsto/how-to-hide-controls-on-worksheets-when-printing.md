---
title: "C&#243;mo: Ocultar controles en hojas de c&#225;lculo al imprimir"
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
  - "controles [desarrollo de Office en Visual Studio], ocultar durante la impresión"
  - "impresión [desarrollo de Office en Visual Studio], ocultar controles"
  - "impresión [desarrollo de Office en Visual Studio], hojas de cálculo"
  - "hojas de cálculo, ocultar controles al imprimir"
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# C&#243;mo: Ocultar controles en hojas de c&#225;lculo al imprimir
  Cuando imprime un documento de Microsoft Office Excel que contiene controles de formularios Windows Forms, los controles son visibles en la hoja de cálculo impresa.  Puede ocultar los controles al imprimir una hoja de cálculo.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Si oculta controles que muestran datos, como <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, los datos del control no serán visibles en la hoja de cálculo impresa.  
  
> [!NOTE]  
>  Es posible que su equipo muestre nombres o ubicaciones diferentes para algunos de los elementos de la interfaz de usuario de Visual Studio en las siguientes instrucciones.  La edición de Visual Studio que tenga y la configuración que esté usando determinan estos elementos.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para ocultar los controles cuando se imprime una hoja de cálculo  
  
1.  Cree o abra un proyecto de Excel en Visual Studio y compruebe que se ve **Sheet1** en el diseñador.  Para obtener información sobre cómo crear proyectos, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  Desde la ficha **Controles comunes** del **Cuadro de herramientas**, arrastre un control <xref:Microsoft.Office.Tools.Excel.Controls.Button> hacia una celda en la `Sheet1`.  
  
3.  En la ventana **Propiedades**, establezca la propiedad <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> en **False**.  
  
## Vea también  
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Información general sobre controles de formularios Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Cómo: Agregar controles de Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Cómo: Cambiar el tamaño de controles en celdas de hojas de cálculo](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  