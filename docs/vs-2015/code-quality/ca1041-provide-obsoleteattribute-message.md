---
title: 'CA1041: proporcionar el mensaje ObsoleteAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d738cf15ebe734cb74e553f38f6eb26af17e8cfd
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542316"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Proporcionar un mensaje ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|Value|
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|Identificador de comprobación|CA1041|
|Category|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Causa
 Un tipo o miembro se marca con un <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo que no tiene la <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> propiedad especificada.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.ObsoleteAttribute>se utiliza para marcar los tipos y miembros de biblioteca en desuso. Los consumidores de la biblioteca deben evitar el uso de cualquier tipo o miembro que esté marcado como obsoleto. Esto se debe a que es posible que no se admita y finalmente se quitará de las versiones posteriores de la biblioteca. Cuando se compila un tipo o un miembro marcado mediante <xref:System.ObsoleteAttribute> , se <xref:System.ObsoleteAttribute.Message%2A> muestra la propiedad del atributo. Esto proporciona información al usuario sobre el miembro o tipo obsoleto. Generalmente, esta información incluye el tiempo que los diseñadores de biblioteca y el reemplazo preferido usarán el tipo o miembro obsoleto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue el `message` parámetro al <xref:System.ObsoleteAttribute> constructor.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla porque la <xref:System.ObsoleteAttribute.Message%2A> propiedad proporciona información crítica sobre el tipo o miembro obsoleto.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un miembro obsoleto que tiene un declarado correctamente <xref:System.ObsoleteAttribute> .

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Consulte también
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
