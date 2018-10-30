---
title: 'Cómo: recuperar el servicio de proyecto de SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e8f9faa0ca539c3b5381aca4159cc4653543087a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880603"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Cómo: recuperar el servicio de proyecto de SharePoint
  Puede acceder al servicio de proyecto de SharePoint en los siguientes tipos de soluciones:  
  
-   Una extensión del sistema del proyecto de SharePoint, como una extensión de proyecto, la extensión de elemento de proyecto o la definición de tipo de elemento de proyecto. Para obtener más información acerca de estos tipos de extensiones, consulte [extender el sistema de proyecto de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Una extensión de la **conexiones de SharePoint** nodo **Explorador de servidores**. Para obtener más información acerca de estos tipos de extensiones, consulte [extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
-   Otro tipo de extensión de Visual Studio, como un paquete VSPackage.  
  
## <a name="retrieve-the-service-in-project-system-extensions"></a>Recuperar el servicio en las extensiones del sistema de proyecto  
 En cualquier extensión del sistema del proyecto de SharePoint, puede tener acceso el servicio del proyecto mediante el uso de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto.  
  
 También puede recuperar el servicio del proyecto mediante el uso de los procedimientos siguientes.  
  
#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Para recuperar el servicio en una extensión de proyecto  
  
1.  En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaz, busque el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método.  
  
2.  Use la *projectService* parámetro para tener acceso al servicio.  
  
     En el ejemplo de código siguiente se muestra cómo usar el servicio del proyecto para escribir un mensaje a la **salida** ventana y **lista de errores** ventana en una extensión de proyecto simple.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]  
  
     Para obtener más información acerca de cómo crear extensiones de proyecto, vea [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Para recuperar el servicio en una extensión de elemento de proyecto  
  
1.  En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaz, busque el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método.  
  
2.  Use la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> propiedad de la *projectItemType* parámetro para recuperar el servicio.  
  
     En el ejemplo de código siguiente se muestra cómo usar el servicio del proyecto para escribir un mensaje a la **salida** ventana y **lista de errores** ventana en una extensión simple de la **dedefinicióndelista** elemento de proyecto.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]  
  
     Para obtener más información acerca de cómo crear extensiones de elemento de proyecto, vea [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).  
  
#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Para recuperar el servicio en una definición de tipo de elemento de proyecto  
  
1.  En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaz, busque el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método.  
  
2.  Use la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> propiedad de la *typeDefinition* parámetro para recuperar el servicio.  
  
     En el ejemplo de código siguiente se muestra cómo usar el servicio del proyecto para escribir un mensaje a la **salida** ventana y **lista de errores** ventana en una definición de tipo de elemento de proyecto simple.  
  
     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]  
  
     Para obtener más información acerca de cómo definir tipos de elemento de proyecto, vea [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).  
  
## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Recuperar el servicio en las extensiones del explorador de servidores  
 En una extensión de la **conexiones de SharePoint** nodo **Explorador de servidores**, solo puede acceder al servicio de proyecto mediante el uso de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objeto.  
  
#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Para recuperar el servicio en una extensión de explorador de servidores  
  
1.  Obtener un <xref:System.IServiceProvider> objeto desde el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objeto en la extensión.  
  
2.  Use la <xref:System.IServiceProvider.GetService%2A> método para solicitar un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto.  
  
     En el ejemplo de código siguiente se muestra cómo usar el servicio del proyecto para escribir un mensaje a la **salida** ventana y **lista de errores** ventana en un menú contextual que la extensión se agrega a los nodos de la lista de **Explorador de servidores**.  
  
     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]  
  
     Para obtener más información sobre cómo extender el **conexiones de SharePoint** nodo **Explorador de servidores**, consulte [Cómo: Extender un nodo de SharePoint en el Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Recuperar el servicio en otras extensiones de Visual Studio  
 Puede recuperar el servicio del proyecto en un VSPackage, o en cualquier extensión de Visual Studio que tiene acceso a un <xref:EnvDTE80.DTE2> objeto en el modelo de objetos de automatización, como un asistente de plantilla de proyecto que implementa el <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz.  
  
 En un VSPackage, puede solicitar un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto utilizando uno de los métodos siguientes:  
  
- El <xref:System.IServiceProvider.GetService%2A> método de un VSPackage administrado que se deriva el <xref:Microsoft.VisualStudio.Shell.Package> clase. Para obtener más información, consulte [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md).  
  
- Estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> método. Para obtener más información, consulte [GetGlobalService Use](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).  
  
  En una extensión de Visual Studio que tiene acceso a un <xref:EnvDTE80.DTE2> objeto, puede solicitar un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto utilizando el <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> método de un <xref:Microsoft.VisualStudio.Shell.ServiceProvider> objeto. Para obtener más información, consulte [obtención de un servicio del objeto DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).  
  
## <a name="see-also"></a>Vea también
 [Usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md)   
 [Cómo: usar asistentes con plantillas de proyecto](../extensibility/how-to-use-wizards-with-project-templates.md)  
  
