---
title: 'Cómo: controlar conflictos de implementación | Microsoft Docs'
description: Vea un ejemplo de cómo implementar su propio código para controlar los conflictos de implementación de un elemento de proyecto de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 975fa69a503f5e2acd3e90defd9fa9895c70db00
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903512"
---
# <a name="how-to-handle-deployment-conflicts"></a>Cómo: controlar conflictos de implementación
  Puede proporcionar su propio código para controlar los conflictos de implementación de un elemento de proyecto de SharePoint. Por ejemplo, puede determinar si algún archivo del elemento de proyecto actual ya existe en la ubicación de implementación y, a continuación, eliminar los archivos implementados antes de que se implemente el elemento de proyecto actual. Para obtener más información acerca de los conflictos de implementación, vea [extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-handle-a-deployment-conflict"></a>Para controlar un conflicto de implementación

1. Cree una extensión de elemento de proyecto, una extensión de proyecto o una definición de un nuevo tipo de elemento de proyecto. Para obtener más información, vea los temas siguientes:

    - [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

    - [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

    - [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. En la extensión, controle el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> evento de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> objeto (en una extensión de elemento de proyecto o una extensión de proyecto) o un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> objeto (en una definición de un nuevo tipo de elemento de proyecto).

3. En el controlador de eventos, determine si hay un conflicto entre el elemento de proyecto que se está implementando y la solución implementada en el sitio de SharePoint, en función de los criterios que se aplican a su escenario. Puede usar la <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemEventArgs.ProjectItem%2A> propiedad del parámetro de argumentos de evento para analizar el elemento de proyecto que se está implementando y puede analizar los archivos en la ubicación de implementación mediante una llamada a un comando de SharePoint que defina para este fin.

     En el caso de muchos tipos de conflictos, puede que primero quiera determinar qué paso de implementación se está ejecutando. Para ello, puede usar la <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.DeploymentStepInfo%2A> propiedad del parámetro de argumentos de evento. Aunque normalmente tiene sentido detectar conflictos durante el <xref:Microsoft.VisualStudio.SharePoint.Deployment.DeploymentStepIds.AddSolution> paso de implementación integrado, puede comprobar si hay conflictos durante cualquier paso de implementación.

4. Si existe un conflicto, use el <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> método de la <xref:Microsoft.VisualStudio.SharePoint.DeploymentStepStartedEventArgs.Conflicts%2A> propiedad de los argumentos del evento para crear un nuevo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objeto. Este objeto representa el conflicto de implementación. En la llamada al <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflictCollection.Add%2A> método, especifique también el método al que se llama para resolver el conflicto.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra el proceso básico para controlar un conflicto de implementación en una extensión de elemento de proyecto para los elementos de proyecto de definición de lista. Para controlar un conflicto de implementación para un tipo de elemento de proyecto diferente, pase una cadena diferente a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Para obtener más información, vea [extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md).

 Para simplificar, el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> controlador de eventos en este ejemplo supone que existe un conflicto de implementación (es decir, siempre agrega un nuevo <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objeto) y el `Resolve` método simplemente devuelve **true** para indicar que se resolvió el conflicto. En un escenario real, el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.DeploymentStepStarted> controlador de eventos determinará primero si existe un conflicto entre un archivo en el elemento de proyecto actual y un archivo en la ubicación de implementación y, a continuación, agregará un <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentConflict> objeto solo si existe un conflicto. Por ejemplo, puede usar la `e.ProjectItem.Files` propiedad en el controlador de eventos para analizar los archivos en el elemento de proyecto, y puede llamar a un comando de SharePoint para analizar los archivos en la ubicación de implementación. Del mismo modo, en un escenario real, el `Resolve` método puede llamar a un comando de SharePoint para resolver el conflicto en el sitio de SharePoint. Para obtener más información sobre cómo crear comandos de SharePoint, consulte [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-vb[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/VisualBasic/deploymentconflict/extension/deploymentconflictextension.vb#1)]
 [!code-csharp[SPExtensibility.ProjectItemExtension.DeploymentConflict#1](../sharepoint/codesnippet/CSharp/deploymentconflict/extension/deploymentconflictextension.cs#1)]

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte también
- [Extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Extender elementos de proyecto de SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Cómo: ejecutar código cuando se ejecutan los pasos de implementación](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
