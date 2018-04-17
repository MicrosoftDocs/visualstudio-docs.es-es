---
title: 'CA1400: Deben existir puntos de entrada P Invoke | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 53e677308d5dcb5e89b410e4ab06a33a6c0caab4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: Deben existir puntos de entrada P/Invoke
|||  
|-|-|  
|TypeName|PInvokeEntryPointsShouldExist|  
|Identificador de comprobación|CA1400|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un método público o protegido se marca con la <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. No se pudo encontrar la biblioteca no administrada o el método no coincide con una función de la biblioteca. Si la regla no encuentra el nombre del método exactamente como se especifica, busca ANSI o versiones de caracteres anchos del método aplicando el sufijo del nombre del método con 'A' o 'W'. Si se encuentra ninguna coincidencia, la regla intenta buscar una función con el formato de nombre __stdcall (_MyMethod@12, donde 12 representa la longitud de los argumentos). Si se encuentra ninguna coincidencia, y el nombre del método empieza por '#', la regla busca la función como una referencia ordinal en lugar de una referencia de nombre.  
  
## <a name="rule-description"></a>Descripción de la regla  
 No hay ninguna comprobación en tiempo de compilación para asegurarse de que los métodos que se marcan con <xref:System.Runtime.InteropServices.DllImportAttribute> se encuentran en la DLL no administrada que se hace referencia. Si ninguna función que tiene el nombre especificado está en la biblioteca, o los argumentos al método no coinciden con los argumentos de función, common language runtime produce una excepción.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, corrija el método que tiene el <xref:System.Runtime.InteropServices.DllImportAttribute> atributo. Asegúrese de que la biblioteca no administrada existe y está en el mismo directorio que el ensamblado que contiene el método. Si la biblioteca está presente y que los que se hace referencia correctamente, compruebe que el nombre del método, el tipo de valor devuelto y la firma de argumento coinciden con la función de biblioteca.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla cuando la biblioteca no administrada está en el mismo directorio que el ensamblado administrado que hace referencia a él. Puede que sea seguro suprimir una advertencia de esta regla en el caso de que la biblioteca no administrada no se pudo encontrar.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un tipo que infringe la regla. Ninguna función que se denomina `DoSomethingUnmanaged` se produce en kernel32.dll.  
  
 [!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>