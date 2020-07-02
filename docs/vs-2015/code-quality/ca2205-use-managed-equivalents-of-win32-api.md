---
title: 'CA2205: usar equivalentes administrados de la API Win32 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 85e27ab04ca81f5513a0b09bc41548f4a7c2430d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547685"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Utilizar equivalentes administrados de la API Win32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Valor|
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|Identificador de comprobación|CA2205|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Se define un método de invocación de plataforma y existe un método con la funcionalidad equivalente en la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] biblioteca de clases.

## <a name="rule-description"></a>Descripción de la regla
 Se usa un método de invocación de plataforma para llamar a una función DLL no administrada y se define mediante el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo o la `Declare` palabra clave en Visual Basic. Un método de invocación de plataforma definido incorrectamente puede provocar excepciones en tiempo de ejecución debido a problemas como una función errónea, una asignación errónea de tipos de datos de parámetros y valores devueltos, y especificaciones de campo incorrectas, como la Convención de llamada y el juego de caracteres. Si está disponible, generalmente es más sencillo y menos propenso a errores llamar al método administrado equivalente que definir y llamar directamente al método no administrado. Llamar a un método de invocación de plataforma también puede provocar problemas de seguridad adicionales que se deben solucionar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace la llamada a la función no administrada por una llamada a su equivalente administrado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si el método de reemplazo sugerido no proporciona la funcionalidad necesaria.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una definición de método de invocación de plataforma que infringe la regla. Además, se muestran las llamadas al método de invocación de plataforma y al método administrado equivalente.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1404: llamar a GetLastError inmediatamente después de P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: mueve P/Invoke a la clase NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: deben existir puntos de entrada P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: P/Invoke no debe estar visible](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: especificar el cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
