---
title: "Cómo: controlar los conflictos de implementación | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SharePoint development in Visual Studio, extending deployment
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: c3bbd5bc7d69fbc48d2c754151a3ec6b5fcb612c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-handle-deployment-conflicts"></a>Cómo: Controlar conflictos de implementación
  Puede proporcionar su propio código para controlar conflictos de implementación en un elemento de proyecto de SharePoint. Por ejemplo, puede determinar si los archivos en el elemento de proyecto actual ya existen en la ubicación de implementación y, a continuación, elimine los archivos implementados antes de implementa el elemento de proyecto actual. Para obtener más información acerca de los conflictos de implementación, consulte [extender SharePoint empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
### <a name="to-handle-a-deployment-conflict"></a>Para solucionar un conflicto de implementación  
  
1.  Crear una extensión de elemento de proyecto, una extensión de proyecto o una definición de un nuevo tipo de elemento de proyecto. Para obtener más información, vea los temas siguientes:  
  
    -   [Cómo: Crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)  
  
    -   [Cómo: Crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)  
  
    -   [Cómo: Definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)  
  
2.  En la extensión, controlar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> eventos de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objeto (de una extensión de elemento de proyecto o extensión de proyecto) o un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objeto (en una definición de un nuevo tipo de elemento de proyecto).  
  
3.  En el controlador de eventos, determinar si hay un conflicto entre el elemento de proyecto que se va a implementar y la solución implementada en el sitio de SharePoint, en función de criterios que se aplican a su escenario. Puede usar el <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> propiedad del parámetro de argumentos del evento para analizar el elemento de proyecto que se va a implementar y se pueden analizar los archivos en la ubicación de implementación mediante una llamada a un comando de SharePoint que se define para este propósito.  
  
     Para muchos tipos de conflictos, primero debe determinar qué paso de implementación se está ejecutando. Puede hacerlo mediante el uso de la <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> propiedad del parámetro de argumentos del evento. Aunque normalmente tiene sentido para detectar conflictos durante la integrada <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> paso de implementación, puede comprobar si hay conflictos en algún paso de implementación.  
  
4.  Si existe un conflicto, use la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> método de la <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> propiedad de los argumentos de evento para crear un nuevo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objeto. Este objeto representa el conflicto de implementación. En la llamada a la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> (método), especifique también el método que se llama para resolver el conflicto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra el proceso básico para administrar un conflicto de implementación en una extensión de elemento de proyecto para los elementos de proyecto de definición de lista. Para controlar un conflicto de implementación para un tipo de elemento de proyecto diferente, pasa una cadena diferente para el <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Para obtener más información, consulte [extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md).  
  
 Para simplificar, el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> controlador de eventos en este ejemplo se supone que existe un conflicto de implementación (es decir, siempre agrega un nuevo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objeto) y el `Resolve` método simplemente devuelve **true** para indicar que se resolvió el conflicto. En un escenario real, el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> controlador de eventos debería determinar primero si existe un conflicto entre un archivo en el elemento de proyecto actual y un archivo en la ubicación de implementación y, a continuación, agregue un <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objeto solo si existe un conflicto. Por ejemplo, puede usar el `e.ProjectItem.Files` propiedad en el controlador de eventos para analizar los archivos en el elemento de proyecto y puede llamar a un comando de SharePoint para analizar los archivos en la ubicación de implementación. De forma similar, en un escenario real la `Resolve` método podría llamar a un comando de SharePoint para resolver el conflicto en el sitio de SharePoint. Para obtener más información acerca de cómo crear comandos de SharePoint, vea [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Este ejemplo requiere referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## <a name="deploying-the-extension"></a>Implementar la extensión  
 Para implementar la extensión, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Extensión de SharePoint de empaquetado e implementación](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)   
 [Cómo: ejecutar código cuando implementación se ejecutan los pasos](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)   
 [Cómo: Crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)  
  
  