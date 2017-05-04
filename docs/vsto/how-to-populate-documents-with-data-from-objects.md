---
title: "C&#243;mo: Rellenar documentos con datos de objetos | Microsoft Docs"
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
  - "documentos [desarrollo de Office en Visual Studio], rellenar con datos"
  - "datos [desarrollo de Office en Visual Studio], agregar a documentos"
ms.assetid: 83e6ebac-e468-4bef-a91c-78c7bf597a75
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# C&#243;mo: Rellenar documentos con datos de objetos
  El acceso a los datos de un objeto de datos funciona de la misma manera en los proyectos de nivel de documento de Microsoft Office Word que en los proyectos de Windows Forms. Se usan las mismas herramientas y el mismo código para colocar datos de un objeto en la solución y se pueden usar controles de Windows Forms para mostrar los datos. Además, puede mostrar datos mediante controles host. Los controles host son objetos nativos de Microsoft Office Word que se han mejorado mediante funcionalidad de enlace de eventos y datos. Para obtener más información, consulta [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
 Para rellenar el documento con datos de un objeto, es necesario completar tres pasos básicos:  
  
-   Agregar un control al documento que se puede enlazar a datos.  
  
-   Agregar un objeto de datos al documento.  
  
-   Conectar el objeto de datos a BindingSource.  
  
## Agregar un objeto de datos  
  
#### Para agregar un objeto de datos  
  
-   Abra la ventana **Orígenes de datos** y cree un origen de datos a partir de un objeto. Para obtener más información, consulta [Cómo: Conectarse a los datos en objetos](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
## Conectar el objeto de datos a BindingSource  
 En los proyectos de nivel de documento, se agregan controles al documento y se enlazan a datos en tiempo de diseño.  
  
 En proyectos de complemento de VSTO, se crean controles y se enlazan en tiempo de ejecución.  
  
### Proyectos de nivel del documento  
  
##### Para conectar el objeto de datos a BindingSource  
  
1.  Arrastre el campo de datos que quiera desde la ventana **Orígenes de datos** al documento. Así se crea un control automáticamente.  
  
2.  En el código, cree una instancia del tipo del objeto que eligió para el origen de datos.  
  
3.  Asigne la instancia a la propiedad <xref:System.Windows.Forms.BindingSource.DataSource%2A> de la clase <xref:System.Windows.Forms.BindingSource>.  
  
### Proyectos de nivel de la aplicación  
  
##### Para conectar el objeto de datos a BindingSource  
  
1.  En el código, cree una instancia del tipo del objeto que está asociado con el origen de datos.  
  
2.  Cree una instancia de <xref:System.Windows.Forms.BindingSource>.  
  
3.  Asigne la instancia del origen de datos a la propiedad <xref:System.Windows.Forms.BindingSource.DataSource%2A> de la clase <xref:System.Windows.Forms.BindingSource>.  
  
4.  Agregue el origen de datos como un enlace de datos al control.  
  
## Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Cómo: Rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Cómo: Actualizar un origen de datos con datos de un control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Conectar a los datos en aplicaciones de Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Información general sobre el componente BindingSource](../Topic/BindingSource%20Component%20Overview.md)  
  
  