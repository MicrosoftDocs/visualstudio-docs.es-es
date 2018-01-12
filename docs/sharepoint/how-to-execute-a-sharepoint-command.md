---
title: "Cómo: ejecutar un comando de SharePoint | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint commands [SharePoint development in Visual Studio], executing
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8cfbcf4b00e4551b568e9124e839423f58d922c9
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-execute-a-sharepoint-command"></a>Cómo: Ejecutar un comando de SharePoint
  Si desea utilizar el modelo de objetos de servidor en una extensión de herramientas de SharePoint, debe crear una personalizada *comando de SharePoint* para llamar a la API. Después de definir el comando e implementarlo con la extensión de herramientas de SharePoint, la extensión puede ejecutar el comando para llamar al modelo de objetos de servidor de SharePoint. Para ejecutar el comando, utilice uno de los métodos de ExecuteCommand de un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto.  
  
 Para obtener más información sobre la finalidad de los comandos de SharePoint, vea [llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-execute-a-sharepoint-command"></a>Para ejecutar un comando de SharePoint  
  
1.  En la extensión de herramientas de SharePoint, obtenga una <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto. La manera de obtener un <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto depende del tipo de extensión que se va a crear:  
  
    -   En una extensión del sistema del proyecto de SharePoint, use la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A> propiedad.  
  
         Para obtener más información acerca de las extensiones de sistema de proyecto, vea [extender el sistema de proyectos de SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   En una extensión de la **las conexiones de SharePoint** nodo **Explorador de servidores**, use el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A> propiedad. Para obtener un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext> objeto, utilice el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A> propiedad.  
  
         Para obtener más información acerca de **Explorador de servidores** extensiones, consulte [extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   En el código que no forma parte de una extensión de las herramientas de SharePoint, como un Asistente para plantillas de proyecto, utilice la <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A> propiedad.  
  
         Para obtener más información acerca de cómo recuperar el servicio del proyecto, consulte [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Llame a uno de los métodos de ExecuteCommand de la <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objeto. Pase el nombre del comando que desea ejecutar en el primer argumento del método ExecuteCommand. Si el comando tiene un parámetro personalizado, pase ese parámetro para el segundo argumento del método ExecuteCommand.  
  
     Hay una sobrecarga ExecuteCommand diferente para cada firma de comando admitidos. En la tabla siguiente se enumera las firmas compatibles y qué sobrecarga que se utilizará para cada firma.  
  
    |Firma de comando|Sobrecarga ExecuteCommand que se usa|  
    |-----------------------|------------------------------------|  
    |El comando tiene solo el valor predeterminado <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro y no devuelve ningún valor.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |El comando tiene solo el valor predeterminado <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro y un valor devuelto.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |El comando tiene dos parámetros (el valor predeterminado <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro y un parámetro personalizado) y no devuelve ningún valor.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |El comando tiene dos parámetros y un valor devuelto.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo utilizar el <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> sobrecarga para llamar a la `Contoso.Commands.UpgradeSolution` comandos que se describen en [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/deploymentstepextension/upgradestep.vb#6)]  
  
 El `Execute` método mostrado en este ejemplo es una implementación de la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> método de la <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> interfaz en un paso de implementación personalizado. Para ver este código en el contexto de un ejemplo más extenso, vea [Tutorial: crear un paso de implementación personalizado para proyectos de SharePoint de](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Tenga en cuenta los siguientes detalles sobre la llamada a la <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> método:  
  
-   El primer parámetro identifica el comando que desea llamar. Esta cadena coincide con el valor que se pasa a la <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> en la definición de comando.  
  
-   El segundo parámetro es el valor que se van a pasar al segundo parámetro personalizado del comando. En este caso, es la ruta de acceso completa del archivo .wsp que se actualiza en el sitio de SharePoint.  
  
-   El código no pasa la parte implícita <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parámetro al comando. Este parámetro se pasa al comando automáticamente cuando se invoque el comando desde una extensión del sistema del proyecto de SharePoint o una extensión de la **las conexiones de SharePoint** nodo **Explorador de servidores**. En otros tipos de soluciones, como se muestra en un asistente de plantilla de proyecto que implementa el <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> interfaz, este parámetro es **null**.  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Este ejemplo requiere una referencia al ensamblado Microsoft.VisualStudio.SharePoint.  
  
## <a name="see-also"></a>Vea también  
 [Llamar a los modelos de objetos de SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Cómo: crear un comando de SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Tutorial: Extender el Explorador de servidores para mostrar elementos web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  