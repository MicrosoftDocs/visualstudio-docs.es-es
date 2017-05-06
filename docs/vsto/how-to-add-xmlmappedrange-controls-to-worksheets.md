---
title: "C&#243;mo: Agregar controles XMLMappedRange a hojas de c&#225;lculo"
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
  - "controles [desarrollo de Office en Visual Studio], agregar a hojas de cálculo"
  - "XMLMappedRange (control), agregar a hojas de cálculo"
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# C&#243;mo: Agregar controles XMLMappedRange a hojas de c&#225;lculo
  Cuando se asigna un elemento XML a una celda en Microsoft Office Excel, Visual Studio agrega automáticamente un control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> a la hoja de cálculo.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  El control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> no está disponible en el **Cuadro de herramientas** ni en la ventana **Orígenes de datos**.  Además, no puede crear controles <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> mediante programación.  
  
### Para agregar un control XMLMappedRange a una hoja de cálculo  
  
1.  Abra el libro de Excel en el diseñador de Visual Studio.  
  
2.  Abra la hoja de cálculo a la que desee agregar el control.  
  
3.  En la pestaña **Desarrollador**, haga clic en **Código fuente**.  
  
    > [!NOTE]  
    >  Si la ficha **Desarrollador** no está visible en la cinta de opciones, debe habilitarla.  Para obtener más información, vea [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
     Se abre el panel de tareas **Código fuente XML**.  
  
4.  En el panel de tareas **Código fuente XML**, haga clic en **Asignaciones XML**.  
  
5.  En el cuadro de diálogo **Asignaciones XML**, haga clic en **Agregar**.  
  
     Aparecerá el cuadro de diálogo **Código fuente XML**.  
  
6.  Seleccione un esquema XML en el cuadro de diálogo **Código fuente XML** y haga clic en **Abrir**.  
  
     El esquema se agrega al cuadro de diálogo **Asignaciones XML**.  
  
7.  En el cuadro de diálogo **Asignaciones XML**, haga clic en **Aceptar**.  
  
8.  Arrastre un elemento desde el panel de tareas **Código fuente XML** hacia una celda de la hoja de cálculo.  
  
     Se crea un control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> que se agrega al proyecto.  
  
    > [!NOTE]  
    >  Si arrastra un elemento principal desde el panel de tareas **Código fuente XML**, se crea un control <xref:Microsoft.Office.Tools.Excel.ListObject>.  
  
## Vea también  
 [XmlMappedRange &#40;Control&#41;](../vsto/xmlmappedrange-control.md)   
 [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)   
 [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitaciones de programación de elementos y controles Host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Cómo: Asignar esquemas a hojas de cálculo en Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  