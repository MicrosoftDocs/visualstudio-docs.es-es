---
title: "&#39;&lt;nombreDeClase1&gt;&#39; no puede heredar de &lt;tipo&gt; &#39;&lt;nombreDeClase2&gt;&#39; porque &#39;&lt;nombreDeClase2&gt;&#39; se declar&#243; como &#39;NotInheritable&#39; | Microsoft Docs"
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
  - "vbc30299"
  - "bc30299"
helpviewer_keywords: 
  - "BC30299"
ms.assetid: 627d50f5-9e75-495d-93f7-50096ba2ea08
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeClase1&gt;&#39; no puede heredar de &lt;tipo&gt; &#39;&lt;nombreDeClase2&gt;&#39; porque &#39;&lt;nombreDeClase2&gt;&#39; se declar&#243; como &#39;NotInheritable&#39;
Una clase intenta heredar de otra clase, pero la clase base deseada se especificó como `NotInheritable`. Las clases `NotInheritable` se usan principalmente para evitar una derivación imprevista.  
  
 **Identificador de error:** BC30299  
  
### Para corregir este error  
  
-   Quitar la palabra clave `NotInheritable` de la definición de la clase base deseada o quitar la instrucción `Inherits`.  
  
## Vea también  
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)   
 [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement)