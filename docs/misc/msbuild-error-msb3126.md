---
title: "Error de MSBuild MSB3126 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsNotInstalled"
helpviewer_keywords: 
  - "MSB3126"
ms.assetid: 0c92cbb6-9100-4433-8113-f2f3a1432243
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3126
**MSB3126: La aplicación usa asociaciones de archivo pero no está marcada para instalación.  No se pueden usar asociaciones de archivo para aplicaciones que no están instaladas, como aplicaciones hospedadas en un explorador web.**  
  
 Este error se produce cuando una aplicación se configura para utilizar asociaciones de archivo pero el modo de la instalación de la aplicación sólo está establecido como en línea.  Como las aplicaciones en línea se ejecutan normalmente en un explorador, las asociaciones de archivo no están disponibles.  
  
### Para corregir este error  
  
-   Establezca el **Modo y configuración de instalación** en **La aplicación también está disponible sin conexión \(se puede iniciar desde el menú Inicio\)**.  Para obtener más información, vea [Cómo: Especificar el modo de instalación en línea y sin conexión de ClickOnce](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md).  
  
## Vea también  
 [Panel Publicar, Diseñador de proyectos](../ide/reference/publish-page-project-designer.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)