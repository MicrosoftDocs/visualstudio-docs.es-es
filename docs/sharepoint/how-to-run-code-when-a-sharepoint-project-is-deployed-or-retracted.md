---
title: Procedimiento Ejecutar código cuando un proyecto de SharePoint es implementa o retracta | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bb5ba251df3271e704ea4b455c5cc47003ab8e2e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53933627"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Procedimiento Ejecute código al implementar o retirar un proyecto de SharePoint
  Si desea realizar tareas adicionales al implementar o retirar un proyecto de SharePoint, puede controlar los eventos generados por Visual Studio. Para obtener más información, consulte [ampliar SharePoint empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Para ejecutar código cuando un proyecto de SharePoint está implementando o retirando  
  
1. Crear una extensión de elemento de proyecto, una extensión de proyecto o una definición de un nuevo tipo de elemento de proyecto. Para obtener más información, vea los temas siguientes:  
  
   -   [Cómo: Crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
   -   [Cómo: Crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
   -   [Cómo: Definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2. En la extensión, tener acceso a la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto. Para obtener más información, vea [Cómo: Recuperar el servicio de proyecto de SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3. Controlar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos del servicio del proyecto.  
  
4. En el evento controladores, utilice el <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> para obtener información acerca de la sesión actual de la implementación. Por ejemplo, puede determinar qué proyecto se encuentra en la sesión actual de la implementación y si se está implementando o retirando.  
  
   En el ejemplo de código siguiente se muestra cómo controlar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos en una extensión de proyecto. Esta extensión escribe un mensaje adicional a la **salida** ventana cuando la implementación se inicia y se completa para un proyecto de SharePoint.  
  
   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compile-the-code"></a>Compilar el código  
 Este ejemplo requiere referencias a los ensamblados siguientes:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y otros archivos que desea distribuir con la extensión. Para obtener más información, consulte [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Ampliar la implementación y empaquetado de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Cómo: Ejecutar código cuando se ejecutan los pasos de implementación](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
