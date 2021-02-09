---
title: Usar el servicio de proyecto de SharePoint | Microsoft Docs
description: Use el servicio de proyecto de SharePoint para realizar tareas relacionadas con el sistema del proyecto. Ver una lista de características del servicio de proyecto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5366be3ed60da9225eaf10b19f58ccd77bffbb90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892195"
---
# <a name="use-the-sharepoint-project-service"></a>Usar el servicio de proyecto de SharePoint
  El sistema de proyectos de SharePoint incluye un servicio de proyectos que puede usar para realizar tareas relacionadas con el sistema de proyectos. El servicio de proyectos es un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.

 Puede acceder al servicio de proyectos de SharePoint en cualquier extensión de herramientas de SharePoint. También puede tener acceso a él en otros tipos de extensiones de Visual Studio, como complementos y VSPackages. Para obtener más información, vea [Cómo: recuperar el servicio de proyecto de SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Características del servicio Project
 En la tabla siguiente se enumeran las tareas que puede realizar mediante el servicio de proyectos de SharePoint y el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> o propiedad que desea usar para realizar cada tarea.

|Tarea|Miembro para usar|
|----------|-------------------|
|Acceda a cualquier proyecto de SharePoint que esté abierto en Visual Studio.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|
|Acceda a todos los tipos de elemento de proyecto de SharePoint que están disponibles (incluidos los tipos de elemento de proyecto integrados y personalizados).|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|
|Acceda a todos los pasos de implementación que están disponibles para los proyectos de SharePoint (incluidos los pasos de implementación integrados y personalizados).|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|
|Acceda a los eventos que se producen cuando un desarrollador refactoriza el código en un proyecto de SharePoint.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|
|Ejecute un *comando de SharePoint* personalizado que llame al modelo de objetos de servidor de SharePoint. Para obtener más información sobre los comandos de SharePoint, consulte [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|
|Convierta un tipo del sistema de proyecto de SharePoint en un tipo del modelo de objetos de automatización de Visual Studio o modelo de objetos de integración y viceversa. Para obtener más información, vea [convertir entre tipos de sistema de proyectos de SharePoint y otros tipos de proyectos de Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>.|
|Escriba mensajes en la ventana de **salida** o en **lista de errores** ventana de Visual Studio.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|
|Acceda a otros servicios que están disponibles en Visual Studio.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|
|Recupere la ruta de acceso de la carpeta de instalación del sitio de SharePoint local que se usa para depurar la solución.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|
|Determine si [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] o [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] están instalados en el equipo.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|
|Valide una característica o paquete en una solución de SharePoint.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|

## <a name="see-also"></a>Vea también
- [Convertir entre tipos de sistema de proyectos de SharePoint y otros tipos de proyectos de Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Cómo: recuperar el servicio de proyecto de SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Extensión de las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Información general del modelo de programación de extensiones de SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Cómo: Obtener un servicio del objeto DTE](/previous-versions/bb166401(v=vs.140))