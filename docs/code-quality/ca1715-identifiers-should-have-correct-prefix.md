---
title: 'CA1715: Los identificadores deberían tener el prefijo correcto'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 883b5a5a00f5be3203b8113103193dd3e597ddfd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Los identificadores deberían tener el prefijo correcto
|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|Identificador de comprobación|CA1715|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se desencadena en interfaces.<br /><br /> Poco problemático: cuando se desencadena en parámetros de tipo genérico.|

## <a name="cause"></a>Motivo
 El nombre de una interfaz visible externamente no empieza por una mayúscula 'I'.

 -o bien-

 El nombre de un parámetro de tipo genérico en un tipo visible externamente o el método no inicia con una mayúscula ' t '.

## <a name="rule-description"></a>Descripción de la regla
 Por convención, los nombres de determinados elementos de programación comienzan con un prefijo concreto.

 Nombres de interfaz deben empezar con una mayúscula 'I' seguida de otra letra mayúscula. Esta regla notifica las infracciones para los nombres de interfaz como 'MyInterface' y 'IsolatedInterface'.

 Nombres de parámetro de tipo genérico deben comenzar con una mayúscula ' t ' y, opcionalmente, puede ir seguido por otra letra mayúscula. Esta regla informa de las infracciones de los nombres de parámetros de tipo genérico como "V" y 'Type'.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre el identificador se incluyen el prefijo correctamente.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 **En el ejemplo siguiente se muestra una interfaz con nombre incorrectamente.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

## <a name="example"></a>Ejemplo
 **En el ejemplo siguiente se corrige la infracción anterior agregando el prefijo de la interfaz con 'I'.**

 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="example"></a>Ejemplo
 **En el ejemplo siguiente se muestra un parámetro de tipo genérico incorrectamente con nombre.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

## <a name="example"></a>Ejemplo
 **En el ejemplo siguiente se corrige la infracción anterior agregando el prefijo de parámetro de tipo genérico ' t '.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1722: Los identificadores no deberían tener el prefijo incorrecto](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)