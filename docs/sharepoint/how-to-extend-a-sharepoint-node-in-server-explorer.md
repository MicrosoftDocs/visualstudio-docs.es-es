---
title: 'Cómo: extender un nodo de SharePoint en Explorador de servidores | Microsoft Docs'
description: Aprenda a extender un nodo de SharePoint en Explorador de servidores mediante el nodo conexiones de SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4983930a7c16edef826a5912abf0870598b1f906
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943801"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Cómo: extender un nodo de SharePoint en Explorador de servidores
  Puede extender los nodos en el nodo **conexiones de SharePoint** en **Explorador de servidores**. Esto resulta útil si desea agregar nuevos nodos secundarios, elementos de menú contextual o propiedades a un nodo existente. Para obtener más información, vea [Extensión del nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Para extender un nodo de SharePoint en Explorador de servidores

1. Cree un proyecto de biblioteca de clases.

2. Agregue referencias a los siguientes ensamblados:

    - Microsoft.VisualStudio.SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System.ComponentModel.Composition

3. Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.

4. Agregue el atributo <xref:System.ComponentModel.Composition.ExportAttribute> a la clase. Este atributo permite a Visual Studio detectar y cargar la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementación. Pase el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo al constructor de atributo.

5. Agregue el atributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> a la clase. Este atributo especifica el identificador de cadena para el tipo de nodo que desea extender.

     Para especificar los tipos de nodos integrados que proporciona Visual Studio, pase uno de los siguientes valores de enumeración al constructor de atributo:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Use estos valores para especificar los nodos de conexión de sitio (los nodos que muestran direcciones URL de sitio), los nodos de sitio o todos los demás nodos primarios de **Explorador de servidores**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Use estos valores para especificar uno de los nodos integrados que representan un componente individual en un sitio de SharePoint, como un nodo que representa una lista, un campo o un tipo de contenido.

6. En la implementación del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> método, use los miembros del parámetro *NodeType* para agregar características al nodo. Este parámetro es un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> objeto que proporciona acceso a los eventos definidos en la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfaz. Por ejemplo, puede controlar los siguientes eventos:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Controle este evento para agregar nuevos nodos secundarios al nodo. Para obtener más información, consulte [Cómo: agregar un nodo de SharePoint personalizado a explorador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Controle este evento para agregar un elemento de menú contextual personalizado al nodo.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Controle este evento para agregar propiedades personalizadas al nodo. Las propiedades aparecen en la ventana **propiedades** cuando se selecciona el nodo.

## <a name="example"></a>Ejemplo
 En el ejemplo de código siguiente se muestra cómo crear dos tipos diferentes de extensiones de nodo:

- Extensión que agrega un elemento de menú contextual a los nodos del sitio de SharePoint. Al hacer clic en el elemento de menú, se muestra el nombre del nodo en el que se hizo clic.

- Una extensión que agrega una propiedad personalizada denominada **ContosoExampleProperty** a cada nodo que representa un campo denominado **Body**.

  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]

  Esta extensión agrega una propiedad de cadena editable a los nodos. También puede crear propiedades personalizadas que muestren datos de solo lectura desde el servidor de SharePoint. Para obtener un ejemplo en el que se muestra cómo hacerlo, vea [Tutorial: extender explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="compile-the-code"></a>Compilar el código
 Este ejemplo requiere referencias a los ensamblados siguientes:

- Microsoft.VisualStudio.SharePoint

- Microsoft. VisualStudio. SharePoint. Explorer. Extensions

- System.ComponentModel.Composition

- System.Windows.Forms

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión de **Explorador de servidores** , cree un [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vea también
- [Cómo: agregar un nodo de SharePoint personalizado a Explorador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Extensión del nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Tutorial: extender Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Asociar datos personalizados con las extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
