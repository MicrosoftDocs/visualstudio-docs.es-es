---
title: "Error de MSBuild MSB2006 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedElement"
helpviewer_keywords: 
  - "MSB2006"
ms.assetid: 89dc1b89-1621-46bc-9fe6-6d98cbcbebc8
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB2006
**El archivo de proyecto no contiene el elemento raíz \<{0}\>.**  
  
 El nombre del elemento raíz no se ha escrito correctamente o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] no lo reconoce.  
  
### Para corregir este error  
  
-   Compruebe si se ha escrito correctamente el nombre de elemento.  
  
-   Compruebe si el archivo de proyecto ha sido modificado o dañado.  Si se ha modificado o dañado, abra el proyecto en la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en que se creó, guárdelo y, a continuación, intente convertirlo de nuevo.  
  
## Vea también  
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Recursos adicionales](../msbuild/additional-msbuild-resources.md)