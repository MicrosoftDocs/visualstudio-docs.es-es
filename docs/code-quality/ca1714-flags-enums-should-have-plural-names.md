---
title: "CA1714: Las enumeraciones Flags deberían tener nombres en plural | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b83cb82dab5f723c656b51a5322df7d7aad4570c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
 [Diseño de enum](/dotnet/standard/design-guidelines/enum)