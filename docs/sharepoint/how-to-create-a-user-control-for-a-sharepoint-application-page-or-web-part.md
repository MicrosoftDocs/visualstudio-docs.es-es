---
title: "C&#243;mo: Crear un control de usuario para una p&#225;gina de aplicaci&#243;n o elemento web de SharePoint"
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
  - "controles de usuario [desarrollo de SharePoint en Visual Studio], agregar"
  - "controles de usuario [desarrollo de SharePoint en Visual Studio], crear"
ms.assetid: 492ea376-7188-4b5a-a2eb-adc0e3f51484
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: Crear un control de usuario para una p&#225;gina de aplicaci&#243;n o elemento web de SharePoint
  Puede crear controles de usuario personalizados que proporcionan funcionalidad personalizada para la solución de SharePoint, y puede reutilizar esa funcionalidad dentro del proyecto.  Puede incluir controles de usuario en un elemento web o página de aplicación, agregar más controles ASP.NET y controles de SharePoint, así como definir propiedades y métodos para el control.  Para obtener más información sobre los controles de usuario, vea los [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) y [controles de usuario y controles de servidor en SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### Para crear un control de usuario para SharePoint  
  
1.  En Visual Studio, abra o cree un proyecto de SharePoint.  
  
     Vea [Plantillas de proyecto y de elementos de proyecto de SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  En el **Explorador de soluciones**, elija el nodo del proyecto.  
  
3.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
     Se abrirá el cuadro de diálogo **Agregar nuevo elemento**.  
  
4.  En el panel **Instalado**, elija el nodo **Office\/SharePoint**.  
  
5.  En la lista de plantillas de SharePoint, elija **Control de usuario \(solución de granja de servidores únicamente\)**.  
  
    > [!NOTE]  
    >  Los controles de usuario funcionan solo en soluciones de granja.  
  
6.  En el cuadro **Nombre**, especifique un nombre para el control de usuario y, a continuación, elija el botón **Agregar**.  
  
     Visual Studio agrega varias carpetas y archivos al proyecto.  Para obtener más información sobre estos archivos, vea [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     De forma predeterminada, el archivo de control de usuario aparece en la vista **Código fuente** del diseñador de Visual Web Developer.  En esta vista, puede modificar el marcador XML del control.  Puede cambiar a la vista **Diseño** si desea diseñar el control visualmente arrastrando los controles desde el **Cuadro de herramientas**.  Vea [NIB: Design View, Web Page Designer](http://msdn.microsoft.com/es-es/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Si desea controlar los eventos que se producen en el control, agregue código al archivo de código del control de usuario.  
  
     Este archivo aparece en el **Explorador de soluciones** bajo el archivo de control de usuario y tiene una extensión .cs o .vb, según el lenguaje del proyecto.  
  
## Vea también  
 [Crear controles reutilizables para elementos web o páginas de aplicación](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Crear páginas de aplicación para SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Crear elementos web para SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  