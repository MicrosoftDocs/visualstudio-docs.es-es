---
title: 'CA1026: No deben usarse parámetros predeterminados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 888e1b5d551e357eb732dfe3f7661d51cbdf089d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923141"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: No deben usarse parámetros predeterminados

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|Identificador de comprobación|CA1026|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Un tipo visible externamente contiene un método visible externamente que utiliza un parámetro predeterminado.

## <a name="rule-description"></a>Descripción de la regla
Los métodos que utilizan parámetros predeterminados se permiten en el Common Language Specification (CLS); sin embargo, CLS permite a los compiladores omitir los valores que se asignan a estos parámetros. El código que se escribe para los compiladores que omiten los valores de parámetro predeterminados debe proporcionar explícitamente argumentos para cada parámetro predeterminado. Para mantener el comportamiento que desea en los lenguajes de programación, los métodos que utilizan parámetros predeterminados deben reemplazarse por sobrecargas de método que proporcionan los parámetros predeterminados.

El compilador omite los valores de los parámetros predeterminados C++ para la extensión administrada para cuando tiene acceso al código administrado. El compilador Visual Basic admite métodos que tienen parámetros predeterminados que utilizan la palabra clave [opcional](/dotnet/visual-basic/language-reference/modifiers/optional) .

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, reemplace el método que usa los parámetros predeterminados con sobrecargas de método que proporcionan los parámetros predeterminados.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un método que usa parámetros predeterminados y los métodos sobrecargados que proporcionan una funcionalidad equivalente.

[!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1025: Reemplazar argumentos repetitivos con una matriz params](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Vea también
[Independencia del lenguaje y componentes independientes del lenguaje](/dotnet/standard/language-independence-and-language-independent-components)