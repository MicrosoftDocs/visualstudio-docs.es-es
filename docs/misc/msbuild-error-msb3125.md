---
title: "Error de MSBuild MSB3125 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsNoEntryPoint"
helpviewer_keywords: 
  - "MSB3125"
ms.assetid: f8a08b05-1946-4788-8577-ceefde785e95
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3125
**MSB3125: La aplicación usa asociaciones de archivo pero no tiene ningún parámetro de compilación EntryPoint.**  
  
 Este error se produce cuando no hay ningún parámetro de compilación EntryPoint.  Cuando se configura una aplicación para utilizar asociaciones de archivo, debe haber un parámetro de compilación entryPoint en el manifiesto de aplicación.  El elemento \< entryPoint \> identifica el ensamblado que se debería ejecutar cuando se ejecuta la aplicación.  
  
### Para corregir este error  
  
-   Establezca el [\<entryPoint\> \(Elemento\)](../deployment/entrypoint-element-clickonce-application.md) en un valor válido.  Para obtener más información, vea [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
## Vea también  
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)