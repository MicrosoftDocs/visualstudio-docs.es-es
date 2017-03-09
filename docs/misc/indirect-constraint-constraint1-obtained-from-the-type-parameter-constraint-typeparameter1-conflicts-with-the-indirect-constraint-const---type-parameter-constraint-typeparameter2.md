---
title: "La restricci&#243;n indirecta &#39;&lt;constraint1&gt;&#39; que se obtuvo de la restricci&#243;n de par&#225;metro de tipo &#39;&lt;typeparameter1&gt;&#39; est&#225; en conflicto con la restricci&#243;n indirecta &#39;&lt;constraint2&gt;&#39; que se obtuvo de la restricci&#243;n de par&#225;metro de tipo &#39;&lt;typeparameter2&gt;&#39; | Microsoft Docs"
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
  - "bc32109"
  - "vbc32109"
helpviewer_keywords: 
  - "BC32109"
ms.assetid: 37abd3b4-25dc-4959-8617-ce93a02bbf47
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La restricci&#243;n indirecta &#39;&lt;constraint1&gt;&#39; que se obtuvo de la restricci&#243;n de par&#225;metro de tipo &#39;&lt;typeparameter1&gt;&#39; est&#225; en conflicto con la restricci&#243;n indirecta &#39;&lt;constraint2&gt;&#39; que se obtuvo de la restricci&#243;n de par&#225;metro de tipo &#39;&lt;typeparameter2&gt;&#39;
Se ha declarado un tipo genérico con restricciones en conflicto debido a una combinación de restricciones indirectas.  
  
 La instrucción siguiente puede generar este error.  
  
```  
Public Class testClass(Of t1 As {t2, t3}, t2 As Structure, t3 As Class)  
```  
  
 La restricciones indirectas `Structure` y `Class` provocan un conflicto con el parámetro de tipo `t1`, porque la restricción `Structure` requiere que el argumento de tipo correspondiente sea un tipo de valor, mientras que `Class` requiere que sea un tipo de referencia.  
  
 **Id. de error:** BC32109  
  
### Para corregir este error  
  
-   Cambie las restricciones de parámetro de tipo para evitar restricciones en conflicto.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Estructura \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Clase \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)