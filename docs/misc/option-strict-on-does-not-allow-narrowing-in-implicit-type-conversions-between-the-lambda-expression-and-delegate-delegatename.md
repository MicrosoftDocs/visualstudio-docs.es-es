---
title: "Option Strict On no permite la restricci&#243;n en las conversiones de tipo impl&#237;citas entre la expresi&#243;n lambda y el delegado &#39;&lt;nombreDelegado&gt;&#39;. | Microsoft Docs"
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
  - "bc36662"
  - "vbc36662"
helpviewer_keywords: 
  - "BC36662"
ms.assetid: 4504497b-56ba-4631-ad7b-59975f7fee04
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On no permite la restricci&#243;n en las conversiones de tipo impl&#237;citas entre la expresi&#243;n lambda y el delegado &#39;&lt;nombreDelegado&gt;&#39;.
Con `Option Strict` On, no puede haber una conversión de restricción entre el tipo de datos de un parámetro de un delegado y el parámetro correspondiente de una expresión lambda asignada a una variable de ese tipo de delegado. Por ejemplo, en el código siguiente, el delegado `Del` tiene un parámetro de tipo `Integer`.  
  
```vb#  
Delegate Function Del(ByVal p As Integer) As String  
```  
  
 Por lo tanto, el parámetro correspondiente de cualquier expresión lambda que se asigna a una variable de tipo `Del` puede ser `Integer` o cualquier tipo de datos para el que hay una conversión de ampliación desde `Integer`.  
  
```vb#  
' Valid. Dim example1 As Del = Function(n As Integer) "Valid" Dim example2 As Del = Function(n As Long) "Valid" ' Not valid. Dim example3 As Del = Function(n As Short) "Not Valid"  
```  
  
 **Identificador de error:** BC36662  
  
### Para corregir este error  
  
-   Cambie el tipo de datos del parámetro en el delegado o la expresión lambda para que exista la relación de ampliación necesaria.  
  
-   No especifique tipos de datos de parámetro en la expresión lambda. Los tipos se inferirán de los parámetros correspondientes en el delegado.  
  
    ```vb#  
    Dim example4 As Del = Function(n) "Valid"  
    ```  
  
## Vea también  
 [Expresiones lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Delegados](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)   
 [Conversiones de ampliación y de restricción](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [Conversión de delegado flexible](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)