---
title: 'CA1715: Los identificadores deben tener el prefijo correcto'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7c1e50c814c22ccddb43e90b41752f3f0bc5797e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986964"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Los identificadores deben tener el prefijo correcto

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|Identificador de comprobación|CA1715|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático: cuando se desencadena en interfaces.<br /><br /> Indivisible - cuando se genera en parámetros de tipo genérico.|

## <a name="cause"></a>Motivo
 El nombre de una interfaz visible externamente no empieza por una mayúscula 'I'.

 O bien

 El nombre de un parámetro de tipo genérico en un tipo visible externamente o el método no inicia con una mayúscula ' t '.

## <a name="rule-description"></a>Descripción de la regla
 Por convención, los nombres de ciertos elementos de programación se inicie con un prefijo específico.

 Nombres de interfaz deben empezar con una mayúscula 'I' seguida de otra letra mayúscula. Esta regla notifica las infracciones de nombres de interfaz como 'MyInterface' y 'IsolatedInterface'.

 Los nombres de parámetro de tipo genérico deben comenzar con una mayúscula ' t ' y, opcionalmente, puede ir seguida por otra letra mayúscula. Esta regla notifica las infracciones de los nombres de parámetro de tipo genérico, como 'V' y 'Type'.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre el identificador se incluyen el prefijo correctamente.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 **El ejemplo siguiente muestra una interfaz denominada incorrectamente.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

## <a name="example"></a>Ejemplo
 **El ejemplo siguiente corrige la infracción anterior agregando el prefijo de la interfaz 'I'.**

 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="example"></a>Ejemplo
 **El ejemplo siguiente muestra un parámetro de tipo genérico incorrectamente con nombre.**

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