---
title: Extender el nodo conexiones de SharePoint en Explorador de servidores | Microsoft Docs
titleSuffix: ''
description: Extienda el nodo conexiones de SharePoint en la ventana Explorador de servidores de Visual Studio. Agregar propiedades personalizadas a los nodos. Obtener datos para nodos integrados.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1f77e0044b8ae3c7456a31bb9c9153ba9e9f4c99
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218040"
---
# <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Extensión del nodo Conexiones de SharePoint en el Explorador de servidores
  En Visual Studio, puede conectarse a los sitios locales de SharePoint en el equipo de desarrollo mediante el nodo **conexiones de SharePoint** de la ventana de **Explorador de servidores** . Este nodo muestra muchos de los componentes de los sitios locales de SharePoint en una vista de árbol jerárquica. Por ejemplo, puede ver las listas, las bibliotecas de documentos y los tipos de contenido en los sitios locales. Para obtener más información acerca del uso de **Explorador de servidores** para conectarse a sitios locales de SharePoint, consulte [examinar conexiones de SharePoint mediante explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md).

 Puede extender el nodo **conexiones de SharePoint** mediante la creación de extensiones para nodos existentes o mediante la creación de un tipo de nodo personalizado y su adición a la jerarquía de nodos.

## <a name="tasks-for-extending-the-sharepoint-connections-node"></a>Tareas para extender el nodo conexiones de SharePoint
 Para extender un nodo existente, cree una extensión de Visual Studio que implemente la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaz. Al extender un nodo, puede Agregar funcionalidad al nodo, como sus propios elementos de menú contextual o propiedades personalizadas. Para obtener más información, consulte [Cómo: extender un nodo de SharePoint en explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

 Para crear un tipo de nodo personalizado, cree una extensión de Visual Studio que implemente la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> interfaz. Cree un nodo personalizado si desea mostrar los componentes de los sitios de SharePoint que no se muestran en **Explorador de servidores** de forma predeterminada. Por ejemplo, **Explorador de servidores** no muestra la galería de elementos Web de un sitio de SharePoint de forma predeterminada, pero puede Agregar un nodo personalizado que lo hace. Para obtener más información, consulte [Cómo: agregar un nodo de SharePoint personalizado a explorador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) y [tutorial: extender Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="add-custom-properties-to-nodes"></a>Agregar propiedades personalizadas a los nodos
 Al extender un nodo o crear un tipo de nodo personalizado, puede Agregar propiedades personalizadas al nodo. Las propiedades aparecen en la ventana **propiedades** cuando se selecciona el nodo.

 Hay dos tipos de propiedades personalizadas que se pueden agregar a un nodo:

- Propiedades que muestran un conjunto de datos de solo lectura del sitio de SharePoint. Los datos describen el componente de SharePoint que representa el nodo. Para ver un tutorial que muestra cómo hacerlo, vea [Tutorial: extender explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

- Propiedades que muestran datos personalizados de lectura/escritura. Para obtener un ejemplo de código que muestra cómo hacerlo, consulte [Cómo: extender un nodo de SharePoint en explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md).

## <a name="get-data-for-built-in-nodes"></a>Obtener datos para nodos integrados
 Todos los nodos integrados que proporciona Visual Studio incluyen algunos datos sobre el componente de SharePoint que representan. Por ejemplo, un nodo que representa una lista en el sitio de SharePoint proporciona algunos datos sobre la lista, como el título y la dirección URL de la vista predeterminada de la lista.

 Para obtener acceso a estos datos, recupere un objeto de datos de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode> objeto que representa el nodo en el que está interesado. El tipo del objeto de datos depende del tipo de nodo.

 En el ejemplo de código siguiente se muestra cómo obtener el objeto de datos para un nodo de lista. Para ver este ejemplo en el contexto de un ejemplo más grande, consulte [Cómo: obtener datos para un nodo integrado de SharePoint en explorador de servidores](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md).

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb" id="Snippet11":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs" id="Snippet11":::

 En la tabla siguiente se enumeran los tipos de objetos de datos para cada tipo de nodo integrado.

|Tipo de nodo|Tipo de objeto de datos|
|---------------|----------------------|
|Nodo de sitio de SharePoint|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerSiteNodeInfo>|
|Tipo de contenido|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IContentTypeNodeInfo>|
|Característica|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFeatureNodeInfo>|
|Campo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IFieldNodeInfo>|
|List|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListNodeInfo>|
|Lista de plantillas|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListTemplateNodeInfo>|
|Vista de lista (Microsoft. SharePoint. SPView)|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IListViewNodeInfo>|
|Asociación de flujo de trabajo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowAssociationNodeInfo>|
|Plantilla de flujo de trabajo|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.IWorkflowTemplateNodeInfo>|

 Para obtener más información sobre el uso de la <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> propiedad, vea [asociar datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).

## <a name="see-also"></a>Consulte también
- [Tutorial: extender Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Cómo: extender un nodo de SharePoint en Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Cómo: agregar un nodo de SharePoint personalizado a Explorador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Cómo: obtener datos para un nodo integrado de SharePoint en Explorador de servidores](../sharepoint/how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer.md)
- [Asociar datos personalizados con las extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
- [Examen de las conexiones de SharePoint mediante el Explorador de servidores](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Extensión de las herramientas de SharePoint en Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
