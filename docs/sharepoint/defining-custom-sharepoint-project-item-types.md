---
title: "Defining Custom SharePoint Project Item Types"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: be300c24-fd1b-4fc7-a4e9-a5df1d81d3fc
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Defining Custom SharePoint Project Item Types
  Si desea crear un nuevo tipo de elemento de proyecto de SharePoint, puede definirlo.  Por ejemplo, Visual Studio no incluye elementos de proyecto de SharePoint para agregar campos o acciones a un sitio de SharePoint.  Puede definir sus propios tipos de elementos de proyecto de SharePoint para crear campos, acciones personalizadas u otros tipos de componentes de SharePoint.  
  
## Tareas para definir tipos de elemento de proyecto de SharePoint  
 Para definir un tipo de elemento de proyecto personalizado, compile un ensamblado de extensión de Visual Studio que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  Para obtener más información, vea [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
 Cuando defina un tipo de elemento de proyecto personalizado, también puede agregar la funcionalidad siguiente al elemento de proyecto:  
  
-   Agregue un elemento de menú contextual al elemento de proyecto.  El elemento de menú aparece al abrir el menú contextual para el elemento de proyecto en **Explorador de soluciones** haciendo clic con el botón secundario en el elemento de proyecto o eligiendo y elige las claves de cambio \+ de la F10.  Para obtener más información, vea [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).  
  
-   Agregue una propiedad personalizada al elemento de proyecto.  La propiedad aparece en la ventana **Propiedades** cuando se elige el elemento de proyecto en **Explorador de soluciones**.  Para obtener más información, vea [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 Para permitir que otros desarrolladores usen el elemento de proyecto en Visual Studio, cree un archivo .spdata y una plantilla de elementos o una plantilla de proyecto que esté asociada al elemento de proyecto.  Para obtener más información, vea [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## Entender la relación entre las extensiones tipos de elemento de proyecto y las instancias de elemento de proyecto  
 Al definir un tipo de elemento de proyecto de SharePoint, Visual Studio carga su extensión cuando se agrega un elemento de proyecto del tipo asociado a un proyecto de SharePoint.  Por ejemplo, si define un nuevo tipo de elemento de proyecto **Acción personalizada**, Visual Studio carga su extensión cuando un usuario agrega un elemento de proyecto **Acción personalizada** a un proyecto.  Visual Studio usa la misma instancia de la extensión para todas las instancias del tipo de elemento de proyecto asociado.  En el ejemplo anterior, si el usuario agrega un segundo elemento de proyecto **Acción personalizada** al proyecto, la misma instancia de su extensión se usa para personalizar el segundo elemento de proyecto.  
  
 Para obtener acceso a una instancia concreta del tipo de elemento de proyecto, controle uno de los eventos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> del parámetro *projectItemTypeDefinition* en su implementación del método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  Por ejemplo, para determinar cuándo se agrega un elemento de proyecto del tipo personalizado a un proyecto, controle el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded>.  Para obtener más información, vea [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## Vea también  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Tutorial: Crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Tutorial: crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  