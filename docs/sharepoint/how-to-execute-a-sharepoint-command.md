---
title: "How to: Execute a SharePoint Command | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint commands [SharePoint development in Visual Studio], executing"
ms.assetid: 2d1a163b-b601-4dac-bcea-328f24cb4d57
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# How to: Execute a SharePoint Command
  Si desea utilizar el modelo de objetos de servidor en una extensión de herramientas de SharePoint, debe crear un *comando de SharePoint* personalizado para llamar a la API.  Después de definir el comando e implementarlo con la extensión de herramientas de SharePoint, la extensión puede ejecutar el comando para llamar en el modelo de objetos de servidor de SharePoint.  Para ejecutar el comando, use uno de los métodos ExecuteCommand de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  
  
 Para obtener más información sobre el propósito de los comandos de SharePoint, vea [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### Para ejecutar un comando de SharePoint  
  
1.  En la extensión de herramientas de SharePoint, obtenga un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  La manera de obtener un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> depende del tipo de extensión que se esté creando:  
  
    -   En una extensión del sistema de proyectos de SharePoint, use la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.SharePointConnection%2A>.  
  
         Para obtener más información sobre extensiones del sistema de proyectos, vea [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
    -   En una extensión del nodo **Conexiones de SharePoint** en el **Explorador de servidores**, use la propiedad <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext.SharePointConnection%2A>.  Para obtener un objeto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeContext>, use la propiedad <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode.Context%2A>.  
  
         Para obtener más información sobre las extensiones del **Explorador de servidores**, vea [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
    -   En código que no forme parte de una extensión de las herramientas SharePoint, como un asistente de plantilla de proyecto, use la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.  
  
         Para obtener más información acerca de la recuperación de un servicio de proyecto, vez [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
2.  Llame a uno de los métodos ExecuteCommand del objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  Pase el nombre del comando que desea ejecutar al primer argumento del método ExecuteCommand.  Si el comando tiene un parámetro personalizado, páselo al segundo argumento del método ExecuteCommand.  
  
     Hay una sobrecarga ExecuteCommand diferente para cada firma de comando compatible.  En la tabla siguiente se enumeran las firmas compatibles y qué sobrecarga usar con cada una.  
  
    |firma de comando|Sobrecarga ExecuteCommand que se usa|  
    |----------------------|------------------------------------------|  
    |El comando solo tiene el parámetro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> predeterminado y no devuelve valor.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |El comando solo tiene el parámetro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> predeterminado y un valor devuelto.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |El comando tiene dos parámetros \(parámetro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> predeterminado y un parámetro personalizado\) y ningún valor devuelto.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
    |El comando tiene dos parámetros y un valor devuelto.|<xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>|  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo utilizar la sobrecarga <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A> para llamar al comando `Contoso.Commands.UpgradeSolution` que se describe en [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md).  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/deploymentstepextension/upgradestep.cs#6)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/deploymentstepextension/upgradestep.vb#6)]  
  
 El método `Execute` mostrado en este ejemplo es una implementación del método <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep.Execute%2A> de la interfaz <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep> en un paso de implementación personalizado.  Para consultar este código en el contexto de un ejemplo mayor, vea [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
 Observe los detalles siguientes sobre la llamada al método <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection.ExecuteCommand%2A>:  
  
-   El primer parámetro identifica el comando que desea llamar.  Esta cadena coincide con el valor que pasa a <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> en la definición de comando.  
  
-   El segundo parámetro es el valor que desea pasar al segundo parámetro personalizado del comando.  En este caso, es la ruta de acceso completa del archivo .wsp que se actualiza en el sitio de SharePoint.  
  
-   El código no pasa el parámetro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> implícito al comando.  Este parámetro se pasa automáticamente al comando cuando se le llama desde una extensión del sistema de proyectos de SharePoint o una extensión del nodo **Conexiones de SharePoint** del **Explorador de servidores**.  En otros tipos de soluciones, por ejemplo, en un asistente de plantilla de proyecto que implemente la interfaz <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>, este parámetro es **null**.  
  
## Compilar el código  
 En este ejemplo se requiere una referencia al ensamblado Microsoft.VisualStudio.SharePoint.  
  
## Vea también  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  