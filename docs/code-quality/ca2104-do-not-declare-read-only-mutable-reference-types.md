---
title: 'CA2104: No declarar tipos de referencias mutables de solo lectura'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 80d40dd60b0a6b6e507b903fd7a6185c5419422e
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551697"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: No declarar tipos de referencias mutables de solo lectura

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

 El modificador de solo lectura ([readonly](/dotnet/csharp/language-reference/keywords/readonly) en C#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], y [const](/cpp/cpp/const-cpp) en C++) en un tipo de referencia (puntero de C++) del campo impide que el campo reemplazado por una instancia diferente del tipo de referencia. Sin embargo, el modificador no impide que los datos de instancia del campo que se modifica mediante el tipo de referencia.

 Campos de matriz de solo lectura están exentos de esta regla, pero en su lugar, provoca una infracción de la [CA2105: los campos de matriz deben no ser de solo lectura](../code-quality/ca2105-array-fields-should-not-be-read-only.md) regla.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite el modificador de solo lectura, o bien, si un cambio importante es aceptable, sustituya el campo con un tipo inmutable.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una advertencia de esta regla si el tipo de campo es inmutable.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra una declaración de campo que provoca una infracción de esta regla.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]