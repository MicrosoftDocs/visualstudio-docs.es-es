---
title: 'CA1026: No debería utilizar parámetros predeterminados'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec4a248be45489eafcbd208329a52cfc06d8237f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825358"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: No debería utilizar parámetros predeterminados

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|Identificador de comprobación|CA1026|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo visible externamente contiene un método visible externamente que utiliza un parámetro predeterminado.

## <a name="rule-description"></a>Descripción de la regla
 Se permiten los métodos que utilizan parámetros predeterminados en el Common Language Specification (CLS); Sin embargo, CLS permite que los compiladores omitan los valores que se asignan a estos parámetros. Código que se escribe para los compiladores omitan los valores de parámetro predeterminado debe proporcionar explícitamente los argumentos para cada parámetro predeterminado. Para mantener el comportamiento que desea en lenguajes de programación, se deben reemplazar los métodos que utilizan parámetros predeterminados con sobrecargas de método que proporcionan los parámetros predeterminados.

 Cuando tiene acceso a código administrado, el compilador omite los valores de parámetros predeterminados de extensión administrada de C++. El compilador de Visual Basic admite métodos que tienen parámetros predeterminados que usan el [opcional](/dotnet/visual-basic/language-reference/modifiers/optional) palabra clave.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace el método que utiliza los parámetros predeterminados con sobrecargas de método que proporcionan los parámetros predeterminados.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método que utiliza los parámetros predeterminados y los métodos sobrecargados que proporcionan una funcionalidad equivalente.

 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1025: Reemplaza argumentos repetitivos con una matriz de parámetros](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Vea también
 [Independencia del lenguaje y componentes independientes del lenguaje](/dotnet/standard/language-independence-and-language-independent-components)