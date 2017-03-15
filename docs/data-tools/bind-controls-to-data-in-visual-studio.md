---
title: "Enlazar controles a los datos en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "Orígenes de datos (ventana)"
  - "orígenes de datos, mostrar datos"
  - "datos, mostrar"
  - "mostrar datos"
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 40
caps.handback.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Enlazar controles a los datos en Visual Studio
Para mostrar los datos a los usuarios de la aplicación, puede enlazarlos a controles.  Puede crear estos controles enlazados a datos arrastrando los elementos de la ventana **Orígenes de datos** a una superficie de diseño en Visual Studio.  
  
 En este tema se describen los orígenes de datos que puede utilizar para crear controles enlazados a datos.  También se describen algunas de las tareas generales implicadas en el enlace de datos.  Para obtener detalles concretos sobre cómo crear controles enlazados a datos, vea [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md), [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) y [Enlazar controles de Silverlight a datos en Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md).  
  
## Orígenes de datos  
 Un origen de datos representa los datos que está disponibles para la aplicación.  Puede crear orígenes de datos a partir de bases de datos, servicios u objetos.  Para obtener más información, vea [Información general sobre orígenes de datos](../data-tools/add-new-data-sources.md).  
  
 Algunos orígenes de datos permiten crear controles enlazados a datos arrastrando los elementos de la ventana **Orígenes de datos**, mientras que otros no lo permiten.  En la tabla siguiente se muestran los orígenes de datos que se admiten.  
  
|Origen de datos|Compatibilidad con arrastrar y colocar en el **Diseñador de Windows Forms**|Compatibilidad con arrastrar y colocar en **WPF Designer**|Compatibilidad con arrastrar y colocar en el **Diseñador de Silverlight**|  
|---------------------|---------------------------------------------------------------------------------|----------------------------------------------------------------|-------------------------------------------------------------------------------|  
|Conjunto de datos|Sí|Sí|No|  
|Entity Data Model|No<sup>1</sup>|Sí|Sí|  
|Clases LINQ to SQL|No<sup>2</sup>|No<sup>2</sup>|No<sup>2</sup>|  
|Servicios como [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], servicios WCF y servicios Web|Sí|Sí|Sí|  
|Objeto|Sí|Sí|Sí|  
|SharePoint|Sí|Sí|Sí|  
  
 1.  Cuando el Diseñador de Windows Forms está abierto, las entidades de la ventana **Orígenes de datos** son de solo lectura y no se pueden arrastrar al diseñador.  Sin embargo, todavía puede crear los controles enlazados a datos agregando un nuevo origen de datos de objeto basado en el Entity Data Model y arrastrando, a continuación, esos objetos hasta el diseñador.  
  
 2.  Las clases LINQ to SQL no aparecen en la ventana **Orígenes de datos**.  Sin embargo, puede agregar un nuevo origen de datos de objeto basado en clases LINQ to SQL y, a continuación, arrastrar esos objetos al diseñador para crear los controles enlazados a datos.  Para obtener más información, vea [Tutorial: Crear clases de LINQ to SQL \(Object Relational Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md).  
  
## Orígenes de datos \(Ventana\)  
 Los orígenes de datos están disponible para su proyecto como elementos en la ventana **Orígenes de datos**.  Puede arrastrar los elementos desde esta ventana para crear controles enlazados a los datos subyacentes.  Para obtener más información, vea [Orígenes de datos \(ventana\)](../Topic/Data%20Sources%20Window.md).  
  
 Por cada tipo de datos que aparece en la ventana **Orígenes de datos**, se crea un control predeterminado al arrastrar el elemento hasta el diseñador.  Antes de arrastrar un elemento de la ventana **Orígenes de datos**, puede cambiar el control que se creará.  Para obtener más información, vea [Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## Tareas necesarias para enlazar controles a datos  
 En la siguiente tabla se incluyen algunas de las más tareas comunes para enlazar controles a datos.  
  
|Tarea|Más información|  
|-----------|---------------------|  
|Abrir la ventana **Orígenes de datos**|[Cómo: Abrir la ventana Orígenes de datos](../data-tools/how-to-open-the-data-sources-window.md)|  
|Agregar un origen de datos al proyecto.|[Cómo: Conectarse a los datos de una base de datos](../data-tools/how-to-connect-to-data-in-a-database.md)<br /><br /> [Cómo: Conectarse a los datos en objetos](../Topic/How%20to:%20Connect%20to%20Data%20in%20Objects.md)<br /><br /> [Cómo: Conectarse a los datos en un servicio](../data-tools/how-to-connect-to-data-in-a-service.md)|  
|Establecer el control que se crea cuando se arrastra un elemento de la ventana **Orígenes de datos** al diseñador.|[Establecer el control que se creará al arrastrar desde la ventana Orígenes de datos](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|  
|Modifique la lista de controles que están asociados a elementos en la ventana **Orígenes de datos**.|[Agregar controles personalizados a la ventana de orígenes de datos](../data-tools/add-custom-controls-to-the-data-sources-window.md)|  
|Crear controles enlazados a datos.|[Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)<br /><br /> [Enlazar controles de Silverlight a datos en Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)|  
  
 Es posible que después de crear controles enlazados a datos, desee hacer una de las tareas siguientes.  
  
|Tarea|Para obtener más información|  
|-----------|----------------------------------|  
|Editar los datos en el origen de datos subyacente|[Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)|  
|Validar los cambios realizados en los datos|[Validar datos](../Topic/Validating%20Data.md)|  
|Guardar los datos actualizados en la base de datos|[Guardar datos](../data-tools/saving-data.md)|  
  
## Vea también  
 [Enlazar controles de Windows Forms a datos en Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Enlazar controles WPF a datos en Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Enlazar controles de Silverlight a datos en Visual Studio](../Topic/Binding%20Silverlight%20Controls%20to%20Data%20in%20Visual%20Studio.md)   
 [Cómo: Enlazar controles a imágenes desde una base de datos](../data-tools/bind-controls-to-pictures-from-a-database.md)   
 [Información general de las aplicaciones de datos en Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Conectarse a datos en Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Modificar datos en la aplicación](../data-tools/editing-data-in-your-application.md)   
 [Validar datos](../Topic/Validating%20Data.md)   
 [Guardar datos](../data-tools/saving-data.md)   
 [Herramientas para trabajar con orígenes de datos en Visual Studio](../Topic/Tools%20for%20Working%20with%20Data%20Sources%20in%20Visual%20Studio.md)