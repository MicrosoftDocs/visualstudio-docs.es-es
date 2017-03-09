---
title: "No se puede implementar &#39;&lt;interfacename1&gt;.&lt;membername&gt;&#39; porque su implementaci&#243;n podr&#237;a entrar en conflicto con la implementaci&#243;n de &#39;&lt;interfacename2&gt;.&lt;membername&gt;&#39; para algunos argumentos de tipo. | Microsoft Docs"
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
  - "bc32125"
  - "vbc32125"
helpviewer_keywords: 
  - "BC32125"
ms.assetid: 74321d27-4ff8-440c-b5de-d67e98fff274
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede implementar &#39;&lt;interfacename1&gt;.&lt;membername&gt;&#39; porque su implementaci&#243;n podr&#237;a entrar en conflicto con la implementaci&#243;n de &#39;&lt;interfacename2&gt;.&lt;membername&gt;&#39; para algunos argumentos de tipo.
Una clase implementa más de una interfaz genérica, una de las cuales se hereda de la otra, y dos implementaciones de un miembro de interfaz podría entrar en conflicto para ciertos valores de argumentos de tipo.  
  
 Las instrucciones siguientes pueden generar este error.  
  
```  
Public Interface iFace1(Of t) Sub testSub() End Interface Public Interface iFace2(Of u) Inherits iFace1(Of u) End Interface Public Class testClass(Of y, z) Implements iFace1(Of y), iFace2(Of z) Public Sub testSuby() Implements iFace1(Of y).testSub End Sub Public Sub testSubz() Implements iFace1(Of z).testSub End Sub End Class  
```  
  
 Puesto que `iFace2` hereda de `iFace1` usando su propio parámetro de tipo \(`u`\), `testClass` implementaría dos versiones de `iFace1.testSub` con firmas idénticas si se pasa el mismo argumento de tipo a `y` y `z`. Esto produciría ambigüedad sobre a qué versión se debe acceder.  
  
 **Identificador de error:** BC32125  
  
### Para corregir este error  
  
-   Cambie la estructura de herencia de las interfaces para que `iFace1` no se pueda implementar con dos argumentos de tipo diferente.  
  
     O bien  
  
-   Quite de la instrucción `Implements` las interfaces que produzcan el conflicto de implementación.  
  
## Vea también  
 [Class \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Palabra clave Implements e instrucción Implements](http://msdn.microsoft.com/es-es/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)