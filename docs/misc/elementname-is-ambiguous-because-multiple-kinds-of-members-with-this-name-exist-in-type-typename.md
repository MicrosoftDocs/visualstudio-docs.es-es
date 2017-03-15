---
title: "&#39;&lt;nombreElemento&gt;&#39; es ambiguo porque existen varios tipos de miembros con este nombre en e. &lt;tipo&gt; &#39;&lt;nombreTipo&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31429"
  - "vbc31429"
helpviewer_keywords: 
  - "BC31429"
ms.assetid: fdc92c16-934d-47c0-9c44-332cbd58b73b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreElemento&gt;&#39; es ambiguo porque existen varios tipos de miembros con este nombre en e. &lt;tipo&gt; &#39;&lt;nombreTipo&gt;&#39;.
Una expresión obtiene acceso a un elemento de programación definido en una clase, estructura, módulo o interfaz que contiene más de un miembro con el mismo nombre.  
  
 La causa más probable de este error es la *distinción de mayúsculas y minúsculas*. Los nombres de Visual Basic no distinguen mayúsculas y minúsculas, lo que significa que pueden aparecer de forma diferente en distintos lugares del código. Por ejemplo, si define una variable con el nombre `XYZ` y posteriormente accede a ella como `xyz`, el compilador considera equivalentes los dos nombres.  
  
 Sin embargo, otros lenguajes, como [C\#](/dotnet/csharp/csharp) y [Visual C\+\+](/visual-cpp/top/visual-cpp-in-visual-studio-2015), distinguen mayúsculas y minúsculas. En estos lenguajes, `XYZ` y `xyz` no se consideran el mismo nombre. Por lo tanto, una clase escrita en este tipo de lenguaje podría definir una variable denominada `XYZ` y una propiedad denominada `xyz`. Common Language Runtime \(CLR\) conserva la distinción de mayúsculas y minúsculas en los ensamblados. Sin embargo, si una aplicación de Visual Basic, tiene acceso a un ensamblado con los nombres `XYZ` y `xyz`, aparecen como el mismo nombre.  
  
 **Identificador de error:** BC31429  
  
### Para corregir este error  
  
1.  Si tiene control sobre el código fuente del tipo de definición, considere la posibilidad de cambiar el nombre de los miembros para que se diferencien por algo más que las mayúsculas y minúsculas. Puede que esto no sea posible si el tipo de definición ya se ha publicado y otras aplicaciones lo están usando.  
  
2.  Si no se puede cambiar el nombre de los miembros en el tipo de definición, elimine el elemento de programación citado del código. No se puede tener acceso a un elemento que parece en Visual Basic que tiene varias definiciones.  
  
## Vea también  
 [Nombres de elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Solucionar problemas de variables](/dotnet/visual-basic/programming-guide/language-features/variables/troubleshooting-variables)   
 [Common Language Runtime](../Topic/Common%20Language%20Runtime%20\(CLR\).md)