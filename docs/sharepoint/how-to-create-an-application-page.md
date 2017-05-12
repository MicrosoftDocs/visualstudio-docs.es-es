---
title: "C&#243;mo: Crear una p&#225;gina de aplicaci&#243;n"
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
  - "páginas de aplicación [desarrollo de SharePoint en Visual Studio], agregar"
  - "páginas de aplicación [desarrollo de SharePoint en Visual Studio], crear"
ms.assetid: 9ad7044a-2fa7-4bba-8f25-b9f2cc1b7c6b
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# C&#243;mo: Crear una p&#225;gina de aplicaci&#243;n
  Puede crear una página Web ASP.NET para uno o más sitios de SharePoint.  En SharePoint, estas páginas se llaman páginas de aplicación.  A diferencia de una página de sitio, una página de aplicación contiene código subyacente.  Para obtener más información, vea [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### Para crear una página de aplicación  
  
1.  En Visual Studio, abra o cree un proyecto de SharePoint.  
  
     Para obtener más información, vea [Plantillas de proyecto y de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  En el **Explorador de soluciones**, elija el nodo del proyecto.  
  
3.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
4.  En el cuadro de diálogo de **Agregar nuevo elemento** , expanda el nodo de **sharepoint** y, a continuación el elemento de **2010** .  
  
5.  En la lista de plantillas de SharePoint, elija **Página de aplicación**.  
  
6.  En el cuadro de **Name** , especifique un nombre para la página de aplicación, y elija el botón de **Add** .  
  
     Visual Studio agrega varias carpetas y archivos al proyecto.  Para obtener más información sobre estos archivos, vea [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     En la vista de **Código** el diseñador de Visual Web developer, el archivo de paginación ASP.NET aparece.  Puede diseñar la página agregando controles de **Cuadro de herramientas** y ubicándolos en marcadores de posición de contenido.  Para obtener más información, vea [Vista Código fuente, Diseñador de páginas Web](http://msdn.microsoft.com/es-es/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Si desea controlar eventos de control, agregue código al archivo de código de la página de aplicación.  
  
     El archivo de código aparece si expande el nodo del archivo de paginación ASP.NET y tiene una extensión .cs o .vb, según el lenguaje del proyecto.  Para obtener un ejemplo de cómo crear una página de aplicación, vea [Tutorial: Crear una página de una aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## Vea también  
 [Mapa de contenido del entorno de desarrollo web de Visual Studio](http://msdn.microsoft.com/es-es/9c31f93b-c8fb-4599-9b14-6194ec8c7539)   
 [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Tutorial: Crear una página de una aplicación de SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  