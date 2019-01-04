---
title: 'CA1714: Las enumeraciones Flags deben tener nombres en plural'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cf78041d61da991804a4dcdb0f924dc4a5f489e3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881818"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Las enumeraciones Flags deben tener nombres en plural

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|Identificador de comprobación|CA1714|
|Categoría|Microsoft.Naming|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Una enumeración pública tiene el <xref:System.FlagsAttribute?displayProperty=fullName> y su nombre no termina en ".

## <a name="rule-description"></a>Descripción de la regla
 Tipos que están marcados con <xref:System.FlagsAttribute> tienen nombres que están en plurales porque el atributo indica que se puede especificar más de un valor. Por ejemplo, una enumeración que define los días de la semana esté destinada para su uso en una aplicación que se pueden especificar varios días. Esta enumeración debe tener el <xref:System.FlagsAttribute> y podría denominarse 'Días'. Una enumeración similar que permite sólo un día que se especifique no tendría el atributo y podría ser denominada 'Day'.

 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Cambie el nombre de la enumeración de una palabra en plural o quite el <xref:System.FlagsAttribute> atributo si varios valores de enumeración no deben especificarse al mismo tiempo.

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 Es seguro suprimir una infracción si el nombre es una palabra en plural pero no termina del '. Por ejemplo, si la enumeración de varios días en el que se ha descrito anteriormente fueron denominada 'DíasDeLaSemana', esto infringiría la lógica de la regla, pero no su intención. Se deben suprimir tales infracciones.

## <a name="related-rules"></a>Reglas relacionadas
 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Vea también

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Diseño de enumeraciones](/dotnet/standard/design-guidelines/enum)