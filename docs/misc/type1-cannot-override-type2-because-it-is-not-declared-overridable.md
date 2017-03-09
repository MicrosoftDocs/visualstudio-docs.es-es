---
title: "&#39;&lt;type1&gt;&#39; no puede reemplazar a &lt;type2&gt; porque no est&#225; declarado como &#39;Overridable&#39; | Microsoft Docs"
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
  - "bc31086"
  - "vbc31086"
helpviewer_keywords: 
  - "BC31086"
ms.assetid: ce071994-2e32-4460-a65d-f48f914386c6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;type1&gt;&#39; no puede reemplazar a &lt;type2&gt; porque no est&#225; declarado como &#39;Overridable&#39;
Un miembro de una clase derivada reemplaza un miembro de clase base que no está marcado con el modificador `Overridable`.  
  
 **Id. de error:** BC31086  
  
### Para corregir este error  
  
1.  Agregue el modificador `Overridable` al miembro reemplazado en la clase base.  
  
2.  Utilice la palabra clave `Shadows` para ocultar el elemento en la clase base.  
  
## Vea también  
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)