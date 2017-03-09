---
title: "El par&#225;metro de tipo &#39;&lt;typeparametername1&gt;&#39; debe tener una restricci&#243;n &#39;New&#39; o &#39;Structure&#39; para satisfacer la restricci&#243;n &#39;New&#39; del par&#225;metro de tipo &#39;&lt;typeparametername2&gt;&#39;. | Microsoft Docs"
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
  - "vbc32084"
  - "BC32084"
helpviewer_keywords: 
  - "BC32084"
ms.assetid: a7ff58d3-8c67-40e4-9fd8-92cc00524c22
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro de tipo &#39;&lt;typeparametername1&gt;&#39; debe tener una restricci&#243;n &#39;New&#39; o &#39;Structure&#39; para satisfacer la restricci&#243;n &#39;New&#39; del par&#225;metro de tipo &#39;&lt;typeparametername2&gt;&#39;.
Una instrucción construye un tipo genérico que pasa un parámetro de tipo que no está restringido para satisfacer una restricción `New`.  
  
 La restricción `New` significa que el argumento de tipo proporcionado para ese parámetro de tipo debe exponer un constructor sin parámetros accesible para el código que crea objetos a partir de ella. Todos los tipos de valor tienen constructores sin parámetros, pero no todos los tipos de referencia los tienen. Por lo tanto, la restricción `Structure` satisface la restricción `New`, pero la restricción `Class` o el nombre de clase o interfaz no.  
  
 Las instrucciones siguientes pueden generar este error.  
  
```  
Public Class c1(Of t As New) End Class Public Class c2(Of u) Public testObject As New c1(Of u) End Class  
```  
  
 Si la clase `c2` crea un objeto de `c1`, el parámetro de tipo `u` no satisface la restricción `New` en el parámetro de tipo `t`.  
  
 **Identificador de error:** BC32084  
  
### Para corregir este error  
  
-   Si el parámetro de tipo que se pasará al tipo genérico puede satisfacer la restricción `Structure` o `New`, agregue la restricción adecuada a su definición.  
  
    ```  
    Public Class c2(Of u As Structure)  
    ```  
  
-   Si el parámetro de tipo no puede satisfacer la restricción `Structure` o `New`, no la pase al tipo genérico. Debe pasar algo como argumento de tipo.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Estructura \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Clase \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)