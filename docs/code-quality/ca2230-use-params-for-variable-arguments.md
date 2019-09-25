---
title: 'CA2230: Usar parámetros en argumentos de variable'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseParamsForVariableArguments
- CA2230
helpviewer_keywords:
- CA2230
- UseParamsForVariableArguments
ms.assetid: bf98b733-4855-4110-9f16-eba5a9e79421
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0639d30771b3a6bb288ddbf9644dda2efcd5f90d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231356"
---
# <a name="ca2230-use-params-for-variable-arguments"></a>CA2230: Usar parámetros en argumentos de variable

|||
|-|-|
|TypeName|UseParamsForVariableArguments|
|Identificador de comprobación|CA2230|
|Categoría|Microsoft.Usage|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo
Un tipo público o protegido contiene un método público o protegido que usa la `VarArgs` Convención de llamada.

## <a name="rule-description"></a>Descripción de la regla
La `VarArgs` Convención de llamada se utiliza con ciertas definiciones de método que toman un número variable de parámetros. Un método que usa `VarArgs` la Convención de llamada no es compatible Common Language Specification (CLS) y puede que no sea accesible a través de lenguajes de programación.

En C#, la `VarArgs` Convención de llamada se usa cuando la lista de parámetros de un método `__arglist` finaliza con la palabra clave. Visual Basic no admite la `VarArgs` Convención de llamada y visual C++ solo permite su uso en código no administrado que utiliza la notación de elipse `...` .

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla C#en, utilice la palabra clave [params](/dotnet/csharp/language-reference/keywords/params) en `__arglist`lugar de.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestran dos métodos, uno que infringe la regla y otro que cumple la regla.

[!code-csharp[FxCop.Usage.UseParams#1](../code-quality/codesnippet/CSharp/ca2230-use-params-for-variable-arguments_1.cs)]

## <a name="see-also"></a>Vea también

- <xref:System.Reflection.CallingConventions?displayProperty=fullName>
- [Independencia del lenguaje y componentes independientes del lenguaje](/dotnet/standard/language-independence-and-language-independent-components)