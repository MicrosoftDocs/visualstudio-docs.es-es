---
title: "No se puede implementar el miembro &#39;&lt;classname&gt;.&lt;procedurename&gt;&#39; que coincide con esta firma porque la clase &#39;&lt;classname&gt;&#39; contiene varios miembros que tienen un nombre y una firma iguales a estos: &#39;&lt;signaturelist&gt;&#39; | Microsoft Docs"
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
  - "bc30935"
  - "vbc30935"
helpviewer_keywords: 
  - "BC30935"
ms.assetid: 1165b630-668d-417d-9e18-9b8ffe7f6980
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede implementar el miembro &#39;&lt;classname&gt;.&lt;procedurename&gt;&#39; que coincide con esta firma porque la clase &#39;&lt;classname&gt;&#39; contiene varios miembros que tienen un nombre y una firma iguales a estos: &#39;&lt;signaturelist&gt;&#39;
Un procedimiento o propiedad intenta invalidar un procedimiento o una propiedad heredados, pero el compilador encuentra más de una versión del procedimiento o propiedad de base con el mismo nombre y firma.  
  
 Este error puede producirse en una situación con tipos genéricos construidos, como se muestra en las siguientes declaraciones de esqueleto.  
  
```  
Public Class baseClass(Of t) Public Overridable Sub doSomething(ByVal inputValue As String) End Sub Public Overridable Sub doSomething(ByVal inputValue As t) End Sub End Class Public Class derivedClass Inherits baseClass(Of String) Overrides Sub doSomething(ByVal inputValue As String) End Sub End Class  
```  
  
 Dado que `derivedClass` hereda `baseClass` que proporciona `String` a su parámetro de tipo `t`, las dos versiones de `doSomething` en `baseClass` tienen firmas idénticas en lo que se refiere a `derivedClass`. Como resultado, el compilador no puede determinar qué versión debe invalidar.  
  
 **Identificador de error:** BC30935  
  
### Para corregir este error  
  
-   Cambie el argumento o los argumentos de tipo que suministra a la clase base para que no produzcan una o varias firmas idénticas de procedimientos o propiedades de miembro.  
  
     O bien  
  
-   Si necesita heredar la clase base con el conjunto de argumentos de tipo que está usando, no invalide el procedimiento ni la propiedad citados en este mensaje de error.  
  
## Vea también  
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [NO ESTÁ EN LA COMPILACIÓN: Invalidar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)