---
title: "Error de MSBuild MSB4133 | Microsoft Docs"
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
  - "MSB4133"
ms.assetid: 5f18937a-fda1-4315-81f9-7cee02802a6d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB4133
**MSB4133: Se ha especificado una versión de herramientas predeterminada "\<x.x.\>", pero no se pudo encontrar su definición.**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] no encuentra el conjunto de herramientas definido en el archivo de proyecto como `DefaultToolsVersion`.  
  
### Para corregir este error  
  
-   Asegúrese de que `DefaultToolsVersion` se especifica correctamente y que este conjunto de herramientas está definido en el Registro o en el archivo de configuración de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
## Vea también  
 <xref:Microsoft.Build.BuildEngine.Toolset>   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)