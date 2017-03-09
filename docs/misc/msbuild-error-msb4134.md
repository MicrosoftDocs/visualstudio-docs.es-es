---
title: "Error de MSBuild MSB4134 | Microsoft Docs"
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
  - "MSB4134"
ms.assetid: 2e4e6beb-c0c9-40ef-b75c-1c16244eba10
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB4134
**MSB4134: DefaultToolsVersion no se puede establecer una vez cargado un proyecto en el motor.**  
  
 Este error se produce cuando se intenta cambiar el valor de `DefaultToolsVersion` después de que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] haya compilado un proyecto.  
  
### Para corregir este error  
  
-   Cambie el valor de `DefaultToolsVersion` antes de compilar un proyecto.  
  
## Vea también  
 <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>   
 <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)