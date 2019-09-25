---
title: 'CA1400: Deben existir puntos de entrada P-Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5503f00995a4720207ea0ea9c29201d379e70adb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234906"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Debe haber puntos de entrada P/Invoke

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|Identificador de comprobación|CA1400|
|Categoría|Microsoft.Interoperability|
|Cambio importante|Poco problemático|

## <a name="cause"></a>Motivo
Un método público o protegido se marca con <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. No se pudo encontrar la biblioteca no administrada o el método no coincide con una función de la biblioteca. Si la regla no puede encontrar el nombre del método exactamente como se especifica, busca versiones ANSI o de caracteres anchos del método subiendo el nombre del método con "A" o "W". Si no se encuentra ninguna coincidencia, la regla intenta encontrar una función mediante el formato de nombre _ __MyMethod@12Stdcall (, donde 12 representa la longitud de los argumentos). Si no se encuentra ninguna coincidencia y el nombre del método comienza por "#", la regla busca la función como una referencia ordinal en lugar de una referencia de nombre.

## <a name="rule-description"></a>Descripción de la regla
No hay ninguna comprobación en tiempo de compilación disponible para asegurarse de que los métodos marcados con <xref:System.Runtime.InteropServices.DllImportAttribute> se encuentran en el archivo dll no administrado al que se hace referencia. Si no hay ninguna función que tenga el nombre especificado en la biblioteca o los argumentos del método no coinciden con los argumentos de la función, el Common Language Runtime produce una excepción.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
Para corregir una infracción de esta regla, corrija el método que tiene <xref:System.Runtime.InteropServices.DllImportAttribute> el atributo. Asegúrese de que la biblioteca no administrada existe y está en el mismo directorio que el ensamblado que contiene el método. Si la biblioteca está presente y se hace referencia a ella correctamente, compruebe que el nombre del método, el tipo de valor devuelto y la firma del argumento coinciden con la función de biblioteca.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
No suprima una advertencia de esta regla cuando la biblioteca no administrada está en el mismo directorio que el ensamblado administrado que hace referencia a ella. Podría ser seguro suprimir una advertencia de esta regla en caso de que no se pudiera encontrar la biblioteca no administrada.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra un tipo que infringe la regla. No se produce ninguna función `DoSomethingUnmanaged` denominada en Kernel32. dll.

[!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]

## <a name="see-also"></a>Vea también
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>