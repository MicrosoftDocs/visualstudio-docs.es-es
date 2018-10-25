---
title: 'CA2205: Utilizar equivalentes administrados de API de Win32 | Microsoft Docs'
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
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ba23b176ed4f2120f4675611567955bdaf652153
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49907474"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Utilizar equivalentes administrados de la API Win32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|Identificador de comprobación|CA2205|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo
 Una invocación de plataforma se define el método y existe un método con la funcionalidad equivalente en el [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] biblioteca de clases.

## <a name="rule-description"></a>Descripción de la regla
 Una plataforma de invocación de método se usa para llamar a una función DLL no administrada y se define utilizando el <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> atributo, o la `Declare` palabra clave en Visual Basic. Método de invocación de una plataforma definida incorrectamente puede generar excepciones en tiempo de ejecución debido a problemas como una función con nombre incorrecto, una asignación de tipos de datos de valor devueltos y de parámetro y las especificaciones de campo incorrecto, como la convención de llamada y el carácter defectuosa conjunto. Si está disponible, por lo general es más sencillo y menos propenso a errores llamar al método administrado equivalente que to definir y llamar directamente al método no administrado. Una llamada a una plataforma de invocar el método también pueden provocar problemas de seguridad adicionales que deban solucionarse.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, reemplace la llamada a la función no administrada con una llamada a su equivalente administrado.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla si el método de reemplazo sugerido no proporciona la funcionalidad necesaria.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente se muestra una plataforma de invocación de definición de método que infringe la regla. Además, las llamadas a la plataforma de invocación de método y se muestra el método administrado equivalente.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1404: Llame a GetLastError inmediatamente después de P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: Mueva P/Invokes a la clase NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: Deben existir puntos de entrada P/Invoke](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: Los elementos P/Invoke no deben estar visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Especifique cálculo de referencias para argumentos de cadena P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)



