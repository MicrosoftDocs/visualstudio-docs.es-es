---
title: "C&#243;mo: Agregar una referencia de salida del proyecto"
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
  - "referencias de salida del proyecto [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, herramientas para paquetes avanzadas"
  - "desarrollo de SharePoint en Visual Studio, referencias de salida del proyecto"
ms.assetid: 9d6bc25e-bf0d-4483-a691-2ad7a796fa80
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: Agregar una referencia de salida del proyecto
  Para implementar ensamblados de proyectos que no sean de SharePoint \(o archivos .xap de proyectos de Silverlight\) en SharePoint, agréguelos como referencias de salida del proyecto.  
  
 Este proceso crea una dependencia de compilación de soluciones entre los dos proyectos.  Los proyectos asociados con las referencias de salida del proyecto se compilan antes de que el proyecto de SharePoint se compile y se implemente.  
  
### Para agregar una referencia de salida del proyecto  
  
1.  Cargue una solución que contenga al menos un proyecto de SharePoint y un proyecto que no sea de SharePoint.  
  
2.  En **Explorador de soluciones**, elija un elemento del nodo de proyecto de SharePoint.  
  
3.  En la ventana de **Propiedades** , elija la propiedad de **Referencias de salida del proyecto** , y elija el botón de puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](~/docs/sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")\) situado junto a.  
  
4.  En el cuadro de diálogo de **Referencias de salida del proyecto** , elija el botón de **Add** .  
  
5.  En el panel propiedades, elija la flecha situada junto a la propiedad de **Tipo de implementación** , y elija un valor adecuado para el elemento de no de SharePoint que se hace referencia, por ejemplo **ElementFile**.  
  
6.  Elija la flecha situada junto a **Nombre de proyecto**, elija el nombre del elemento de proyecto de no de SharePoint, y elija el botón de **Aceptar** .  
  
## Vea también  
 [Proporcionar información de empaquetado e implementación en los elementos del proyecto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Cómo: Marcar los controles como seguros](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  