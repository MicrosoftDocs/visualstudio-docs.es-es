---
title: "How to: Get Data for a Built-In SharePoint Node in Server Explorer | Microsoft Docs"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], extending a node"
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
ms.assetid: 86d04e0a-c114-427e-9945-da5fa339fda4
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# How to: Get Data for a Built-In SharePoint Node in Server Explorer
  Desde cada uno de los nodos de SharePoint integrados en el **Explorador de servidores**, puede obtener los datos del componente de SharePoint subyacente que cada nodo representa.  Para obtener más información, vea [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo se obtienen datos de la lista de SharePoint subyacente representada por un nodo de lista en el **Explorador de servidores**.  De forma predeterminada, los nodos de lista tienen un elemento de menú contextual **Ver en el explorador** en el que se puede hacer clic para abrir las listas en un explorador web.  En este ejemplo, los nodos de lista se extienden agregando un elemento de menú contextual **Ver en Visual Studio** que abre las listas directamente en Visual Studio.  El código tiene acceso a los datos de la lista para que el nodo pueda ver la dirección URL de la lista y se abra en Visual Studio.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#10)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#10)]  
  
 En este ejemplo se usa el servicio de proyecto de SharePoint para obtener el objeto <xref:EnvDTE.DTE> que se usa para abrir listas en Visual Studio.  Para obtener más información sobre el servicio de proyecto de SharePoint, vea [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
 Para obtener más información sobre las tareas básicas implicadas en la creación de una extensión de un nodo de SharePoint, vea [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Compilar el código  
 Para este ejemplo se requieren referencias a los siguientes ensamblados:  
  
-   EnvDTE  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
## Implementar la extensión  
 Para implementar la extensión del **Explorador de servidores**, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado y el resto de archivos que desee distribuir con la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  