---
title: "&#39;&lt;nombreTipoDerivado&gt;&#39; no puede heredar del &lt;tipo&gt; &#39;&lt;nombreTipoBaseConstruido&gt;&#39; porque ampl&#237;a el acceso del tipo &lt;nombreTipoInterno&gt; a la &lt;regi&#243;n&gt; &#39;&lt;nombreRegi&#243;n&gt;&#39;. | Microsoft Docs"
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
  - "vbc30921"
  - "BC30921"
helpviewer_keywords: 
  - "BC30921"
ms.assetid: b0dd971a-80e2-4d37-925b-854d17411546
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreTipoDerivado&gt;&#39; no puede heredar del &lt;tipo&gt; &#39;&lt;nombreTipoBaseConstruido&gt;&#39; porque ampl&#237;a el acceso del tipo &lt;nombreTipoInterno&gt; a la &lt;regi&#243;n&gt; &#39;&lt;nombreRegi&#243;n&gt;&#39;.
Una clase o interfaz derivada intenta ampliar el nivel de acceso de un tipo interno. Para ello, lo usa como un argumento de tipo para una clase base o una interfaz.  
  
 El código siguiente puede generar este error.  
  
```  
Public Class containingClass Public Class baseClass(Of t) End Class Friend Class derivedClass Inherits baseClass(Of internalStructure) End Class Private Structure internalStructure Dim firstMember As Integer End Structure End Class  
```  
  
 El código situado fuera de `containingClass` no tiene permitido acceder a `internalStructure`. Sin embargo, se puede acceder a `derivedClass` desde cualquier código del mismo ensamblado. Por lo tanto, `derivedClass` no puede heredar `baseClass` si usa `internalStructure` como un argumento de tipo, porque podría exponer `internalStructure` en toda la región de código de definición.  
  
 **Identificador de error:** BC30921  
  
### Para corregir este error  
  
-   Ajuste los niveles de acceso de las clases o las interfaces para que el tipo derivado no amplíe el nivel de acceso del tipo interno.  
  
     O bien  
  
-   Si no puede ajustar los niveles de acceso, no use el tipo interno como argumento de tipo al construir la clase base o la interfaz.  
  
## Vea también  
 [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Niveles de acceso en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)