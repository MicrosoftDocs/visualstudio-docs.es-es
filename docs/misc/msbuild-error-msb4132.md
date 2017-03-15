---
title: "Error de MSBuild MSB4132 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4132"
ms.assetid: 4ac265a7-0f8d-4fec-ba6e-cd70cbd5d89e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB4132
**MSB4132: No se reconoce la versión de herramientas "'\<versión\>'".**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] encontró un conjunto de herramientas que corresponde al valor especificado de `ToolsVersion`.  
  
### Para corregir este error  
  
-   Especifique un valor válido para `ToolsVersion` en la etiqueta del proyecto o en la línea de comandos cuando utilice el modificador **\/ToolsVersion** de MSBuild.  
  
## Vea también  
 <xref:Microsoft.Build.Tasks.MSBuild.ToolsVersion%2A>   
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)