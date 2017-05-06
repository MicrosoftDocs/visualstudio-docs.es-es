---
title: "How to: Extend a SharePoint Node in Server Explorer"
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
ms.assetid: 5e443950-12e6-40d1-864b-c384b6be4ce4
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# How to: Extend a SharePoint Node in Server Explorer
  Puede ampliar los nodos situados bajo el nodo **Conexiones de SharePoint** en el **Explorador de servidores**.  Esto es útil cuando se desea agregar nuevos nodos secundarios, elementos de menú contextual o propiedades a un nodo existente.  Para obtener más información, vea [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
### Para extender un nodo de SharePoint en el Explorador de servidores  
  
1.  Cree un proyecto de biblioteca de clases  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
    -   System.ComponentModel.Composition  
  
3.  Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  
  
4.  Agregue el atributo <xref:System.ComponentModel.Composition.ExportAttribute> a la clase.  Este atributo permite que Visual Studio detecte y cargue la implementación de <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.  Pase el tipo <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> al constructor del atributo.  
  
5.  Agregue el atributo <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> a la clase.  Este atributo especifica el identificador de cadena del tipo de nodo que desea extender.  
  
     Para especificar tipos de nodos integrados proporcionados por Visual Studio, pase uno de los valores de la enumeración siguiente al constructor del atributo:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: use estos valores para especificar los nodos de conexión del sitio \(los nodos en los que aparece la dirección URL del sitio\), los nodos de sitio o todos los otros nodos primarios del **Explorador de servidores**.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: utilice estos valores para especificar uno de los nodos integrados que representa un componente individual de un sitio de SharePoint, como un nodo que representa una lista, campo o tipo de contenido.  
  
6.  En la implementación del método <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A>, use los miembros del parámetro *nodeType* para agregar características al nodo.  Este parámetro es un objeto <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> que proporciona acceso a los eventos definidos en la interfaz <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents>.  Por ejemplo, puede controlar los eventos siguientes:  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: controle este evento para agregar los nuevos nodos secundarios al nodo.  Para obtener más información, vea [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: controle este evento para agregar un elemento de menú contextual personalizado al nodo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: controle este evento para agregar propiedades personalizadas al nodo.  Las propiedades aparecen en la ventana **Propiedades** cuando el nodo está seleccionado.  
  
## Ejemplo  
 En el siguiente ejemplo de código se muestra cómo crear dos tipos diferentes de extensiones de nodo:  
  
-   Una extensión que agrega un elemento de menú contextual a los nodos de sitio de SharePoint.  Al hacer clic en el elemento de menú, se muestra el nombre del nodo en el que se hizo clic.  
  
-   Una extensión que agrega una propiedad personalizada denominada **ContosoExampleProperty** a cada nodo que representa un campo denominado **Body**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/serverexplorerextension.cs#9)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/serverexplorerextension.vb#9)]  
  
 Esta extensión agrega una propiedad de cadena modificable a los nodos.  También puede crear propiedades personalizadas que muestran los datos de solo lectura del servidor de SharePoint.  Para obtener un ejemplo de cómo hacerlo, vea [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
## Compilar el código  
 Para este ejemplo se requieren referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions  
  
-   System.ComponentModel.Composition  
  
-   System.Windows.Forms  
  
## Implementar la extensión  
 Para implementar la extensión del **Explorador de servidores**, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado y el resto de archivos que desee distribuir con la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [How to: Add a Custom SharePoint Node to Server Explorer](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)  
  
  