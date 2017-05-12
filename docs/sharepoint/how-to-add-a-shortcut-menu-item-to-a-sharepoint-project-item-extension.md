---
title: "How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: d00513a6-d66d-4fbe-9efa-ef3b08c9a73a
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# How to: Add a Shortcut Menu Item to a SharePoint Project Item Extension
  Puede agregar un elemento de menú contextual a un elemento de proyecto de SharePoint existente utilizando una extensión de elemento de proyecto.  El elemento de menú aparece cuando un usuario hace clic con el botón secundario en el elemento de proyecto en el **Explorador de soluciones**.  
  
 En los siguientes pasos se da por supuesto que ha creado una extensión de elemento de proyecto.  Para obtener más información, vea [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
### Para agregar un elemento de menú contextual en una extensión de elemento de proyecto  
  
1.  En el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> de la implementación <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> controle el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> del parámetro *projectItemType*.  
  
2.  En el controlador de eventos del evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested>, agregue un nuevo objeto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> a la colección <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> del parámetro de argumentos del evento.  
  
3.  En el controlador de eventos <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> del nuevo objeto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>, lleve a cabo las tareas que desee ejecutar cuando un usuario haga clic en el elemento de menú contextual.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo crear un elemento de menú contextual para el elemento de proyecto Receptor de eventos.  Cuando el usuario hace clic con el botón secundario en el elemento de proyecto en el **Explorador de soluciones** y, después, hace clic en el elemento de menú **Escribir mensaje en la Ventana de salida**, Visual Studio muestra un mensaje en la **Ventana de salida**.  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemextensionmenu.vb#1)]  
  
 En este ejemplo se usa el servicio de proyecto de SharePoint para escribir el mensaje en la **Ventana de salida**.  Para obtener más información, vea [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilar el código  
 En este ejemplo se necesita un proyecto de biblioteca de clases con referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Implementar la extensión  
 Para implementar la extensión, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado y el resto de archivos que desee distribuir con la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)   
 [How to: Add a Property to a SharePoint Project Item Extension](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  