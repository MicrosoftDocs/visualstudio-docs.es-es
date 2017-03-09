---
title: "No se puede implementar la interfaz &#39;&lt;interfacename1&gt;&#39; porque su implementaci&#243;n podr&#237;a entrar en conflicto con la implementaci&#243;n de otra interfaz implementada &#39;&lt;interfacename2&gt;&#39; para algunos argumentos de tipo. | Microsoft Docs"
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
  - "BC32072"
  - "vbc32072"
helpviewer_keywords: 
  - "BC32072"
ms.assetid: af1cc688-c8cf-4cb2-a8a9-310f5139fe7b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede implementar la interfaz &#39;&lt;interfacename1&gt;&#39; porque su implementaci&#243;n podr&#237;a entrar en conflicto con la implementaci&#243;n de otra interfaz implementada &#39;&lt;interfacename2&gt;&#39; para algunos argumentos de tipo.
Una declaración de clase incluye una instrucción `Implements` que especifica dos o más interfaces, pero al menos una de las interfaces es genérica y dos de las implementaciones podrían entrar en conflicto para determinados valores de argumentos de tipo.  
  
 Las instrucciones siguientes pueden generar este error.  
  
```  
Public Interface iFace1 Sub testSub(ByVal arg As String) End Interface Public Interface iFace2(Of t) Sub testSub(ByVal arg As t) End Interface Public Class testClass Implements iFace1, iFace2(Of String) End Class  
```  
  
 Dado que `iFace2` se construye usando `String`, `testClass` debe implementar dos versiones de `testSub` con firmas idénticas. Esto produciría ambigüedad sobre a qué versión se debe acceder.  
  
 **Identificador de error:** BC32072  
  
### Para corregir este error  
  
-   Cambie el argumento de tipo proporcionado a la interfaz genérica para que no haya ningún conflicto.  
  
     O bien  
  
-   Quite de la instrucción `Implements` las interfaces que produzcan el conflicto de implementación.  
  
## Vea también  
 [Class \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Palabra clave Implements e instrucción Implements](http://msdn.microsoft.com/es-es/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)