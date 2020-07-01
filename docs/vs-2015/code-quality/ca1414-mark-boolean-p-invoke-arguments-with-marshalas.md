---
title: 'CA1414: marcar argumentos P-Invoke booleanos con MarshalAs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 783f7fad05cad18efea2f83b6d76c4c9e644f119
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548387"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Marque los argumentos P/Invoke booleanos con MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|Identificador de comprobación|CA1414|
|Category|Microsoft. Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Una declaración de método de invocación de plataforma incluye un <xref:System.Boolean?displayProperty=fullName> parámetro o un valor devuelto, pero el <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> atributo no se aplica al parámetro o valor devuelto.

## <a name="rule-description"></a>Descripción de la regla
 Un método de invocación de plataforma tiene acceso al código no administrado y se define mediante la `Declare` palabra clave en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . <xref:System.Runtime.InteropServices.MarshalAsAttribute>especifica el comportamiento de cálculo de referencias que se usa para convertir tipos de datos entre código administrado y no administrado. Muchos tipos de datos simples, como <xref:System.Byte?displayProperty=fullName> y <xref:System.Int32?displayProperty=fullName> , tienen una única representación en código no administrado y no requieren la especificación de su comportamiento de serialización; el Common Language Runtime proporciona automáticamente el comportamiento correcto.

 El <xref:System.Boolean> tipo de datos tiene varias representaciones en el código no administrado. Cuando <xref:System.Runtime.InteropServices.MarshalAsAttribute> no se especifica, el comportamiento predeterminado del cálculo de referencias para el <xref:System.Boolean> tipo de datos es <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . Se trata de un entero de 32 bits, que no es adecuado en todas las circunstancias. La representación booleana que requiere el método no administrado debe determinarse y coincidir con la adecuada <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . UnmanagedType. bool es el tipo BOOL de Win32, que siempre es 4 bytes. UnmanagedType. U1 debe usarse para C++ `bool` u otros tipos de 1 byte. Para obtener más información, vea [serialización predeterminada para tipos booleanos](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, aplique <xref:System.Runtime.InteropServices.MarshalAsAttribute> al <xref:System.Boolean> parámetro o al valor devuelto. Establezca el valor del atributo en el correspondiente <xref:System.Runtime.InteropServices.UnmanagedType> .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Incluso si el comportamiento del cálculo de referencias predeterminado es adecuado, el código se mantiene más fácilmente cuando se especifica explícitamente el comportamiento.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran dos métodos de invocación de plataforma marcados con los <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributos adecuados.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1901: las declaraciones P/Invoke deben ser portátiles](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: especificar el cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Consulte también
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>[Serialización predeterminada para los tipos booleanos](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) que [interoperan con código no administrado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
