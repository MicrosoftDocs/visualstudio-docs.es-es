---
title: "Argumentos de tipo no esperados | Microsoft Docs"
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
  - "vbc32088"
  - "bc32088"
helpviewer_keywords: 
  - "BC32088"
ms.assetid: a0918e90-e7ad-4edc-81e1-584e6174bb6c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Argumentos de tipo no esperados
Una cláusula `Implements` facilita argumentos de tipo para el miembro de interfaz que implementa.  
  
 La cláusula `Implements` solo debería identificar la interfaz y el miembro que implementa. Esto significa que, si declara un procedimiento genérico, la cláusula `Of` y los argumentos de tipo deben aparecer en la parte principal de la declaración, igual que lo harían si no implementara un procedimiento de interfaz.  
  
 El código siguiente puede generar este error.  
  
```  
Public Interface testInterface Sub testSub(Of t)() End Interface Public Class testClass Implements testInterface Public Sub testSub() Implements testInterface.testSub(Of t)() End Sub End Class  
```  
  
 La declaración anterior a la cláusula `Implements` debe ser similar a la definición de interfaz, excepto por la posible adición de modificadores de acceso o de procedimiento. El código siguiente evita el error.  
  
```  
Public Sub testSub(Of t)() Implements testInterface.testSub  
```  
  
 **Id. de error:** BC32088  
  
### Para corregir este error  
  
-   Quite la lista de argumentos de tipo de la cláusula `Implements`.  
  
-   Si implementa un miembro genérico de la interfaz, coloque la lista de argumentos de tipo en la parte principal de la declaración, precediendo la palabra clave `Implements`.  
  
## Vea también  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [NO ESTÁ EN LA COMPILACIÓN: Palabra clave Implements e instrucción Implements](http://msdn.microsoft.com/es-es/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)