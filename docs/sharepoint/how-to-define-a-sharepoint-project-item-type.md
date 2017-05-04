---
title: "How to: Define a SharePoint Project Item Type | Microsoft Docs"
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
  - "SharePoint project items, defining your own types"
  - "project items [SharePoint development in Visual Studio], defining your own types"
  - "SharePoint development in Visual Studio, defining new project item types"
ms.assetid: 18b56e7c-4efb-47a2-abfc-e9018ae38267
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# How to: Define a SharePoint Project Item Type
  Defina un tipo de elemento de proyecto cuando desee crear un elemento de proyecto personalizado de SharePoint.  Para obtener más información, vea [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
### Para definir un tipo de elemento de proyecto  
  
1.  Cree un proyecto de biblioteca de clases  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  
  
4.  Agregue a la clase los atributos siguientes:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Este atributo permite que Visual Studio detecte y cargue la implementación de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.  Pase el tipo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> al constructor del atributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  En una definición de tipo de elemento de proyecto, este atributo especifica el identificador de cadena del nuevo elemento.  Se recomienda usar el formato *nombre de compañía*.*nombre de característica* para garantizar que todos los elementos de proyecto tengan un nombre único.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemIconAttribute>.  Este atributo especifica el icono para mostrar de este elemento de proyecto en el **Explorador de soluciones**.  Este atributo es opcional; si no lo aplica a su clase, Visual Studio muestra un icono predeterminado para el elemento de proyecto.  Si establece este atributo, pase el nombre completo de un icono o mapa de bits que esté incrustado en el ensamblado.  
  
5.  En su implementación del método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A>, utilice miembros del parámetro *projectItemTypeDefinition* para definir el comportamiento del tipo de elemento de proyecto.  Este parámetro es un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition> que proporciona acceso a los eventos definidos en las interfaces <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>.  Para obtener acceso a una instancia concreta del tipo de elemento de proyecto, controle los eventos de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>, como <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## Ejemplo  
 En el ejemplo de código siguiente, se muestra cómo definir un tipo de elemento de proyecto simple.  Este tipo de elemento de proyecto escribe un mensaje en la **Ventana de salida** y en la ventana **Lista de errores** cuando un usuario agrega un elemento de proyecto de este tipo a un proyecto.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#2](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemtype.cs#2)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemtype.vb#2)]  
  
 En este ejemplo, se usa el servicio de proyecto de SharePoint para escribir el mensaje en la **Ventana de salida** y en la ventana **Lista de errores**.  Para obtener más información, vea [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilar el código  
 Para este ejemplo se requieren referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Implementar el elemento de proyecto  
 Para permitir que otros desarrolladores usen el elemento de proyecto, cree una plantilla de proyecto o una plantilla de elemento de proyecto.  Para obtener más información, vea [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
 Para implementar el elemento de proyecto, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado, la plantilla y cualquier otro archivo que desee distribuir con el elemento de proyecto.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Tutorial: Crear un elemento de proyecto de columna de sitio con una plantilla de proyecto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)   
 [How to: Add a Shortcut Menu Item to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)  
  
  