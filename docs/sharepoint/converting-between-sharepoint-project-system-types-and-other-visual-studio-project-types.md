---
title: Conversión entre tipos de sistema de proyecto de SharePoint y otros tipos de proyecto de Visual Studio | Documentos de Microsoft
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
ms.openlocfilehash: 6cf039f3d5330b2f4869ae323ac358a1220c2fbf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Convertir los tipos de sistema de proyectos de SharePoint en otros tipos de proyecto de Visual Studio
  En algunos casos podría tener un objeto en el sistema de proyectos de SharePoint y desea utilizar las características de un objeto correspondiente en el modelo de objetos de automatización de Visual Studio o el modelo de objetos de integración, o viceversa. En estos casos, puede usar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método del servicio de proyecto de SharePoint para convertir el objeto en un modelo de objetos diferentes.  
  
 Por ejemplo, podría tener un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto, pero desea utilizar métodos que solo están disponibles en un <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objeto. En este caso, puede usar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método para convertir el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> a una <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.  
  
 Para obtener más información sobre el modelo de objetos de automatización de Visual Studio y el modelo de objetos de integración de Visual Studio, vea [información general de la programación de modelo de herramientas de extensiones de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="types-of-conversions"></a>Conversiones de tipos de  
 En la tabla siguiente se enumera los tipos que este método puede convertir entre el sistema de proyectos de SharePoint y los modelos de objetos de Visual Studio.  
  
|Tipo de sistema de proyecto de SharePoint|Tipos correspondientes en los modelos de objetos de integración y automatización|  
|------------------------------------|-------------------------------------------------------------------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> o<br /><br /> Cualquier interfaz en el modelo de objetos de integración de Visual Studio que se implementa mediante el objeto COM subyacente para el proyecto. Estas interfaces incluyen <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (o una interfaz derivada), y <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. Para obtener una lista de las interfaces principales que se implementan proyectos, vea [componentes principales del proyecto de modelo](/visualstudio/extensibility/internals/project-model-core-components).|  
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> o<br /><br /> A<xref:System.UInt32> valor (también denominada VSITEMID) que identifica el miembro de proyecto en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> que lo contiene. Este valor puede pasarse a la *itemid* parámetro de algunas <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> métodos.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo utilizar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método para convertir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> el objeto a un <xref:EnvDTE.Project>.  
  
 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]  
  
 Para este ejemplo se necesita:  
  
-   Una extensión del sistema del proyecto de SharePoint que tiene una referencia al ensamblado EnvDTE.dll. Para obtener más información, consulte [extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
-   Código que registra el `projectService_ProjectAdded` método para controlar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> eventos de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto. Para obtener un ejemplo, vea [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md)   
 [Cómo: recuperar el servicio de proyecto de SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Información general del modelo de programación de extensiones de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  