---
title: "Error de MSBuild MSB2009 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedAttribute"
helpviewer_keywords: 
  - "MSB2009"
ms.assetid: 34fd83b4-dead-49e5-b1ee-b23dc5a95244
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB2009
**El atributo '\< nombre de atributo\>' del elemento '\< nombre de elemento\>' no es válido.**  
  
 El nombre de atributo no se ha escrito correctamente o [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] no lo reconoce.  
  
### Para corregir este error  
  
-   Compruebe si se ha escrito correctamente el nombre de atributo.  
  
-   Compruebe si el archivo de proyecto ha sido modificado o dañado.  Si se ha modificado o dañado, abra el proyecto en la versión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en que se creó, guárdelo y, a continuación, intente convertirlo de nuevo.  
  
## Vea también  
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)