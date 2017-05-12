---
title: "C&#243;mo: Rellenar documentos con datos de una base de datos"
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
  - "datos, agregar a documentos"
  - "documentos, rellenar con datos"
ms.assetid: 1eb5b13d-7359-407e-8be8-e42c1829f10c
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# C&#243;mo: Rellenar documentos con datos de una base de datos
  Puede acceder a los datos en proyectos de nivel de documento para Microsoft Office de la misma manera que lo hace en proyectos de Windows Forms.  Se usan las mismas herramientas y el mismo código para traer los datos de una base de datos hasta su solución y se pueden usar controles de Windows Forms para mostrar los datos.  
  
 Además, puede mostrar datos mediante controles host.  Los controles host son objetos nativos de Microsoft Office Word que se han mejorado mediante funcionalidad de enlace de eventos y datos.  Para obtener más información, vea [Información general sobre elementos y controles Host](../vsto/host-items-and-host-controls-overview.md).  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 En el siguiente ejemplo se muestra cómo agregar controles enlazados a datos en proyectos de nivel de documento usando un diseñador.  Para ver un ejemplo de cómo agregar controles enlazados a datos en proyectos de complemento de VSTO en tiempo de ejecución, consulte [Tutorial: enlace de datos complejos en un proyecto de complemento de VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.png "vínculo a vídeo") Para ver una demostración en vídeo relacionada, consulte [Enlazar datos a controles de contenido de Word 2007 mediante Visual Studio Tools para el sistema Office \(3.0\)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## Agregar un control a un documento en tiempo de diseño  
  
#### Para rellenar un documento con datos de una base de datos  
  
1.  Abra un proyecto de nivel de documento de Word en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], con el documento abierto en el diseñador.  
  
2.  Abra la ventana **Orígenes de datos** y cree un origen de datos desde una base de datos.  Para obtener más información, consulte [Cómo: Conectarse a los datos de una base de datos](~/data-tools/how-to-connect-to-data-in-a-database.md).  
  
3.  Arrastre el campo que quiera de la ventana **Orígenes de datos** hasta su documento.  
  
 Se agregará un control de contenido al documento.  El tipo del control de contenido depende del tipo de datos del campo que haya seleccionado.  Para obtener más información, vea [Controles de contenido](../vsto/content-controls.md).  
  
 Puede agregar un control diferente seleccionando el campo de datos en la ventana **Orígenes de datos** y, a continuación, eligiendo un control diferente de la lista desplegable.  
  
## Objetos del proyecto  
 Además del control, se agregan automáticamente al proyecto los siguientes objetos relacionados con los datos:  
  
-   Un conjunto de datos con tipo que encapsula las tablas de datos de la base de datos a las que se haya conectado.  Para obtener más información, vea [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) .  
  
-   Un <xref:System.Windows.Forms.BindingSource> que conecta el control al conjunto de datos con tipo.  Para obtener más información, consulte [Información general sobre el componente BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f).  
  
-   Un TableAdapter que conecta el conjunto de datos con tipo a la base de datos.  Para obtener más información, vea [Información general sobre TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
-   Un TableAdapterManager, que se usa para coordinar los adaptadores de tablas del conjunto de datos para habilitar las actualizaciones jerárquicas.  Para obtener más información, consulte [Actualización jerárquica](../data-tools/hierarchical-update.md) e [Información general sobre TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
 Al ejecutar el proyecto, el control muestra el primer registro del origen de datos.  Puede usar el <xref:System.Windows.Forms.BindingSource> para permitir a los usuarios desplazarse por los registros.  
  
#### Para desplazarse por los registros  
  
-   Use métodos <xref:System.Windows.Forms.BindingSource>, como <xref:System.Windows.Forms.BindingSource.MoveNext%2A> y <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>.  
  
 Para obtener información acerca de cómo enviar actualizaciones al conjunto de datos con tipo y a la base de datos, consulte [Cómo: Actualizar un origen de datos con datos de un control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
## Vea también  
 [Enlazar datos a controles en soluciones de Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md)   
 [Enlazar controles de Windows Forms a datos en Visual Studio](../Topic/Binding%20Windows%20Forms%20controls%20to%20data%20in%20Visual%20Studio.md)   
 [Cómo: Rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Cómo: Actualizar un origen de datos con datos de un control Host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Información general sobre el uso de archivos de bases de datos locales en soluciones de Office](../vsto/using-local-database-files-in-office-solutions-overview.md)   
 [Conectar a los datos en aplicaciones de Windows Forms](/visual-studio/data-tools/connecting-to-data-in-windows-forms-applications)   
 [Información general sobre el componente BindingSource](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)  
  
  