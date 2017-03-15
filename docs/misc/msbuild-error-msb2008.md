---
title: "Error de MSBuild MSB2008 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.UnrecognizedChildElement"
helpviewer_keywords: 
  - "MSB2008"
ms.assetid: 3c2afda0-a116-4b2f-af0c-c0f0d1541325
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB2008
**El sistema de proyectos de Visual Studio no puede convertir proyectos de "{0}".  Solo se puede usar para convertir proyectos de cliente de C\# y VB.**  
  
 Solo se pueden convertir proyectos válidos de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] utilizando [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
### Para corregir este error  
  
-   Si el proyecto es de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], compruebe si el archivo de proyecto se ha modificado o está dañado.  Si se ha modificado o dañado, abra el proyecto en la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en que se creó, guárdelo y, a continuación, intente convertirlo de nuevo.  
  
-   Si el proyecto no es de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], utilice la herramienta adecuada para convertirlo.  
  
## Vea también  
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)