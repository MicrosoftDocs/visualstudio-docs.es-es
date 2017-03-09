---
title: "Error de MSBuild MSB3123 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsCountExceedsMaximum"
helpviewer_keywords: 
  - "MSB3123"
ms.assetid: 343aa8a8-9ab9-4dd5-be59-8eccf1f3c012
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3123
**MSB3123: El número de asociaciones de archivo supera el límite de \< límite \>.**  
  
 Cada archivo sólo puede tener un número fijo de extensiones de nombre de archivo asociadas.  Este error se produce cuando se intentan asociar más extensiones de nombre de archivo que el número permitido por el sistema operativo de destino.  
  
### Para corregir este error  
  
-   Limite el número de asociaciones al número especificado.  
  
## Vea también  
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)