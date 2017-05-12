---
title: "How to: Retrieve the SharePoint Project Service"
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
ms.assetid: 3d8b7adf-2603-4247-9b61-6326a1dd0dec
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# How to: Retrieve the SharePoint Project Service
  Se puede obtener acceso al servicio de proyecto de SharePoint en los siguientes tipos de soluciones:  
  
-   Una extensión del sistema de proyectos de SharePoint, como la extensión de un proyecto, la extensión de un elemento de proyecto o la definición de tipo de un elemento de proyecto.  Para obtener más información sobre estos tipos de extensiones, vea [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Una extensión del nodo **Conexiones de SharePoint** en el **Explorador de servidores**.  Para obtener más información sobre estos tipos de extensiones, vea [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Otro tipo de extensión de Visual Studio, como un complemento o un paquete VSPackage.  
  
## Recuperar el servicio en extensiones del sistema de proyectos  
 En cualquier extensión del sistema de proyectos de SharePoint, puede obtener acceso al servicio del proyecto utilizando la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  
  
 También puede recuperar el servicio del proyecto mediante los procedimientos siguientes.  
  
#### Para recuperar el servicio en una extensión de proyecto  
  
1.  En la implementación de la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>, busque el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A>.  
  
2.  Use el parámetro *projectService* para obtener acceso al servicio.  
  
     En el siguiente ejemplo de código se muestra cómo utilizar el servicio del proyecto para escribir un mensaje en la **Ventana de salida** y en la ventana **Lista de errores** en una extensión de proyecto sencilla.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#1)]  
  
     Para obtener más información sobre la creación de extensiones de proyectos, vea [How to: Create a SharePoint Project Extension](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### Para recuperar el servicio en una extensión de elemento de proyecto  
  
1.  En la implementación de la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>, busque el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>.  
  
2.  Use la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> del parámetro *projectItemType* para recuperar el servicio.  
  
     En el siguiente ejemplo de código se muestra cómo utilizar el servicio del proyecto para escribir un mensaje en la **Ventana de salida** y en la ventana **Lista de errores** en una extensión sencilla del elemento de proyecto **Definición de lista**.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#2)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#2)]  
  
     Para obtener más información sobre la creación de extensiones de elementos de proyectos, vea [How to: Create a SharePoint Project Item Extension](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### Para recuperar el servicio en una definición de tipo de un elemento de proyecto  
  
1.  En la implementación de la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>, busque el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>.  
  
2.  Use la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> del parámetro *typeDefinition* para recuperar el servicio.  
  
     En el siguiente ejemplo de código se muestra cómo utilizar el servicio del proyecto para escribir un mensaje en la **Ventana de salida** y en la ventana **Lista de errores** en una definición de tipo de elemento de proyecto sencilla.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/cs/extension/extension.cs#3)]
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromprojectsystemextensions/vb/extension/extension.vb#3)]  
  
     Para obtener más información sobre la definición de los tipos de elementos de proyectos, vea [How to: Define a SharePoint Project Item Type](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## Recuperar el servicio en extensiones del Explorador de servidores  
 En una extensión del nodo **Conexiones de SharePoint** del **Explorador de servidores**, puede obtener acceso al servicio del proyecto utilizando la propiedad <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> de un objeto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>.  
  
#### Para recuperar el servicio en una extensión del Explorador de servidores  
  
1.  Obtenga un objeto <xref:System.IServiceProvider> de la propiedad <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> de un objeto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> en su extensión.  
  
2.  Para solicitar un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>, utilice el método <xref:System.IServiceProvider.GetService%2A>.  
  
     En el siguiente ejemplo de código se muestra cómo utilizar el servicio del proyecto para escribir un mensaje en la **Ventana de salida** y en la ventana **Lista de errores** de un menú contextual que la extensión agrega para hacer una lista de los nodos en el **Explorador de servidores**.  
  
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/cs/extension/extension.cs#1)]
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromspexplorerextensions/vb/extension/extension.vb#1)]  
  
     Para obtener más información sobre cómo extender el nodo **Conexiones de SharePoint** en el **Explorador de servidores**, vea [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Recuperar el servicio en otras extensiones de Visual Studio  
 Puede recuperar el servicio del proyecto en un paquete VSPackage o en cualquier extensión de Visual Studio con acceso a un objeto <xref:EnvDTE80.DTE2> en el modelo de automatización de objetos, como un complemento o un asistente de plantilla de proyecto que implemente la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>.  
  
 En un VSPackage, puede solicitar un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> utilizando uno de los siguientes métodos:  
  
-   El método <xref:System.IServiceProvider.GetService%2A> de un VSPackage administrado que deriva de la clase <xref:Microsoft.VisualStudio.Shell.Package>.  Para obtener más información, vea [Cómo: obtener un servicio](~/extensibility/how-to-get-a-service.md).  
  
-   El método estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>.  Para obtener más información, vea [Cómo: Usar GetGlobalService](~/misc/how-to-use-getglobalservice.md).  
  
 En una extensión de Visual Studio que tiene acceso a un objeto <xref:EnvDTE80.DTE2>, puede solicitar un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> utilizando el método <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> de un objeto <xref:Microsoft.VisualStudio.Shell.ServiceProvider>.  Para obtener más información, vea [Cómo: Obtener un servicio del objeto DTE](~/misc/how-to-get-a-service-from-the-dte-object.md).  
  
### Ejemplo  
 En el ejemplo de código siguiente se muestra cómo recuperar el servicio del proyecto en un complemento Visual Studio.  Para usar este código, ejecútelo desde la clase `Connect` en un proyecto de complemento.  El objeto `_applicationObject` se genera automáticamente en proyectos de complemento; este objeto es una instancia de la interfaz <xref:EnvDTE80.DTE2>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/cs/connect.cs#1)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectservice.fromdte/vb/connect.vb#1)]  
  
 Para este ejemplo se necesita:  
  
-   Un proyecto de complemento de Visual Studio.  Para obtener más información, vea [Cómo: Crear un complemento](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce).  
  
-   Referencias a los ensamblados Microsoft.VisualStudio.OLE.Interop, Microsoft.VisualStudio.Shell y Microsoft.VisualStudio.SharePoint.  
  
## Vea también  
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Cómo: Crear un complemento](http://msdn.microsoft.com/library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)   
 [Cómo: obtener un servicio](~/extensibility/how-to-get-a-service.md)   
 [Cómo: Obtener un servicio del objeto DTE](~/misc/how-to-get-a-service-from-the-dte-object.md)   
 [Cómo: Utilizar los asistentes con las plantillas de proyectos](~/extensibility/how-to-use-wizards-with-project-templates.md)  
  
  