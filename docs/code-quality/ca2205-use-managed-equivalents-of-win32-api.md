---
title: 'CA2205: Utilizar equivalentes administrados de la API Win32'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ad26dcbbbef5a34796ca0aa134653c3c9df5d763
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253257"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Utilizar equivalentes administrados de la API Win32

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|Identificador de comprobación|CA2205|
|Categoría|Microsoft.Usage|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Se define un método de invocación de plataforma y existe un método con la funcionalidad equivalente en .NET.

## <a name="rule-description"></a>Descripción de la regla

Se usa un método de invocación de plataforma para llamar a una función dll no administrada y <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> se define mediante el `Declare` atributo o la palabra clave en Visual Basic. Un método de invocación de plataforma definido incorrectamente puede provocar excepciones en tiempo de ejecución debido a problemas como una función errónea, una asignación errónea de tipos de datos de parámetros y valores devueltos, y especificaciones de campo incorrectas, como la Convención de llamada y el carácter conjunto. Si está disponible, es más sencillo y menos propenso a errores llamar al método administrado equivalente que definir y llamar directamente al método no administrado. Llamar a un método de invocación de plataforma también puede provocar problemas de seguridad adicionales que se deben solucionar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, reemplace la llamada a la función no administrada por una llamada a su equivalente administrado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias

Suprima una advertencia de esta regla si el método de reemplazo sugerido no proporciona la funcionalidad necesaria.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra una definición de método de invocación de plataforma que infringe la regla. Además, se muestran las llamadas al método de invocación de plataforma y al método administrado equivalente.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1404: Llamar a GetLastError inmediatamente después de P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: Movimiento P/Invoke a la clase NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: Deben existir puntos de entrada P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: Las invocacións P/no deben ser visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: Especificar serialización para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)