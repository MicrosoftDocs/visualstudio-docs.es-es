---
title: "El par&#225;metro de tipo con una restricci&#243;n &#39;Structure&#39; no se puede usar como restricci&#243;n. | Microsoft Docs"
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
  - "vbc32114"
  - "bc32114"
helpviewer_keywords: 
  - "BC32114"
ms.assetid: 442b2048-9dc4-4223-bcfc-4d96bf8d14de
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro de tipo con una restricci&#243;n &#39;Structure&#39; no se puede usar como restricci&#243;n.
Un parámetro de tipo con una restricción `Structure` se usa como restricción para otro parámetro de tipo.  
  
 La restricción `Structure` necesita que el argumento de tipo pasado a su parámetro de tipo sea un tipo de valor. Sin embargo, un tipo de valor no puede implementarse ni heredarse, por lo que no tiene sentido usarlo como restricción, que necesitaría el otro parámetro de tipo para implementarlo o heredarlo.  
  
 La única interpretación significativa de esta situación es que ambos argumentos de tipo deben ser del mismo tipo exacto. Si ese es el caso, el tipo genérico necesita solo un parámetro de tipo.  
  
 La instrucción siguiente puede generar este error.  
  
 `Class c1(Of t1 As Structure, t2 As t1)`  
  
 El tipo pasado a `t2` no puede implementar ni heredar el tipo pasado a `t1`, porque el tipo pasado a `t1` debe ser un tipo de valor.  
  
 **Identificador de error:** BC32114  
  
### Para corregir este error  
  
-   Elimine el parámetro de tipo restringido a `Structure` de la lista de restricciones en el otro parámetro de tipo.  
  
-   Si ambos parámetros de tipo necesitan el mismo tipo de valor, defina el tipo genérico con un solo parámetro de tipo.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Estructura \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)