---
title: 'CA2217: No marcar enumeraciones con FlagsAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c0a400dc960a1b7eab7165dba718dc70b3f88437
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920917"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: No marcar enumeraciones con FlagsAttribute

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|Identificador de comprobación|CA2217|
|Categoría|Microsoft.Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Motivo

Una enumeración visible externamente está marcada con <xref:System.FlagsAttribute>y tiene uno o más valores que no son potencias de dos o una combinación de los otros valores definen en la enumeración.

## <a name="rule-description"></a>Descripción de la regla

Una enumeración debe tener <xref:System.FlagsAttribute> está presente sólo si cada valor definido en la enumeración es una potencia de dos o una combinación de valores definidos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones

Para corregir una infracción de esta regla, quite <xref:System.FlagsAttribute> de la enumeración.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias

No suprima las advertencias de esta regla.

## <a name="example-that-should-not-have-the-attribute"></a>Ejemplo que no debería tener el atributo

El ejemplo siguiente muestra una enumeración, `Color`, que contiene el valor 3. 3 no es una potencia de dos, o una combinación de cualquiera de los valores definidos. El `Color` enumeración no debe marcarse con <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>Ejemplo que debe tener el atributo

El ejemplo siguiente muestra una enumeración, `Days`, que cumple los requisitos para que se marcan con <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>Reglas relacionadas

[CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también

- <xref:System.FlagsAttribute?displayProperty=fullName>
