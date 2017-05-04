---
title: "C&#243;mo: Rellenar hojas de c&#225;lculo con datos de una base de datos | Microsoft Docs"
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
  - "datos [desarrollo de Office en Visual Studio], agregar a hojas de cálculo"
  - "bases de datos [desarrollo de Office en Visual Studio], rellenar hojas de cálculo"
  - "hojas de cálculo [desarrollo de Office en Visual Studio], llenar"
ms.assetid: e9e37cf1-53ca-45d0-8409-5428be7f96c5
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# C&#243;mo: Rellenar hojas de c&#225;lculo con datos de una base de datos
  Puede tener acceso a los datos de los proyectos de Office de documento\- nivel de la misma manera que tiene acceso a datos a proyectos de Windows Forms.  Se utilizan las mismas herramientas y el mismo código para colocar datos en la solución, e incluso es posible utilizar controles de Windows Forms para que se muestren los datos.  Además, puede aprovechar los controles denominados controles host, que son objetos nativos de Microsoft Office Excel que se han mejorado con eventos y capacidad de enlace de datos.  Para obtener más información, vea [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 En el ejemplo siguiente se muestra cómo agregar controles enlazados a datos a proyectos en el nivel del documento utilizando un diseñador.  Para obtener un ejemplo que muestra cómo agregar controles enlazados a datos a proyectos de nivel de aplicación en tiempo de ejecución, vea [Tutorial: enlace de datos complejos en el proyecto de complemento de VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Dispone de una demostración en vídeo relacionada en [How Do I: Transfer Data Into an Excel Worksheet?](http://go.microsoft.com/fwlink/?LinkID=130277) y [How Do I: Consume Database Data in Excel?](http://go.microsoft.com/fwlink/?LinkID=130287).  
  
## Agregar un control enlazado a datos a una hoja de cálculo en tiempo de diseño  
  
#### Para rellenar una hoja de cálculo con datos de una base de datos  
  
1.  Abra un proyecto de nivel de documento de Excel en Visual Studio, con la hoja de cálculo abierta en el diseñador.  
  
2.  Abra la ventana **Orígenes de datos** y cree un origen de datos para el proyecto.  Para obtener más información, vea [Cómo: Conectarse a los datos de una base de datos](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
3.  Arrastre el campo o la tabla que desee desde la ventana **Orígenes de datos** a la hoja de cálculo.  
  
 En la hoja de cálculo se creará uno de los controles siguientes:  
  
-   Si arrastra un campo, se crea un control <xref:Microsoft.Office.Tools.Excel.NamedRange> en la hoja de cálculo.  Para obtener más información, vea [NamedRange &#40;Control&#41;](../vsto/namedrange-control.md).  
  
-   Si arrastra una tabla, se crea un control <xref:Microsoft.Office.Tools.Excel.ListObject> en la hoja de cálculo.  Para obtener más información, vea [ListObject &#40;Control&#41;](../vsto/listobject-control.md).  
  
 Puede agregar un control diferente si selecciona la tabla o el campo en la ventana **Orígenes de datos** y después elige un control diferente en la lista desplegable.  
  
## Objetos del proyecto  
 Además del control, los siguientes objetos relacionados con datos se agregan automáticamente al proyecto:  
  
-   Un conjunto de datos con tipo que encapsula las tablas de datos que haya conectado con la base de datos.  Para obtener más información, vea [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   Un objeto <xref:System.Windows.Forms.BindingSource> que conecta el control con el conjunto de datos con tipo.  Para obtener más información, vea [Información general sobre el componente BindingSource](../Topic/BindingSource%20Component%20Overview.md).  
  
-   Un objeto TableAdapter que conecta el conjunto de datos con tipo a la base de datos.  Para obtener más información, vea [Información general sobre TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
-   Un objeto TableAdapterManager, que se utiliza para coordinar los adaptadores de la tabla del conjunto de datos para habilitar las actualizaciones jerárquicas.  Para obtener más información, vea [Actualización jerárquica](../data-tools/hierarchical-update.md) y [Información general sobre TableAdapterManager](../Topic/TableAdapterManager%20Overview.md).  
  
 Cuando se ejecuta el proyecto, el control muestra el primer registro del origen de datos.  Puede utilizar <xref:System.Windows.Forms.BindingSource> para permitirles a los usuarios desplazarse por los registros.  
  
#### Para desplazarse por los registros  
  
-   Use métodos <xref:System.Windows.Forms.BindingSource> como <xref:System.Windows.Forms.BindingSource.MoveNext%2A> y <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Para obtener información sobre cómo enviar actualizaciones al conjunto de datos con tipo y a la base de datos, vea [Cómo: Actualizar un origen de datos con datos de un control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Cómo: Rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Cómo: Rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Cómo: Rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md)   
 [Cómo: Actualizar un origen de datos con datos de un control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Cómo se hago: Transferir los datos Into una hoja de cálculo de Excel](http://go.microsoft.com/fwlink/?LinkID=130277)   
 [Cómo se hago: ¿Utiliza los datos de la base de datos en Excel?](http://go.microsoft.com/fwlink/?LinkID=130287)  
  
  