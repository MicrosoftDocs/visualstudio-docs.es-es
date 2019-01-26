---
title: 'CA1041: Proporcionar un mensaje ObsoleteAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3931501d913a8518f80deccdf9ebe1667e51b661
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54923719"
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Proporcionar un mensaje ObsoleteAttribute

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

## <a name="when-to-suppress-warnings"></a>Cuándo Suprimir advertencias
 No suprima una advertencia de esta regla porque el <xref:System.ObsoleteAttribute.Message%2A> propiedad proporciona información crítica sobre el tipo o miembro obsoleto.

## <a name="example"></a>Ejemplo
 El ejemplo siguiente muestra un miembro obsoleto que tiene declarado correctamente <xref:System.ObsoleteAttribute>.

 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]

## <a name="see-also"></a>Vea también
 <xref:System.ObsoleteAttribute?displayProperty=fullName>