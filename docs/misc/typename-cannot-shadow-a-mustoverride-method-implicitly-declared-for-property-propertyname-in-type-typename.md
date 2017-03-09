---
title: "&#39;&lt;typename&gt;&#39; no puede prevalecer sobre un m&#233;todo &#39;MustOverride&#39; declarado impl&#237;citamente para la propiedad &#39;&lt;propertyname&gt;&#39; en &lt;tipo&gt; &#39;&lt; typename &gt;&#39; | Microsoft Docs"
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
  - "bc31416"
  - "vbc31416"
helpviewer_keywords: 
  - "BC31416"
ms.assetid: a52aee3c-a19e-412d-bb91-ef1b79e8675f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; no puede prevalecer sobre un m&#233;todo &#39;MustOverride&#39; declarado impl&#237;citamente para la propiedad &#39;&lt;propertyname&gt;&#39; en &lt;tipo&gt; &#39;&lt; typename &gt;&#39;
El nombre de método especificado entra en conflicto con un método `MustOverride` generado implícitamente por una propiedad de la clase base. Por ejemplo, si declara una propiedad denominada `Prop1`, el compilador genera los procedimientos implícitos `get_Prop1` y `set_Prop1`.  
  
 **Identificador de error:** BC31416  
  
### Para corregir este error  
  
1.  Asigne al método un nombre único.  
  
2.  Quite el modificador `MustOverride` de la propiedad de la clase base.  
  
## Vea también  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)