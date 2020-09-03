---
title: 'CA1717: solo las enumeraciones FlagsAttribute deben tener nombres en plural | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c58c218991226a954185853097dc81da36c69ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543694"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Solo las enumeraciones FlagsAttribute deben tener nombres en plural
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|Identificador de comprobación|CA1717|
|Category|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 El nombre de una enumeración visible externamente finaliza en una palabra plural y la enumeración no está marcada con el <xref:System.FlagsAttribute?displayProperty=fullName> atributo.

## <a name="rule-description"></a>Descripción de la regla
 Las convenciones de nomenclatura dictan que un nombre plural para una enumeración indica que se puede especificar más de un valor de la enumeración simultáneamente. El <xref:System.FlagsAttribute> indica a los compiladores que la enumeración se debe tratar como un campo de bits que habilita las operaciones bit a bit en la enumeración.

 Si solo se puede especificar un valor de una enumeración a la vez, el nombre de la enumeración debe ser una palabra singular. Por ejemplo, una enumeración que define los días de la semana puede estar pensada para su uso en una aplicación donde se pueden especificar varios días. Esta enumeración debe tener <xref:System.FlagsAttribute> y se puede llamar ' Days '. Una enumeración similar que permite especificar un solo día no tendría el atributo y se podría llamar ' Day '.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce el tiempo necesario para obtener información sobre una nueva biblioteca de software y aumenta la confianza del cliente de que la biblioteca fue desarrollada por alguien que tenga experiencia en el desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Haga que el nombre de la enumeración sea una palabra singular o agregue la <xref:System.FlagsAttribute> .

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de la regla si el nombre termina en una palabra singular.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1714: Las enumeraciones Flags deben tener nombres en plural](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte también
 <xref:System.FlagsAttribute?displayProperty=fullName>[Diseño de enumeración](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
