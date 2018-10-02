---
title: 'CA1400: Deben existir puntos de entrada P / Invoke | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0544fb21533e3f114ab1efdc315d844b4cad0acb
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592304"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Deben existir puntos de entrada P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1400: deben existir puntos de entrada P / Invoke](https://docs.microsoft.com/visualstudio/code-quality/ca1400-p-invoke-entry-points-should-exist).

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|Identificador de comprobación|CA1400|
|Categoría|Microsoft.Interoperability|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un método público o protegido se marca con el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. No se pudo encontrar la biblioteca no administrada o el método no coincide con una función de la biblioteca. Si la regla no encuentra el nombre del método exactamente como se especifica, busca ANSI o versiones de caracteres anchos del método por delante el nombre del método con "A" o "W". Si no se encuentra ninguna coincidencia, la regla intenta encontrar una función con el formato de nombre __stdcall (_MyMethod@12, donde 12 representa la longitud de los argumentos). Si se encuentra ninguna coincidencia, y el nombre del método empieza por '#', la regla busca la función como una referencia ordinal en lugar de una referencia de nombre.

## <a name="rule-description"></a>Descripción de la regla
 No hay comprobación en tiempo de compilación está disponible para asegurarse de que los métodos marcados con <xref:System.Runtime.InteropServices.DllImportAttribute> se encuentran en la DLL no administrada que se hace referencia. Si ninguna función que tiene el nombre especificado está en la biblioteca, o los argumentos al método no coinciden con los argumentos de función, el common language runtime produce una excepción.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, corrija el método que tiene el <xref:System.Runtime.InteropServices.DllImportAttribute> atributo. Asegúrese de que la biblioteca no administrada existe y está en el mismo directorio que el ensamblado que contiene el método. Si la biblioteca está presente y que los que se hace referencia correctamente, compruebe que el nombre del método, el tipo de valor devuelto y la firma de argumento coinciden con la función de biblioteca.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla cuando la biblioteca no administrada está en el mismo directorio que el ensamblado administrado que hace referencia a él. Podría ser seguro suprimir una advertencia de esta regla en el caso de que la biblioteca no administrada no se encontró.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un tipo que infringe la regla. Ninguna función que se denomina `DoSomethingUnmanaged` se produce en kernel32.dll.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Vea también
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>



