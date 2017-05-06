---
title: "C&#243;mo: Crear un elemento web de SharePoint"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "elementos web [desarrollo de SharePoint en Visual Studio], agregar"
  - "elementos web [desarrollo de SharePoint en Visual Studio], crear"
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# C&#243;mo: Crear un elemento web de SharePoint
  Puede crear y personalizar un elemento web agregando un elemento de **Elemento web** a cualquier proyecto de SharePoint y después editando el archivo de código del elemento web o utilizando un diseñador.  Para obtener más información, vea [Cómo: Crear un elemento web de SharePoint con un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### Para crear un elemento web de SharePoint  
  
1.  Cree o abra un proyecto de SharePoint.  
  
     Para obtener más información, vea [Plantillas de proyecto y de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Elija el nodo de proyecto de SharePoint en el **Explorador de soluciones** y, a continuación, elija **Proyecto**, **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento**, expanda el nodo **SharePoint** y, a continuación, elija el nodo **2010**.  
  
4.  En la lista de plantillas de SharePoint, elija **Elemento web**.  
  
5.  En el cuadro **Nombre**, especifique un nombre para el elemento web y, a continuación, elija el botón **Agregar**.  
  
     El elemento web aparece en el **Explorador de soluciones**.  Para obtener más información sobre los archivos que incluye un elemento web, vea [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  En el **Explorador de soluciones**, abra el archivo de código para el elemento web que acaba de crear.  
  
     Por ejemplo, si el nombre del elemento web es WebPart1, abra WebPart1.vb \(en Visual Basic\) o WebPart1.cs \(en C\#\).  
  
7.  En el archivo de código, agregue controles al método <xref:System.Web.UI.Control.CreateChildControls%2A>.  
  
     Para obtener un ejemplo, vea [Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## Vea también  
 [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Cómo: Crear un elemento web de SharePoint con un diseñador](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Tutorial: Crear un elemento web para SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Tutorial: Crear un elemento web para SharePoint mediante un diseñador](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  