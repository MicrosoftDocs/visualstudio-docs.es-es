---
title: "La restricci&#243;n &#39;&lt;constraint1&gt;&#39; indirecta obtenida de la restricci&#243;n &#39;&lt;typeparameter1&gt;&#39; del par&#225;metro de tipo entra en conflicto con la restricci&#243;n &#39;&lt;constraint2&gt;&#39;. | Microsoft Docs"
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
  - "bc32111"
  - "vbc32111"
helpviewer_keywords: 
  - "BC32111"
ms.assetid: b03b5840-5318-4844-b2da-1bca4c28d097
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La restricci&#243;n &#39;&lt;constraint1&gt;&#39; indirecta obtenida de la restricci&#243;n &#39;&lt;typeparameter1&gt;&#39; del par&#225;metro de tipo entra en conflicto con la restricci&#243;n &#39;&lt;constraint2&gt;&#39;.
Se ha declarado un tipo genérico con restricciones contradictorias debido a una combinación de restricciones directas e indirectas.  
  
 La instrucción siguiente puede generar este error.  
  
 `Public Class testClass(Of t1 As {t2, Class}, t2 As Structure)`  
  
 La restricción indirecta `Structure` y la restricción directa `Class` producen un conflicto para el parámetro de tipo `t1`, porque la restricción `Structure` requiere que el argumento de tipo correspondiente sea un tipo de valor, mientras que `Class` requiere que sea un tipo de referencia.  
  
 **Identificador de error:** BC32111  
  
### Para corregir este error  
  
-   Cambie las restricciones de parámetro de tipo para evitar restricciones contradictorias.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Estructura \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Clase \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)