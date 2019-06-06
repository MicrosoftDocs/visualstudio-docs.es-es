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
ms.openlocfilehash: 99d53296ad72aef1910a39299be64c7cb03dd49a
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714717"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Utilizar equivalentes administrados de la API Win32

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|Identificador de comprobación|CA2205|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Una invocación de plataforma se define el método y existe un método con la funcionalidad equivalente en. NET.

## <a name="rule-description"></a>Descripción de la regla

Una plataforma de invocación de método se usa para llamar a una función DLL no administrada y se define utilizando el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo, o la `Declare` palabra clave en Visual Basic. Método de invocación de una plataforma definida incorrectamente puede generar excepciones en tiempo de ejecución debido a problemas como una función con nombre incorrecto, una asignación de tipos de datos de valor devueltos y de parámetro y las especificaciones de campo incorrecto, como la convención de llamada y el carácter defectuosa conjunto. Si está disponible, es más sencillo y menos propenso a errores llamar al método administrado equivalente que to definir y llamar directamente al método no administrado. Una llamada a una plataforma de invocar el método también pueden provocar problemas de seguridad adicionales que deban solucionarse.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, reemplace la llamada a la función no administrada con una llamada a su equivalente administrado.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

Suprima una advertencia de esta regla si el método de reemplazo sugerido no proporciona la funcionalidad necesaria.

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra una plataforma de invocación de definición de método que infringe la regla. Además, las llamadas a la plataforma de invocación de método y se muestra el método administrado equivalente.

[!code-csharp[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/CSharp/ca2205-use-managed-equivalents-of-win32-api_1.cs)]
[!code-vb[FxCop.Usage.ManagedEquivalents#1](../code-quality/codesnippet/VisualBasic/ca2205-use-managed-equivalents-of-win32-api_1.vb)]

## <a name="related-rules"></a>Reglas relacionadas

- [CA1404: Llame a GetLastError inmediatamente después de P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)
- [CA1060: Mueva P/Invokes a la clase NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)
- [CA1400: Deben existir puntos de entrada P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)
- [CA1401: P/Invoke no deben estar visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)
- [CA2101: Especifique serialización para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)