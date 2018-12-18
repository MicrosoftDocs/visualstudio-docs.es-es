---
title: 'Cómo: ejecutar código cuando implementación ejecutan los pasos son | Microsoft Docs'
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
ms.openlocfilehash: cebd88cc49afa1092dfcd1d67ffdbf0fa3567ad0
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119770"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Cómo: ejecutar código cuando se ejecutan los pasos de implementación
  Si desea realizar tareas adicionales para un paso de implementación en un proyecto de SharePoint, puede controlar eventos generados por los elementos de proyecto de SharePoint antes y después de cada paso de implementación se ejecuta Visual Studio. Para obtener más información, consulte [extender SharePoint empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-run-code-when-deployment-steps-are-executed"></a>Para ejecutar código cuando se ejecutan los pasos de implementación  
  
1.  Crear una extensión de elemento de proyecto, una extensión de proyecto o una definición de un nuevo tipo de elemento de proyecto. Para obtener más información, vea los temas siguientes:  
  
    -   [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  En la extensión, controlar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> eventos de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objeto (en una extensión de elemento de proyecto o la extensión de proyecto) o un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objeto (en una definición de un nuevo tipo de elemento de proyecto).  
  
3.  En el evento controladores, utilice el <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> y <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> parámetros para obtener información sobre el paso de implementación. Por ejemplo, puede determinar qué paso de implementación se está ejecutando y si la solución se está implementando o retirando.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo controlar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> eventos en una extensión para el elemento de proyecto de la instancia de la lista. Esta extensión escribe un mensaje adicional a la **salida** ventana cuando Visual Studio se recicla el grupo de aplicaciones al implementar y retirar la solución.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]  
  
## <a name="compile-the-code"></a>Compile el código  
 Este ejemplo requiere referencias a los ensamblados siguientes:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploy-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y otros archivos que desea distribuir con la extensión. Para obtener más información, consulte [implementar extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Ampliar la implementación y empaquetado de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Tutorial: Crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)   
 [Cómo: ejecutar código cuando se está implementando o retirando un proyecto de SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)  
  
  
