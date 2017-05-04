---
title: "Extending the SharePoint Connections Node in Server Explorer | Microsoft Docs"
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
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: 8bfa5950-0ef4-4417-9538-cc8a5a1c35e2
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Extending the SharePoint Connections Node in Server Explorer
  En Visual Studio, puede conectar los sitios de SharePoint locales en el equipo de desarrollo utilizando el nodo de **Conexiones de SharePoint** en la ventana de**Explorador de servidores** .  Este nodo muestra muchos de los componentes de los sitios de SharePoint locales en una vista de árbol jerárquica.  Por ejemplo, puede ver las listas, las bibliotecas de documentos y los tipos de contenido en sitios locales. Para obtener más información sobre cómo utilizar el **Explorador de servidores** para conectarse a sitios locales de SharePoint, vea [Examinar las conexiones de SharePoint utilizando el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Puede extender el nodo **Conexiones de SharePoint** creando extensiones para los nodos existentes, o creando un tipo de nodo personalizado y agregándolo a la jerarquía de nodos.  
  
## Tareas para extender el nodo Conexiones de SharePoint  
 Para extender un nodo existente, cree una extensión de Visual Studio que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Al extender un nodo, puede agregar funcionalidad al nodo, por ejemplo sus propios elementos de menú contextual o propiedades personalizadas.  Para obtener más información, vea [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Para crear un tipo de nodo personalizado, cree una extensión de Visual Studio que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Cree un nodo personalizado si desea mostrar los componentes de sitios de SharePoint que no se muestran de forma predeterminada en el **Explorador de servidores**.  Por ejemplo, el **Explorador de servidores** no muestra la galería de elementos web de un sitio de SharePoint de forma predeterminada, pero puede agregar un nodo personalizado que lo haga.  Para obtener más información, vea [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) y [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## Agregar propiedades personalizadas a nodos  
 Al extender un nodo o crear un tipo de nodo personalizado, puede agregar propiedades personalizadas al nodo.  Las propiedades aparecen en la ventana **Propiedades** cuando el nodo está seleccionado.  
  
 Hay dos tipos de propiedades personalizadas que puede agregar a un nodo:  
  
-   Propiedades que muestran un conjunto de datos de solo lectura del sitio de SharePoint.  Los datos describen el componente de SharePoint que representa el nodo.  Para realizar un tutorial donde se muestra cómo llevarlo a cabo, vea [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Propiedades que muestran datos de lectura y escritura personalizados.  Para obtener un ejemplo en el que se muestra cómo hacerlo, vea [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## Obtener datos para nodos integrados  
 Todos los nodos integrados proporcionados por Visual Studio incluyen algunos datos sobre el componente de SharePoint que representan.  Por ejemplo, un nodo que representa una lista en el sitio de SharePoint proporciona algunos datos sobre la lista, como el título y la dirección URL de la vista predeterminada de la lista.  
  
 Para tener acceso a estos datos, recupere un objeto de datos de la propiedad <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> del objeto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> que representa el nodo en el que está interesado.  El tipo del objeto de datos depende del tipo de nodo.  
  
 El siguiente ejemplo de código muestra cómo obtener el objeto de datos de un nodo de lista.  Para ver este ejemplo en el contexto de un ejemplo mayor, vea [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextensionnodeinfo.cs#11)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextensionnodeinfo.vb#11)]  
  
 En la siguiente tabla se enumeran los tipos de objeto de datos de cada tipo de nodo integrado.  
  
|Tipo de nodo|Tipo de objeto de datos|  
|------------------|-----------------------------|  
|Nodo de sitio de SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Tipo de contenido|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Característica|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Campo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|List|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Plantilla de lista|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Vista Lista \(Microsoft.SharePoint.SPView\)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Asociación de flujo de trabajo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Plantilla de flujo de trabajo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Para obtener más información sobre cómo utilizar la propiedad <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, vea [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## Vea también  
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [How to: Get Data for a Built-In SharePoint Node in Server Explorer](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Examinar las conexiones de SharePoint utilizando el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  