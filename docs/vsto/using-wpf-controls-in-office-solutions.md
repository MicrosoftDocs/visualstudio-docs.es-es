---
title: "Usar controles de WPF en soluciones de Office"
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
  - "WPF [desarrollo de Office en Visual Studio]"
ms.assetid: 305a212b-0a95-40ad-87aa-22896fe80a04
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Usar controles de WPF en soluciones de Office
  Aunque las soluciones creadas con las herramientas de desarrollo de Visual Studio para Office están diseñadas para funcionar directamente con controles de Windows Forms, también puede usar controles WPF en sus soluciones.  Windows Presentation Foundation \(WPF\) es una alternativa a los formularios Windows Forms para diseñar interfaces de usuario.  WPF utiliza un lenguaje de marcado denominado lenguaje XAML que proporciona nuevas técnicas con el fin de incorporar interfaces de usuario, multimedia y documentos.  Par más información, consulte [Introducción a WPF en Visual Studio de 2015](http://msdn.microsoft.com/library/582a314e-e23d-4144-b45b-acbbd5579252).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Cualquier elemento de la interfaz de usuario que pueda hospedar controles de Windows Forms en una solución de Office también puede hospedar controles WPF.  Entre estos elementos se incluyen los siguientes:  
  
-   Documentos y hojas de cálculo en personalizaciones de nivel de documento.  
  
-   Paneles de acciones en personalizaciones de nivel de documento.  
  
-   Paneles de tareas personalizados en complementos de VSTO.  
  
-   Áreas de formulario en complementos de VSTO para Outlook.  
  
## Agregar controles WPF a proyectos de Office en tiempo de diseño  
 No puede agregar controles WPF directamente a los elementos de la interfaz de usuario en las soluciones de Office.  En su lugar, agregue un elemento **Control de usuario \(WPF\)** al proyecto y utilícelo como superficie de diseño para los controles de WPF.  A continuación, agregue el control de usuario de WPF a un elemento de la interfaz de usuario del proyecto.  
  
#### Para agregar controles de WPF a un panel de acciones, panel de tareas personalizado o área de formulario  
  
1.  Abra un proyecto al que desea agregar un panel de tareas personalizado, un panel de acciones o un área de formulario.  
  
2.  Agregue un elemento **Control de usuario \(WPF\)** al proyecto.  
  
3.  En el **Cuadro de herramientas**, agregue controles de WPF a la superficie de diseño del control de usuario de WPF.  
  
     De forma predeterminada, cuando el diseñador de controles de usuario de WPF está abierto, el **Cuadro de herramientas** solo contiene controles de WPF.  
  
4.  Compile el proyecto.  
  
5.  Agregue un panel de acciones, área de formulario o panel de tareas personalizado al proyecto:  
  
    -   Para las áreas de formulario, agregue un elemento **Área de formulario de Outlook** al proyecto.  Para obtener más información, vea [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
    -   Para los paneles de acciones, agregue un elemento **Control del panel de acciones** o **Control de usuario** al proyecto.  Para obtener más información, consulte[Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)y[Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
    -   Para los paneles de tareas personalizados, agregue un elemento **Control de usuario** al proyecto.  Para obtener más información, consulte [Cómo: Agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
6.  Desde la pestaña *NombreDeProyecto***Controles de usuario de WPF** del **Cuadro de herramientas**, arrastre el control de usuario de WPF hasta el diseñador para el panel de acciones, área del formulario o panel de tareas personalizado.  
  
     Visual Studio crea automáticamente un objeto <xref:System.Windows.Forms.Integration.ElementHost> que hospeda el control de usuario de WPF en el elemento de la interfaz de usuario.  
  
7.  Recompile el proyecto.  
  
#### Para agregar controles de WPF a un documento u hoja de cálculo en un proyecto de nivel de documento  
  
1.  Abra un proyecto de nivel de documento para Word o Excel.  
  
2.  Agregue un elemento **Control de usuario \(WPF\)** al proyecto.  
  
3.  En el **Cuadro de herramientas**, agregue controles de WPF a la superficie de diseño del control de usuario de WPF.  
  
4.  Compile el proyecto.  
  
5.  Agregue un elemento **Control de usuario** \(es decir, un control de usuario de formularios Windows Forms\) al proyecto.  
  
6.  Abra el diseñador para el control de usuario de formularios Windows Forms.  
  
7.  Desde la pestaña *NombreDeProyecto***Controles de usuario de WPF** del **Cuadro de herramientas**, arrastre el control de usuario de WPF hasta el diseñador.  
  
     Visual Studio crea automáticamente un objeto <xref:System.Windows.Forms.Integration.ElementHost> que hospeda el control de usuario de WPF en el control de usuario de formularios Windows Forms.  
  
8.  Escriba código que agregue mediante programación el control de usuario de formularios Windows Forms al documento o libro.  Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
    > [!NOTE]  
    >  No puede arrastrar el control de usuario de formularios Windows Forms hacia el documento o la hoja de cálculo en el diseñador.  
  
9. Recompile el proyecto.  
  
## Hospedar controles de WPF mediante la clase ElementHost  
 Visual Studio proporciona características que le ayudan a usar controles de Windows Forms en las soluciones de Office, pero no proporciona características similares para los controles WPF.  Por ejemplo, puede agregar controles de formularios Windows Forms a los documentos y hojas de cálculo en tiempo de diseño si arrastra los controles desde el **Cuadro de herramientas** o bien en tiempo de ejecución si utiliza métodos auxiliares.  Sin embargo, estas herramientas no están disponibles para los controles de WPF.  
  
 Los controles de WPF utilizan la clase <xref:System.Windows.Forms.Integration.ElementHost> como una capa de la integración entre un control de formularios Windows Forms y los controles de WPF.  Al agregar controles de WPF a la solución en tiempo de diseño, Visual Studio genera automáticamente un objeto <xref:System.Windows.Forms.Integration.ElementHost>.  
  
## Recursos de WPF  
 Para obtener más información sobre los problemas de arquitectura y diseño relacionados con el hospedaje de controles de WPF en controles de formularios y formularios Windows Forms, vea los temas siguientes:  
  
-   [Arquitectura de entrada de interoperabilidad entre formularios Windows Forms y WPF](http://msdn.microsoft.com/library/0eb6f137-f088-4c5e-9e37-f96afd28f235)  
  
-   [Asignación de propiedades en formularios Windows Forms y WPF](http://msdn.microsoft.com/library/999d8298-9c04-467d-a453-86e41002057d)  
  
-   [Interoperabilidad entre Windows Forms y WPF](http://msdn.microsoft.com/library/9e8aa6b6-112c-4579-98d1-c974917df499)  
  
-   [Controles de formularios Windows Forms y controles equivalentes de WPF](http://msdn.microsoft.com/library/8a157e6b-8054-46db-a5cf-a78966acc7a1)  
  
 Para obtener más información sobre cómo agregar controles de WPF a los controles de formularios y formularios Windows Forms en Visual Studio en tiempo de diseño, vea los temas siguientes:  
  
-   [Tutorial: Crear nuevo contenido de WPF en Windows Forms en tiempo de diseño](http://msdn.microsoft.com/library/2e92d8e8-f0e4-4df7-9f07-2acf35cd798c).  
  
-   [Tutorial: Organizar el contenido de WPF en Windows Forms en tiempo de diseño](http://msdn.microsoft.com/library/5efb1c53-1484-43d6-aa8a-f4861b99bb8a).  
  
-   [Tutorial: Aplicar estilos al contenido de WPF](http://msdn.microsoft.com/library/e574aac7-7ea4-4cdb-8034-bab541f000df)  
  
## Vea también  
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Información general sobre controles de formularios Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Paneles de tareas personalizados](../vsto/custom-task-panes.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Cómo: Agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  