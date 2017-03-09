---
title: "Informaci&#243;n general sobre or&#237;genes de datos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.datasource.datasourcefieldspicker"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "datos [Visual Studio], orígenes de datos"
  - "orígenes de datos"
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
caps.latest.revision: 56
caps.handback.revision: 41
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Informaci&#243;n general sobre or&#237;genes de datos
Los orígenes de datos representan los datos disponibles para la aplicación.  Específicamente, los orígenes de datos representan los datos con los que desea trabajar en su aplicación.  Los orígenes de datos se pueden obtener a partir de bases de datos \(incluidos archivos de base de datos locales\), servicios y objetos.  
  
 Los orígenes de datos que agrega al proyecto se muestran en la ventana **Orígenes de datos**.  En muchos casos, puede arrastrar los orígenes de datos a los diseñadores de Windows Forms, WPF y Silverlight para crear controles que se enlazan a los datos subyacentes.  Para obtener más información, vea [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Visual Studio proporciona herramientas para crear y editar orígenes de datos para su aplicación.  Los orígenes de datos en Visual Studio se representan como Entity Data Models, conjuntos de datos, objetos proxy devueltos por un servicio u otros tipos de objeto, dependiendo de los objetos que devuelva el almacén de datos subyacente.  
  
 Los orígenes de datos se crean y modifican con el **Asistente para la configuración de orígenes de datos**.  
  
## Orígenes de datos creados a partir de bases de datos  
 Puede crear un origen de datos a partir de una base de datos ejecutando el **Asistente para la configuración de orígenes de datos** y seleccionando el tipo de origen de datos en **Base de datos**.  Para obtener más información, vea [Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
 Al crear un origen de datos a partir de una base de datos, Visual Studio genera un *modelo de datos* y lo agrega a su proyecto.  Un modelo de datos es una vista programable, fuertemente tipada, de los datos subyacentes en la base de datos.  Puede utilizar Visual Studio para crear los siguientes tipos de modelos de datos:  
  
-   Un modelo conceptual basado en [Entity Data Model](../Topic/Entity%20Data%20Model.md).  Entity Framework o los servicios de datos de WCF pueden usar este tipo de modelo.  Para obtener más información, vea [Información general de Entity Framework](../Topic/Entity%20Framework%20Overview.md) y [WCF Data Services 4.5](../Topic/WCF%20Data%20Services%204.5.md).  
  
-   DataSet con información de tipos.  Para obtener más información, vea [Trabajar con los conjuntos de datos en Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
-   Clases LINQ to SQL.  Para obtener más información, vea [LINQ a SQL](../Topic/LINQ%20to%20SQL.md).  
  
    > [!NOTE]
    >  A diferencia de los modelos conceptuales y los conjuntos de datos \(datasets\) basados en Entity Data Model, las clases LINQ to SQL no se pueden crear con el **Asistente para la configuración de orígenes de datos**.  Tampoco aparecen en la ventana **Orígenes de datos** y, por consiguiente, no se pueden arrastrar a un diseñador para crear los controles enlazados a datos.  Sin embargo, puede crear un origen de datos de objeto que está basado en clases LINQ to SQL y arrastrar esos objetos al diseñador.  Para obtener más información, vea [Cómo: Crear clases de LINQ to SQL asignadas a tablas y vistas \(Object Relational Designer\)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
### Orígenes de datos creados a partir de archivos de bases de datos locales  
 También puede crear orígenes de datos a partir de los siguientes tipos de archivos: bases de datos de Access \(archivos .mdb\), bases de datos de SQL Server Express LocalDB \(archivos .mdf\) y bases de datos de SQL Server Express \(archivos .mdf\).  Cuando crea orígenes de datos a partir de estos archivos de base de datos, puede agregar directamente los archivos de base de datos a su proyecto.  Para obtener más información, vea los temas siguientes:  
  
-   [Información general de datos locales](../data-tools/local-data-overview.md)  
  
-   [Cómo: Administrar archivos de datos locales en los proyectos](../data-tools/how-to-manage-local-data-files-in-your-project.md)  
  
## Orígenes de datos creados a partir de servicios  
 Puede crear un origen de datos a partir de un servicio ejecutando el **Asistente para la configuración de orígenes de datos** y seleccionando **Servicio** como tipo de origen de datos.  Para obtener más información, vea [Cómo: Conectarse a los datos en un servicio](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
 Al crear un origen de datos a partir de un servicio, Visual Studio agrega una referencia del servicio a su proyecto.  Visual Studio también crea objetos proxy que corresponden a los objetos que son devueltos por el servicio.  Por ejemplo, un servicio que devuelve un conjunto de datos se representa en el proyecto como un conjunto de datos; un servicio que devuelve un tipo u objeto específico se representa como el tipo devuelto.  
  
 Puede crear un origen de datos a partir de los siguientes tipos de servicios:  
  
-   Servicios de datos de WCF  Para obtener más información, vea [Información general](../Topic/WCF%20Data%20Services%20Overview.md).  
  
-   Servicios de Windows Communication Foundation \(WCF\).  Para obtener más información, vea [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md).  
  
-   Servicios Web.  Para obtener más información, vea [Introducción a la programación de servicios web en código administrado](http://msdn.microsoft.com/es-es/bd8861f3-39e1-4c06-995e-677e007eb961).  
  
    > [!NOTE]
    >  Los elementos que aparecen en la ventana **Orígenes de datos** dependen de los datos que devuelve el servicio.  Algunos servicios podrían no proporcionar suficiente información para que el **Asistente para la configuración de orígenes de datos** pueda crear objetos enlazables.  Por ejemplo, si el servicio devuelve un conjunto de datos sin tipo, en la ventana **Orígenes de datos** no aparece ningún elemento cuando el asistente se completa.  Esto se debe a que los conjuntos de datos sin tipo no proporcionan esquemas y, por tanto, el asistente no tiene bastante información para crear el origen de datos.  
  
## Orígenes de datos creados a partir de objetos  
 Puede crear un origen de datos a partir de cualquier objeto que exponga una o más propiedades públicas ejecutando el **Asistente para la configuración de orígenes de datos** y seleccionando el tipo de origen de datos **Objeto** a continuación.  Todas las propiedades públicas de un objeto se muestran en la ventana **Orígenes de datos**.  Para obtener más información, vea [Cómo: Conectarse a los datos en objetos](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md).  
  
 Para obtener más información sobre el enlace a objetos, vea [Enlace de objetos en Visual Studio](../data-tools/bind-objects-in-visual-studio.md).  
  
## Orígenes de datos creados a partir de listas de SharePoint  
 Puede crear un origen de datos a partir de una lista de SharePoint ejecutando el **Asistente para la configuración de orígenes de datos** y seleccionando **SharePoint** como tipo de origen de datos.  SharePoint expone los datos a través de [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], así que crear un origen de datos de SharePoint es como crear un origen de datos de un servicio.  Al seleccionar el elemento **SharePoint** en el **Asistente para la configuración de orígenes de datos**, se abre el cuadro de diálogo **Agregar referencia de servicio** donde se conecta al servicio de datos de SharePoint señalando al servidor de SharePoint.  Para obtener más información, vea [Cómo: Conectarse a los datos en un servicio](../data-tools/how-to-connect-to-data-in-a-service.md).  
  
## Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Crear y editar conjuntos de datos con tipo](../data-tools/creating-and-editing-typed-datasets.md)   
 [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparar la aplicación para recibir datos](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Buscar datos en la aplicación](../data-tools/fetching-data-into-your-application.md)   
 [Enlazar controles a los datos en Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)