---
title: "Error de MSBuild MSB3119 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationExtensionMissingLeadDot"
helpviewer_keywords: 
  - "MSB3119"
ms.assetid: 52d68b0e-01d4-436f-a96c-733fd20a8c04
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3119
**MSB3119: Las extensiones de asociación de archivo deben comenzar con un punto \(.\).**  
  
 Este error se produce cuando se configura una asociación de archivo y la extensión no se inicia con un punto \(.\).  
  
### Para corregir este error  
  
-   Establezca el atributo [Manifiesto de la implementación ClickOnce](../deployment/clickonce-deployment-manifest.md)`extension` en un valor que comience por un punto \(.\), por ejemplo, ".doc."  
  
## Vea también  
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)