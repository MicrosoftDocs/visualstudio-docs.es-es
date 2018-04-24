---
title: 'CA1414: Marque los argumentos P Invoke booleanos con MarshalAs'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
ms.workload:
- multiple
ms.openlocfilehash: eb956c4a5c19441aaa85539909fca3cc7446fd97
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Marque los argumentos P/Invoke booleanos con MarshalAs
|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|Identificador de comprobación|CA1414|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Método de invocación de plataforma declaración incluye un <xref:System.Boolean?displayProperty=fullName> parámetro o valor devuelto, pero la <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> no se aplica el atributo para el parámetro o valor devuelto.

## <a name="rule-description"></a>Descripción de la regla
 Una plataforma de invocación de método tiene acceso al código no administrado y se define utilizando la `Declare` palabra clave en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Especifica el comportamiento de serialización que se utiliza para convertir a tipos de datos entre código administrado y no administrado. Tipos de bases de datos simples, como <xref:System.Byte?displayProperty=fullName> y <xref:System.Int32?displayProperty=fullName>, tiene una única representación en código no administrado y no requieren la especificación de su comportamiento de serialización; common language runtime proporciona automáticamente el comportamiento correcto.

 El <xref:System.Boolean> tipo de datos tiene varias representaciones en código no administrado. Cuando el <xref:System.Runtime.InteropServices.MarshalAsAttribute> no se especifica, el valor predeterminado el comportamiento de cálculo de referencias del <xref:System.Boolean> tipo de datos es <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Se trata de un entero de 32 bits, que no es adecuado en todas las circunstancias. La representación booleana requerida por el método no administrado debe determinarse y coincide con la correspondiente <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool es el tipo BOOL de Win32, que siempre es de 4 bytes. UnmanagedType.U1 se debe utilizar para C++ `bool` u otros tipos de 1 byte.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, aplique <xref:System.Runtime.InteropServices.MarshalAsAttribute> a la <xref:System.Boolean> parámetro o valor devuelto. Establezca el valor del atributo a la correspondiente <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Aunque el valor predeterminado el comportamiento del cálculo de referencias es adecuado, el código se mantiene más fácilmente cuando se especifica explícitamente el comportamiento.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra los métodos que se marcan con la correspondiente de la invocación de plataforma dos <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributos.

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1901: Las declaraciones P/Invoke deben ser portátiles](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Especifique cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Vea también
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Interoperar con código no administrado](/dotnet/framework/interop/index)