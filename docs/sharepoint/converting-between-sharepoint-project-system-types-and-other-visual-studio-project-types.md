---
title: 'Convertir: tipos de sistema de proyectos de SharePoint en otros tipos'
titleSuffix: ''
description: Convertir entre tipos de sistema de proyectos de SharePoint y otros tipos de proyectos de Visual Studio. Vea una lista que detalla los tipos que se pueden convertir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 973c3d4b3c4fa2dc602e45736dc3a2d2f23c7616
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215297"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Convertir entre tipos de sistema de proyectos de SharePoint y otros tipos de proyectos de Visual Studio
  En algunos casos, es posible que tenga un objeto en el sistema de proyectos de SharePoint y desee usar las características de un objeto correspondiente en el modelo de objetos de automatización de Visual Studio o el modelo de objetos de integración, o viceversa. En estos casos, puede utilizar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método del servicio de proyecto de SharePoint para convertir el objeto en un modelo de objetos diferente.

 Por ejemplo, podría tener un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto, pero desea utilizar métodos que solo están disponibles en un <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objeto o. En este caso, puede usar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método para convertir <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> en <xref:EnvDTE.Project> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .

 Para obtener más información sobre el modelo de objetos de automatización de Visual Studio y el modelo de objetos de integración de Visual Studio, vea [información general del modelo de programación de extensiones de herramientas de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Tipos de conversiones
 En la tabla siguiente se enumeran los tipos que este método puede convertir entre el sistema de proyectos de SharePoint y los otros modelos de objetos de Visual Studio.

|Tipo de sistema de proyectos de SharePoint|Tipos correspondientes en los modelos de objetos de integración y automatización|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> or<br /><br /> Cualquier interfaz del modelo de objetos de integración de Visual Studio implementada por el objeto COM subyacente para el proyecto. Estas interfaces incluyen <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (o una interfaz derivada), y <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . Para obtener una lista de las interfaces principales que implementan los proyectos, vea [Project Model Core Components](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> or<br /><br /> Un <xref:System.UInt32> valor (también denominado VSITEMID) que identifica el miembro del proyecto en el <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> que lo contiene. Este valor se puede pasar al parámetro *Itemid* de algunos <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> métodos.|

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo utilizar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método para convertir un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto en <xref:EnvDTE.Project> .

:::code language="csharp" source="../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs" id="Snippet2":::
:::code language="vb" source="../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb" id="Snippet2":::

 Para este ejemplo se necesita:

- Extensión del sistema de proyectos de SharePoint que tiene una referencia al ensamblado de *EnvDTE.dll* . Para obtener más información, vea [Extensión del sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Código que registra el `projectService_ProjectAdded` método para controlar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> evento de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto. Para obtener un ejemplo, vea [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Consulte también

- [Usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Cómo: recuperar el servicio de proyecto de SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Información general del modelo de programación de extensiones de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
