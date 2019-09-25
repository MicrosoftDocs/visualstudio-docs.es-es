---
title: 'CA1011: Considerar pasar los tipos base como parámetros'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ConsiderPassingBaseTypesAsParameters
- CA1011
helpviewer_keywords:
- CA1011
- ConsiderPassingBaseTypesAsParameters
ms.assetid: ce1e1241-dcf4-419b-9363-1d5bc4989279
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: dcb5937f58088684e7bfc204ab4143434b0684ae
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236405"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Considerar pasar los tipos base como parámetros

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|Identificador de comprobación|CA1011|
|Categoría|Microsoft.Design|
|Cambio importante|Problemático|

## <a name="cause"></a>Motivo

Una declaración de método incluye un parámetro formal que es un tipo derivado y el método solo llama a los miembros del tipo base del parámetro.

## <a name="rule-description"></a>Descripción de la regla

Cuando en una declaración de método se especifica un tipo base como parámetro, cualquier tipo derivado del tipo base puede pasarse al método como el argumento correspondiente. Cuando se usa el argumento dentro del cuerpo del método, el método específico que se ejecuta depende del tipo del argumento. Si no se requiere la funcionalidad adicional proporcionada por el tipo derivado, el uso del tipo base permite un uso más amplio del método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie el tipo del parámetro a su tipo base.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Es seguro suprimir una advertencia de esta regla

- Si el método requiere la funcionalidad específica que proporciona el tipo derivado

     \- o -

- para aplicar que solo el tipo derivado, o un tipo más derivado, se pasa al método.

En estos casos, el código será más robusto debido a la comprobación de tipos segura proporcionada por el compilador y el tiempo de ejecución.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra un `ManipulateFileStream`método,, que solo se puede usar <xref:System.IO.FileStream> con un objeto, que infringe esta regla. Un segundo método, `ManipulateAnyStream`, cumple la regla reemplazando el <xref:System.IO.FileStream> parámetro <xref:System.IO.Stream>mediante.

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

[CA1059: Los miembros no deben exponer determinados tipos concretos](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)