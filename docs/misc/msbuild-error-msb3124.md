---
title: "Error de MSBuild MSB3124 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GenerateManifest.FileAssociationsDuplicateExtensions"
helpviewer_keywords: 
  - "MSB3124"
ms.assetid: d8365103-aa9d-400e-9c24-0a43e2bfbd14
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3124
**MSB3124: Ya se ha creado una asociación de archivo para la extensión '\< nombre de extensión \>.'**  
  
 Este error se produce cuando se encuentra una extensión de asociación de archivo duplicada.  
  
### Para corregir este error  
  
-   Quite atributos [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)`extension` que no sean únicos.  Cada atributo enumerado de extensión del elemento \<asociación de archivo\> debe ser único.  
  
## Vea también  
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)