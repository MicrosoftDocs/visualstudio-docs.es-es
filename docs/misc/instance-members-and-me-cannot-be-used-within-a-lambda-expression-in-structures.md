---
title: "No se pueden usar miembros de instancia ni &#39;Me&#39; dentro de una expresi&#243;n lambda en estructuras | Microsoft Docs"
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
  - "vbc36638"
  - "bc36638"
helpviewer_keywords: 
  - "BC36638"
ms.assetid: 5c24a7c7-50f6-4ffb-9ed2-07e2abc4eaf3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden usar miembros de instancia ni &#39;Me&#39; dentro de una expresi&#243;n lambda en estructuras
Desde dentro de una estructura, se ha definido una expresión lambda que hace referencia a un miembro de instancia de la estructura o usa `Me`. El código siguiente muestra estas dos referencias no válidas.  
  
```vb#  
Structure Structure1 Public InstanceMember As Integer Public Function ExampleFun() As Integer '' The error is caused by use of InstanceMember. 'Dim fun1 = Function() InstanceMember '' The error is caused by use of Me. 'Dim fun2 = Function() Me.InstanceMember 'Return fun1() End Function End Structure  
```  
  
 **Identificador de error:** BC36638  
  
### Para corregir este error  
  
-   Asigne el miembro de instancia a una variable local y use la variable local en la instrucción.  
  
    ```vb#  
    Public Function ExampleFunFix() As Integer Dim temp = InstanceMember Dim fun1 = Function() temp Return fun1() End Function  
    ```  
  
## Vea también  
 [Expresiones lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Me](http://msdn.microsoft.com/es-es/a65973c7-cf06-4547-9b25-9fba885525c2)   
 [Structure \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/structure-statement)