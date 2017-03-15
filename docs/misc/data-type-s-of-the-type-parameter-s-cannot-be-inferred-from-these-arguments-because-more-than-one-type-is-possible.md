---
title: "Los tipos de datos de los par&#225;metros de tipo no se pueden inferir de estos argumentos porque hay m&#225;s de un tipo posible. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36653"
  - "bc36653"
  - "vbc36650"
  - "bc36650"
helpviewer_keywords: 
  - "BC36650"
  - "BC36653"
ms.assetid: 79287e1f-7070-4a71-96d2-aee0a0c9d8bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de datos de los par&#225;metros de tipo no se pueden inferir de estos argumentos porque hay m&#225;s de un tipo posible.
Los tipos de datos de los parámetros de tipo no se pueden inferir de estos argumentos porque hay más de un tipo posible. Especificar los tipos de datos explícitamente puede corregir este error.  
  
 Este error se produce en caso de error en la resolución de sobrecarga. Se produce como un mensaje subordinado que indica por qué se ha eliminado un candidato de sobrecarga determinado. El error explica que, si se aplica la inferencia de tipo para determinar el tipo de datos de los parámetros de tipo del procedimiento genérico llamado, el compilador encuentra más de un tipo de datos posible para al menos uno de ellos.  
  
> [!NOTE]
>  Cuando no es posible especificar argumentos \(por ejemplo, para operadores de consulta de expresiones de consulta\), el mensaje de error aparece sin la segunda oración.  
  
 Para obtener más información y ejemplos, vea [Los tipos de datos de los parámetros de tipo del método '\<methodname\>' no se pueden inferir de estos argumentos porque hay más de un tipo posible](../misc/data-type-s-of-the-type-parameter-s-in-method-methodname-cannot-be-inferred-from-these-arguments-because-more-than-one-type-is-possible.md).  
  
 **Identificador de error:** BC36653 y BC36650  
  
## Vea también  
 [Procedimientos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Resolución de sobrecargas](/dotnet/visual-basic/programming-guide/language-features/procedures/overload-resolution)