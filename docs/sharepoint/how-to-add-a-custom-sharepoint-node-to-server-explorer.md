---
title: Procedimiento Agregar un nodo de SharePoint personalizado al explorador de servidores | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bc648abd1d8981bd5c64782bd094e40d507b4142
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937668"
---
# <a name="how-to-add-a-custom-sharepoint-node-to-server-explorer"></a>Procedimiento Agregar un nodo de SharePoint personalizado al explorador de servidores
  Puede agregar nodos personalizados bajo el **conexiones de SharePoint** nodo **Explorador de servidores**. Esto es útil cuando desea mostrar los componentes de SharePoint adicionales que no se muestran en **Explorador de servidores** de forma predeterminada. Para obtener más información, consulte [extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Para agregar un nodo personalizado, primero cree una clase que define el nuevo nodo. A continuación, cree una extensión que agrega el nodo como un elemento secundario de un nodo existente.  
  
### <a name="to-define-the-new-node"></a>Para definir el nuevo nodo  
  
1.  Cree un proyecto de biblioteca de clases.  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  
  
4.  Agregue los siguientes atributos a la clase:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>. Este atributo permite que Visual Studio detecte y cargue su <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> implementación. Pase el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> tipo al constructor del atributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>. En una definición de nodo, este atributo especifica el identificador de cadena para el nuevo nodo. Le recomendamos que use el formato *nombre de la compañía*. *nombre del nodo* para asegurarse de que todos los nodos tienen un identificador único.  
  
5.  En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A> método, los miembros del uso de la *typeDefinition* parámetro para configurar el comportamiento del nuevo nodo. Este parámetro es un <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> objeto que proporciona acceso a los eventos definidos en el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interfaz.  
  
     En el ejemplo de código siguiente se muestra cómo definir un nuevo nodo. En este ejemplo se da por supuesto que el proyecto contiene un icono denominado IconoNodoSecundarioPersonalizado como recurso incrustado.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#6)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#6)]  
  
### <a name="to-add-the-new-node-as-a-child-of-an-existing-node"></a>Para agregar el nuevo nodo como un elemento secundario de un nodo existente  
  
1.  En el mismo proyecto que la definición de nodo, cree una clase que implementa el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> interfaz.  
  
2.  Agregue el atributo <xref:System.ComponentModel.Composition.ExportAttribute> a la clase. Este atributo permite que Visual Studio detecte y cargue su <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementación. Pase el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo al constructor del atributo.  
  
3.  Agregue el atributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> a la clase. En una extensión de nodo, este atributo especifica el identificador de cadena para el tipo de nodo que desea extender.  
  
     Para especificar los tipos de nodo integradas proporcionados por Visual Studio, pase uno de los siguientes valores de enumeración al constructor del atributo:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Use estos valores para especificar los nodos de conexión de sitio (los nodos que muestran direcciones URL del sitio), nodos de sitio o todos los demás nodos primarios en **Explorador de servidores**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Use estos valores para especificar uno de los nodos integrados que representan un componente individual en un sitio de SharePoint, como un nodo que representa una lista, campo o tipo de contenido.  
  
4.  En la implementación de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> método, el identificador de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> eventos de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> parámetro.  
  
5.  En el <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> controlador de eventos, agregue el nuevo nodo a la colección de nodos secundarios de la <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> objeto expuesto por el parámetro de argumentos de evento.  
  
     En el ejemplo de código siguiente se muestra cómo agregar el nuevo nodo como un elemento secundario del nodo de sitio de SharePoint en **Explorador de servidores**.  
  
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#7)]
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#7)]  
  
## <a name="complete-example"></a>Ejemplo completo
 En el ejemplo de código siguiente se proporciona el código completo para definir un nodo simple y agregarlo como elemento secundario del nodo de sitio de SharePoint en **Explorador de servidores**.  
  
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorernode.vb#5)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorernode.cs#5)]  
  
## <a name="compiling-the-code"></a>Compilación del código  
 En este ejemplo se da por supuesto que el proyecto contiene un icono denominado IconoNodoSecundarioPersonalizado como recurso incrustado. Este ejemplo también requiere referencias a los ensamblados siguientes:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## <a name="deploy-the-extension"></a>Implementar la extensión  
 Para implementar el **Explorador de servidores** extensión, cree un [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] paquete de extensión (VSIX) para el ensamblado y otros archivos que desea distribuir con la extensión. Para obtener más información, consulte [implementen extensiones para las herramientas de SharePoint en Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Vea también
 [Extender el nodo Conexiones de SharePoint en el Explorador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Cómo: Extender un nodo de SharePoint en el Explorador de servidores](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Tutorial: Extender el Explorador de servidores para mostrar elementos web](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
