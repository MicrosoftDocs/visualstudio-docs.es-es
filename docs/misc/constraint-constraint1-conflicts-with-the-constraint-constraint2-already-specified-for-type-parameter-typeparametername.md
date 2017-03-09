---
title: "La restricci&#243;n &#39;&lt;restricci&#243;n1&gt;&#39; est&#225; en conflicto con la restricci&#243;n &#39;&lt;restricci&#243;n2&gt;&#39; ya especificada para el par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39; | Microsoft Docs"
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
  - "vbc32119"
  - "bc32119"
helpviewer_keywords: 
  - "BC32119"
ms.assetid: 30e6778d-5c2b-4f2d-a136-4e66fa9fbe4d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La restricci&#243;n &#39;&lt;restricci&#243;n1&gt;&#39; est&#225; en conflicto con la restricci&#243;n &#39;&lt;restricci&#243;n2&gt;&#39; ya especificada para el par&#225;metro de tipo &#39;&lt;nombreDePar&#225;metroDeTipo&gt;&#39;
Se declaró un tipo genérico con restricciones contradictorias en un parámetro de tipo.  
  
 La instrucción siguiente puede generar este error.  
  
 `Public Class testClass(Of t As {Structure, Class })`  
  
 La restricciones `Structure` y `Class` provocan un conflicto con el parámetro de tipo `t`, porque la restricción `Structure` requiere que el argumento de tipo correspondiente sea un tipo de valor, mientras que `Class` requiere que sea un tipo de referencia.  
  
 **Identificador de error:** BC32119  
  
### Para corregir este error  
  
-   Cambie las restricciones de parámetro de tipo para evitar conflictos.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Class \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)