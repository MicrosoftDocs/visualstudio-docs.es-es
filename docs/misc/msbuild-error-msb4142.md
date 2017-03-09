---
title: "Error de MSBuild MSB4142 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4142"
ms.assetid: 56121c76-f952-43d1-ba23-1d1792fef0bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB4142
**MSB4142: MSBuildToolsPath no tiene el mismo valor que MSBuildBinPath para ToolsVersion "\<x.x \>".**  
  
 La definición del conjunto de herramientas especifica valores diferentes para `MSBuildBinPath` y `MSBuildToolsPath`.  
  
### Para corregir este error  
  
-   Asegúrese de que los valores de `MSBuildBinPath` y `MSBuildToolsPath` son iguales en su definición del conjunto de herramientas.  
  
## Vea también  
 [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)