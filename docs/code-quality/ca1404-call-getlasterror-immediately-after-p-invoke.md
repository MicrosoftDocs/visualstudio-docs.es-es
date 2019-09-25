---
title: 'CA1404: Llamar a GetLastError inmediatamente después de P-Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ab789e578dd8603f604cdb00aa5d236250d13670
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235047"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Llamar a GetLastError inmediatamente después de P/Invoke

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|Identificador de comprobación|CA1404|
|Categoría|Microsoft.Interoperability|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo

Se realiza una llamada al <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> método o a la función de Win32 `GetLastError` equivalente, y la llamada que viene inmediatamente antes de no es un método de invocación de plataforma.

## <a name="rule-description"></a>Descripción de la regla
Un método de invocación de plataforma tiene acceso al código no administrado y se define `Declare` mediante la [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] palabra clave <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> en o el atributo. Normalmente, en caso de error, las funciones no administradas `SetLastError` llaman a la función de Win32 para establecer un código de error asociado al error. El autor de la llamada de la función failed `GetLastError` llama a la función de Win32 para recuperar el código de error y determinar la causa del error. El código de error se mantiene por subproceso y se sobrescribe con la siguiente llamada a `SetLastError`. Después de una llamada a un método de invocación de plataforma con errores, el código administrado puede recuperar <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> el código de error llamando al método. Dado que las llamadas internas de otros métodos de biblioteca de clases administradas pueden sobrescribir el código de `GetLastError` error <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> , se debe llamar al método o inmediatamente después de la llamada al método de invocación de plataforma.

La regla omite las llamadas a los siguientes miembros administrados cuando se producen entre la llamada al método de invocación de plataforma y <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>la llamada a. Estos miembros no cambian el código de error y son útiles para determinar el éxito de algunas llamadas a métodos de invocación de plataforma.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, mueva la llamada <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> a para que siga inmediatamente a la llamada al método de invocación de plataforma.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
Es seguro suprimir una advertencia de esta regla si el código entre la llamada al método de invocación de <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> plataforma y la llamada al método no pueden hacer que el código de error cambie de forma explícita o implícita.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un método que infringe la regla y un método que cumple la regla.

[!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
[!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1060: Movimiento P/Invoke a la clase NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

[CA1400: Deben existir puntos de entrada P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

[CA1401: Las invocacións P/no deben ser visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

[CA2101: Especificar serialización para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

[CA2205: Usar equivalentes administrados de la API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)