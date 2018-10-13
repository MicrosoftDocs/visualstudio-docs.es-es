---
title: 'CA1414: Marque los argumentos P / Invoke booleanos con MarshalAs | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 48dde74f2b6bf142d0bc173dbb34dd0c82c3d53d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200062"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Marque los argumentos P/Invoke booleanos con MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|Identificador de comprobación|CA1414|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Método de invocación de una plataforma declaración incluye una <xref:System.Boolean?displayProperty=fullName> parámetro o valor devuelto, pero el <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> no se aplica el atributo en el valor devuelto o parámetro.

## <a name="rule-description"></a>Descripción de la regla
 Una plataforma de invocación de método tiene acceso al código no administrado y se define utilizando el `Declare` palabra clave en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Especifica el comportamiento de serialización que se utiliza para convertir a tipos de datos entre código administrado y no administrado. Tipos de muchos datos simples, como <xref:System.Byte?displayProperty=fullName> y <xref:System.Int32?displayProperty=fullName>, tienen una representación única en código no administrado y no requieren la especificación de su comportamiento de serialización; common language runtime proporciona automáticamente el comportamiento correcto.

 El <xref:System.Boolean> tipo de datos tiene varias representaciones en código no administrado. Cuando el <xref:System.Runtime.InteropServices.MarshalAsAttribute> no se especifica, el valor predeterminado el cálculo de referencias para el <xref:System.Boolean> es de tipo de datos <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Se trata de un entero de 32 bits, que no es adecuado para todas las circunstancias. La representación Boolean requerido por el método no administrado debe determinarse y coincide con la correspondiente <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool es el tipo BOOL de Win32, que siempre es de 4 bytes. UnmanagedType.U1 debe usarse para C++ `bool` u otros tipos de 1 byte. Para obtener más información, consulte [serialización predeterminada para tipos booleanos](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, se aplican <xref:System.Runtime.InteropServices.MarshalAsAttribute> a la <xref:System.Boolean> parámetro o valor devuelto. Establezca el valor del atributo correspondiente <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla. Incluso si el comportamiento de serialización predeterminado es adecuado, el código se mantiene más fácilmente cuando se especifica explícitamente el comportamiento.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra los métodos marcados con los valores adecuados de invocación de plataforma dos <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributos.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1901: Las declaraciones P/Invoke deben ser portables](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Especifique cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Vea también
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Serialización predeterminada para tipos booleanos](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [interoperar con código no administrado](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



