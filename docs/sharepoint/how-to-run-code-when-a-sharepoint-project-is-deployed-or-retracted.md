---
title: "Cómo: ejecutar código cuando un proyecto de SharePoint es implementa o retira | Documentos de Microsoft"
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
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
ms.assetid: 353bbe6d-9b76-48ad-9fba-7e3c3712452f
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b452d28b1fc8173435b4de993561b59a680b0fed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Cómo: Ejecutar código cuando se implementa o retracta un proyecto de SharePoint
  Si desea realizar tareas adicionales al implementar o retirar un proyecto de SharePoint, puede controlar eventos generados por Visual Studio. Para obtener más información, consulte [extender SharePoint empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Para ejecutar código cuando un proyecto de SharePoint se implementa o retira  
  
1.  Crear una extensión de elemento de proyecto, una extensión de proyecto o una definición de un nuevo tipo de elemento de proyecto. Para obtener más información, vea los temas siguientes:  
  
    -   [Cómo: Crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Cómo: Crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Cómo: Definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  En la extensión, tener acceso a la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto. Para obtener más información, consulte [Cómo: Retrieve the SharePoint Project Service](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Controlar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos del servicio del proyecto.  
  
4.  En el evento controladores, usar el <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> para obtener información sobre la sesión de implementación actual. Por ejemplo, puede determinar qué proyecto se encuentra en la sesión de implementación actual y si se va a implementar o retirar.  
  
 En el ejemplo de código siguiente se muestra cómo controlar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos en una extensión de proyecto. Esta extensión escribe un mensaje adicional a la **salida** ventana cuando la implementación se inicia y se completa para un proyecto de SharePoint.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Este ejemplo requiere referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Extensión de SharePoint de empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Cómo: Ejecutar código cuando se ejecutan los pasos de implementación](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
  