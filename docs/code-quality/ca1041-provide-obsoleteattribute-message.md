---
title: 'CA1041: Proporcionar un mensaje ObsoleteAttribute | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1041
- ProvideObsoleteAttributeMessage
helpviewer_keywords:
- ProvideObsoleteAttributeMessage
- CA1041
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5d6c0ac4d5972e06768306be51a92e93da763ce0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
 <xref:System.ObsoleteAttribute>se utiliza para marcar la biblioteca en desuso tipos y miembros. Los consumidores de biblioteca deben evitar el uso de cualquier tipo o miembro que está marcado como obsoleto. Esto es porque podría no ser compatible y finalmente se quitará en versiones posteriores de la biblioteca. Cuando un tipo o miembro marcado mediante <xref:System.ObsoleteAttribute> se compila, el <xref:System.ObsoleteAttribute.Message%2A> se muestra la propiedad del atributo. Esto proporciona información al usuario sobre el miembro o tipo obsoleto. Esta información generalmente incluye cuánto tiempo el tipo obsoleto o miembro se admitirá en los diseñadores de la biblioteca y el sustituto preferido para usar.  
  
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