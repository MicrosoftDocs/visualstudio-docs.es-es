---
title: "How to: Add a Custom SharePoint Node to Server Explorer"
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
  - "SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer"
  - "SharePoint Connections [SharePoint development in Visual Studio], creating a new node type"
ms.assetid: b992a192-f926-45e6-9416-85ddfe1061d0
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# How to: Add a Custom SharePoint Node to Server Explorer
  Puede agregar nodos personalizados bajo el nodo **Conexiones de SharePoint** en el **Explorador de servidores**.  Esto es útil si desea mostrar los componentes de SharePoint que no se muestran de forma predeterminada en el **Explorador de servidores**.  Para obtener más información, vea [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
 Para agregar un nodo personalizado, primero cree una clase que lo defina.  A continuación, cree una extensión que agregue el nodo como elemento secundario a un nodo existente.  
  
### Para definir el nuevo nodo  
  
1.  Cree un proyecto de biblioteca de clases  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
    -   System.Drawing  
  
3.  Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  
  
4.  Agregue a la clase los atributos siguientes:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Este atributo permite que Visual Studio detecte y cargue la implementación de <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>.  Pase el tipo <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> al constructor del atributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute>.  En una definición de nodo, este atributo especifica el identificador de cadena del nuevo nodo.  Se recomienda utilizar el formato *nombre compañía*.*nombre nodo* para asegurarse de que todos los nodos tienen un identificador único.  
  
5.  En su implementación del método <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider.InitializeType%2A>, utilice miembros del parámetro *typeDefinition* para configurar el comportamiento del nuevo nodo.  Este parámetro es un objeto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition> que proporciona acceso a los eventos definidos en la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>.  
  
     En el ejemplo de código siguiente se muestra cómo definir un nuevo nodo.  En este ejemplo se supone que su proyecto contiene un icono denominado IconoNodoSecundarioPersonalizado como recurso incrustado.  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#6](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#6)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#6](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#6)]  
  
### Para agregar el nuevo nodo como elemento secundario de un nodo existente  
  
1.  En el mismo proyecto que la definición de nodo, cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
2.  Agregue el atributo <xref:System.ComponentModel.Composition.ExportAttribute> a la clase.  Este atributo permite que Visual Studio detecte y cargue la implementación de <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Pase el tipo <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> al constructor del atributo.  
  
3.  Agregue el atributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> a la clase.  En una extensión de nodo, este atributo especifica el identificador del tipo de nodo que desea extender.  
  
     Para especificar tipos de nodos integrados proporcionados por Visual Studio, pase uno de los valores de la enumeración siguiente al constructor del atributo:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: use estos valores para especificar los nodos de conexión del sitio \(los nodos en los que aparece la dirección URL del sitio\), los nodos de sitio o todos los otros nodos primarios del **Explorador de servidores**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: utilice estos valores para especificar uno de los nodos integrados que representa un componente individual de un sitio de SharePoint, como un nodo que representa una lista, campo o tipo de contenido.  
  
4.  En la implementación del método <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>, controle el evento <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested> del parámetro <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>.  
  
5.  En el controlador de eventos <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>, agregue el nuevo nodo a la colección de nodos secundarios del objeto <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeEventArgs.Node%2A> que expone el parámetro de argumentos de evento.  
  
     En el ejemplo de código siguiente se muestra cómo agregar el nuevo nodo como un elemento secundario del nodo de sitio de SharePoint en el **Explorador de servidores**.  
  
     [!code-csharp[SPExtensibility.ProjectSystemExtension.General#7](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#7)]
     [!code-vb[SPExtensibility.ProjectSystemExtension.General#7](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#7)]  
  
## Ejemplo completo  
 El ejemplo de código siguiente proporciona el código completo para definir un nodo simple y agregarlo como un elemento secundario del nodo de sitio de SharePoint en el **Explorador de servidores**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#5](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorernode.cs#5)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#5](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorernode.vb#5)]  
  
## Compilar el código  
 En este ejemplo se supone que su proyecto contiene un icono denominado IconoNodoSecundarioPersonalizado como recurso incrustado.  Para este ejemplo también son necesarias referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
-   System.Drawing  
  
## Implementar la extensión  
 Para implementar la extensión del **Explorador de servidores**, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado y el resto de archivos que desee distribuir con la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [How to: Extend a SharePoint Node in Server Explorer](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
  