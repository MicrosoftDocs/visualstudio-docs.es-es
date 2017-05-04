---
title: "How to: Create a SharePoint Command | Microsoft Docs"
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
  - "SharePoint commands [SharePoint development in Visual Studio], creating"
ms.assetid: e1fda8f0-eae1-4278-91c1-19a5e1fc327f
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# How to: Create a SharePoint Command
  Si desea utilizar el modelo de objetos de servidor en una extensión de herramientas de SharePoint, debe crear un *comando de SharePoint* personalizado para llamar a la API.  Defina el comando de SharePoint en un ensamblado que pueda llamar directamente al modelo de objetos de servidor.  
  
 Para obtener más información sobre el propósito de los comandos de SharePoint, vea [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### Para crear un comando de SharePoint  
  
1.  Cree un proyecto de biblioteca de clases con la siguiente configuración:  
  
    -   Tiene por destino .NET Framework 3.5.  Para obtener más información sobre cómo seleccionar la versión de .NET Framework de destino, vea [Cómo: Usar como destino una versión de .NET Framework](../Topic/How%20to:%20Target%20a%20Version%20of%20the%20.NET%20Framework.md).  
  
    -   Tiene por destino AnyCPU o x64.  De forma predeterminada, la plataforma de destino para los proyectos de biblioteca de clases es AnyCPU.  Para obtener más información sobre cómo seleccionar la plataforma de destino, vea [NIB: How to: Optimize an Application for a Specific CPU Type](http://msdn.microsoft.com/es-es/294a75d2-4279-4b72-8298-2bea05be907a).  
  
    > [!NOTE]  
    >  No puede implementar un comando de SharePoint en el mismo proyecto que define una extensión de herramientas de SharePoint, porque los comandos de SharePoint tienen como destino .NET Framework 3.5 y la extensión de herramientas de SharePoint tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  Debe definir los comandos de SharePoint que su extensión utilice en un proyecto independiente.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  En una clase del proyecto, cree un método que defina su comando de SharePoint.  El método debe cumplir las siguientes directrices:  
  
    -   Puede tener uno o dos parámetros.  
  
         El primero debe ser un objeto <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>.  Este objeto proporciona el Microsoft.SharePoint.SPSite o Microsoft.SharePoint.SPWeb en el que se ejecuta el comando.  También proporciona un objeto <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> que se puede utilizar para escribir los mensajes en la **Ventana de salida** o **Lista de errores** de Visual Studio.  
  
         El segundo parámetro puede ser un tipo de su elección, pero este parámetro es opcional.  Puede agregar este parámetro al comando de SharePoint si necesita pasar los datos de la extensión de herramientas de SharePoint al comando.  
  
    -   Puede tener un valor devuelto, pero es opcional.  
  
    -   El segundo parámetro y el valor devuelto deben ser un tipo que WCF \(Windows Communication Foundation\) pueda serializar.  Para obtener más información, vea [Tipos admitidos por el serializador de contrato de datos](../Topic/Types%20Supported%20by%20the%20Data%20Contract%20Serializer.md) y [Utilización de la clase XmlSerializer](../Topic/Using%20the%20XmlSerializer%20Class.md).  
  
    -   El método puede tener cualquier visibilidad \(**public**, **internal** o **private**\) y puede ser estático o no estático.  
  
4.  Aplique el <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> al método.  Este atributo especifica el identificador del comando; este identificador no tiene que coincidir con el nombre del método.  
  
     Debe especificar el mismo identificador único al llamar al comando desde la extensión de herramientas de SharePoint.  Para obtener más información, vea [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra un comando de SharePoint que tiene el identificador `Contoso.Commands.UpgradeSolution`.  Este comando utiliza API en el modelo de objetos de servidor para actualizar a una solución implementada.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/CS/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectextension.upgradedeploymentstep/vb/sharepointcommands/commands.vb#5)]  
  
 Además del primer parámetro <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> implícito, este comando también tiene un parámetro de cadena personalizado que contiene la ruta de acceso completa del archivo .wsp que se actualiza en el sitio de SharePoint.  Para consultar este código en el contexto de un ejemplo mayor, vea [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## Compilar el código  
 Para este ejemplo se requieren referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## Implementar el comando  
 Para implementar el comando, incluya el ensamblado del comando en el mismo paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] con el ensamblado de la extensión que utiliza el comando.  También debe agregar una entrada para el ensamblado del comando en el archivo extension.vsixmanifest.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  