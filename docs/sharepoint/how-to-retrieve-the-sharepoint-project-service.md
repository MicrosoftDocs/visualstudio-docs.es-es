---
title: 'Cómo: recuperar el servicio de proyecto de SharePoint | Microsoft Docs'
description: Aprenda a acceder al servicio de proyecto de SharePoint en extensiones del sistema de proyectos, extensiones de Explorador de servidores u otras extensiones de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6ae4000bb0ef147a8f601ce80483b9f2ecbe2de8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955234"
---
# <a name="how-to-retrieve-the-sharepoint-project-service"></a>Cómo: recuperar el servicio de proyecto de SharePoint
  Puede tener acceso al servicio de proyecto de SharePoint en los siguientes tipos de soluciones:

- Extensión del sistema de proyectos de SharePoint, como una extensión de proyecto, una extensión de elemento de proyecto o una definición de tipo de elemento de proyecto. Para obtener más información sobre estos tipos de extensiones, vea [extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Una extensión del nodo **conexiones de SharePoint** en **Explorador de servidores**. Para obtener más información sobre estos tipos de extensiones, vea [extender el nodo conexiones de SharePoint en explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

- Otro tipo de extensión de Visual Studio, como un VSPackage.

## <a name="retrieve-the-service-in-project-system-extensions"></a>Recuperar el servicio en las extensiones del sistema del proyecto
 En cualquier extensión del sistema de proyectos de SharePoint, puede tener acceso al servicio de proyecto utilizando la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectService%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto.

 También puede recuperar el servicio de proyecto mediante los procedimientos siguientes.

#### <a name="to-retrieve-the-service-in-a-project-extension"></a>Para recuperar el servicio en una extensión de proyecto

1. En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interfaz, busque el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método.

2. Use el parámetro *projectService* para tener acceso al servicio.

     En el ejemplo de código siguiente se muestra cómo usar el servicio de proyecto para escribir un mensaje en la ventana de **salida** y **lista de errores** ventana en una extensión de proyecto simple.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#1)]

     Para obtener más información sobre la creación de extensiones de proyecto, vea [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-extension"></a>Para recuperar el servicio en una extensión de elemento de proyecto

1. En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interfaz, busque el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método.

2. Use la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType.ProjectService%2A> propiedad del parámetro *projectItemType* para recuperar el servicio.

     En el ejemplo de código siguiente se muestra cómo usar el servicio de proyecto para escribir un mensaje en la ventana de **salida** y **lista de errores** ventana en una extensión simple del elemento de proyecto de **definición de lista** .

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#2)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#2](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#2)]

     Para obtener más información sobre la creación de extensiones de elementos de proyecto, vea [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

#### <a name="to-retrieve-the-service-in-a-project-item-type-definition"></a>Para recuperar el servicio en una definición de tipo de elemento de proyecto

1. En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interfaz, busque el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método.

2. Use la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.ProjectService%2A> propiedad del parámetro *typeDefinition* para recuperar el servicio.

     En el ejemplo de código siguiente se muestra cómo usar el servicio de proyecto para escribir un mensaje en la ventana de **salida** y **lista de errores** ventana en una definición de tipo de elemento de proyecto simple.

     [!code-vb[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.vb#3)]
     [!code-csharp[SPExtensibility.ProjectService.FromProjectSystemExtensions#3](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromprojectsystemextensions.getprojectservice/extension/extension.cs#3)]

     Para obtener más información sobre cómo definir los tipos de elemento de proyecto, vea [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="retrieve-the-service-in-server-explorer-extensions"></a>Recuperar el servicio en extensiones de Explorador de servidores
 En una extensión del nodo **conexiones de SharePoint** en **Explorador de servidores**, puede tener acceso al servicio de proyecto utilizando la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objeto.

#### <a name="to-retrieve-the-service-in-a-server-explorer-extension"></a>Para recuperar el servicio en una extensión de Explorador de servidores

1. Obtiene un <xref:System.IServiceProvider> objeto de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.ServiceProvider%2A> propiedad de un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objeto de la extensión.

2. Use el <xref:System.IServiceProvider.GetService%2A> método para solicitar un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto.

     En el ejemplo de código siguiente se muestra cómo usar el servicio de proyecto para escribir un mensaje en la ventana de **salida** y **lista de errores** ventana desde un menú contextual que la extensión agrega a los nodos de lista de **Explorador de servidores**.

     [!code-vb[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/VisualBasic/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.vb#1)]
     [!code-csharp[SPExtensibility.ProjectService.FromSPExplorerExtensions#1](../sharepoint/codesnippet/CSharp/spextensibility.projectservice.fromspexplorerextensions.getprojectservice/extension/extension.cs#1)]

     Para obtener más información sobre cómo extender el nodo **conexiones de SharePoint** en **Explorador de servidores**, consulte [Cómo: extender un nodo de SharePoint en explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="retrieve-the-service-in-other-visual-studio-extensions"></a>Recuperación del servicio en otras extensiones de Visual Studio
 Puede recuperar el servicio de proyecto en un VSPackage o en cualquier extensión de Visual Studio que tenga acceso a un <xref:EnvDTE80.DTE2> objeto en el modelo de objetos de automatización, como un asistente para plantillas de proyecto que implementa la <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz.

 En un VSPackage, puede solicitar un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto mediante uno de los métodos siguientes:

- <xref:System.IServiceProvider.GetService%2A>Método de un VSPackage administrado que se deriva de la <xref:Microsoft.VisualStudio.Shell.Package> clase. Para obtener más información, consulte [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md).

- Método estático <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> . Para obtener más información, vea [usar GetGlobalService](../extensibility/internals/service-essentials.md#how-to-use-getglobalservice).

  En una extensión de Visual Studio que tiene acceso a un <xref:EnvDTE80.DTE2> objeto, puede solicitar un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto mediante el <xref:Microsoft.VisualStudio.Shell.ServiceProvider.GetService%2A> método de un <xref:Microsoft.VisualStudio.Shell.ServiceProvider> objeto. Para obtener más información, vea [obtener un servicio desde el objeto DTE](../extensibility/how-to-get-a-service.md#getting-a-service-from-the-dte-object).

## <a name="see-also"></a>Vea también
- [Usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Cómo: obtener un servicio](../extensibility/how-to-get-a-service.md)
- [Cómo: usar asistentes con plantillas de proyecto](../extensibility/how-to-use-wizards-with-project-templates.md)
