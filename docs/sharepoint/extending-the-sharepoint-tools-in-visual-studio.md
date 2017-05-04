---
title: "Extending the SharePoint Tools in Visual Studio | Microsoft Docs"
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
  - "Visual Studio, extending tools"
  - "extensibility [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Tools in Visual Studio
  Las herramientas de SharePoint en Visual Studio cumplen los requisitos de muchos escenarios de desarrollo de aplicaciones.  Sin embargo, puede haber casos en los que no proporcionen la funcionalidad que usted u otros desarrolladores de software requieren.  En estos casos, puede extender las herramientas SharePoint para crear la funcionalidad que necesita.  
  
## Cómo extender las Herramientas de SharePoint  
 Puede extender el sistema de proyectos de SharePoint y el nodo **Conexiones de SharePoint** en la ventana **Explorador de servidores**.  
  
### Extender el sistema de proyectos de SharePoint  
 Visual Studio incluye un conjunto de plantillas de proyecto y plantillas de elementos que se pueden usar para crear soluciones de SharePoint.  Por ejemplo, hay plantillas para los receptores de eventos, las definiciones de lista, los flujos de trabajo y los elementos web.  Sin embargo, también puede definir sus propios tipos de elementos de proyecto de SharePoint para crear componentes de SharePoint, como campos o acciones personalizadas.  También puede crear extensiones para los tipos de elemento de proyecto de SharePoint que ya están instalados en Visual Studio y puede crear extensiones para los proyectos de SharePoint.  
  
 Para obtener más información, vea [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### Extender el nodo Conexiones de SharePoint en el Explorador de servidores  
 En Visual Studio, puede utilizar el nodo de**Conexiones de SharePoint** en la ventana de**Explorador de servidores** para ver muchos de los componentes de uno o más sitios de SharePoint locales en una vista de árbol jerárquica. También puede extender el nodo de **Conexiones de SharePoint** de las maneras siguientes:  
  
-   Agregando sus propios nodos.  Esto es útil si desea mostrar los componentes de sitios de SharePoint que no se muestran de forma predeterminada.  
  
-   Extendiendo los nodos existentes.  Por ejemplo, puede agregar un nuevo nodo secundario a un nodo existente o puede agregar un elemento de menú contextual a un nodo y realizar las tareas cuando un desarrollador hace clic en el elemento de menú.  
  
 Para obtener más información, vea [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## Requisitos del equipo de desarrollo  
 Para crear extensiones para las herramientas de SharePoint, el equipo de desarrollo debe cumplir los mismos requisitos para crear soluciones de SharePoint en Visual Studio.  Para obtener más información, vea [Requisitos para desarrollar soluciones de SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 Se recomienda asimismo instalar [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  El SDK incluye plantillas de proyecto y herramientas que puede utilizar para extender Visual Studio.  En concreto, el SDK incluye una plantilla de proyecto que puede utilizar para crear un paquete de extensión de Visual Studio \(VSIX\) con facilidad.  Los paquetes VSIX son la mejor manera de implementar extensiones de Visual Studio en Visual Studio.  Todas las extensiones de SharePoint se deben implementar utilizando los paquetes VSIX.  En todos los tutoriales en esta documentación se supone que tiene [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] instalado.  
  
 Para descargar el SDK, vea [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=164562](http://go.microsoft.com/fwlink/?LinkId=164562).  Para obtener más información sobre las extensiones de Visual Studio, vea [Desarrollar extensiones de Visual Studio](../Topic/Developing%20Visual%20Studio%20Extensions.md).  
  
## Vea también  
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Reference &#40;SharePoint Tools Extensibility&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  