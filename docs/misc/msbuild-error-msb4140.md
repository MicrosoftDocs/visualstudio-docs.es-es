---
title: "Error de MSBuild MSB4140 | Microsoft Docs"
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
  - "MSB4140"
ms.assetid: 13546558-4ed4-44c2-89a6-f69a2b43ed07
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB4140
**MSB4140: La versión de herramientas predeterminada no se ha especificado en el Registro ni en el archivo de configuración.**  
  
 El proyecto no especifica un valor `ToolsVersion` predeterminado.  Por consiguiente, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] no sabe qué valor debe utilizar.  
  
### Para corregir este error  
  
-   Asegúrese de que hay un valor `DefaultToolsVersion` especificado en el Registro donde están definidos los conjuntos de herramientas, o en un archivo de configuración \(como msbuild.exe.config\).  
  
## Vea también  
 [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)