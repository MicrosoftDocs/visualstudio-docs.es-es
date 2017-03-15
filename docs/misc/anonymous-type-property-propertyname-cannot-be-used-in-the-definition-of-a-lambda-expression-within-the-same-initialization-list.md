---
title: "No se puede usar la propiedad de tipo an&#243;nimo &#39;&lt;propertyname&gt;&#39; en la definici&#243;n de una expresi&#243;n lambda en la misma lista de inicializaci&#243;n. | Microsoft Docs"
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
  - "vbc36549"
  - "bc36549"
helpviewer_keywords: 
  - "BC36549"
ms.assetid: 6d04692a-957a-41ce-a19c-fcb06a186d1a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede usar la propiedad de tipo an&#243;nimo &#39;&lt;propertyname&gt;&#39; en la definici&#243;n de una expresi&#243;n lambda en la misma lista de inicializaci&#243;n.
Las propiedades definidas en la lista de inicialización de un tipo anónimo no pueden formar parte de una definición de la expresión lambda en la misma lista. Por ejemplo, en el código siguiente, la propiedad `Num` no puede incluirse en la definición de `LambdaFun`.  
  
```vb#  
' Not valid.  
'Dim anon = New With {.Num = 4, .LambdaFun = Function() .Num > 0}  
```  
  
 **Identificador de error:** BC36549  
  
### Para corregir este error  
  
1.  Considere la posibilidad de dividir el tipo anónimo en dos partes:  
  
    ```vb#  
    Dim anon1 = New With {.Num = 4}  
    Dim anon2 = New With {.LambdaFun = Function() anon1.Num > 0}  
    ' - or -  
    Dim anon3 = New With {.lambdaFun = Function(n As Integer) n > 0}  
    Console.WriteLine((anon2.LambdaFun)())  
    Console.WriteLine(anon3.lambdaFun(anon1.Num))  
    anon1.Num = -5  
    Console.WriteLine((anon2.LambdaFun)())  
    Console.WriteLine(anon3.lambdaFun(anon1.Num))  
    ```  
  
     Tenga en cuenta que si declara `anon1.Num` como una propiedad `Key`, no se puede cambiar su valor.  
  
2.  Como alternativa,puede usar una instrucción de función normal para tener acceso a la propiedad de tipo anónimo:  
  
    ```vb#  
    Function testNum(ByVal n As Integer) As Boolean  
        Return n > 0  
    End Function  
    Console.WriteLine(testNum(anon1.Num))  
    ```  
  
3.  De forma similar, puede usar una función lambda definida fuera del tipo anónimo:  
  
    ```vb#  
    Dim lambdaFun1 = Function() anon1.Num > 0  
    Dim lambdaFun2 = Function(n As Integer) n > 0  
    ```  
  
## Vea también  
 [Expresiones lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Tipos anónimos](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)