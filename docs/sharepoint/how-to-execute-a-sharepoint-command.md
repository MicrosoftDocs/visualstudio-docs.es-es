---
title: 'Cómo: ejecutar un comando de SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 789b77f3161b5fe566ea033060e8cab16cbaecc7
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016992"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Cómo: ejecutar un comando de SharePoint
  Si desea usar el modelo de objetos de servidor en una extensión de herramientas de SharePoint, debe crear un *comando de SharePoint* personalizado para llamar a la API. Después de definir el comando e implementarlo con la extensión de herramientas de SharePoint, la extensión puede ejecutar el comando para llamar al modelo de objetos de servidor de SharePoint. Para ejecutar el comando, use uno de los métodos ExecuteCommand de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto.

 Para obtener más información sobre el propósito de los comandos de SharePoint, consulte [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-execute-a-sharepoint-command"></a>Para ejecutar un comando de SharePoint

1. En la extensión de herramientas de SharePoint, obtenga un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto. La forma de obtener un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto depende del tipo de extensión que se está creando:

    - En una extensión del sistema de proyectos de SharePoint, use la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> propiedad.

         Para obtener más información acerca de las extensiones del sistema de proyectos, vea [extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

    - En una extensión del nodo **conexiones de SharePoint** en **Explorador de servidores**, use la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> propiedad. Para obtener un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> objeto, utilice la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> propiedad.

         Para obtener más información acerca de las extensiones de **Explorador de servidores** , consulte [extender el nodo conexiones de SharePoint en explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

    - En el código que no forma parte de una extensión de las herramientas de SharePoint, como un asistente para plantillas de proyecto, use la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> propiedad.

         Para obtener más información sobre cómo recuperar el servicio de proyecto, vea [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

2. Llame a uno de los métodos ExecuteCommand del <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto. Pase el nombre del comando que desea ejecutar al primer argumento del método ExecuteCommand. Si el comando tiene un parámetro personalizado, pase el parámetro al segundo argumento del método ExecuteCommand.

     Hay una sobrecarga de ExecuteCommand diferente para cada firma de comando admitida. En la tabla siguiente se enumeran las firmas admitidas y qué sobrecarga se debe usar para cada firma.

    |Firma de comando|Sobrecarga ExecuteCommand que se va a usar|
    |-----------------------|------------------------------------|
    |El comando solo tiene el <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro predeterminado y ningún valor devuelto.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |El comando solo tiene el <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro predeterminado y un valor devuelto.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |El comando tiene dos parámetros (el <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro predeterminado y un parámetro personalizado) y ningún valor devuelto.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|
    |El comando tiene dos parámetros y un valor devuelto.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo usar la <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> sobrecarga para llamar al `Contoso.Commands.UpgradeSolution` comando que se describe en [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]

 El `Execute` método que se muestra en este ejemplo es una implementación del <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> método de la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfaz en un paso de implementación personalizado. Para ver este código en el contexto de un ejemplo más grande, vea [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

 Tenga en cuenta los siguientes detalles sobre la llamada al <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> método:

- El primer parámetro identifica el comando al que desea llamar. Esta cadena coincide con el valor que se pasa a <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> en la definición de comando.

- El segundo parámetro es el valor que se desea pasar al segundo parámetro personalizado del comando. En este caso, es la ruta de acceso completa del archivo *. wsp* que se está actualizando al sitio de SharePoint.

- El código no pasa el parámetro implícito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> al comando. Este parámetro se pasa al comando automáticamente cuando se llama al comando desde una extensión del sistema de proyectos de SharePoint o una extensión del nodo **conexiones de SharePoint** en **Explorador de servidores**. En otros tipos de soluciones, como en un asistente para plantillas de proyecto que implementa la <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz, este parámetro es **null**.

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere una referencia al ensamblado Microsoft. VisualStudio. SharePoint.

## <a name="see-also"></a>Consulte también
- [Llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Tutorial: extender Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
