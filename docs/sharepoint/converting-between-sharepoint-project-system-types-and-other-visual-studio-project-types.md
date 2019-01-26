---
title: Conversión entre tipos de sistema de proyecto de SharePoint y otros tipos de proyecto de Visual Studio | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aec5557b2837317bfd634035875628ef0e68220c
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863362"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Convertir entre tipos de sistema de proyectos de SharePoint y otros tipos de proyecto de Visual Studio
  En algunos casos podría tener un objeto en el sistema del proyecto de SharePoint y desea usar las características de un objeto correspondiente en el modelo de objetos de automatización de Visual Studio o el modelo de objetos de integración, o viceversa. En estos casos, puede usar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método del servicio del proyecto de SharePoint para convertir el objeto en un modelo de objetos diferentes.

 Por ejemplo, podría tener un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto, pero desea usar métodos que solo están disponibles en un <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objeto. En este caso, puede usar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método para convertir el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> a un <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.

 Para obtener más información sobre el modelo de objetos de automatización de Visual Studio y el modelo de objetos de integración de Visual Studio, consulte [información general del modelo de programación de SharePoint de extensiones](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Tipos de conversiones
 En la tabla siguiente se enumera los tipos que este método se puede convertir entre el sistema del proyecto de SharePoint y los otros modelos de objetos de Visual Studio.

|Tipo de sistema de proyecto de SharePoint|Tipos correspondientes en los modelos de objetos de automatización e integración|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> o<br /><br /> Cualquier interfaz en el modelo de objetos de integración de Visual Studio que se implementa mediante el objeto COM subyacente para el proyecto. Estas interfaces incluyen <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (o una interfaz derivada), y <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. Para obtener una lista de las interfaces principales que se implementan los proyectos, vea [componentes principales del proyecto de modelo](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> o<br /><br /> Un<xref:System.UInt32> valor (también denominado VSITEMID) que identifica el miembro del proyecto en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> que lo contiene. Este valor puede pasarse a la *itemid* parámetro de algunas <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> métodos.|

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo usar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método para convertir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto a un <xref:EnvDTE.Project>.

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 Para este ejemplo se necesita:

-   Una extensión del sistema del proyecto de SharePoint que tiene una referencia a la *EnvDTE.dll* ensamblado. Para obtener más información, consulte [extender el sistema de proyecto de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

-   Código que registra el `projectService_ProjectAdded` método para controlar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> eventos de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto. Como ejemplo, vea [Cómo: Crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Vea también

- [Usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Cómo: Recuperar el servicio de proyecto de SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Información general del modelo de programación de SharePoint de extensiones](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
