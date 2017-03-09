---
title: "Error de MSBuild MSB4141 | Microsoft Docs"
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
  - "MSB4141"
ms.assetid: 0d190884-e64d-4d6b-817d-ce4644788fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB4141
**MSB4141: No se ha especificado MSBuildToolsPath para el elemento ToolsVersion "\<x.x\>."**  
  
 Se ha definido un conjunto de herramientas personalizado pero no se ha especificado ningún valor para `MSBuildToolsPath`.  
  
### Para corregir este error  
  
-   Especifique un valor válido para `MSBuildToolsPath` cuando defina un conjunto de herramientas personalizado en el Registro o en el archivo de configuración de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## Vea también  
 [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)