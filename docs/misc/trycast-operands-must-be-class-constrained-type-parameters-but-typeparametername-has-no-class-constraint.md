---
title: "Los operandos &#39;TryCast&#39; deben ser par&#225;metros de tipo con restricci&#243;n de clase, pero &#39;&lt;typeparametername&gt;&#39; no tiene restricci&#243;n de clase | Microsoft Docs"
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
  - "BC30793"
  - "vbc30793"
helpviewer_keywords: 
  - "BC30793"
ms.assetid: a38a1da9-4413-4a69-a2ce-0b6d51c2c4ef
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los operandos &#39;TryCast&#39; deben ser par&#225;metros de tipo con restricci&#243;n de clase, pero &#39;&lt;typeparametername&gt;&#39; no tiene restricci&#243;n de clase
El operador [TryCast \(Operador\)](/dotnet/visual-basic/language-reference/operators/trycast-operator) se utiliza con un operando de parámetro de tipo que no está garantizado que sea un tipo de referencia.  
  
 `TryCast` solo funciona con tipos de referencia, como clases o interfaces. Cuando se pasa un parámetro de tipo como argumento a `TryCast`, debe restringir ese parámetro de tipo para que sea un tipo de referencia. Para ello, puede incluir uno o varios de los siguientes elementos en la lista de restricciones del parámetro de tipo:  
  
-   Uno o más nombres de interfaz \(el argumento de tipo debe implementar todas ellas\)  
  
-   Como máximo, un nombre de clase \(el argumento de tipo debe heredar de ella\)  
  
-   La restricción [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator) \(el argumento de tipo debe exponer un constructor sin parámetros al que el código de creación pueda acceder y, por tanto, debe ser una clase\)  
  
-   La restricción [Class \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) \(el tipo de argumento debe ser un tipo de referencia\)  
  
 **Id. de error:** BC30793  
  
### Para corregir este error  
  
-   Si necesita pasar este parámetro de tipo a `TryCast`, restrínjalo con una o varias restricciones de la lista anterior.  
  
-   Si no puede requerir el parámetro de tipo para que acepte solo un tipo de referencia, no puede utilizarlo con `TryCast`. Es posible que pueda usar [CType \(Función\)](/dotnet/visual-basic/language-reference/functions/ctype-function) en su lugar.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [Conversiones de ampliación y de restricción](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Conversiones implícitas y explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)