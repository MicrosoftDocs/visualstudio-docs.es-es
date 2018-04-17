---
title: 'CA1041: Proporcionar un mensaje ObsoleteAttribute | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc851ef4b4ef1cdca9bdb1f9692d3bbc7f0a795c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="ca1041-provide-obsoleteattribute-message"></a>CA1041: Proporcionar un mensaje ObsoleteAttribute
|||  
|-|-|  
|TypeName|ProvideObsoleteAttributeMessage|  
|Identificador de comprobación|CA1041|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## <a name="cause"></a>Motivo  
 Un tipo o miembro se marca mediante un <xref:System.ObsoleteAttribute?displayProperty=fullName> atributo que no tiene su <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName> propiedad especificada.  
  
## <a name="rule-description"></a>Descripción de la regla  
 <xref:System.ObsoleteAttribute> se utiliza para marcar la biblioteca en desuso tipos y miembros. Los consumidores de biblioteca deben evitar el uso de cualquier tipo o miembro que está marcado como obsoleto. Esto es porque podría no ser compatible y finalmente se quitará en versiones posteriores de la biblioteca. Cuando un tipo o miembro marcado mediante <xref:System.ObsoleteAttribute> se compila, el <xref:System.ObsoleteAttribute.Message%2A> se muestra la propiedad del atributo. Esto proporciona información al usuario sobre el miembro o tipo obsoleto. Esta información generalmente incluye cuánto tiempo el tipo obsoleto o miembro se admitirá en los diseñadores de la biblioteca y el sustituto preferido para usar.  
  
## <a name="how-to-fix-violations"></a>Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue el `message` parámetro para el <xref:System.ObsoleteAttribute> constructor.  
  
## <a name="when-to-suppress-warnings"></a>Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla porque el <xref:System.ObsoleteAttribute.Message%2A> propiedad proporciona información crítica sobre el tipo o miembro obsoleto.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra un miembro obsoleto que tiene declarado correctamente <xref:System.ObsoleteAttribute>.  
  
 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-csharp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]  
  
## <a name="see-also"></a>Vea también  
 <xref:System.ObsoleteAttribute?displayProperty=fullName>