---
title: "Associating Custom Data with SharePoint Tools Extensions | Microsoft Docs"
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
  - "projects [SharePoint development in Visual Studio], associating custom data"
  - "project items [SharePoint development in Visual Studio], associating custom data"
  - "SharePoint project items, associating custom data"
  - "SharePoint projects, associating custom data"
  - "SharePoint development in Visual Studio, extensibility features"
ms.assetid: cfc87272-85a1-4c36-89e4-2662417d59ea
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Associating Custom Data with SharePoint Tools Extensions
  Puede agregar datos personalizados a ciertos objetos en las extensiones de herramientas de SharePoint.  Esto es útil cuando se tienen datos en una parte de la extensión a la que desea tener acceso más adelante desde otro código de la extensión.  En lugar de implementar una manera personalizada para almacenar y tener acceso a los datos, puede asociar los datos a un objeto de la extensión y recuperar después los datos del mismo objeto.  
  
 Agregar datos personalizados a los objetos también es útil cuando se desea conservar datos pertinentes para un elemento específico en Visual Studio.  Las extensiones de herramientas de SharePoint simplemente se cargan una vez en Visual Studio, de modo que la extensión podría funcionar en cualquier momento con varios elementos diferentes \(como proyectos, elementos de proyecto o nodos **Server Explorer**\).  Si tiene datos personalizados que solo atañen a un elemento específico, puede agregarlos al objeto que representa ese elemento.  
  
 Al agregar datos personalizados a los objetos de las extensiones de herramientas de SharePoint, los datos no se conservan.  Los datos están disponibles solo durante la vida útil del objeto.  Una vez que el objeto es reclamado por la recolección de elementos no utilizados, se pierden los datos.  
  
 En las extensiones del sistema de proyectos de SharePoint, también puede guardar los datos de cadena que se conservan una vez descargada una extensión.  Para obtener más información, vea [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Objetos que pueden contener datos personalizados  
 Puede agregar datos personalizados a cualquier objeto del modelo de objetos de herramientas de SharePoint que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>.  Esta interfaz define solo una propiedad, <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A>, que es una colección de objetos de datos personalizados.  Los tipos siguientes implementan <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMappedFolder>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IMenuItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectMember>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentContext>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNode>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType>  
  
-   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeDefinition>  
  
## Agregar y recuperar datos personalizados  
 Para agregar datos personalizados a un objeto de extensión de herramientas de SharePoint, obtenga la propiedad <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> del objeto al que desea agregar los datos y utilice el método <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.Add%2A> para agregar los datos al objeto.  
  
 Para recuperar datos personalizados de un objeto de una extensión de herramientas de SharePoint, obtenga la propiedad <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> del objeto y utilice uno de los métodos siguientes:  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.TryGetValue%2A>.  Este método devuelve **true** si existe el objeto de datos, o **false** si no existe.  Puede utilizar este método para recuperar instancias de tipos de valor o tipos de referencia.  
  
-   <xref:Microsoft.VisualStudio.SharePoint.IAnnotationDictionary.GetValue%2A>.  Este método devuelve el objeto de datos si existe o **null** si no existe.  Solo puede utilizar este método para recuperar instancias de tipos de referencia.  
  
 En el siguiente ejemplo de código se determina si un objeto de datos concreto ya está asociado a un elemento de proyecto.  Si el objeto de datos aún no está asociado al elemento de proyecto, el código agrega el objeto a la propiedad <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject.Annotations%2A> del elemento de proyecto.  Para consultar este ejemplo en el contexto de un ejemplo mayor, vea [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#13)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#13](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#13)]  
  
## Vea también  
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)   
 [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)  
  
  