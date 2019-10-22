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
ms.openlocfilehash: 931b1e5099bf221fefc7a8f4a19524d2531a4418
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609487"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Utilizar equivalentes administrados de la API Win32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|Identificador de comprobación|CA2205|
|Categoría|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Se define un método de invocación de plataforma y existe un método con la funcionalidad equivalente en la biblioteca de clases de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="rule-description"></a>Descripción de la regla
 Se usa un método de invocación de plataforma para llamar a una función DLL no administrada y se define mediante el atributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> o la palabra clave `Declare` en Visual Basic. Un método de invocación de plataforma definido incorrectamente puede provocar excepciones en tiempo de ejecución debido a problemas como una función errónea, una asignación errónea de tipos de datos de parámetros y valores devueltos, y especificaciones de campo incorrectas, como la Convención de llamada y el carácter conjunto. Si está disponible, generalmente es más sencillo y menos propenso a errores llamar al método administrado equivalente que definir y llamar directamente al método no administrado. Llamar a un método de invocación de plataforma también puede provocar problemas de seguridad adicionales que se deben solucionar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace la llamada a la función no administrada por una llamada a su equivalente administrado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si el método de reemplazo sugerido no proporciona la funcionalidad necesaria.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una definición de método de invocación de plataforma que infringe la regla. Además, se muestran las llamadas al método de invocación de plataforma y al método administrado equivalente.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1404: Llame a GetLastError inmediatamente después de P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: Mueva P/Invokes a la clase NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Deben existir puntos de entrada P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: Los elementos P/Invoke no deben estar visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Especifique cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
