---
title: "Error de MSBuild MSB3187 | Microsoft Docs"
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
  - "MSBuild.GenerateManifest.PlatformMismatch"
helpviewer_keywords: 
  - "MSB3187"
ms.assetid: c5e93c14-b099-4176-bf1b-dbecc47fb3fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3187
**MSB3187: El ensamblado al que se hace referencia '\<ensamblado\>' se aplica a un procesador diferente del de la aplicación.**  
  
 Esta advertencia se genera cuando la plataforma de destino de la aplicación \(arquitectura del procesador\) está establecida en neutra \(MSIL\) y el ensamblado al que se hace referencia no es neutro, o bien, cuando la arquitectura de la plataforma no es neutra y la dependencia sí lo es.  Asimismo, si ambos dependen de la plataforma, su arquitectura debe coincidir.  Además, la arquitectura de la aplicación y la arquitectura del ensamblado de punto de entrada siempre deben coincidir.  
  
### Para corregir este error  
  
-   Asegúrese de que la plataforma de destino de la aplicación \(arquitectura del procesador\) coincida con todos los ensamblados a los que se haga referencia y la arquitectura del ensamblado de punto de entrada.  
  
## Vea también  
 [Configuración de compilador avanzada \(Cuadro de diálogo, Visual Basic\)](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md)   
 [Compilar \(Página, Diseñador de proyectos\) \(C\#\)](../ide/reference/build-page-project-designer-csharp.md)