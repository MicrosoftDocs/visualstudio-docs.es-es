---
title: "Extending the SharePoint Project System"
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
  - "SharePoint development in Visual Studio, extending projects"
  - "SharePoint development in Visual Studio, extending project items"
ms.assetid: 654b2973-a5c9-44be-a3d2-8bc3d15f9624
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Project System
  Puede crear soluciones de SharePoint mediante un conjunto de plantillas de proyecto y plantillas de elementos de Visual Studio.  Estas plantillas cumplen los requisitos de muchos escenarios de desarrollo, pero se pueden detectar casos donde no proporcionan funcionalidad que necesita.  En estos casos, puede extender el sistema de proyectos de SharePoint.  
  
## Información general del sistema de proyectos de SharePoint  
 El sistema de proyectos de SharePoint se basa en el componente fundamental que son los *elementos de proyecto de SharePoint*.  Un elemento de proyecto de SharePoint representa una personalización de SharePoint única, por ejemplo una definición de lista, elemento web o tipo de contenido.  
  
 Un proyecto de SharePoint es un proyecto de Visual Studio que incluye uno o varios elementos de proyecto de SharePoint.  Los proyectos de SharePoint también contienen componentes adicionales que definen cómo se agrupan los elementos de proyecto en características y paquetes para la implementación.  
  
 Para obtener más información sobre el contenido de los elementos de proyecto de SharePoint y los proyectos de SharePoint, vea [Creating Item Templates and Project Templates for SharePoint Project Items](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).  
  
## Cómo extender el sistema de proyectos de SharePoint  
 Puede extender el sistema de proyectos de SharePoint de las maneras siguientes:  
  
-   Puede definir sus propios tipos de elemento de proyecto de SharePoint y asociarlos con nuevas plantillas de elemento o de proyecto de Visual Studio.  Por ejemplo, puede definir un tipo de elemento de proyecto de SharePoint para crear una acción personalizada o un campo.  Para obtener más información, vea [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md).  
  
-   Puede extender los tipos de elemento de proyecto de SharePoint que ya están instalados en Visual Studio.  Por ejemplo, puede agregar un elemento de menú contextual a un elemento **Explorador de soluciones** el y personalizarlo cuando un desarrollador elige el elemento de menú.  Para obtener más información, vea [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md).  
  
-   Puede extender proyectos de SharePoint.  Por ejemplo, puede agregar controladores de eventos que realicen tareas concretas cuando se agregan o quitan elementos de los proyectos de SharePoint.  Para obtener más información, vea [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md).  
  
-   Puede extender el comportamiento de empaquetado e implementación de los elementos de proyecto y los proyectos de SharePoint.  Por ejemplo, puede crear pasos de implementación que se ejecuten cuando implementa o retracta un proyecto, o llevar a cabo tareas personalizadas adicionales cuando Visual Studio ejecute ciertos pasos de implementación.  Para obtener más información, vea [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md).  
  
## Tareas comunes de desarrollo  
 Puede realizar las siguientes tareas comunes en las extensiones del sistema de proyectos de SharePoint:  
  
-   Guardar los datos de cadena personalizados con los elementos de proyecto y en varios tipos de archivos de proyecto.  Para obtener más información, vea [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
-   Convertir un objeto del sistema de proyectos de SharePoint en un objeto correspondiente del modelo de objetos de automatización de Visual Studio o del modelo de objetos de integración, y viceversa.  Para obtener más información, vea [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).  
  
## Vea también  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Extending SharePoint Project Items](../sharepoint/extending-sharepoint-project-items.md)   
 [Extending SharePoint Projects](../sharepoint/extending-sharepoint-projects.md)   
 [Extending SharePoint Packaging and Deployment](../sharepoint/extending-sharepoint-packaging-and-deployment.md)   
 [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)   
 [Converting Between SharePoint Project System Types and Other Visual Studio Project Types](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)  
  
  