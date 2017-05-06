---
title: "How to: Create a SharePoint Project Item Extension"
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
  - "project items [SharePoint development in Visual Studio], extending"
  - "SharePoint project items, extending"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 163738b9-e25a-49c9-8f33-4b57a2da6b07
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# How to: Create a SharePoint Project Item Extension
  Cree una extensión de elemento de proyecto cuando desee agregar funcionalidad a un elemento de proyecto de SharePoint que ya se encuentra instalado en Visual Studio.  Para obtener más información, vea [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
### Para crear una extensión de elemento de proyecto  
  
1.  Cree un proyecto de biblioteca de clases  
  
2.  Agregue referencias a los siguientes ensamblados:  
  
    -   Microsoft.VisualStudio.SharePoint  
  
    -   System.ComponentModel.Composition  
  
3.  Cree una clase que implemente la interfaz <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  
  
4.  Agregue a la clase los atributos siguientes:  
  
    -   <xref:System.ComponentModel.Composition.ExportAttribute>.  Este atributo permite que Visual Studio detecte y cargue la implementación de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>.  Pase el tipo <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> al constructor del atributo.  
  
    -   <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>.  En una extensión de elemento de proyecto, este atributo identifica el elemento que desea extender.  Pase el identificador del elemento de proyecto al constructor del atributo.  Para obtener una lista de los id. de los elementos de proyecto incluidos en Visual Studio, vea [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
5.  En la implementación del método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A>, use los miembros del parámetro *projectItemType* para definir el comportamiento de la extensión.  Este parámetro es un objeto <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemType> que proporciona acceso a los eventos definidos en las interfaces <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFileEvents>.  Para obtener acceso a una instancia concreta del tipo de elemento de proyecto que va a extender, controle los eventos de <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents>, como <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> y <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemInitialized>.  
  
## Ejemplo  
 En el ejemplo de código siguiente se muestra cómo crear una extensión simple para el elemento de proyecto Receptor de eventos.  Cada vez que el usuario agrega un elemento de proyecto Receptor de eventos a un proyecto de SharePoint, esta extensión escribe un mensaje en la **Ventana de salida** y en la ventana **Lista de errores**.  
  
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#1](../snippets/csharp/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/cs/extension/projectitemextension.cs#1)]
 [!code-vb[SPExtensibility.ProjectSystemExtension.General#1](../snippets/visualbasic/VS_Snippets_OfficeSP/spextensibility.projectsystemextension.general/vb/extension/projectitemextension.vb#1)]  
  
 En este ejemplo, se usa el servicio de proyecto de SharePoint para escribir el mensaje en la **Ventana de salida** y en la ventana **Lista de errores**.  Para obtener más información, vea [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).  
  
## Compilar el código  
 Para este ejemplo se requieren referencias a los siguientes ensamblados:  
  
-   Microsoft.VisualStudio.SharePoint  
  
-   System.ComponentModel.Composition  
  
## Implementar la extensión  
 Para implementar la extensión, cree un paquete de extensión \(VSIX\) de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] para el ensamblado y el resto de archivos que desee distribuir con la extensión.  Para obtener más información, vea [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## Vea también  
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
  