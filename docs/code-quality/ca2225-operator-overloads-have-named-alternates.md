---
title: "CA2225: Las sobrecargas del operador tienen alternativas con nombre | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperatorOverloadsHaveNamedAlternates"
  - "CA2225"
helpviewer_keywords: 
  - "CA2225"
  - "OperatorOverloadsHaveNamedAlternates"
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2225: Las sobrecargas del operador tienen alternativas con nombre
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperatorOverloadsHaveNamedAlternates|  
|Identificador de comprobación|CA2225|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Se detectó una sobrecarga del operador y no se encontró el método alternativo con el nombre esperado.  
  
## Descripción de la regla  
 La sobrecarga de operadores permite el uso de símbolos para representar los cálculos de un tipo.  Por ejemplo, un tipo que sobrecarga el símbolo más \(\+\) para la suma normalmente tendría un miembro alternativo denominado 'Add'.  El miembro alternativo con nombre proporciona acceso a la misma funcionalidad que el operador; esto se hace para los desarrolladores que programan en lenguajes que no admiten operadores sobrecargados.  
  
 Esta regla examina los operadores mostrados en la tabla siguiente.  
  
|C\#|Visual Basic|C\+\+|Nombre alternativo|  
|---------|------------------|-----------|------------------------|  
|\+ \(binario\)|\+|\+ \(binario\)|Agregar|  
|\+\=|\+\=|\+\=|Agregar|  
|&|Y|&|BitwiseAnd|  
|&\=|And\=|&\=|BitwiseAnd|  
|&#124;|O bien|&#124;|BitwiseOr|  
|&#124;\=|Or\=|&#124;\=|BitwiseOr|  
|\-\-|N\/D|\-\-|Decremento|  
|\/|\/|\/|Dividir|  
|\/\=|\/\=|\/\=|Dividir|  
|\=\=|\=|\=\=|Equals|  
|^|Xor|^|Xor|  
|^\=|Xor\=|^\=|Xor|  
|\>|\>|\>|Comparar|  
|\>\=|\>\=|\>\=|Comparar|  
|\+\+|N\/D|\+\+|Incremento|  
|\!\=|\<\>|\!\=|Equals|  
|\<\<|\<\<|\<\<|LeftShift|  
|\<\<\=|\<\<\=|\<\<\=|LeftShift|  
|\<|\<|\<|Comparar|  
|\<\=|\<\=|\<\=|Comparar|  
|&&|N\/D|&&|LogicalAnd|  
|&#124;&#124;|N\/D|&#124;&#124;|LogicalOr|  
|\!|N\/D|\!|LogicalNot|  
|%|Mod|%|Mod o Remainder|  
|%\=|N\/D|%\=|Mod|  
|\* \(binario\)|\*|\*|Multiply|  
|\*\=|N\/D|\*\=|Multiply|  
|~|Not|~|OnesComplement|  
|\>\>|\>\>|\>\>|RightShift|  
|\>\>\=|N\/D|\>\>\=|RightShift|  
|\- \(binario\)|\- \(binario\)|\- \(binario\)|Restar|  
|\-\=|N\/D|\-\=|Restar|  
|true|IsTrue|N\/D|IsTrue \(propiedad\)|  
|\- \(unario\)|N\/D|\-|Negate|  
|\+ \(unario\)|N\/D|\+|Plus|  
|false|IsFalse|False|IsTrue \(propiedad\)|  
  
 N\/D \=\= no se puede sobrecargar en el lenguaje seleccionado.  
  
 La regla también comprueba los operadores de conversión implícitos y explícitos de un tipo \(`SomeType`\) comprobando los métodos denominados `ToSomeType` y `FromSomeType`.  
  
 En el lenguaje C\#, cuando se sobrecarga un operador binario, el operador correspondiente de asignación \(si existe\) también se sobrecarga de modo implícito.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, implemente el método alternativo para el operador; denomínelo utilizando el nombre alternativo recomendado.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla si va a implementar una biblioteca compartida.  Las aplicaciones pueden omitir una advertencia de esta regla.  
  
## Ejemplo  
 En el siguiente ejemplo se define una estructura que infringe esta regla.  Para corregir el ejemplo, agregue un método público `Add(int x, int y)` a la estructura.  
  
 [!code-cs[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]  
  
## Reglas relacionadas  
 [CA1046: No sobrecargar el operador de igualdad en los tipos de referencia](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2226: Los operadores deben tener sobrecargar simétricas](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Reemplazar Equals al sobrecargar operadores de igualdad](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: Reemplazar el método GetHashCode al reemplazar el método Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Sobrecargar el operador de igualdad al reemplazar el tipo de valor de igualdad](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)