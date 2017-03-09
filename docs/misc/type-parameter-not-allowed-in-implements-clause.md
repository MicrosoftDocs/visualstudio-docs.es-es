---
title: "Par&#225;metro de tipo no permitido en la cl&#225;usula &#39;Implements&#39; | Microsoft Docs"
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
  - "vbc32056"
  - "bc32056"
helpviewer_keywords: 
  - "BC32056"
ms.assetid: a62d773b-e878-4817-8638-da49849477d7
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Par&#225;metro de tipo no permitido en la cl&#225;usula &#39;Implements&#39;
Una cláusula `Implements` de un tipo genérico especifica un parámetro de tipo como el miembro que se va a implementar.  
  
 Una cláusula `Implements` debe especificar una interfaz y un miembro. Puede pasar un parámetro de tipo a la interfaz, pero no puede pasarla al miembro, ni usarla como nombre del miembro.  
  
 Las instrucciones siguientes pueden generar este error.  
  
```  
Class c1(Of t) Implements i1(Of t) Public Sub doSomething() Implements t End Class  
```  
  
 **Identificador de error:** BC32056  
  
### Para corregir este error  
  
-   Especifique el nombre de la interfaz y un miembro original de la interfaz que sigue a la palabra clave `Implements`. Puede pasar el parámetro de tipo a la interfaz si es necesario.  
  
    ```  
    Public Sub doSomething() Implements i1(Of t).doSomething  
    ```  
  
## Vea también  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [NO ESTÁ EN LA COMPILACIÓN: Palabra clave Implements e instrucción Implements](http://msdn.microsoft.com/es-es/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)