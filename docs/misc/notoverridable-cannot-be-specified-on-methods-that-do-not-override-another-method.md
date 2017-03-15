---
title: "&#39;NotOverridable&#39; no se puede especificar en m&#233;todos que no invalidan otro m&#233;todo | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31088"
  - "bc31088"
helpviewer_keywords: 
  - "BC31088"
ms.assetid: 0241197c-51fa-48b8-9a2a-4205d25641d3
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;NotOverridable&#39; no se puede especificar en m&#233;todos que no invalidan otro m&#233;todo
Las propiedades y los métodos son `NotOverridable` de forma predeterminada. El modificador `NotOverridable` solo puede usarse en métodos que invalidan otra propiedad u otro método.  
  
 **Identificador de error:** BC31088  
  
### Para corregir este error  
  
-   Quite el modificador`NotOverridable` de las propiedades y los métodos que no invalidan otro miembro.  
  
## Vea también  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)