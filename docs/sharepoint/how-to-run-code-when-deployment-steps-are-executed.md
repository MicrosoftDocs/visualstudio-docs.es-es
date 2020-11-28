---
title: 'Cómo: ejecutar código cuando se ejecutan los pasos de implementación | Microsoft Docs'
description: Ejecute el código para controlar los eventos generados por los elementos de proyecto de SharePoint antes y después de que Visual Studio ejecute un paso de implementación.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 00b921d8500c95ebbb771b5c0b5817db87b7c6ca
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304455"
---
# <a name="how-to-run-code-when-deployment-steps-are-executed"></a>Cómo: ejecutar código cuando se ejecutan los pasos de implementación
  Si desea realizar tareas adicionales para un paso de implementación en un proyecto de SharePoint, puede controlar los eventos generados por los elementos de proyecto de SharePoint antes y después de que Visual Studio ejecute cada paso de implementación. Para obtener más información, vea [extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-deployment-steps-are-executed"></a>Para ejecutar el código cuando se ejecutan los pasos de implementación

1. Cree una extensión de elemento de proyecto, una extensión de proyecto o una definición de un nuevo tipo de elemento de proyecto. Para obtener más información, vea los temas siguientes:

    - [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. En la extensión, controle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> eventos y de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objeto (en una extensión de proyecto o extensión de elemento de proyecto) o un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objeto (en una definición de un nuevo tipo de elemento de proyecto).

3. En los controladores de eventos, use los <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs> <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepCompletedEventArgs> parámetros y para obtener información sobre el paso de implementación. Por ejemplo, puede determinar qué paso de implementación se está ejecutando y si la solución se está implementando o retirando.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo controlar los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepCompleted> eventos y en una extensión del elemento de proyecto de instancia de lista. Esta extensión escribe un mensaje adicional en la ventana de **salida** cuando Visual Studio recicla el grupo de aplicaciones al implementar y retirar la solución.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handledeploymentstepevents.vb#4)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#4](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handledeploymentstepevents.cs#4)]

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
- [Extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Cómo: ejecutar código cuando se implementa o retracta un proyecto de SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md)
