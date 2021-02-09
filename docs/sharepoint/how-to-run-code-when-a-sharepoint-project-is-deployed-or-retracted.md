---
title: Ejecutar código cuando se implementa o se retira un proyecto de SharePoint
titleSuffix: ''
description: Obtenga información sobre cómo ejecutar código cuando se implementa o retracta un proyecto de SharePoint para que pueda controlar los eventos generados por Visual Studio.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 3362606a7e8c5f2278c2ebfb973321e5b8f3157e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99850144"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Cómo: ejecutar código cuando se implementa o retracta un proyecto de SharePoint
  Si desea realizar tareas adicionales cuando se implementa o retracta un proyecto de SharePoint, puede controlar los eventos generados por Visual Studio. Para obtener más información, vea [extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Para ejecutar código cuando se implementa o retracta un proyecto de SharePoint

1. Cree una extensión de elemento de proyecto, una extensión de proyecto o una definición de un nuevo tipo de elemento de proyecto. Para obtener más información, vea los temas siguientes:

   - [Cómo: crear una extensión de elemento de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Cómo: crear una extensión de proyecto de SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Cómo: definir un tipo de elemento de proyecto de SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. En la extensión, acceda al <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto. Para obtener más información, vea [Cómo: recuperar el servicio de proyecto de SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. Controle <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos y del servicio de proyecto.

4. En los controladores de eventos, use el <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> parámetro para obtener información acerca de la sesión de implementación actual. Por ejemplo, puede determinar qué proyecto se encuentra en la sesión de implementación actual y si se está implementando o retirando.

   En el ejemplo de código siguiente se muestra cómo controlar los <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos y en una extensión de proyecto. Esta extensión escribe un mensaje adicional en la ventana de **salida** cuando se inicia la implementación y finaliza para un proyecto de SharePoint.

   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión, cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vea también
- [Extender el empaquetado e implementación de SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Cómo: ejecutar código cuando se ejecutan los pasos de implementación](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
