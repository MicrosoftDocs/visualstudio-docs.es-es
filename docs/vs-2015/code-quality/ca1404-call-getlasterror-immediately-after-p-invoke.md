---
title: 'CA1404: Llame a GetLastError inmediatamente después de P / Invoke | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a7f1f4d036bd035368cce10684899d880481e37b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58986792"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Llamar a GetLastError inmediatamente después de P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|Identificador de comprobación|CA1404|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Se realiza una llamada a la <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> método o el equivalente de Win32 `GetLastError` función y la llamada que se incluye inmediatamente anterior no es una plataforma de invocación de método.

## <a name="rule-description"></a>Descripción de la regla
 Una plataforma de invocación de método tiene acceso al código no administrado y se define utilizando el `Declare` palabra clave en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo. Por lo general, en caso de error, las funciones no administradas llamar a Win32 `SetLastError` función para establecer un código de error que está asociado con el error. El llamador de la función con errores, las llamadas Win32 `GetLastError` función para recuperar el código de error y determinar la causa del error. El código de error se mantiene por subproceso y se sobrescribe con la siguiente llamada a `SetLastError`. Después de una llamada a una plataforma con errores de invocación de método, el código administrado puede recuperar el código de error mediante una llamada a la <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> método. Dado que el código de error que pueda sobrescribirse mediante llamadas internas desde otros métodos de la biblioteca de clases administradas, el `GetLastError` o <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> debe llamarse al método inmediatamente después de la invocación de plataforma llamada al método.

 La regla omite las llamadas a los siguientes miembros administrados cuando se producen entre la llamada a la plataforma de invocación de método y la llamada a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Estos miembros no cambian el error de código y son útiles para determinar el éxito de algunas plataformas invocan llamadas a métodos.

-   <xref:System.IntPtr.Zero?displayProperty=fullName>

-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, mueva la llamada a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> para que sigue inmediatamente a la llamada a la plataforma de invocación de método.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el código entre la plataforma de invocar la llamada al método y el <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> llamada al método no puede producir explícitamente o implícitamente cambiar el código de error.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un método que infringe la regla y un método que cumple la regla.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1060: Mueva P/Invokes a la clase NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Deben existir puntos de entrada P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke no deben estar visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Especifique serialización para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Utilizar equivalentes administrados de la API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
