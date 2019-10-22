---
title: 'CA1404: llamar a GetLastError inmediatamente después de P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2664837c17894f7ca336d650a7e08e21c45d955f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661319"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Llame a GetLastError inmediatamente después de P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|Identificador de comprobación|CA1404|
|Categoría|Microsoft. Interoperability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Se realiza una llamada al método <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> o a la función `GetLastError` de Win32 equivalente, y la llamada que viene inmediatamente antes de no es un método de invocación de plataforma.

## <a name="rule-description"></a>Descripción de la regla
 Un método de invocación de plataforma tiene acceso al código no administrado y se define mediante la palabra clave `Declare` en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o el atributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Normalmente, en caso de error, las funciones no administradas llaman a la función `SetLastError` de Win32 para establecer un código de error asociado al error. El autor de la llamada de la función failed llama a la función `GetLastError` de Win32 para recuperar el código de error y determinar la causa del error. El código de error se mantiene por subproceso y se sobrescribe con la siguiente llamada a `SetLastError`. Después de una llamada a un método de invocación de plataforma con errores, el código administrado puede recuperar el código de error llamando al método <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Dado que las llamadas internas de otros métodos de la biblioteca de clases administradas pueden sobrescribir el código de error, se debe llamar al método `GetLastError` o <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> inmediatamente después de la llamada al método de invocación de plataforma.

 La regla omite las llamadas a los siguientes miembros administrados cuando se producen entre la llamada al método de invocación de plataforma y la llamada a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Estos miembros no cambian el código de error y son útiles para determinar el éxito de algunas llamadas a métodos de invocación de plataforma.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, mueva la llamada a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> para que siga inmediatamente a la llamada al método de invocación de plataforma.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el código entre la llamada al método de invocación de plataforma y la llamada al método <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> no pueden hacer que el código de error cambie.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un método que infringe la regla y un método que cumple la regla.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1060: Mueva P/Invokes a la clase NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Deben existir puntos de entrada P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: Los elementos P/Invoke no deben estar visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Especifique cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Utilizar equivalentes administrados de la API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
