---
title: "Option Strict On no permite conversiones impl&#237;citas de &#39;&lt;tipo1&gt;&#39; a &#39;&lt;tipo2&gt;&#39;; el tipo de colecci&#243;n de Visual Basic 6.0 no es compatible con el tipo de colecci&#243;n de .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30753"
  - "bc30753"
helpviewer_keywords: 
  - "BC30753"
ms.assetid: 7e1bb22e-a507-483e-bfd6-f3a43e24a232
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On no permite conversiones impl&#237;citas de &#39;&lt;tipo1&gt;&#39; a &#39;&lt;tipo2&gt;&#39;; el tipo de colecci&#243;n de Visual Basic 6.0 no es compatible con el tipo de colecci&#243;n de .NET Framework
`Option Strict On` no permite conversiones implícitas de '`<type1>`' a '`<type2>`'; el tipo de colección de Visual Basic 6.0 no es compatible con el tipo de colección de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
 El objeto de colección que se usa en Visual Basic 6.0 difiere de la colección que se usa en [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)].  
  
 **Identificador de error:** BC30753  
  
### Para corregir este error  
  
-   Convierta explícitamente los objetos de la colección mediante una de las palabras clave de conversión de tipos. Las palabras clave [CType \(Función\)](/dotnet/visual-basic/language-reference/functions/ctype-function) y [DirectCast \(Operador\)](/dotnet/visual-basic/language-reference/operators/directcast-operator) lanzan una excepción de tiempo de ejecución si se produce un error de conversión. La palabra clave [TryCast \(Operador\)](/dotnet/visual-basic/language-reference/operators/trycast-operator) devuelve [Nothing](/dotnet/visual-basic/language-reference/nothing) si se produce un error de conversión.  
  
## Vea también  
 [CType \(Función\)](/dotnet/visual-basic/language-reference/functions/ctype-function)   
 [DirectCast \(Operador\)](/dotnet/visual-basic/language-reference/operators/directcast-operator)   
 [TryCast \(Operador\)](/dotnet/visual-basic/language-reference/operators/trycast-operator)   
 [Nothing](/dotnet/visual-basic/language-reference/nothing)   
 [NO ESTÁ EN LA COMPILACIÓN Colecciones en Visual Basic](http://msdn.microsoft.com/es-es/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)