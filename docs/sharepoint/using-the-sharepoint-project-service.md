---
title: Using the SharePoint Project Service | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
ms.assetid: bfb6cbc7-6c28-4e1a-abb4-88f149e7712c
caps.latest.revision: "34"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6bf5ac3acb0b0693c6c53de6705fee105f7f3404
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-sharepoint-project-service"></a>Utilizar el servicio de proyecto de SharePoint
  El sistema de proyectos de SharePoint incluye un servicio de proyectos que puede usar para realizar tareas relacionadas con el sistema de proyectos. El servicio de proyectos es un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService>.  
  
 Puede acceder al servicio de proyectos de SharePoint en cualquier extensión de herramientas de SharePoint. También puede tener acceso a él en otros tipos de extensiones de Visual Studio, como complementos y VSPackages. Para obtener más información, consulte [Cómo: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
## <a name="project-service-features"></a>Características de Servicios de Project Server  
 En la tabla siguiente se enumeran las tareas que puede realizar mediante el servicio de proyectos de SharePoint y el método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> o propiedad que desea usar para realizar cada tarea.  
  
|Tarea|Miembro para usar|  
|----------|-------------------|  
|Acceda a cualquier proyecto de SharePoint que esté abierto en Visual Studio.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|  
|Acceda a todos los tipos de elemento de proyecto de SharePoint que están disponibles (incluidos los tipos de elemento de proyecto integrados y personalizados).|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|  
|Acceda a todos los pasos de implementación que están disponibles para los proyectos de SharePoint (incluidos los pasos de implementación integrados y personalizados).|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|  
|Acceda a los eventos que se producen cuando un desarrollador refactoriza el código en un proyecto de SharePoint.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|  
|Ejecutar un personalizado *comando de SharePoint* que llama al modelo de objetos de servidor de SharePoint. Para obtener más información acerca de los comandos de SharePoint, vea [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|  
|Convierta un tipo del sistema de proyecto de SharePoint en un tipo del modelo de objetos de automatización de Visual Studio o modelo de objetos de integración y viceversa. Para obtener más información, consulte [convertir entre SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>.|  
|Escribir mensajes en el **salida** ventana o **lista de errores** ventana de Visual Studio.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|  
|Acceda a otros servicios que están disponibles en Visual Studio.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|  
|Recupere la ruta de acceso de la carpeta de instalación del sitio de SharePoint local que se usa para depurar la solución.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|  
|Determine si [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] o [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] están instalados en el equipo.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|  
|Valide una característica o paquete en una solución de SharePoint.|Propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|  
  
## <a name="see-also"></a>Vea también  
 [Conversión entre tipos de sistema de proyecto de SharePoint y otros tipos de proyecto de Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Cómo: recuperar el servicio de proyecto de SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Información general sobre el modelo de programación de SharePoint de extensiones de herramientas](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Cómo: Obtener un servicio del objeto DTE](http://msdn.microsoft.com/library/bb166401.aspx)  
  
  