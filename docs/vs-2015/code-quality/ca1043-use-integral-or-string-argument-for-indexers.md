---
title: 'CA1043: Use el argumento integral o de cadena para los indizadores | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 528b3a1f301544ccb20cfa6bddc31c0a5c50d1ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668299"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Utilizar argumento integral o de cadena para los indizadores
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|Identificador de comprobación|CA1043|
|Categoría|Microsoft. Design|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público o protegido contiene un indexador público o protegido que usa un tipo de índice distinto de <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName> o <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>Descripción de la regla
 Los indizadores, es decir, las propiedades indizadas, deben utilizar tipos enteros o de cadena para el índice. Estos tipos se utilizan normalmente para indizar estructuras de datos y aumentar la facilidad de uso de la biblioteca. El uso del tipo de <xref:System.Object> se debe restringir a los casos en los que no se puede especificar el tipo de cadena o entero concreto en tiempo de diseño. Si el diseño requiere otros tipos para el índice, reconsidere si el tipo representa un almacén de datos lógico. Si no representa un almacén de datos lógico, use un método.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, cambie el índice a un tipo de cadena o entero, o bien use un método en lugar del indexador.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Suprima una advertencia de esta regla solo después de considerar detenidamente la necesidad del indexador no estándar.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un indexador que utiliza un índice de <xref:System.Int32>.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1023: Los indizadores no deben ser multidimensionales](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)
