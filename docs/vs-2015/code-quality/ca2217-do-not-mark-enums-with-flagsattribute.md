---
title: 'CA2217: no marcar enumeraciones con FlagsAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b584e355f5b64984f57dd17606dfb0a2f781c62d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547672"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: No marcar enumeraciones con FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|Identificador de comprobación|CA2217|
|Category|Microsoft. Usage|
|Cambio problemático|No trascendental|

## <a name="cause"></a>Causa
 Una enumeración visible externamente está marcada con <xref:System.FlagsAttribute> y tiene uno o más valores que no son potencias de dos o una combinación de los demás valores definidos en la enumeración.

## <a name="rule-description"></a>Descripción de la regla
 Una enumeración solo debe tener <xref:System.FlagsAttribute> presente si cada valor definido en la enumeración es una potencia de dos o una combinación de valores definidos.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, quite <xref:System.FlagsAttribute> de la enumeración.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima las advertencias de esta regla.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una enumeración, color, que contiene el valor 3, que no es una potencia de dos ni una combinación de ninguno de los valores definidos. La enumeración de color no se debe marcar con <xref:System.FlagsAttribute> .

 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cpp/FxCop.Usage.EnumNoFlags.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/cs/FxCop.Usage.EnumNoFlags.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags/vb/FxCop.Usage.EnumNoFlags.vb#1)]

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra una enumeración, Days, que cumple los requisitos para que se marque con System. FlagsAttribute.

 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cpp/FxCop.Usage.EnumNoFlags2.cpp#1)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/cs/FxCop.Usage.EnumNoFlags2.cs#1)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.EnumNoFlags2/vb/FxCop.Usage.EnumNoFlags2.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte también
 <xref:System.FlagsAttribute?displayProperty=fullName>
