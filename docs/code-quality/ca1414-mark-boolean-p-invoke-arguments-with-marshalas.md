---
title: 'CA1414: Marcar los argumentos P-Invoke booleanos con MarshalAs'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 31159ec2e90c96579940f276f1d0410cdf3dadb1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931442"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Marcar los argumentos P/Invoke booleanos con MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|Identificador de comprobación|CA1414|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Método de invocación de una plataforma declaración incluye una <xref:System.Boolean?displayProperty=fullName> parámetro o valor devuelto, pero el <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> no se aplica el atributo en el valor devuelto o parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Una plataforma de invocación de método tiene acceso al código no administrado y se define utilizando el `Declare` palabra clave en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Especifica el comportamiento de serialización que se utiliza para convertir a tipos de datos entre código administrado y no administrado. Tipos de muchos datos simples, como <xref:System.Byte?displayProperty=fullName> y <xref:System.Int32?displayProperty=fullName>, tienen una representación única en código no administrado y no requieren la especificación de su comportamiento de serialización; common language runtime proporciona automáticamente el comportamiento correcto.

 El <xref:System.Boolean> tipo de datos tiene varias representaciones en código no administrado. Cuando el <xref:System.Runtime.InteropServices.MarshalAsAttribute> no se especifica, el valor predeterminado el cálculo de referencias para el <xref:System.Boolean> es de tipo de datos <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Se trata de un entero de 32 bits, que no es adecuado para todas las circunstancias. La representación Boolean requerido por el método no administrado debe determinarse y coincide con la correspondiente <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool es el tipo BOOL de Win32, que siempre es de 4 bytes. UnmanagedType.U1 debe usarse para C++ `bool` u otros tipos de 1 byte.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, se aplican <xref:System.Runtime.InteropServices.MarshalAsAttribute> a la <xref:System.Boolean> parámetro o valor devuelto. Establezca el valor del atributo correspondiente <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima las advertencias de esta regla. Incluso si el comportamiento de serialización predeterminado es adecuado, el código se mantiene más fácilmente cuando se especifica explícitamente el comportamiento.

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra los métodos marcados con los valores adecuados de invocación de plataforma <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributos.

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1901: Las declaraciones P/Invoke deben ser portátiles](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Especifique serialización para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Vea también

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Interoperating with Unmanaged Code](/dotnet/framework/interop/index) (Interoperar con código no administrado)