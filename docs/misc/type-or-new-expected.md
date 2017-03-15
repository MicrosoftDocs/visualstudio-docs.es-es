---
title: "Se esperaba un tipo o &#39;New&#39;. | Microsoft Docs"
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
  - "vbc32092"
  - "bc32092"
helpviewer_keywords: 
  - "BC32092"
ms.assetid: b3041c1d-837c-4d58-bbb4-5c46f227b66d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba un tipo o &#39;New&#39;.
Un parámetro de tipo en la declaración de un tipo genérico presenta una lista de restricciones con la palabra clave `As`, pero no especifica una restricción válida.  
  
 Una restricción en un parámetro de tipo debe ser una clase o interfaz válida, o una de las palabras clave `Class`, `Structure` o `New`. Si especifica una restricción no válida o no especifica ninguna en absoluto, el compilador genera este error.  
  
 **Identificador de error:** BC32092  
  
### Para corregir este error  
  
1.  Determina la forma en que el parámetro de tipo debe restringirse y especifique la restricción adecuada en la lista de restricciones.  
  
2.  Si quiere restringir el parámetro de tipo por una clase o interfaz, asegúrese de que se escribe correctamente en la restricción.  
  
3.  Recuerde separar varias restricciones en un único parámetro de tipo mediante comas y escriba la lista de restricciones entre llaves \(`{ }`\).  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Clase \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Estructura \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)