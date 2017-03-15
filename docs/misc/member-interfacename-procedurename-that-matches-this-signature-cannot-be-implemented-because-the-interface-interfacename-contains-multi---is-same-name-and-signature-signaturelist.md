---
title: "No se puede implementar el miembro &#39;nombreInterfaz&#39;.&lt;nombreProcedimiento&gt;&#39; que coincide con esta signatura porque la interfaz &#39;&lt;nombreInterfaz&gt;&#39; contiene varios miembros que tienen un nombre y una signatura iguales a estos: &#39;&lt;listaSignaturas&gt;&#39; | Microsoft Docs"
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
  - "vbc30937"
  - "bc30937"
helpviewer_keywords: 
  - "BC30937"
ms.assetid: e917d85e-95e0-431a-9d09-39ce5d4fc894
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede implementar el miembro &#39;nombreInterfaz&#39;.&lt;nombreProcedimiento&gt;&#39; que coincide con esta signatura porque la interfaz &#39;&lt;nombreInterfaz&gt;&#39; contiene varios miembros que tienen un nombre y una signatura iguales a estos: &#39;&lt;listaSignaturas&gt;&#39;
Un procedimiento o propiedad intenta implementar un procedimiento o una propiedad definida en una interfaz implementada, pero el compilador encuentra más de una versión del procedimiento o propiedad de interfaz con el mismo nombre y signatura.  
  
 Este error puede producirse en una situación con tipos genéricos construidos, como se muestra en las siguientes declaraciones de esqueleto.  
  
```  
Public Interface baseInterface(Of t) Sub doSomething(ByVal inputValue As String) Sub doSomething(ByVal inputValue As t) End Class Public Class implementingClass Implements baseInterface(Of String) Sub doSomething(ByVal inputValue As String) _ Implements baseInterface(Of String).doSomething End Sub End Class  
```  
  
 Dado que `implementingClass` implementa `baseInterface` que proporciona `String` a su parámetro de tipo `t`, las dos versiones de `doSomething` en `baseInterface` tienen signaturas idénticas en lo que se refiere a `implementingClass`. Como resultado, el compilador no puede determinar qué versión debe implementar.  
  
 **Identificador de error:** BC30937  
  
### Para corregir este error  
  
-   Cambie el argumento o los argumentos de tipo que suministra a la clase base para que no produzcan una o varias signaturas idénticas de procedimientos o propiedades de miembro.  
  
     O bien  
  
-   No implemente esta clase base. No puede implementarla con el conjunto de argumentos de tipo que está usando, porque debe implementar cada uno de sus miembros.  
  
## Vea también  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Palabra clave Implements e instrucción Implements](http://msdn.microsoft.com/es-es/b96560f7-6413-480f-a1e2-f80253bab5be)