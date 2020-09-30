---
title: 'Cómo: agregar un nodo de SharePoint personalizado a Explorador de servidores | Microsoft Docs'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5a74c9c879df57a5ff6444626870ee9f021fb4e9
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584890"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Cómo: agregar un nodo de SharePoint personalizado a Explorador de servidores
  Puede agregar nodos personalizados en el nodo **conexiones de SharePoint** en **Explorador de servidores**. Esto resulta útil si desea mostrar componentes de SharePoint adicionales que no se muestran en **Explorador de servidores** de forma predeterminada. Para obtener más información, vea [Extensión del nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

 Para agregar un nodo personalizado, primero cree una clase que defina el nuevo nodo. A continuación, cree una extensión que agregue el nodo como elemento secundario de un nodo existente.

### <a name="to-define-the-new-node"></a>Para definir el nuevo nodo

1. Cree un proyecto de biblioteca de clases.

2. Agregue referencias a los siguientes ensamblados:

    - Microsoft.VisualStudio.SharePoint

    - Microsoft. VisualStudio. SharePoint. Explorer. Extensions

    - System.ComponentModel.Composition

    - System.Drawing

3. Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.

4. Agregue los siguientes atributos a la clase:

    - <xref:System.ComponentModel.Composition.ExportAttribute>. Este atributo permite a Visual Studio detectar y cargar la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> implementación. Pase el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> tipo al constructor de atributo.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. En una definición de nodo, este atributo especifica el identificador de cadena para el nuevo nodo. Se recomienda usar el formato nombre de la *compañía*. *nombre del nodo* para asegurarse de que todos los nodos tienen un identificador único.

5. En la implementación del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> método, use los miembros del parámetro *typeDefinition* para configurar el comportamiento del nuevo nodo. Este parámetro es un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> objeto que proporciona acceso a los eventos definidos en la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfaz.

     En el ejemplo de código siguiente se muestra cómo definir un nuevo nodo. En este ejemplo se da por supuesto que el proyecto contiene un icono denominado CustomChildNodeIcon como un recurso incrustado.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]

### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Para agregar el nuevo nodo como elemento secundario de un nodo existente

1. En el mismo proyecto que la definición de nodo, cree una clase que implemente la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaz.

2. Agregue el atributo <xref:System.ComponentModel.Composition.ExportAttribute> a la clase. Este atributo permite a Visual Studio detectar y cargar la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementación. Pase el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo al constructor de atributo.

3. Agregue el atributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> a la clase. En una extensión de nodo, este atributo especifica el identificador de cadena para el tipo de nodo que desea extender.

     Para especificar los tipos de nodos integrados que proporciona Visual Studio, pase uno de los siguientes valores de enumeración al constructor de atributo:

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Use estos valores para especificar los nodos de conexión de sitio (los nodos que muestran direcciones URL de sitio), los nodos de sitio o todos los demás nodos primarios de **Explorador de servidores**.

    - <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Use estos valores para especificar uno de los nodos integrados que representan un componente individual en un sitio de SharePoint, como un nodo que representa una lista, un campo o un tipo de contenido.

4. En la implementación del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> método, controle el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> evento del <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> parámetro.

5. En el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> controlador de eventos, agregue el nuevo nodo a la colección de nodos secundarios del <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> objeto expuesto por el parámetro de argumentos de evento.

     En el ejemplo de código siguiente se muestra cómo agregar el nuevo nodo como elemento secundario del nodo de sitio de SharePoint en **Explorador de servidores**.

     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]

## <a name="complete-example"></a>Ejemplo completo
 En el ejemplo de código siguiente se proporciona el código completo para definir un nodo simple y agregarlo como elemento secundario del nodo del sitio de SharePoint en **Explorador de servidores**.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]

## <a name="compiling-the-code"></a>Compilación del código
 En este ejemplo se da por supuesto que el proyecto contiene un icono denominado CustomChildNodeIcon como un recurso incrustado. En este ejemplo también se necesitan referencias a los siguientes ensamblados:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

- System.Drawing

## <a name="deploy-the-extension"></a>Implementar la extensión
 Para implementar la extensión de **Explorador de servidores** , cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y cualquier otro archivo que desee distribuir con la extensión. Para obtener más información, vea [deploy Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vea también
- [Extensión del nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Cómo: extender un nodo de SharePoint en Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [Tutorial: extender Explorador de servidores para mostrar elementos Web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
