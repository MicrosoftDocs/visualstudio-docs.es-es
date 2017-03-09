---
title: "Error de resoluci&#243;n de sobrecarga porque ning&#250;n &#39;&lt;method&gt;&#39; accesible se puede llamar sin una conversi&#243;n de restricci&#243;n: &lt;error&gt; | Microsoft Docs"
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
  - "vbc30519"
  - "bc30519"
helpviewer_keywords: 
  - "BC30519"
ms.assetid: 3b3e724d-6fad-4146-b47d-6525493b2fa8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Error de resoluci&#243;n de sobrecarga porque ning&#250;n &#39;&lt;method&gt;&#39; accesible se puede llamar sin una conversi&#243;n de restricci&#243;n: &lt;error&gt;
Ha realizado una llamada a un método sobrecargado, pero el compilador no encuentra un método que se pueda llamar sin una conversión de restricción. Una conversión de restricción cambia un valor a un tipo de datos que no pueda mantener precisamente algunos de los valores posibles.  
  
 **Identificador de error:** BC30519  
  
### Para corregir este error  
  
-   Especifique `Option Strict Off`.  
  
## Vea también  
 [Propiedades y métodos sobrecargados](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods)   
 [Conversiones de ampliación y de restricción](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)