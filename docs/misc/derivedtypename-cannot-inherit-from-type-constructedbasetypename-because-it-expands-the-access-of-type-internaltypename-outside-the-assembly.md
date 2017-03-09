---
title: "&#39;&lt;nombreDeTipoDerivado&gt;&#39; no puede heredar del &lt;tipo&gt; &#39;&lt;nombreDeTipoBaseConstruido&gt;&#39; porque ampl&#237;a el acceso del tipo &lt;nombreDeTipoInterno&gt; fuera del ensamblado. | Microsoft Docs"
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
  - "BC30922"
  - "vbc30922"
helpviewer_keywords: 
  - "BC30922"
ms.assetid: 81909654-7e67-4b89-81a3-25ae57f678f7
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeTipoDerivado&gt;&#39; no puede heredar del &lt;tipo&gt; &#39;&lt;nombreDeTipoBaseConstruido&gt;&#39; porque ampl&#237;a el acceso del tipo &lt;nombreDeTipoInterno&gt; fuera del ensamblado.
Una clase o interfaz derivada intenta ampliar el nivel de acceso de un tipo restringido. Para ello, lo usa como un argumento de tipo para una clase base o una interfaz.  
  
 El código siguiente pueden generar este error.  
  
```  
Public Class baseClass(Of t)  
End Class  
Public Class derivedClass  
    Inherits baseClass(Of restrictedStructure)  
End Class  
Friend Structure restrictedStructure  
    Dim firstMember As Integer  
End Structure  
```  
  
 El código situado fuera del ensamblado no puede acceder a `restrictedStructure`. Sin embargo, se puede acceder a `derivedClass` desde cualquier código que pueda hacer referencia a este. Por lo tanto, `derivedClass` no puede heredar `baseClass` si usa `restrictedStructure` como un argumento de tipo, porque ello podría exponer `restrictedStructure` al código de cualquier ensamblado.  
  
 **Identificador de error:** BC30922  
  
### Para corregir este error  
  
-   Ajuste los niveles de acceso de las clases o las interfaces para que el tipo derivado no amplíe el nivel de acceso del tipo restringido.  
  
     O bien  
  
-   Si no puede ajustar los niveles de acceso, no use el tipo restringido como un argumento de tipo al construir la clase base o la interfaz.  
  
## Vea también  
 [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement)   
 [Fundamentos de la herencia](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [Niveles de acceso en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)