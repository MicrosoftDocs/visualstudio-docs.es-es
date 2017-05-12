---
title: "Calling into the SharePoint Object Models"
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
  - "SharePoint development in Visual Studio, client object model"
  - "SharePoint development in Visual Studio, server object model"
  - "SharePoint commands [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: 99934f9e-901e-464e-ac8c-22c6c86440f4
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Calling into the SharePoint Object Models
  Al crear extensiones para las herramientas de SharePoint en Visual Studio, puede tener que llamar a las API de SharePoint para realizar ciertas tareas.  Por ejemplo, si crea un paso de implementación personalizado para los proyectos de SharePoint, tal vez tenga que llamar a las API de SharePoint para algunas de las tareas de la implementación de soluciones.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] proporcionan dos modelos de objetos diferentes que puede utilizar en las extensiones de herramientas de SharePoint: un modelo de objetos de servidor y un modelo de objetos de cliente.  Cada uno presenta ventajas y desventajas en el contexto de las extensiones de herramientas de SharePoint.  
  
 Para ver una introducción a los modelos de objeto de SharePoint, vea [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## Uso del modelo de objetos de cliente en proyectos de extensión  
 Al desarrollar una extensión para las herramientas SharePoint, puede utilizar el modelo de objetos de cliente como cualquier otro conjunto de API administradas.  Puede agregar las referencias a los ensamblados en el modelo de objetos del cliente a su proyecto y llamar directamente a las API en el modelo de objetos del cliente desde el código.  
  
 Sin embargo, el modelo de objetos de cliente tiene dos inconvenientes en el contexto de las extensiones de herramientas de SharePoint:  
  
-   El modelo de objetos de cliente proporciona solo un subconjunto del modelo de objetos de servidor.  Si tiene que utilizar funcionalidad de SharePoint que no se expone en el modelo de objetos de cliente, debe usar el modelo de objetos de servidor.  
  
-   Aunque usar el modelo de objetos de cliente en las extensiones de herramientas de SharePoint serviría en la mayoría de los casos, puede haber escenarios en los que las llamadas al modelo de objetos de cliente no funcionen tal y como se espera.  El modelo de objetos de cliente se ha diseñado para usarlo en las aplicaciones cliente para llamar a los sitios de SharePoint en un servidor remoto o en una granja de servidores.  Las herramientas de SharePoint en Visual Studio solo funcionan con una instalación de SharePoint local en el equipo de desarrollo.  Por consiguiente, cuando se usa el modelo de objetos de cliente en una extensión de herramientas de SharePoint, se llama a un sitio de SharePoint en el equipo local, que no es la forma en que se diseño el modelo de objetos de cliente para ser usado.  
  
 Para un tutorial que muestra cómo utilizar el modelo de objetos de cliente en una extensión de herramientas de SharePoint en Visual Studio, vea [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## Uso del modelo de objetos de servidor en proyectos de extensión  
 El modelo de objetos de servidor es un supraconjunto del modelo de objetos de cliente.  Con el modelo de objetos de servidor, puede usar todas las características que [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] y [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] exponen mediante programación.  
  
 Las extensiones de herramientas de SharePoint pueden usar las API del modelo de objetos de servidor, pero no pueden llamarlas directamente.  Solo se puede llamar al modelo de objetos de servidor desde un proceso de 64 bits que tenga como destino .NET Framework 3.5.  Sin embargo, las extensiones de herramientas de SharePoint requieren [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] y se ejecutan en el proceso de Visual Studio de 32 bits.  Esto evita que las extensiones de herramientas de SharePoint hagan referencia directamente a los ensamblados del modelo de objetos de servidor de SharePoint.  
  
 Si desea utilizar el modelo de objetos de servidor en una extensión de herramientas de SharePoint, debe crear un *comando de SharePoint* personalizado para llamar a la API.  Defina el comando de SharePoint en un ensamblado secundario que puede llamar directamente al modelo de objetos de servidor.  En el proyecto de extensión, llame indirectamente al comando de SharePoint utilizando el método ExecuteCommand de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection>.  
  
 Para obtener más información sobre cómo crear y utilizar los comandos de SharePoint, vea [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md) y [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).  Para obtener información sobre cómo implementar los comandos de SharePoint, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Para ver tutoriales que muestran cómo crear y utilizar los comandos de SharePoint, vea [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) y [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### Entender cómo se ejecutan los comandos de SharePoint  
 Los ensamblados que definen los comandos de SharePoint se cargan en un proceso de host de 64 bits denominado vssphost4.exe.  Después de llamar a un comando de SharePoint en una extensión de herramientas de SharePoint, el comando lo ejecuta vssphost4.exe, no el proceso de Visual Studio de 32 bits \(devenv.exe\).  Puede controlar algunos aspectos de cómo se ejecutan los comandos de SharePoint estableciendo valores en el Registro.  Para obtener más información, vea [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
  