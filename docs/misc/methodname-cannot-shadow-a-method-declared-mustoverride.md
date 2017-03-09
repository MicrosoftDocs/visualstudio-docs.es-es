---
title: "&#39;&lt;methodname&gt;&#39; no puede prevalecer sobre un m&#233;todo declarado como &#39;MustOverride&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31404"
  - "bc31404"
helpviewer_keywords: 
  - "BC31404"
ms.assetid: 3e7bb4a0-14af-46ba-bc62-2234c16f1827
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;methodname&gt;&#39; no puede prevalecer sobre un m&#233;todo declarado como &#39;MustOverride&#39;.
Una propiedad o método con el modificador `MustOverride` y el mismo nombre se declara en una clase derivada.  
  
 **Identificador de error:** BC31404  
  
### Para corregir este error  
  
1.  Agregue el modificador `Overrides` a la propiedad o método de reemplazo en la clase derivada.  
  
2.  Quite el modificador `MustOverride` de la propiedad o método en la clase base.  
  
## Vea también  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)