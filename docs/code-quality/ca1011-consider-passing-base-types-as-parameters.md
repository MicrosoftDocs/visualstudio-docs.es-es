---
title: 'CA1011: Considere pasar los tipos base como parámetros'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b968a94b76f0b2161eef84fdad2cf01288165e65
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899414"
---
# <a name="ca1011-consider-passing-base-types-as-parameters"></a>CA1011: Considere pasar los tipos base como parámetros

|||
|-|-|
|TypeName|ConsiderPassingBaseTypesAsParameters|
|Identificador de comprobación|CA1011|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo

Una declaración de método incluye un parámetro formal que es un tipo derivado y el método llama a solo los miembros del tipo base del parámetro.

## <a name="rule-description"></a>Descripción de la regla

Cuando en una declaración de método se especifica un tipo base como parámetro, cualquier tipo derivado del tipo base puede pasarse al método como el argumento correspondiente. Cuando el argumento se utiliza en el cuerpo del método, el método específico que se ejecuta depende del tipo del argumento. Si no se requiere la funcionalidad adicional proporcionada por el tipo derivado, el uso del tipo base permite un uso más amplio del método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, cambie el tipo del parámetro a su tipo base.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Es seguro suprimir una advertencia de esta regla

- Si el método requiere la funcionalidad específica que proporciona el tipo derivado

     \- o -

- para exigir que solo el tipo derivado, o un tipo más derivado, se pasa al método.

En estos casos, el código será más sólido debido a la comprobación de tipos seguros proporcionado por el compilador y el tiempo de ejecución.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra un método, `ManipulateFileStream`, que puede utilizarse solo con un <xref:System.IO.FileStream> objeto, lo que infringe esta regla. Un segundo método, `ManipulateAnyStream`, cumple la regla reemplazando el <xref:System.IO.FileStream> parámetro mediante el uso de un <xref:System.IO.Stream>.

[!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
[!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
[!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

[CA1059: Los miembros no deben exponer algunos tipos concretos](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)