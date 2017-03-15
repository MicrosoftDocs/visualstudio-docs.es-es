---
title: "Error de MSBuild MSB4135 | Microsoft Docs"
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
  - "MSB4135"
ms.assetid: 9192f772-ad13-42f7-b53f-c5e31846fa5f
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB4135
**MSB4135: Error al leer la información del conjunto de herramientas de la clave del Registro "'\<clave\>'" o una subclave. '  \<key\>'**  
  
 No se pudo leer la información del conjunto de herramientas personalizado definido en el Registro.  
  
### Para corregir este error  
  
-   Si ha definido un conjunto de herramientas personalizado en el Registro, asegúrese de que tiene un formato de Registro válido, que el nombre de `ToolsVersion` es correcto y que el valor de `MSBuildBinPath` o `MSBuildToolsPath` es correcto.  
  
## Vea también  
 [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Elemento Project \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)