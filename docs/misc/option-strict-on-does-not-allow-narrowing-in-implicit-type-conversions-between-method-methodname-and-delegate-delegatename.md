---
title: "Option Strict On no permite restricciones en conversiones de tipo impl&#237;citas entre el m&#233;todo &#39;&lt;nombreM&#233;todo&gt;&#39; y el delegado &#39;&lt;nombreDelegado&gt;&#39;. | Microsoft Docs"
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
  - "bc36663"
  - "vbc36663"
helpviewer_keywords: 
  - "BC36663"
ms.assetid: fefc7ab5-b587-4ff9-a6bc-4c4e5d4b6b29
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On no permite restricciones en conversiones de tipo impl&#237;citas entre el m&#233;todo &#39;&lt;nombreM&#233;todo&gt;&#39; y el delegado &#39;&lt;nombreDelegado&gt;&#39;.
Cuando se activa `Option Strict`, no se puede realizar una conversión de restricción entre el tipo de datos de un parámetro en un delegado y el parámetro correspondiente de una función o `Sub` asignado a una variable de ese tipo de delegado. Por ejemplo, el delegado de función `Del` tiene un parámetro de tipo `Integer`, y las funciones `Conversion1`, `Conversion2`, y `Conversion3` tienen un parámetro de tipos numéricos diferentes.  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String Function Conversion1(ByVal n As Integer) As String Return "Valid" End Function Function Conversion2(ByVal n As Long) As String Return "Valid" End Function Function Conversion3(ByVal n As Short) As String Return "Not valid" End Function  
```  
  
 Como no hay una conversión de ampliación de `Integer` a `Integer` y a `Long`, las siguientes asignaciones son válidas.  
  
```vb#  
' Valid. Dim funDel1 As Del = AddressOf Conversion1 Dim funDel2 As Del = AddressOf Conversion2  
```  
  
 La conversión de `Integer` a `Short` es una conversión de reducción. Por consiguiente, la siguiente asignación no es válida.  
  
```vb#  
' Not valid. Dim funDel3 As Del = AddressOf Conversion3  
```  
  
 Identificador de error: BC36663  
  
### Para corregir este error  
  
-   Cambie el tipo de datos del parámetro en el delegado o el método para que exista la relación de ampliación necesaria.  
  
## Vea también  
 [Conversión de delegado flexible](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Delegados](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Conversiones de ampliación y de restricción](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [NO ESTÁ EN LA COMPILACIÓN: Delegados y el operador AddressOf](http://msdn.microsoft.com/es-es/7b2ed932-8598-4355-b2f7-5cedb23ee86f)