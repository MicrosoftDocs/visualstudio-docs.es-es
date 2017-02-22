---
title: "CA2104: No declarar tipos de referencias mutables de solo lectura | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
  - "CA2104"
helpviewer_keywords: 
  - "CA2104"
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2104: No declarar tipos de referencias mutables de solo lectura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|Identificador de comprobación|CA2104|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo visible externamente contiene un campo de sólo lectura visible externamente que es un tipo de referencia que se puede cambiar.  
  
## Descripción de la regla  
 Un tipo que mutable es un tipo cuyos datos de instancia se pueden modificar.  La clase <xref:System.Text.StringBuilder?displayProperty=fullName> es un ejemplo de un tipo de referencia mutable.  Contiene miembros que pueden cambiar el valor de una instancia de la clase.  Un ejemplo de un tipo de referencia inmutable es la clase <xref:System.String?displayProperty=fullName>.  Una vez creadas las instancias del tipo, su valor nunca puede cambiar.  
  
 El modificador de solo lectura \([readonly](/dotnet/csharp/language-reference/keywords/readonly) en C\#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y [const](/visual-cpp/cpp/const-cpp) en C\+\+\) en un campo de tipo de referencia \(puntero en C\+\+\) evita que una instancia diferente del tipo de referencia reemplace al campo.  Sin embargo, el modificador no evita que los datos de instancia del campo se modifiquen a través del tipo de referencia.  
  
 Los campos de matriz de sólo lectura están exentos de esta regla pero en su lugar producen una infracción de la regla [CA2105: Los campos de matrices no deberían ser de solo lectura](../code-quality/ca2105-array-fields-should-not-be-read-only.md).  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el modificador de sólo lectura o, si es posible realizar un cambio importante, reemplace el campo por un tipo inmutable.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla si el tipo del campo es inmutable.  
  
## Ejemplo  
 El ejemplo siguiente muestra una declaración de campo que infringe esta regla.  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-cs[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]