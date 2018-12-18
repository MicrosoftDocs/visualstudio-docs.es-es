---
title: 'CA1800: No convertir innecesariamente'
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: a1db0f421f72e5b63b14c95a706b738bea1a4174
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550523"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: No convertir innecesariamente

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|Identificador de comprobación|CA1800|
|Categoría|Microsoft.Performance|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
Un método realiza conversiones de tipos duplicadas en uno de sus argumentos o variables locales.

Para un análisis completo por esta regla, el ensamblado probado debe compilarse usando información de depuración y el archivo de programa asociado (.pdb) de la base de datos debe estar disponible.

## <a name="rule-description"></a>Descripción de la regla
Las conversiones duplicadas reducen el rendimiento, sobre todo cuando se realizan en instrucciones de iteración compactas. Para las operaciones de conversión explícita de duplicados, almacena el resultado de la conversión en una variable local y use la variable local en lugar de las operaciones de conversión duplicadas.

Si C# `is` operador se usa para comprobar si la conversión se realizará correctamente antes de realiza la conversión real, considere la posibilidad de probar el resultado de la `as` operador en su lugar. Esto proporciona la misma funcionalidad sin la operación de conversión implícita que se realiza mediante el `is` operador. O bien, en C# 7.0 y versiones posteriores, use la `is` operador con [coincidencia de patrones](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) para comprobar la conversión de tipos y convertir la expresión a una variable de ese tipo en un solo paso.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, modifique la implementación del método para minimizar el número de operaciones de conversión.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla u omitir completamente, la regla si el rendimiento no constituye un problema.

## <a name="examples"></a>Ejemplos
 El ejemplo siguiente muestra un método que infringe la regla mediante el uso de C# `is` operador. Un segundo método cumple la regla reemplazando el `is` operador con una prueba con el resultado de la `as` operador, lo que disminuye el número de operaciones de conversión por iteración de dos a uno. Un tercer método también cumple la regla mediante el uso de `is` con [coincidencia de patrones](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) para crear una variable del tipo deseado si la conversión de tipos se realizaría correctamente.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 El ejemplo siguiente muestra un método, `start_Click`, que tiene varias conversiones explícitas duplicadas, lo que infringe la regla y un método, `reset_Click`, que cumple la regla almacenando la conversión en una variable local.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Vea también

- [As (referencia de C#)](/dotnet/csharp/language-reference/keywords/as)
- [Is (referencia de C#)](/dotnet/csharp/language-reference/keywords/is)