---
title: "Manifiestos de implementaci&#243;n y aplicaci&#243;n en soluciones de Office | Microsoft Docs"
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
  - "manifiestos [desarrollo de Office en Visual Studio]"
  - "manifiestos de implementación [desarrollo de Office en Visual Studio]"
  - "manifiestos de aplicación [desarrollo de Office en Visual Studio]"
  - "ensamblados [desarrollo de Office en Visual Studio], actualizar"
ms.assetid: 4e9abc7c-ef9f-4cb2-a7a9-c95c5f4a1fb7
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Manifiestos de implementaci&#243;n y aplicaci&#243;n en soluciones de Office
  Un manifiesto de aplicación es un archivo XML que proporciona información que utiliza una solución de Office para buscar y actualizar sus ensamblados. Un manifiesto de aplicación puede utilizarse con un manifiesto de implementación, que es un archivo XML almacenado en el servidor que proporciona la información necesaria para encontrar la versión más reciente del manifiesto de aplicación y de los ensamblados.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Estructura de manifiesto para soluciones de Office  
 Para las soluciones de Microsoft Office creadas con las herramientas de desarrollo de Office en Visual Studio, todos los manifiestos se basan en el esquema estándar de ClickOnce. Al implementar sus soluciones de Office, los manifiestos de aplicación de nivel de documento y de proyectos de complementos VSTO se encuentran en la caché de ClickOnce. Los manifiestos de implementación no se copian en el equipo cliente.  
  
 Para obtener información sobre el contenido de los manifiestos de aplicación e implementación de los proyectos de Office, consulte [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md) y [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
## Crear manifiestos de aplicación e implementación  
 Los manifiestos de aplicación se crean automáticamente como parte del proceso de compilación. Cada vez que compila un proyecto de nivel de documento, la ubicación del manifiesto de implementación se incrusta en el documento como una propiedad de documento personalizada. Para los complementos VSTO, la ubicación del manifiesto de implementación se almacena en el registro.  
  
 Para obtener más información acerca del **Asistente de publicación**, consulte [Implementar una solución de Office mediante ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Para obtener más información sobre cómo funcionan los manifiestos con las soluciones de Office, consulte [Implementar una solución de Office](../vsto/deploying-an-office-solution.md).  
  
## Vea también  
 [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)   
 [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Manifiestos de aplicación para soluciones de Office](../vsto/application-manifests-for-office-solutions.md)   
 [Manifiestos de implementación para soluciones de Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)  
  
  