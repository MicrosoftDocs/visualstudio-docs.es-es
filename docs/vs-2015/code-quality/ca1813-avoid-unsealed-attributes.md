---
title: 'CA1813: evitar atributos no sellados | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8d86f4a9ecbdfff451fed21f93c0fe6a7679d471
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543954"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Evitar los atributos no sellados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|AvoidUnsealedAttributes|
|Identificador de comprobación|CA1813|
|Category|Microsoft. performance|
|Cambio problemático|Problemático|

## <a name="cause"></a>Causa
 Un tipo público hereda de <xref:System.Attribute?displayProperty=fullName> , no es abstracto y no está sellado ( `NotInheritable` en Visual Basic).

## <a name="rule-description"></a>Descripción de la regla
 La biblioteca de clases de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] proporciona los métodos para recuperar los atributos personalizados. De forma predeterminada, estos métodos buscan en la jerarquía de herencia de atributos; por ejemplo <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> , busca el tipo de atributo especificado o cualquier tipo de atributo que extienda el tipo de atributo especificado. Al sellar el atributo, se elimina la búsqueda a través de la jerarquía de herencia y puede mejorar el rendimiento.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, selle el tipo de atributo o haga que sea abstracto.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 Es seguro suprimir una advertencia de esta regla. Solo debe hacerlo si va a definir una jerarquía de atributo y no puede sellar el atributo ni hacer que sea abstracto.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un atributo personalizado que cumple esta regla.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Reglas relacionadas
 [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Marcar atributos con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Consulte también
 [Atributos](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
