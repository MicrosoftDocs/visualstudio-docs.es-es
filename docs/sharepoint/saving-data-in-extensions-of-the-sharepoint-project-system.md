---
title: "Saving Data in Extensions of the SharePoint Project System | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SharePoint project items, saving string data"
  - "project items [SharePoint development in Visual Studio], saving string data"
  - "projects [SharePoint development in Visual Studio], saving string data"
  - "SharePoint projects, saving string data"
ms.assetid: 903b9da7-2eea-404c-9a7a-7bc15cb90d6c
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Saving Data in Extensions of the SharePoint Project System
  Al extender el sistema de proyectos de SharePoint, puede guardar los datos de cadena que persisten después de cerrar un proyecto de SharePoint.  Los datos están normalmente asociados a un elemento de proyecto determinado o con el propio proyecto.  
  
 Si tiene datos que no es necesario conservar, puede agregarlos a cualquier objeto del modelo de objetos de herramientas de SharePoint que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.IAnnotatedObject>.  Para obtener más información, vea [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md).  
  
## Guardar los datos asociados a un elemento de proyecto  
 Cuando tiene datos asociados a un elemento de proyecto de SharePoint determinado, como el valor de una propiedad que se agrega a un elemento de proyecto, puede guardarlos en el archivo .spdata del elemento de proyecto.  Para hacerlo, use la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>.  Los datos que agrega a esta propiedad se guardan en el elemento **ExtensionData** en el archivo .spdata del elemento de proyecto.  Para obtener más información, vea [ExtensionData Element](../sharepoint/extensiondata-element.md).  
  
 En el siguiente ejemplo de código se muestra cómo usar la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> para guardar el valor de una propiedad de cadena que se define en un tipo de elemento de proyecto de SharePoint personalizado.  Para consultar este ejemplo en el contexto de un ejemplo mayor, vea [How to: Add a Property to a Custom SharePoint Project Item Type](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).  
  
 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/cs/extension/projectitemtypeproperty.cs#14)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#14](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectitemextension.menuandproperty/vb/extension/projectitemtypeproperty.vb#14)]  
  
## Guardar los datos asociados a un proyecto  
 Cuando tenga datos de nivel de proyecto, como el valor de una propiedad que se agrega a los proyectos de SharePoint, puede guardarlos en el archivo de proyecto \(archivo .csproj o .vbproj\) o en el archivo de opciones de usuario del proyecto \(el archivo .csproj.user o .vbproj.user\).  El archivo que elija para guardar los datos depende de cómo desea que se usen:  
  
-   Si desea que los datos estén disponibles para todos los desarrolladores que abran el proyecto de SharePoint, guárdelos en el archivo de proyecto.  Este archivo se protege siempre para las bases de datos de control de código fuente, por lo que los datos de este archivo están disponibles para otros desarrolladores que desprotejan el proyecto.  
  
-   Si desea que los datos estén disponibles únicamente para el programador actual que tiene abierto el proyecto de SharePoint en Visual Studio, guárdelos en el archivo de opciones de usuario del proyecto.  Este archivo no se suele proteger para las bases de datos de control de código fuente, por lo que los datos de este archivo no están disponibles para otros desarrolladores que desprotejan el proyecto.  
  
### Guardar datos en el archivo de proyecto  
 Para guardar los datos en el archivo de proyecto, convierta un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> en un objeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> y, a continuación, use el método <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A>.  En el ejemplo de código siguiente se muestra cómo usar este método para guardar el valor de una propiedad de proyecto en el archivo de proyecto.  Para consultar este ejemplo en el contexto de un ejemplo mayor, vea [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#3](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#3)]
 [!code-vb[SpExt_SPCustomPrjProperty#3](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#3)]  
  
 Para obtener más información sobre cómo convertir los objetos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> en otros tipos del modelo de objetos de automatización de Visual Studio o del modelo de objetos de integración, vea [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
### Guardar datos en el archivo de opciones de usuario del proyecto  
 Para guardar los datos en el archivo de opciones de usuario del proyecto, use la propiedad <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.ProjectUserFileData%2A> de un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>.  En el ejemplo de código siguiente se muestra cómo usar esta propiedad para guardar el valor de una propiedad de proyecto en el archivo de opciones de usuario del proyecto.  Para consultar este ejemplo en el contexto de un ejemplo mayor, vea [How to: Add a Property to SharePoint Projects](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).  
  
 [!code-csharp[SpExt_SPCustomPrjProperty#2](../snippets/csharp/VS_Snippets_OfficeSP/spext_spcustomprjproperty/cs/customspproperty/customproperty.cs#2)]
 [!code-vb[SpExt_SPCustomPrjProperty#2](../snippets/visualbasic/VS_Snippets_OfficeSP/spext_spcustomprjproperty/vb/customspproperty/customproperty.vb#2)]  
  
## Vea también  
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Associating Custom Data with SharePoint Tools Extensions](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)  
  
  