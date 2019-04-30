---
title: 'CA1717: Solo las enumeraciones FlagsAttribute deberían tener nombres en plural | Documentos de Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: cc585c348451e0189caeabaf6269606e6b73b219
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431880"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Solo las enumeraciones FlagsAttribute deben tener nombres en plural
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|Identificador de comprobación|CA1717|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 El nombre de una enumeración visible externamente termina en una palabra en plural y la enumeración no está marcada con el <xref:System.FlagsAttribute?displayProperty=fullName> atributo.

## <a name="rule-description"></a>Descripción de la regla
 Convenciones de nomenclatura dictan que un nombre plural para una enumeración indica que se puede especificar más de un valor de la enumeración al mismo tiempo. El <xref:System.FlagsAttribute> indica a los compiladores que la enumeración debe tratarse como un campo de bits que habilita las operaciones bit a bit en la enumeración.

 Si solo puede especificarse un valor de enumeración a la vez, el nombre de la enumeración debe ser una palabra en singular. Por ejemplo, una enumeración que define los días de la semana esté destinada para su uso en una aplicación que se pueden especificar varios días. Esta enumeración debe tener el <xref:System.FlagsAttribute> y podría denominarse 'Días'. Una enumeración similar que permite sólo un día que se especifique no tendría el atributo y podría ser denominada 'Day'.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce el tiempo que se requiere para obtener información sobre una nueva biblioteca de software y aumenta la confianza del cliente que la biblioteca fue desarrollada por alguien que tenga experiencia en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre de la enumeración de una palabra en singular o agregar el <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de la regla si el nombre termina en una palabra en singular.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1714: Las enumeraciones Flags deberían tener nombres en plurales](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también
 <xref:System.FlagsAttribute?displayProperty=fullName> [Diseño de enumeraciones](http://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
