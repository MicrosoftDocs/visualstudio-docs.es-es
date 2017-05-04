---
title: "How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type | Microsoft Docs"
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
ms.assetid: f6ec47a7-e7d9-4e26-810b-77943a1ab04c
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type
  Al definir un tipo de elemento del proyecto de SharePoint personalizado, puede agregar un elemento de menú contextual al elemento de proyecto.  El elemento de menú aparece cuando un usuario hace clic con el botón secundario en el elemento de proyecto en el **Explorador de soluciones**.  
  
 En los siguientes pasos se supone que ha definido un tipo de elemento de proyecto de SharePoint.  Para obtener más información, vea [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
### Para agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado  
  
1.  En el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> de la implementación de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> controle el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> del parámetro *projectItemTypeDefinition*.  
  
2.  En el controlador de eventos del evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>, agregue un nuevo objeto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> a la colección <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> del parámetro de argumentos del evento.  
  
3.  En el controlador de eventos <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> para el nuevo objeto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> , realice las tareas que desee ejecutar cuando el usuario elige el elemento de menú contextual.  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra cómo agregar un elemento de menú contextual a un tipo de elemento de proyecto personalizado.  Cuando el usuario abre el menú contextual del elemento de proyecto en **Explorador de soluciones** y elija el elemento de menú **Mensaje de escritura a la ventana de resultados** , Visual Studio muestra un mensaje en la ventana **Resultados** .  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypemenu.vb#4)]  
  
 En este ejemplo se usa el servicio de proyecto de SharePoint para escribir el mensaje en la **Ventana de salida**.  Para obtener más información, vea [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilar el código  
 En este ejemplo se necesita un proyecto de biblioteca de clases con referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Implementar el elemento de proyecto  
 Para permitir que otros desarrolladores usen el elemento de proyecto, cree una plantilla de proyecto o una plantilla de elemento de proyecto.  Para obtener más información, vea [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Para implementar el elemento de proyecto, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado, la plantilla y cualquier otro archivo que desee distribuir con el elemento de proyecto.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)  
  
  