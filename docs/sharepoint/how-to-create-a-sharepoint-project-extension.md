---
title: "How to: Create a SharePoint Project Extension"
ms.custom: ""
ms.date: "04/28/2017"
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
ms.assetid: ceecb9cb-4a5d-44c9-992f-9624737ac996
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# How to: Create a SharePoint Project Extension
  Cree una extensión de proyecto cuando desee agregar funcionalidad a un proyecto SharePoint que esté abierto en Visual Studio.  Para obtener más información, vea [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### Para crear una extensión de proyecto  
  
1.  Cree un proyecto de biblioteca de clases  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  
  
4.  Agregue <xref:System.ComponentModel.Composition.ExportAttribute> a la clase.  Este atributo permite que Visual Studio detecte y cargue la implementación de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.  Pase el tipo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> al constructor del atributo.  
  
5.  En la implementación del método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>, use los miembros del parámetro *projectService* para definir el comportamiento de la extensión.  Este parámetro es un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> que proporciona acceso a los eventos definidos en la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>.  
  
## Ejemplo  
 El siguiente ejemplo de código muestra cómo crear una extensión de proyecto simple que controla la mayoría de los eventos de proyecto de SharePoint que define la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents>.  Para probar el código, cree un proyecto de SharePoint en [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] y, a continuación, agregue más proyectos a la solución, cambie los valores de propiedad del proyecto, o elimine o excluya un proyecto.  La extensión notifica los eventos escribiendo los mensajes en el Ventana de **salida** y **Lista de errores**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectextension.cs#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectextension.vb#3)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/savedatatoprojectfile.vb#3)]  
  
 En este ejemplo, se usa el servicio de proyecto de SharePoint para escribir el mensaje en la **Ventana de salida** y en la ventana **Lista de errores**.  Para obtener más información, vea [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Para obtener ejemplos que muestran cómo controlar los eventos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested>, vea [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md) y [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
## Compilar el código  
 Para este ejemplo se requieren referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Implementar la extensión  
 Para implementar la extensión, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado y el resto de archivos que desee distribuir con la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [How to: Add a Shortcut Menu Item to SharePoint Projects](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [Walkthrough: Creating a SharePoint Project Extension](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)  
  
  