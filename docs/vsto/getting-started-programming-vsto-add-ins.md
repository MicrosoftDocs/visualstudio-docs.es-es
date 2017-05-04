---
title: "Introducci&#243;n a la programaci&#243;n de complementos de VSTO | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectItem.Outlook"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "complementos [desarrollo de Office en Visual Studio], introducción"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], introducción"
ms.assetid: 9ac1e6ea-9511-4633-80f9-dc7641f22b63
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Introducci&#243;n a la programaci&#243;n de complementos de VSTO
  Puede utilizar complementos de VSTO para automatizar las aplicaciones de Microsoft Office, ampliar las características de la aplicación y personalizar la interfaz de usuario de la aplicación.  Para obtener información acerca de los complementos de VSTO en comparación con otros tipos de soluciones de Office que puede crear con Visual Studio, consulte [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## Crear proyectos de complementos de VSTO  
 Para crear proyectos de complementos de VSTO, use una de las plantillas de proyecto de complementos de VSTO del cuadro de diálogo **Nuevo proyecto**.  Estas plantillas incluyen las referencias de ensamblado necesarias y los archivos del proyecto.  Visual Studio proporciona plantillas de proyecto de complementos de VSTO para la mayoría de las aplicaciones de Office.  
  
 Para obtener más información sobre la creación de un proyecto de complemento de VSTO, consulte [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  Para obtener más información sobre las plantillas de proyecto, consulte [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md).  
  
## Desarrollar proyectos de complementos de VSTO  
 Cuando se crea un proyecto de complemento de VSTO, Visual Studio crea automáticamente un archivo de código ThisAddIn.vb \(en [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]\) o ThisAddIn.cs \(en C\#\).  Este archivo contiene la clase `ThisAddIn`, que proporciona la base para el complemento de VSTO.  Puede utilizar los miembros de esta clase para ejecutar código cuando el complemento de VSTO se carga o descarga, para tener acceso al modelo de objetos de la aplicación host y para ampliar las características de la aplicación.  Para obtener más información, vea [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
## Automatizar aplicaciones mediante modelos de objetos  
 Los modelos de objetos de las aplicaciones de Microsoft Office exponen muchos tipos que se pueden programar en un complemento de VSTO.  Puede usar estos tipos para automatizar la aplicación.  Por ejemplo, puede crear y enviar un mensaje de correo electrónico en Outlook o abrir un documento y agregar contenido en Word mediante programación.  Para obtener más información acerca de cómo obtener acceso al modelo de objetos de la aplicación host en el código, consulte [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
 Para obtener más información acerca de los modelos de objetos de aplicaciones de Microsoft Office concretas, vea los temas siguientes:  
  
-   [Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md)  
  
-   [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md)  
  
-   [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)  
  
-   [Soluciones de InfoPath](../vsto/infopath-solutions.md)  
  
-   [Soluciones de PowerPoint](../vsto/powerpoint-solutions.md)  
  
-   [Soluciones de Project](../vsto/project-solutions.md)  
  
-   [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)  
  
## Personalización de la interfaz de usuario de las aplicaciones  
 Hay varias maneras de personalizar la interfaz de usuario de la aplicación host mediante un complemento de VSTO:  
  
-   Para Excel y Word, puede agregar controles administrados a documentos.  Para obtener más información, vea [Extender documentos de Word y libros de Excel en complementos de VSTO en tiempo de ejecución](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
-   Puede personalizar la cinta de opciones si la aplicación lo admite.  Para obtener más información, consulte [Información general sobre la cinta de opciones](../vsto/ribbon-overview.md).  
  
-   Puede crear un panel de tareas personalizado si la aplicación lo admite.  Para obtener más información, vea [Paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
-   Para Outlook, puede crear un área de formulario personalizada.  Para obtener más información, vea [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md).  
  
-   Para todas las aplicaciones de Microsoft Office, puede mostrar Windows Forms en el complemento de VSTO.  
  
 Para obtener más información acerca de la personalización de la IU de las aplicaciones de Microsoft Office, vea [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## Pasos siguientes  
 Para obtener información sobre cómo crear complementos de VSTO, vea los siguientes tutoriales:  
  
-   [Tutorial: Crear el primer complemento de VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
-   [Tutorial: Crear el primer complemento de VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
-   [Tutorial: Crear el primer complemento de VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
-   [Tutorial: Crear el primer complemento de VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
-   [Tutorial: Crear el primer complemento de VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
 Estos tutoriales presentan las herramientas de desarrollo de Office en Visual Studio y el modelo de programación de complementos de VSTO.  
  
 Para obtener una lista de temas que le guiarán a través de algunas de las tareas comunes en proyectos de Office, vea [Tareas comunes en la programación de Office](../vsto/common-tasks-in-office-programming.md).  
  
## Vea también  
 [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Introducción &#40;Desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md)  
  
  