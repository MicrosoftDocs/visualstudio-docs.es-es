---
title: "Las variables locales que se encuentren dentro de m&#233;todos de estructuras no se pueden declarar &#39;Static&#39; | Microsoft Docs"
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
  - "vbc31400"
  - "bc31400"
helpviewer_keywords: 
  - "BC31400"
ms.assetid: 38b8adee-3593-40fb-b0a4-e2a47599567f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las variables locales que se encuentren dentro de m&#233;todos de estructuras no se pueden declarar &#39;Static&#39;
El modificador `Static` no se puede usar con variables locales en estructuras.  
  
 **Id. de error:** BC31400  
  
### Para corregir este error  
  
1.  Quite el modificador `Static` de la variable local.  
  
2.  Declare la variable como una variable estática con un ámbito más amplio.  
  
## Vea también  
 [Static](/dotnet/visual-basic/language-reference/modifiers/static)