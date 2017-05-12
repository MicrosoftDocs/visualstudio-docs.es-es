---
title: "Extending SharePoint Projects"
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
  - "projects [SharePoint development in Visual Studio], extending"
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint projects, extending"
ms.assetid: 4643012b-6e6c-4b7c-bb92-b04b34f6c715
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Extending SharePoint Projects
  Cree una extensión de proyecto cuando desee personalizar características de nivel de proyecto de SharePoint.  Por ejemplo, puede agregar propiedades de proyecto personalizadas o responder a los eventos de nivel de proyecto que se generan cuando el usuario desarrolla una solución de SharePoint en Visual Studio.  
  
## Crear extensiones de proyecto  
 Para extender un elemento de proyecto, compile un ensamblado de extensión de Visual Studio que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Para obtener más información, vea [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
 Cuando se crea una extensión de proyecto, también se puede agregar la siguiente funcionalidad a los proyectos de SharePoint:  
  
-   Un elemento de menú contextual.  El elemento de menú aparece al abrir el menú contextual para un nodo de proyecto de SharePoint en **Explorador de soluciones** haciendo clic con el botón secundario en el nodo o eligiendo y elige las claves de cambio \+ de la F10.  Para obtener más información, vea [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).  
  
-   Una propiedad personalizada.  La propiedad aparece en la ventana **Propiedades** al elegir un proyecto de SharePoint en **Explorador de soluciones**.  Para obtener más información, vea [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 Encontrará un tutorial que describe cómo crear, implementar y probar una extensión de proyecto en [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).  
  
## Introducción a la relación entre las extensiones de proyecto y las instancias de proyecto  
 Cuando se crea una extensión de proyecto, la extensión se carga cuando se abre cualquier tipo de proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] incluye varias plantillas de proyecto de SharePoint, como definiciones de lista, tipos de contenido y receptores de eventos.  Sin embargo, solo hay un tipo de proyecto de SharePoint.  Los tipos de proyecto que aparecen en el cuadro de diálogo **Nuevo proyecto** solo son plantillas que empaquetan uno o más elementos de proyecto de SharePoint.  Dado que solo hay un tipo de proyecto de SharePoint, las extensiones creadas para un proyecto se aplican a todos los proyectos de SharePoint.  Por ejemplo, no puede crear una extensión que se aplique solo a un proyecto de **tipo de contenido**.  
  
 Para obtener acceso a una instancia de proyecto concreta, controle uno de los eventos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> del parámetro *projectService* en su implementación del método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>.  Por ejemplo, para determinar cuándo se agrega un proyecto de SharePoint a una solución, controle el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded>.  Para obtener más información, vea [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## Vea también  
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)  
  
  