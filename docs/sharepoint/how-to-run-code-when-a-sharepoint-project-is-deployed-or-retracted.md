---
title: 'Cómo: ejecutar código cuando un proyecto de SharePoint es implementa o retracta | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 4fa7d2652e65e26686a5058fcb2c8f5130fbbdde
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119803"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Cómo: ejecutar código cuando se está implementando o retirando un proyecto de SharePoint
  Si desea realizar tareas adicionales al implementar o retirar un proyecto de SharePoint, puede controlar los eventos generados por Visual Studio. Para obtener más información, consulte [ampliar SharePoint empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Para ejecutar código cuando un proyecto de SharePoint está implementando o retirando  
  
1.  Crear una extensión de elemento de proyecto, una extensión de proyecto o una definición de un nuevo tipo de elemento de proyecto. Para obtener más información, vea los temas siguientes:  
  
    -   [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  En la extensión, tener acceso a la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto. Para obtener más información, consulte [Cómo: recuperar el servicio de proyecto de SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
3.  Controlar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos del servicio del proyecto.  
  
4.  En el evento controladores, utilice el <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> para obtener información acerca de la sesión actual de la implementación. Por ejemplo, puede determinar qué proyecto se encuentra en la sesión actual de la implementación y si se está implementando o retirando.  
  
 En el ejemplo de código siguiente se muestra cómo controlar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos en una extensión de proyecto. Esta extensión escribe un mensaje adicional a la **salida** ventana cuando la implementación se inicia y se completa para un proyecto de SharePoint.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]  
  
## <a name="compile-the-code"></a>Compile el código  
 Este ejemplo requiere referencias a los ensamblados siguientes:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y otros archivos que desea distribuir con la extensión. Para obtener más información, consulte [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Ampliar la implementación y empaquetado de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Cómo: ejecutar código cuando se ejecutan los pasos de implementación](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)  
  
