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
ms.openlocfilehash: dd1799f67036ab55de5b136d746ce938835de87f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668322"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Proporcionar un mensaje ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|Identificador de comprobación|CA1041|
|Categoría|Microsoft. Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo o miembro se marca con un atributo de <xref:System.ObsoleteAttribute?displayProperty=fullName> que no tiene su propiedad <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> especificada.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.ObsoleteAttribute> se usa para marcar tipos y miembros de biblioteca en desuso. Los consumidores de la biblioteca deben evitar el uso de cualquier tipo o miembro que esté marcado como obsoleto. Esto se debe a que es posible que no se admita y finalmente se quitará de las versiones posteriores de la biblioteca. Cuando se compila un tipo o miembro marcado con <xref:System.ObsoleteAttribute>, se muestra la propiedad <xref:System.ObsoleteAttribute.Message%2A> del atributo. Esto proporciona información al usuario sobre el miembro o tipo obsoleto. Generalmente, esta información incluye el tiempo que los diseñadores de biblioteca y el reemplazo preferido usarán el tipo o miembro obsoleto.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue el parámetro `message` al constructor <xref:System.ObsoleteAttribute>.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla porque la propiedad <xref:System.ObsoleteAttribute.Message%2A> proporciona información crítica sobre el tipo o miembro obsoleto.

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestra un miembro obsoleto que tiene una <xref:System.ObsoleteAttribute> declarada correctamente.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Vea también
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
