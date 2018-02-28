---
title: "Cómo: ejecutar código cuando implementación se ejecutan los pasos | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: ad603c9f303cd5bf2b3dc317efddd2694e10a867
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Cómo: Ejecutar código cuando se ejecutan los pasos de implementación
  Si desea realizar tareas adicionales para un paso de implementación en un proyecto de SharePoint, puede controlar eventos que se producen por elementos de proyecto de SharePoint antes y después de que Visual Studio ejecuta cada paso de implementación. Para obtener más información, consulte [extender SharePoint empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>Para ejecutar código cuando se ejecutan los pasos de implementación  
  
1.  Crear una extensión de elemento de proyecto, una extensión de proyecto o una definición de un nuevo tipo de elemento de proyecto. Para obtener más información, vea los temas siguientes:  
  
    -   [Cómo: Crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Cómo: Crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Cómo: Definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  En la extensión, controlar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> eventos de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objeto (de una extensión de elemento de proyecto o extensión de proyecto) o un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objeto (en una definición de un nuevo tipo de elemento de proyecto).  
  
3.  En el evento controladores, utilice el <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> y <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> parámetros para obtener información sobre el paso de implementación. Por ejemplo, puede determinar qué paso de implementación se está ejecutando y si la solución se va a implementar o retirar.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo controlar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> eventos en una extensión para el elemento de proyecto de la instancia de lista. Esta extensión escribe un mensaje adicional a la **salida** ventana cuando Visual Studio recicla el grupo de aplicaciones mientras implementa y retracta la solución.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Este ejemplo requiere referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Extensión de SharePoint de empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Tutorial: Crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Cómo: Ejecutar código cuando se implementa o retracta un proyecto de SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  