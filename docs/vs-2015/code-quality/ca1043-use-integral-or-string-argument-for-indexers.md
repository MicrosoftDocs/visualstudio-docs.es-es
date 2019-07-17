---
title: 'CA1043: Utilizar argumento integral o de cadena para los indizadores | Documentos de Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 643d91ad51e9511bbd4440d2f84fbd441c768a53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143215"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Utilizar un argumento integral o de cadena en indizadores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|Identificador de comprobación|CA1043|
|Categoría|Microsoft.Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo público o protegido contiene un indizador público o protegido que utiliza un tipo de índice distinto <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, o <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 Los indizadores, es decir, las propiedades indizadas, deben utilizar tipos enteros o de cadena para el índice. Estos tipos se utilizan normalmente para indizar las estructuras de datos y aumentan la facilidad de uso de la biblioteca. El uso de la <xref:System.Object> tipo debería estar restringido a aquellos casos donde no se puede especificar el tipo entero o una cadena específico en tiempo de diseño. Si el diseño requiere otros tipos para el índice, reconsidere si el tipo representa un almacén de datos lógico. Si no representa un almacén de datos lógico, utilice un método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambiar el índice a un tipo entero o cadena o usar un método en lugar del indizador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla después de considerar cuidadosamente la necesidad de que el indizador no estándar.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un indizador que usa un <xref:System.Int32> índice.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1023: Los indizadores no deben ser multidimensionales](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)
