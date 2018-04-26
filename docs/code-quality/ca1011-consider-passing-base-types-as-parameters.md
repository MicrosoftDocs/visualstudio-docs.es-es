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
ms.workload:
- multiple
ms.openlocfilehash: 1eaa68b6046fd2d3cfb6370b18de2b478b16db9d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
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
 Cuando en una declaración de método se especifica un tipo base como parámetro, cualquier tipo derivado del tipo base puede pasarse al método como el argumento correspondiente. Cuando se utiliza el argumento en el cuerpo del método, el método específico que se ejecuta depende del tipo del argumento. Si la funcionalidad adicional proporcionada por el tipo derivado no resulta necesaria, el uso del tipo base permite que el método se utilice más ampliamente.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el tipo del parámetro a su tipo base.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla

-   Si el método necesita la funcionalidad específica que proporciona el tipo derivado

     \- o -

-   para exigir que sólo el tipo derivado, o un tipo más derivado, se pasa al método.

 En estos casos, el código será más sólido debido a la comprobación de tipos inflexibles proporcionada por el compilador y el tiempo de ejecución.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método, `ManipulateFileStream`, que se puede utilizar únicamente con un <xref:System.IO.FileStream> objeto, lo que infringe esta regla. Un segundo método, `ManipulateAnyStream`, cumple la regla reemplazando el <xref:System.IO.FileStream> parámetro mediante el uso de un <xref:System.IO.Stream>.

 [!code-csharp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CSharp/ca1011-consider-passing-base-types-as-parameters_1.cs)]
 [!code-cpp[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/CPP/ca1011-consider-passing-base-types-as-parameters_1.cpp)]
 [!code-vb[FxCop.Design.ConsiderPassingBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1011-consider-passing-base-types-as-parameters_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1059: Los miembros no deben exponer algunos tipos concretos](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)