---
title: "CA1041: Proporcionar un mensaje ObsoleteAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1041"
  - "ProvideObsoleteAttributeMessage"
helpviewer_keywords: 
  - "ProvideObsoleteAttributeMessage"
  - "CA1041"
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1041: Proporcionar un mensaje ObsoleteAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideObsoleteAttributeMessage|  
|Identificador de comprobación|CA1041|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo o miembro se marca mediante un atributo <xref:System.ObsoleteAttribute?displayProperty=fullName> para la que no se ha especificado su propiedad <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName>.  
  
## Descripción de la regla  
 <xref:System.ObsoleteAttribute> se utiliza para marcar los tipos y miembros obsoletos de la biblioteca.  Los consumidores de la biblioteca deberían evitar el uso de cualquier tipo o miembro marcado como obsoleto.  Esto es porque puede que no se admita y que se quite finalmente de las versiones posteriores de la biblioteca.  Cuando se compila un tipo o miembro marcado mediante <xref:System.ObsoleteAttribute>, se muestra la propiedad <xref:System.ObsoleteAttribute.Message%2A> del atributo.  Esto proporciona información al usuario sobre el miembro o tipo obsoleto.  Esta información generalmente incluye cuánto tiempo se sigue admitiendo el tipo o miembro obsoleto por los diseñadores de la biblioteca y el sustituto preferido que se va a utilizar.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue el parámetro `message` al constructor <xref:System.ObsoleteAttribute>.  
  
## Cuándo suprimir advertencias  
 No suprima una advertencia de esta regla porque la propiedad <xref:System.ObsoleteAttribute.Message%2A> proporciona información importante sobre el tipo o miembro desusado.  
  
## Ejemplo  
 En el siguiente ejemplo se muestra un miembro obsoleto que tiene un <xref:System.ObsoleteAttribute> declarado correctamente.  
  
 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-cs[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]  
  
## Vea también  
 <xref:System.ObsoleteAttribute?displayProperty=fullName>