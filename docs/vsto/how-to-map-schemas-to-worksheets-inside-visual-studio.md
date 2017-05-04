---
title: "C&#243;mo: Asignar esquemas a hojas de c&#225;lculo en Visual Studio | Microsoft Docs"
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
  - "Excel [desarrollo de Office en Visual Studio], esquemas XML"
  - "asignaciones [desarrollo de Office en Visual Studio], esquemas XML a hojas de cálculo de Excel"
  - "hojas de cálculo [desarrollo de Office en Visual Studio], esquemas XML"
  - "esquemas XML [desarrollo de Office en Visual Studio], asignar"
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# C&#243;mo: Asignar esquemas a hojas de c&#225;lculo en Visual Studio
  Se puede asignar un esquema XML a una hoja de cálculo mientras la hoja de cálculo está abierta en un proyecto de Visual Studio.  Se usan las mismas herramientas de Microsoft Office Excel que se usan cuando el libro está abierto fuera de Visual Studio.  El proyecto de Office crea los mismos objetos independientemente de si asigna el esquema a la hoja de cálculo antes o después de crear la solución de Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  No puede utilizar esquemas XML compuestos en las soluciones de Excel.  
  
### Para asignar un esquema XML a una hoja de cálculo de Excel en Visual Studio  
  
1.  Abra el libro o proyecto de plantilla de Excel en Visual Studio.  
  
2.  Haga clic en la hoja de cálculo para mover el foco al diseñador.  
  
3.  En la cinta de opciones, haga clic en la ficha **Desarrollador**.  
  
    > [!NOTE]  
    >  Si la ficha **Desarrollador** no está visible, debe mostrarla primero.  Para obtener más información, vea [Cómo: Mostrar la pestaña Programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  En el grupo **XML**, haga clic en **Origen**.  
  
     Se abrirá la ventana **Código fuente XML**.  
  
5.  En la ventana **Código fuente XML**, haga clic en **Asignaciones XML**.  
  
     Se abrirá el cuadro de diálogo **Asignaciones XML**.  
  
6.  En el cuadro de diálogo **Asignaciones XML**, haga clic en **Agregar**.  
  
7.  Vaya a su archivo de esquema, selecciónelo y, a continuación, haga clic en **Abrir**.  
  
8.  Haga clic en **Aceptar**.  
  
     El esquema se representa en la ventana **Código fuente XML**.  En el proyecto, se genera una clase <xref:System.Data.DataSet> con tipo basada en el esquema y se crea una clase <xref:System.Windows.Forms.BindingSource>.  
  
9. Arrastre los elementos de la ventana **Código fuente XML** hacia los lugares de su hoja de cálculo donde desea crear los controles correspondientes.  
  
     Si arrastra un elemento no extensible de esquema, el proyecto de Office genera un control <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> que automáticamente se enlace a <xref:System.Windows.Forms.BindingSource>.  
  
     Si arrastra un elemento extensible de esquema, el proyecto de Office genera un control <xref:Microsoft.Office.Tools.Excel.ListObject> que automáticamente no está enlazado a un origen de datos.  Para obtener más información, vea [Esquemas y datos XML en personalizaciones de nivel de documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## Vea también  
 [Cómo: Asignar esquemas a documentos de Word en Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Esquemas y datos XML en personalizaciones de nivel de documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  