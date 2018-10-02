---
title: 'CA1813: Evitar atributos no sellados | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c422e4e261374d591acd0630f428f139b29cfcca
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591904"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Evitar atributos no sellados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1813: evitar atributos no sellados](https://docs.microsoft.com/visualstudio/code-quality/ca1813-avoid-unsealed-attributes).

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|Identificador de comprobación|CA1813|
|Categoría|Microsoft.Performance|
|Cambio problemático|Problemático|

## <a name="cause"></a>Motivo
 Un tipo público hereda de <xref:System.Attribute?displayProperty=fullName>, no es abstracta y no está sellado (`NotInheritable` en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla
 La biblioteca de clases de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] proporciona los métodos para recuperar los atributos personalizados. De forma predeterminada, estos métodos buscan la jerarquía de herencia del atributo; Por ejemplo <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> busca el tipo de atributo especificado o cualquier tipo de atributo que extiende el tipo de atributo especificado. Sellar el atributo elimina la búsqueda a través de la jerarquía de herencia y puede mejorar el rendimiento.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, selle el tipo de atributo o establecerlo como abstracto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla. Debe hacerlo sólo si está definiendo una jerarquía de atributo y no se puede sellar el atributo o establecerlo como abstracto.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un atributo personalizado que cumple esta regla.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Marcar atributos con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Vea también
 [Atributos](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



