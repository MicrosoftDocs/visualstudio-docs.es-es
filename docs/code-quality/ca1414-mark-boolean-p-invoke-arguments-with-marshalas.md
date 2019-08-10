---
title: 'CA1414: Marcar los argumentos P-Invoke booleanos con MarshalAs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e8d47b73009e0bd742c989ddc0311644453e5d9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921866"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Marcar los argumentos P/Invoke booleanos con MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|Identificador de comprobación|CA1414|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
Una declaración de método de invocación <xref:System.Boolean?displayProperty=fullName> de plataforma incluye un parámetro o <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> un valor devuelto, pero el atributo no se aplica al parámetro o valor devuelto.

## <a name="rule-description"></a>Descripción de la regla
Un método de invocación de plataforma tiene acceso al código no administrado y se define `Declare` mediante la [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] palabra clave <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>en o. <xref:System.Runtime.InteropServices.MarshalAsAttribute>especifica el comportamiento de cálculo de referencias que se usa para convertir tipos de datos entre código administrado y no administrado. Muchos tipos de datos simples, <xref:System.Byte?displayProperty=fullName> como y <xref:System.Int32?displayProperty=fullName>, tienen una única representación en código no administrado y no requieren la especificación de su comportamiento de serialización; el Common Language Runtime proporciona automáticamente el comportamiento correcto.

El <xref:System.Boolean> tipo de datos tiene varias representaciones en el código no administrado. Cuando no <xref:System.Boolean> <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>se especifica, el comportamiento predeterminado del cálculo de referencias para el tipo de datos es. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Se trata de un entero de 32 bits, que no es adecuado en todas las circunstancias. La representación booleana que requiere el método no administrado debe determinarse y coincidir con la adecuada <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool es el tipo BOOL de Win32, que siempre es 4 bytes. UnmanagedType. U1 debe usarse para C++ `bool` u otros tipos de 1 byte.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, <xref:System.Runtime.InteropServices.MarshalAsAttribute> aplique <xref:System.Boolean> al parámetro o al valor devuelto. Establezca el valor del atributo en el correspondiente <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima las advertencias de esta regla. Incluso si el comportamiento del cálculo de referencias predeterminado es adecuado, el código se mantiene más fácilmente cuando se especifica explícitamente el comportamiento.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran métodos de invocación de plataforma marcados con los atributos adecuados <xref:System.Runtime.InteropServices.MarshalAsAttribute> .

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Reglas relacionadas
[CA1901: Las declaraciones P/Invoke deben ser portátiles](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

[CA2101: Especificar serialización para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Vea también

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)