---
title: "La variable &#39;ReadOnly&#39; no puede ser el destino de una asignaci&#243;n en una expresi&#243;n lambda dentro de un constructor | Microsoft Docs"
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
  - "bc36602"
  - "vbc36602"
helpviewer_keywords: 
  - "BC36602"
ms.assetid: f96f8c79-86df-4727-bc6d-f0844da21395
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable &#39;ReadOnly&#39; no puede ser el destino de una asignaci&#243;n en una expresi&#243;n lambda dentro de un constructor
Hizo referencia a una variable `ReadOnly` desde una expresión lambda, lo que no está permitido. El código siguiente provoca este error al enviar la variable de `ReadOnly``m` como el argumento de un parámetro `ByRef`.  
  
```vb#  
Class Class1 ReadOnly m As Integer Sub New() ' The use of m triggers the error. Dim f = Function() Test(m) End Sub Function Test(ByRef n As Integer) As String End Function End Class  
```  
  
 **Identificador de error:** BC36602  
  
### Para corregir este error  
  
-   Si es posible, cambie el parámetro `n` de la función `Test` a un parámetro `ByVal`, como se muestra en el código siguiente.  
  
    ```vb#  
    Class Class1Fix1 ReadOnly m As Integer Sub New() Dim f = Function() Test(m) End Sub Function Test(ByVal n As Integer) As String End Function End Class  
    ```  
  
### Para corregir este error  
  
-   Asigne la variable `ReadOnly``m` a una variable local en el constructor y use la variable local en lugar de `m`, como se muestra en el código siguiente.  
  
    ```vb#  
    Class Class1Fix2 ReadOnly m As Integer Sub New() Dim temp = m Dim f = Function() Test(temp) End Sub Function Test(ByRef n As Integer) As String End Function End Class  
    ```  
  
## Vea también  
 [Expresiones lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)