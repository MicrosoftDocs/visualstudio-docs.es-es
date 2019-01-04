---
title: Procedimiento Ejecutar un comando de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], executing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d6e529420db8261e87c856e2fc80ef436bbc3e73
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53953123"
---
# <a name="how-to-execute-a-sharepoint-command"></a>Procedimiento Ejecutar un comando de SharePoint
  Si desea utilizar el modelo de objetos de servidor en una extensión de herramientas de SharePoint, debe crear una personalizada *comando de SharePoint* para llamar a la API. Después de definir el comando e implementarlo con la extensión de herramientas de SharePoint, la extensión puede ejecutar el comando para llamar al modelo de objetos de servidor de SharePoint. Para ejecutar el comando, utilice uno de los métodos de ExecuteCommand de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto.  
  
 Para obtener más información sobre la finalidad de los comandos de SharePoint, vea [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-execute-a-sharepoint-command"></a>Para ejecutar un comando de SharePoint  
  
1.  En la extensión de herramientas de SharePoint, obtenga una <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto. La manera de obtener un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto depende del tipo de extensión que se va a crear:  
  
    -   En una extensión del sistema del proyecto de SharePoint, use la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> propiedad.  
  
         Para obtener más información acerca de las extensiones del sistema de proyecto, vea [extender el sistema de proyecto de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   En una extensión de la **conexiones de SharePoint** nodo **Explorador de servidores**, utilice el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> propiedad. Para obtener un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> de objeto, utilice el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> propiedad.  
  
         Para obtener más información acerca de **Explorador de servidores** extensiones, vea [extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   En el código que no forma parte de una extensión de las herramientas de SharePoint, como un Asistente para plantillas de proyecto, utilice el <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> propiedad.  
  
         Para obtener más información acerca de cómo recuperar el servicio del proyecto, vea [usar el servicio de proyecto de SharePoint](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Llame a uno de los métodos de ExecuteCommand de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto. Pase el nombre del comando que desea ejecutar en el primer argumento del método ExecuteCommand. Si el comando tiene un parámetro personalizado, pasar ese parámetro para el segundo argumento del método ExecuteCommand.  
  
     Hay una sobrecarga de ExecuteCommand diferente para cada firma de comando admitidos. En la tabla siguiente se enumera las firmas compatibles y qué sobrecarga que se usará para cada firma.  
  
    |Firma de comando|Sobrecarga ExecuteCommand que usar|  
    |-----------------------|------------------------------------|  
    |El comando tiene solo el valor predeterminado <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro y no devuelve ningún valor.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |El comando tiene solo el valor predeterminado <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro y un valor devuelto.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |El comando tiene dos parámetros (el valor predeterminado <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro y un parámetro personalizado) y no devuelve ningún valor.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |El comando tiene dos parámetros y un valor devuelto.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo usar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> sobrecarga para llamar a la `Contoso.Commands.UpgradeSolution` comandos que se describen en [Cómo: Crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 El `Execute` método que se muestra en este ejemplo es una implementación de la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> método de la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfaz en un paso de implementación personalizado. Para ver este código en el contexto de un ejemplo más extenso, vea [Tutorial: Crear un paso de implementación personalizado para proyectos de SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Tenga en cuenta los siguientes detalles acerca de la llamada a la <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> método:  
  
-   El primer parámetro identifica el comando que desea llamar. Esta cadena coincide con el valor que se pasa a la <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> en la definición de comando.  
  
-   El segundo parámetro es el valor que se van a pasar al segundo parámetro del comando personalizado. En este caso, es la ruta de acceso completa de la *.wsp* archivo que se está actualizando al sitio de SharePoint.  
  
-   El código no pasa implícito <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro al comando. Este parámetro se pasa al comando automáticamente cuando se invoque el comando desde una extensión del sistema del proyecto de SharePoint o una extensión de la **conexiones de SharePoint** nodo **Explorador de servidores**. En otros tipos de soluciones, como se muestra en un asistente de plantilla de proyecto que implementa el <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz, este parámetro es **null**.  
  
## <a name="compile-the-code"></a>Compilar el código  
 En este ejemplo requiere una referencia al ensamblado Microsoft.VisualStudio.SharePoint.  
  
## <a name="see-also"></a>Vea también
 [Llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Cómo: Crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Tutorial: Extender el Explorador de servidores para mostrar elementos web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
