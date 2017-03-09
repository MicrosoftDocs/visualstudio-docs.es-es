---
title: "&#39;System.ObsoleteAttribute&#39; no se puede aplicar a las definiciones &#39;AddHandler&#39;, &#39;RemoveHandler&#39; o &#39;RaiseEvent&#39; | Microsoft Docs"
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
  - "bc31142"
  - "vbc31142"
helpviewer_keywords: 
  - "BC31142"
ms.assetid: 2bddde2e-9ca0-4f72-8910-0789a6350af8
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.ObsoleteAttribute&#39; no se puede aplicar a las definiciones &#39;AddHandler&#39;, &#39;RemoveHandler&#39; o &#39;RaiseEvent&#39;
'System.ObsoleteAttribute' no se puede aplicar a las definiciones 'AddHandler', 'RemoveHandler' o 'RaiseEvent'. Si es necesario, aplique el atributo directamente al evento.  
  
 Un evento personalizado aplica <xref:System.ObsoleteAttribute> a su procedimiento `AddHandler`, `RemoveHandler` o `RaiseEvent`.  
  
 El atributo <xref:System.ObsoleteAttribute> marca un elemento de programación como que ya no se usa y notifica a los usuarios que el elemento se va a quitar de versiones futuras del producto.  
  
 No tiene sentido hacer que determinadas partes de un evento personalizado sigan estando en uso mientras otras han dejado de usarse.  
  
 **Identificador de error:** BC31142  
  
### Para corregir este error  
  
-   Quite el atributo <xref:System.ObsoleteAttribute> de la declaración de procedimiento individual y aplíquelo a la declaración de evento general.  
  
## Vea también  
 <xref:System.ObsoleteAttribute>   
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/addhandler-statement)   
 [RemoveHandler \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/removehandler-statement)   
 [RaiseEvent \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/raiseevent-statement)