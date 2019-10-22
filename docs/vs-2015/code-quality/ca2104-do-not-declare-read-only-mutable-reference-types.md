---
title: 'CA2104: no declarar tipos de referencia mutable de solo lectura | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fd81f9ea250cd1592f755a2aa6cb3ca09280a533
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666041"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: No declarar tipos de referencias mutables de solo lectura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|Identificador de comprobación|CA2104|
|Categoría|Microsoft.Security|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo visible externamente contiene un campo de sólo lectura visible externamente que es un tipo de referencia que se puede cambiar.

## <a name="rule-description"></a>Descripción de la regla
 Un tipo que mutable es un tipo cuyos datos de instancia se pueden modificar. La clase <xref:System.Text.StringBuilder?displayProperty=fullName> es un ejemplo de un tipo de referencia mutable. Contiene miembros que pueden cambiar el valor de una instancia de la clase. Un ejemplo de un tipo de referencia inmutable es la clase <xref:System.String?displayProperty=fullName>. Una vez creada la instancia, su valor nunca puede cambiar.

 El modificador de solo lectura ([ReadOnly](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) in C#, [ReadOnly](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] y [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) in C++) en un campo de tipo de referencia (puntero C++en) impide que el campo se reemplace por otra instancia del tipo de referencia. Sin embargo, el modificador no impide que los datos de instancia del campo se modifiquen a través del tipo de referencia.

 Los campos de matriz de solo lectura están exentos de esta regla pero, en su lugar, causan una infracción de [CA2105: los campos de matriz no deben ser reglas de solo lectura](../code-quality/ca2105-array-fields-should-not-be-read-only.md) .

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el modificador de solo lectura o, si es aceptable un cambio importante, reemplace el campo por un tipo inmutable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el tipo de campo es inmutable.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una declaración de campo que provoca una infracción de esta regla.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
