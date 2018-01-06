---
title: Extender el nodo Conexiones de SharePoint en el Explorador de servidores | Documentos de Microsoft
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
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
ms.assetid: 8bfa5950-0ef4-4417-9538-cc8a5a1c35e2
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: fe9fb4a12d45cf5d713fb76fe3fe04e1346a8355
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Extender el nodo Conexiones de SharePoint en el Explorador de servidores
  En Visual Studio, puede conectarse a los sitios de SharePoint locales en el equipo de desarrollo mediante el uso de la **las conexiones de SharePoint** nodo en el**Explorador de servidores** ventana. Este nodo muestra muchos de los componentes de sitios de SharePoint locales en una vista de árbol jerárquico. Por ejemplo, puede ver las listas, bibliotecas de documentos y tipos de contenido en los sitios locales. Para obtener más información sobre el uso de **Explorador de servidores** para conectarse a sitios locales de SharePoint, vea [examinar las conexiones de SharePoint utilizando el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).  
  
 Puede ampliar el **las conexiones de SharePoint** nodo mediante la creación de extensiones para los nodos existentes o crear un tipo de nodo personalizado y agregándolo a la jerarquía de nodos.  
  
## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Tareas para extender el nodo Conexiones de SharePoint  
 Para extender un nodo existente, crear una extensión de Visual Studio que implementa el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaz. Al extender un nodo, puede agregar funcionalidad al nodo como sus propios elementos de menú contextual o propiedades personalizadas. Para obtener más información, consulte [Cómo: Extender un nodo de SharePoint en el Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
 Para crear un tipo de nodo personalizado, cree una extensión de Visual Studio que implemente la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaz. Cree un nodo personalizado si desea mostrar los componentes de sitios de SharePoint que no se muestran en **Explorador de servidores** de forma predeterminada. Por ejemplo, **Explorador de servidores** ¿no se puede agregar la Galería de elementos Web de un sitio de SharePoint de manera predeterminada, pero se muestre un nodos personalizado que lo haga. Para obtener más información, consulte [Cómo: agregar un nodo de SharePoint personalizado al explorador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) y [Tutorial: Extender el Explorador de servidores para mostrar elementos de Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="adding-custom-properties-to-nodes"></a>Agregar propiedades personalizadas a nodos  
 Al extender un nodo o crear un tipo de nodo personalizado, puede agregar propiedades personalizadas al nodo. Las propiedades aparecen en la **propiedades** ventana cuando se selecciona el nodo.  
  
 Hay dos tipos de propiedades personalizadas que pueden agregar a un nodo:  
  
-   Propiedades que muestran un conjunto de datos de solo lectura del sitio de SharePoint. Los datos describen el componente de SharePoint que representa el nodo. Para ver un tutorial que muestra cómo hacerlo, consulte [Tutorial: Extender el Explorador de servidores para mostrar elementos de Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
-   Propiedades que muestran datos de lectura/escritura personalizado. Para obtener un ejemplo de código que muestra cómo hacerlo, consulte [Cómo: Extender un nodo de SharePoint en el Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).  
  
## <a name="getting-data-for-built-in-nodes"></a>Obtener datos para nodos integrados  
 Todos los nodos integrados proporcionados por Visual Studio incluyen algunos datos sobre el componente de SharePoint que representan. Por ejemplo, un nodo que representa una lista en el sitio de SharePoint proporciona algunos datos sobre la lista, como el título y la dirección URL de la vista predeterminada de la lista.  
  
 Para tener acceso a estos datos, recupere un objeto de datos desde el <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objeto que representa el nodo que le interesen. El tipo del objeto de datos depende del tipo del nodo.  
  
 En el ejemplo de código siguiente se muestra cómo obtener el objeto de datos de un nodo de lista. Para ver este ejemplo en el contexto de un ejemplo más extenso, vea [Cómo: obtener datos para un nodo integrado de SharePoint en el Explorador de servidores](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#11)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#11](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#11)]  
  
 En la tabla siguiente se enumera los tipos de objeto de datos para cada tipo de nodo integrado.  
  
|Tipo de nodo|Tipo de objeto de datos|  
|---------------|----------------------|  
|Nodo de sitio de SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|  
|Tipo de contenido|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|  
|Característica|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|  
|Campo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|  
|Lista|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|  
|Plantilla de lista|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|  
|Vista de lista (Microsoft.SharePoint.SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|  
|Asociación de flujo de trabajo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|  
|Plantilla de flujo de trabajo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|  
  
 Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad, vea [asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Extender el Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Cómo: Extender un nodo de SharePoint en el Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Cómo: agregar un nodo de SharePoint personalizado al explorador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Cómo: obtener datos para un nodo integrado de SharePoint en el Explorador de servidores](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)   
 [Asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Examinar las conexiones de SharePoint mediante el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Extender las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)  
  
  