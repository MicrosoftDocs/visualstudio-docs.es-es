---
title: 'CA1800: No convertir innecesariamente'
ms.date: 10/26/2017
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 942a9911d0dadbf5f130344735ca9aa504cb71fd
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921596"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: No convertir innecesariamente

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|Identificador de comprobación|CA1800|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
Un método realiza conversiones duplicadas en uno de sus argumentos o variables locales.

Para realizar un análisis completo de esta regla, el ensamblado probado se debe compilar con la información de depuración y el archivo de base de datos de programa (. pdb) asociado debe estar disponible.

## <a name="rule-description"></a>Descripción de la regla
Las conversiones duplicadas reducen el rendimiento, sobre todo cuando se realizan en instrucciones de iteración compactas. En el caso de operaciones de conversión duplicadas explícitas, almacene el resultado de la conversión en una variable local y use la variable local en lugar de las operaciones de conversión duplicada.

Si el C# `is` operador se usa para comprobar si la conversión se realizará correctamente antes de que se realice la conversión real, considere `as` la posibilidad de probar el resultado del operador en su lugar. Esto proporciona la misma funcionalidad sin la operación de conversión implícita realizada por el `is` operador. O bien, C# en 7,0 y versiones posteriores, `is` utilice el operador con [coincidencia de patrones](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) para comprobar la conversión de tipos y convertir la expresión en una variable de ese tipo en un solo paso.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, modifique la implementación del método para minimizar el número de operaciones de conversión.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla o pasar por alto la regla por completo si el rendimiento no es un problema.

## <a name="examples"></a>Ejemplos
En el ejemplo siguiente se muestra un método que infringe la regla mediante el C# `is` operador. Un segundo método cumple la regla reemplazando el `is` operador por una prueba con el resultado `as` del operador, lo que reduce el número de operaciones de conversión por iteración de dos a uno. Un tercer método también cumple la regla `is` mediante con la coincidencia de [patrones](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) para crear una variable del tipo deseado si la conversión de tipos se realiza correctamente.

[!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

En el ejemplo siguiente se muestra un `start_Click`método,, que tiene varias conversiones explícitas duplicadas, que infringe la regla, y `reset_Click`un método,, que cumple la regla almacenando la conversión en una variable local.

[!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
[!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Vea también

- [as (C# referencia)](/dotnet/csharp/language-reference/keywords/as)
- [is (C# referencia)](/dotnet/csharp/language-reference/keywords/is)