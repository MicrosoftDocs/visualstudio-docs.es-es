---
title: "Los tipos de datos de los par&#225;metros de tipo no se pueden inferir de estos argumentos porque no se convierten en el mismo tipo | Microsoft Docs"
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
  - "vbc36659"
  - "bc36659"
  - "vbc36656"
  - "bc36656"
helpviewer_keywords: 
  - "BC36659"
  - "BC36659"
ms.assetid: 0aa809da-3b44-4d78-b3c5-0a148bdf7ce8
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de datos de los par&#225;metros de tipo no se pueden inferir de estos argumentos porque no se convierten en el mismo tipo
Los tipos de datos de los parámetros de tipo no se pueden inferir de estos argumentos porque no se convierten en el mismo tipo. Especificar los tipos de datos explícitamente puede corregir este error.  
  
 Este error se produce cuando en caso de error en la resolución de sobrecarga. Se produce como un mensaje subordinado que indica por qué se ha eliminado un candidato de sobrecarga determinado. El error explica que el compilador no puede usar la inferencia de tipos para encontrar tipos de datos para los parámetros de tipo que son compatibles con los argumentos.  
  
> [!NOTE]
>  Cuando no es posible especificar argumentos \(por ejemplo, para operadores de consulta de expresiones de consulta\), el mensaje de error aparece sin la segunda oración.  
  
 Para obtener más información y ejemplos, vea [Los tipos de datos de los parámetros de tipo del método '\<nombreMétodo\>' no se pueden inferir de estos argumentos porque no se convierten al mismo tipo.](../misc/data-type-s-of-the-type-parameter-s-in-method-methodname-cannot-be-inferred-from-these-arguments-because-they-do-not-convert-to-the-same-type.md).  
  
 **Identificador de error:** BC36659 y BC36656  
  
## Vea también  
 [Conversión de delegado flexible](/dotnet/visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion)   
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Resolución de sobrecargas](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)