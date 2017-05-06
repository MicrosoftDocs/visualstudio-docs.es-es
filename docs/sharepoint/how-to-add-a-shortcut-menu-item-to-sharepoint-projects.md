---
title: "How to: Add a Shortcut Menu Item to SharePoint Projects"
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
ms.assetid: bb251fe9-f1bf-4ddd-9359-4b7f78fbd50f
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# How to: Add a Shortcut Menu Item to SharePoint Projects
  Puede agregar un elemento de menú contextual a un proyecto de SharePoint.  El elemento de menú aparece cuando un usuario hace clic con el botón secundario en un nodo de proyecto del **Explorador de soluciones**.  
  
 En los siguientes pasos se presupone que ya ha creado una extensión de proyecto.  Para obtener más información, vea [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
### Para agregar un elemento de menú contextual a los proyectos de SharePoint  
  
1.  En el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> de la implementación de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> controle el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> del parámetro *projectService*.  
  
2.  En el controlador de eventos del evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested>, agregue un nuevo objeto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> a la colección <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.AddMenuItems%2A> o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectMenuItemsRequestedEventArgs.ActionMenuItems%2A> del parámetro de argumentos del evento.  
  
3.  En el controlador de eventos <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> del nuevo objeto <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>, lleve a cabo las tareas que desee ejecutar cuando un usuario haga clic en el elemento de menú contextual.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo se agrega un elemento de menú contextual a los nodos de proyecto de SharePoint en el **Explorador de soluciones**.  Cuando el usuario hace clic con el botón secundario en un nodo de proyecto y hace clic en el elemento de menú **Escribir mensaje en la Ventana de salida**, Visual Studio muestra un mensaje en la **Ventana de salida**.  En este ejemplo se usa el servicio de proyecto de SharePoint para mostrar el mensaje.  Para obtener más información, vea [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.Menu#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/cs/extension/projectitemextensionmenu.cs#1)]
 [!code-vb[SPExtensibility.ProjectExtension.Menu#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.menu/vb/extension/projectitemextensionmenu.vb#1)]  
  
## Compilar el código  
 En este ejemplo se necesita un proyecto de biblioteca de clases con referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Implementar la extensión  
 Para implementar la extensión, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado y el resto de archivos que desee distribuir con la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)  
  
  