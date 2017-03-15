---
title: "Una expresi&#243;n lambda no se puede convertir a &#39;&lt;nombreDeTipo&gt;&#39; porque &#39;&lt;nombreDeTipo&gt;&#39; no es un tipo de delegado | Microsoft Docs"
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
  - "bc36625"
  - "vbc36625"
helpviewer_keywords: 
  - "BC36625"
ms.assetid: c03634d4-d831-4f8c-b6ab-566465968e4d
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Una expresi&#243;n lambda no se puede convertir a &#39;&lt;nombreDeTipo&gt;&#39; porque &#39;&lt;nombreDeTipo&gt;&#39; no es un tipo de delegado
Las expresiones lambda se pueden usar cuando los delegados son válidos. Se pueden convertir a tipos de delegado compatibles, pero no a ningún otro tipo. Por ejemplo, puede definir un tipo de delegado y asignarle una expresión lambda o enviar una expresión lambda como argumento para un parámetro <xref:System.Func%601>. Estos ejemplos se muestran en el código siguiente.  
  
```vb#  
Module Module1 Delegate Function FunDel(ByVal m As Integer) As Boolean Sub Main() ' Assign a lambda expression to a function delegate. Dim negative As FunDel = Function(n As Integer) n < 0 Console.WriteLine(negative(-3)) ' Send a lambda as the argument to a delegate parameter. Dim numbers() As Integer = {3, 4, 2, 8, 1, 0, 9, 13, 42} Dim evens = numbers.Where(Function(n) n Mod 2 = 0) For Each even In evens Console.WriteLine(even) Next End Sub End Module  
```  
  
 **Identificador de error:** BC36625  
  
## Vea también  
 [Expresiones lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)