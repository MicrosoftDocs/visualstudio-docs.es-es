---
title: 'CA1041: Proporcionar un mensaje ObsoleteAttribute | Microsoft Docs'
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
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 298f6d3cbfc8b71443fe9e8e9733e5729963cea8
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592360"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Proporcionar un mensaje ObsoleteAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [CA1041: proporcionar ObsoleteAttribute mensaje](https://docs.microsoft.com/visualstudio/code-quality/ca1041-provide-obsoleteattribute-message).

|||
|-|-|
|TypeName|ProvideObsoleteAttributeMessage|
|Identificador de comprobación|CA1041|
|Categoría|Microsoft.Design|
|Cambio problemático|Poco problemático|

## <a name="cause"></a>Motivo
 Un tipo o miembro se marca con un <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo que no tiene su <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> propiedad especificada.

## <a name="rule-description"></a>Descripción de la regla
 <xref:System.ObsoleteAttribute> se utiliza para marcar una biblioteca en desuso tipos y miembros. Los consumidores de la biblioteca deben evitar el uso de cualquier tipo o miembro que está marcado como obsoleto. Esto es porque es posible que no se admite y, finalmente, se quitará de las versiones posteriores de la biblioteca. Cuando un tipo o miembro marcado mediante <xref:System.ObsoleteAttribute> se compila, el <xref:System.ObsoleteAttribute.Message%2A> se muestra la propiedad del atributo. Esto proporciona información al usuario sobre el miembro o tipo obsoleto. Por lo general, esta información incluye cuánto tipo obsoleto o miembro se admitirá en los diseñadores de biblioteca y el reemplazo preferido para usar.

## <a name="how-to-fix-violations"></a>Cómo corregir infracciones
 Para corregir una infracción de esta regla, agregue el `message` parámetro para el <xref:System.ObsoleteAttribute> constructor.

## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias
 No suprima una advertencia de esta regla porque el <xref:System.ObsoleteAttribute.Message%2A> propiedad proporciona información crítica sobre el tipo o miembro obsoleto.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un miembro obsoleto que tiene declarado correctamente <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cpp/FxCop.Design.ObsoleteAttributeOnMember.cpp#1)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/cs/FxCop.Design.ObsoleteAttributeOnMember.cs#1)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ObsoleteAttributeOnMember/vb/FxCop.Design.ObsoleteAttributeOnMember.vb#1)]

## <a name="see-also"></a>Vea también
 <xref:System.ObsoleteAttribute?displayProperty=fullName>



