---
title: "C&#243;mo: Desplazarse por los registros de una base de datos en una hoja de c&#225;lculo"
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
  - "datos [desarrollo de Office en Visual Studio], desplazarse por los registros de bases de datos"
  - "bases de datos [desarrollo de Office en Visual Studio], desplazarse por registros"
  - "registros [desarrollo de Office en Visual Studio], desplazarse"
  - "hojas de cálculo [desarrollo de Office en Visual Studio], desplazarse por registros"
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# C&#243;mo: Desplazarse por los registros de una base de datos en una hoja de c&#225;lculo
  El procedimiento siguiente explica cómo usar el diseñador para mostrar un campo único de una tabla de base de datos de una hoja de cálculo de Microsoft Office Excel, con controles que permiten al usuario final desplazarse entre todos los registros.  
  
 Solo puede utilizar el diseñador en proyectos en el nivel del documento.  Sin embargo, puede agregar controles y enlazarlos a datos mediante programación en tiempo de ejecución.  Para obtener más información, vea [Tutorial: enlace de datos complejos en un proyecto de complemento de VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### Para desplazarse entre los registros de base de datos en una hoja de cálculo  
  
1.  Abra un proyecto de aplicación de Excel en Visual Studio.  
  
2.  Abra la ventana **Orígenes de datos** y cree un origen de datos a partir de la base de datos.  Para obtener más información, vea [Cómo: Conectarse a los datos de una base de datos](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
3.  Expanda la tabla que contiene los datos que desea mostrar y seleccione la columna concreta.  
  
4.  Abra la lista de controles y seleccione **NamedRange**.  
  
5.  Arrastre el control <xref:Microsoft.Office.Tools.Excel.NamedRange> a la celda donde desea que aparezcan los datos.  
  
6.  En la ficha **Formularios Windows Forms** del **Cuadro de herramientas**, agregue un control <xref:System.Windows.Forms.BindingNavigator> a la hoja de cálculo y configure los controles que desea utilizar.  Para obtener más información, vea [Información general sobre el control BindingNavigator &#40;formularios Windows Forms&#41;](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0).  
  
## Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  