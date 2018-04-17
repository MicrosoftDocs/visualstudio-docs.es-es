---
title: 'CA1714: Las enumeraciones Flags deberían tener nombres en plural | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: d5dc35718a20743ce6ed1502dbd1d9ed3c8a626e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Las enumeraciones Flags deberían tener nombres en plural
|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|Identificador de comprobación|CA1714|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## <a name="cause"></a>Motivo  
 Una enumeración pública tiene el <xref:System.FlagsAttribute?displayProperty=fullName> y su nombre no termina en '.  
  
## <a name="rule-description"></a>Descripción de la regla  
 Tipos que se marcan con <xref:System.FlagsAttribute> tienen nombres que están en plurales porque el atributo indica que se puede especificar más de un valor. Por ejemplo, una enumeración que define los días de la semana puede ser pensada para su uso en una aplicación donde puede especificar varios días. Esta enumeración debe tener la <xref:System.FlagsAttribute> y podría denominarse 'Días'. Una enumeración similar que permite sólo un día que se especifique el atributo no es necesario y podría ser denominada 'Day'.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime. Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Cambie el nombre de la enumeración en una palabra en plural o quite el <xref:System.FlagsAttribute> atributo si varios valores de enumeración no deben especificarse al mismo tiempo.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 Es seguro suprimir una infracción si el nombre es una palabra en plural pero no termina en del '. Por ejemplo, si la enumeración de varios días que se ha descrito anteriormente se denominara 'DíasDeLaSemana', esto infringiría la lógica de la regla pero no su intención. Este tipo de infracciones debería suprimirse.  
  
## <a name="related-rules"></a>Reglas relacionadas  
 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>Vea también  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Diseño de enumeraciones](/dotnet/standard/design-guidelines/enum)