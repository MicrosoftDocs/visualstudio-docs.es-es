---
title: "Soluciones de Outlook"
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
  - "soluciones [desarrollo de Office en Visual Studio], Outlook"
  - "proyectos de Office [desarrollo de Office en Visual Studio], Outlook"
  - "soluciones de Office [desarrollo de Office en Visual Studio], Outlook"
  - "plantillas [desarrollo de Office en Visual Studio], Outlook"
  - "proyectos [desarrollo de Office en Visual Studio], Outlook"
  - "Outlook [desarrollo de Office en Visual Studio]"
  - "correo electrónico [desarrollo de Office en Visual Studio], soluciones de Outlook"
ms.assetid: 2ae3cd9c-bf31-4efa-8b18-b6b1c34a8d93
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Soluciones de Outlook
  Visual Studio proporciona plantillas de proyecto que puede usar para crear complementos de VSTO para Microsoft Office Outlook. Puede usar los complementos de VSTO para automatizar Outlook, ampliar las características de Outlook o personalizar la interfaz de usuario \(UI\) de Outlook. Para obtener más información sobre los complementos de VSTO, consulte [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Crear un proyecto de complemento de VSTO de Outlook  
 Crear proyectos de Outlook mediante la plantilla de proyecto **Complemento de Outlook** en el cuadro de diálogo **Nuevo proyecto**. Estas plantillas incluyen las referencias de ensamblado y los archivos de proyecto necesarios.  
  
 Para obtener más información sobre cómo crear un proyecto de complemento VSTO, vea [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Para obtener más información sobre las plantillas de proyecto, vea [Información general sobre las plantillas de Office Project](../vsto/office-project-templates-overview.md).  
  
## Modelo de programación de complementos de VSTO de Outlook  
 Al crear un proyecto de complemento de VSTO de Outlook, Visual Studio genera una clase, denominada `ThisAddIn`, que es la base de su solución. Esta clase proporciona un punto de partida para escribir el código y expone el modelo de objetos de Outlook en el complemento de VSTO.  
  
 Para obtener más información sobre la clase `ThisAddIn` y otras características que puede usar en un complemento de VSTO, vea [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
## Automatizar Outlook mediante el modelo de objetos de Outlook  
 El modelo de objetos de Outlook expone muchos tipos que puede usar para automatizar Outlook. Estos tipos le permiten escribir código para llevar a cabo tareas comunes:  
  
-   Crear y enviar mensajes de correo electrónico mediante programación.  
  
-   Enviar nuevas convocatorias de reunión.  
  
-   Buscar elementos en las carpetas de Outlook.  
  
 Para obtener más información, consulta [Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md).  
  
## Personalizar la interfaz de usuario de una aplicación de Outlook  
  
|Tarea|Para obtener más información|  
|-----------|----------------------------------|  
|Agregar pestañas personalizadas a la cinta de un Inspector de Outlook.|[Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)|  
|Agregar grupos personalizados a una pestaña integrada en un Inspector de Outlook.|[Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)|  
|Agregar un panel de tareas personalizado que aparezca en un Inspector de Outlook|[Paneles de tareas personalizados](../vsto/custom-task-panes.md).|  
|Agregar un área de formulario que amplíe o sustituya los formularios de Outlook existentes.|[Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Para obtener más información sobre cómo personalizar la interfaz de usuario de Outlook y de otras aplicaciones de Microsoft Office, consulte [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Información general sobre el modelo de objetos de Outlook](../vsto/outlook-object-model-overview.md)|Proporciona información general sobre los objetos que proporciona el modelo de objetos de Outlook.|  
|[Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)|Explica las herramientas que proporciona Visual Studio que facilitan el diseño, el desarrollo y la depuración de las áreas de formulario.|  
|[Tutorial: Crear el primer complemento de VSTO para Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Muestra cómo crear un complemento de VSTO para Microsoft Office Outlook.|  
|[Desarrollo de Outlook 2010 en Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Área de MSDN Library donde podrá encontrar artículos y documentación de referencia sobre el desarrollo de soluciones de Outlook \(no específicos del desarrollo de Office mediante Visual Studio\).|  
  
  