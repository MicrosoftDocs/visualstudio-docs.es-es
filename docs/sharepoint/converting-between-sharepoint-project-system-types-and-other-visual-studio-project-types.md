---
title: "Converting Between SharePoint Project System Types and Other Visual Studio Project Types | Microsoft Docs"
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
  - "SharePoint project service"
ms.assetid: ad5d8ab2-1659-4e6a-8783-47e0dad44b11
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Converting Between SharePoint Project System Types and Other Visual Studio Project Types
  Puede darse el caso en el que tiene un objeto en el sistema de proyectos de SharePoint y desea utilizar características de un objeto correspondiente del modelo de objetos de automatización o del modelo de objetos de integración de Visual Studio, o viceversa.  En estos casos, puede utilizar el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> del servicio de proyecto de SharePoint para convertir el objeto en un modelo de objetos diferente.  
  
 Por ejemplo, podría tener un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>, pero desea utilizar métodos que solo están disponibles en el objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> o <xref:EnvDTE.Project>.  En este caso, puede usar el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> para convertir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> en <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 Para obtener más información sobre el modelo de objetos de automatización y el modelo de objetos de integración de Visual Studio, vea [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## Tipos de conversiones  
 En la tabla siguiente se enumeran los tipos que este método puede convertir del sistema de proyectos de SharePoint en otros modelos de objetos de Visual Studio.  
  
|Tipo de sistema de proyectos de SharePoint|Tipos correspondientes en los modelos de objetos de integración y automatización|  
|------------------------------------------------|--------------------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> o<br /><br /> Cualquier interfaz del modelo de objetos de integración de Visual Studio implementada por el objeto COM subyacente para el proyecto.  Estas interfaces incluyen <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> \(o una interfaz derivada\) y <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.  Para obtener una lista de las interfaces principales implementadas por los proyectos, vea [Componentes principales de modelo de proyecto](../extensibility/internals/project-model-core-components.md).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> o<br /><br /> Un valor <xref:System.UInt32> que identifica el miembro de proyecto \(también denominado VSITEMID\) en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> que lo contiene.  Este valor puede pasarse al parámetro *itemid* de algunos métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>.|  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo se usa el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> para convertir un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> en un objeto <xref:EnvDTE.Project>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#2)]  
  
 Para este ejemplo se necesita:  
  
-   Una extensión del sistema de proyectos de SharePoint que tenga una referencia al ensamblado EnvDTE.dll.  Para obtener más información, vea [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Código que registra el método `projectService_ProjectAdded` para controlar el evento <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  Para obtener un ejemplo, vea [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## Vea también  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [How to: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  