---
title: 'Cómo: Extender un nodo de SharePoint en el Explorador de servidores | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9522e793171500b7b7f0a356eff63947fdba84cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Cómo: Extender un nodo de SharePoint en el Explorador de servidores
  Puede extender los nodos en el **las conexiones de SharePoint** nodo **Explorador de servidores**. Esto es útil cuando desea agregar nuevos nodos secundarios, elementos de menú contextual o propiedades a un nodo existente. Para obtener más información, consulte [extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Para extender un nodo de SharePoint en el Explorador de servidores  
  
1.  Cree un proyecto de biblioteca de clases.  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
4.  Agregue el <xref:System.ComponentModel.Composition.ExportAttribute> a la clase de atributo. Este atributo permite que Visual Studio detecte y cargue el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementación. Pasar el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo al constructor de atributo.  
  
5.  Agregue el <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> a la clase de atributo. Este atributo especifica el identificador de cadena para el tipo de nodo que desea extender.  
  
     Para especificar los tipos de nodos integrados proporcionados por Visual Studio, pase uno de los siguientes valores de enumeración al constructor de atributo:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Use estos valores para especificar los nodos de conexión del sitio (los nodos que se muestran las direcciones URL del sitio), nodos de sitio o todos los otros nodos primarios del **Explorador de servidores**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Se usa estos valores para especificar uno de los nodos integrados que representan un componente individual de un sitio de SharePoint, como un nodo que representa una lista, campo o tipo de contenido.  
  
6.  En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> método, los miembros del uso de la *nodeType* parámetro para agregar características al nodo. Este parámetro es un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> objeto que proporciona acceso a los eventos definidos en el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfaz. Por ejemplo, puede administrar los siguientes eventos:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Controlar este evento para agregar nuevos nodos secundarios al nodo. Para obtener más información, consulte [Cómo: agregar un nodo de SharePoint personalizado al explorador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Controlar este evento para agregar un elemento de menú contextual personalizado al nodo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Controlar este evento para agregar propiedades personalizadas al nodo. Las propiedades aparecen en la **propiedades** ventana cuando se selecciona el nodo.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra cómo crear dos tipos diferentes de extensiones de nodo:  
  
-   Una extensión que agrega un elemento de menú contextual a los nodos de sitio de SharePoint. Al hacer clic en el elemento de menú, muestra el nombre del nodo que se ha hecho clic.  
  
-   Una extensión que agrega una propiedad personalizada denominada **ContosoExampleProperty** a cada nodo que representa un campo denominado **cuerpo**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]  
  
 Esta extensión agrega una propiedad de cadena modificable a los nodos. También puede crear propiedades personalizadas que muestran datos de solo lectura desde el servidor de SharePoint. Para obtener un ejemplo que muestra cómo hacerlo, consulte [Tutorial: Extender el Explorador de servidores para mostrar elementos de Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## <a name="compiling-the-code"></a>Compilar el código  
 Este ejemplo requiere referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## <a name="deploying-the-extension"></a>Implementar la extensión  
 Para implementar la **Explorador de servidores** extensión, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, consulte [extensiones de implementación para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar un nodo de SharePoint personalizado al explorador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Tutorial: Extender el Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Asociación de datos personalizados con extensiones de herramientas de SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  