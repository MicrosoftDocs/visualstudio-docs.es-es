---
title: "CA1715: Los identificadores deber&#237;an tener el prefijo correcto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1715"
  - "IdentifiersShouldHaveCorrectPrefix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectPrefix"
  - "CA1715"
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# CA1715: Los identificadores deber&#237;an tener el prefijo correcto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectPrefix|  
|Identificador de comprobación|CA1715|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático: cuando se desencadena en interfaces.<br /><br /> No problemático: cuando se produce en parámetros de tipo genérico.|  
  
## Motivo  
 El nombre de una interfaz visible externamente no empieza por "I" mayúscula.  
  
 O bien  
  
 El nombre de un parámetro de tipo genérico en un tipo o método visible externamente no empieza por "T" mayúscula.  
  
## Descripción de la regla  
 Por convención, los nombres de determinados elementos de programación comienzan con un prefijo concreto.  
  
 Los nombres de interfaz deberían comenzar con una 'I' mayúscula seguida de otra letra mayúscula.  Esta regla crea un informe de las infracciones de los nombres de interfaz como 'MyInterface' y 'IsolatedInterface'.  
  
 Los nombres de parámetro de tipo genérico deben empezar por una 'T' mayúscula y, opcionalmente, pueden ir seguidos de otra letra mayúscula.  Esta regla informa acerca de las infracciones en los nombres del parámetro de tipo genérico como "V" y "Type".  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## Cómo corregir infracciones  
 Cambie el nombre del identificador para que se aplique el prefijo correctamente.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 **En el ejemplo siguiente se muestra una interfaz con un nombre incorrecto.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## Ejemplo  
 **En el ejemplo siguiente se corrige la infracción anterior agregando el prefijo 'I' a la interfaz.**  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## Ejemplo  
 **En el ejemplo siguiente se muestra un parámetro de tipo genérico al que se asigna un nombre incorrecto.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]  
  
## Ejemplo  
 **En el ejemplo siguiente se corrige la infracción anterior agregando el prefijo 'T' al parámetro de tipo genérico.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]  
  
## Reglas relacionadas  
 [CA1722: Los identificadores no deberían tener el prefijo incorrecto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)