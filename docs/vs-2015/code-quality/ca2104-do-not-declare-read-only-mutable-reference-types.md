---
title: 'CA2104: No declarar tipos de referencias mutables de solo lectura | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 03bb90b11e994ce2f823deb7e2395afc6aee7e04
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995909"
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
 Un tipo que mutable es un tipo cuyos datos de instancia se pueden modificar. La <xref:System.Text.StringBuilder?displayProperty=fullName> clase es un ejemplo de un tipo de referencia mutable. Contiene a miembros que se pueden cambiar el valor de una instancia de la clase. Un ejemplo de un tipo de referencia inmutable es el <xref:System.String?displayProperty=fullName> clase. Una vez se ha creado una instancia, su valor nunca puede cambiar.

 El modificador de solo lectura ([readonly](http://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) en C#, [ReadOnly](http://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) en [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], y [const](http://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) en C++) en un tipo de referencia (puntero de C++) del campo impide que el campo reemplazado por una instancia diferente del tipo de referencia. Sin embargo, el modificador no impide que los datos de instancia del campo que se modifica mediante el tipo de referencia.

 Campos de matriz de solo lectura están exentos de esta regla, pero en su lugar, provoca una infracción de la [CA2105: Campos de matriz deben no ser de solo lectura](../code-quality/ca2105-array-fields-should-not-be-read-only.md) regla.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el modificador de solo lectura, o bien, si un cambio importante es aceptable, sustituya el campo con un tipo inmutable.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el tipo de campo es inmutable.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una declaración de campo que provoca una infracción de esta regla.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
