---
title: "CA1813: Evitar atributos no sellados | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1813"
  - "AvoidUnsealedAttributes"
helpviewer_keywords: 
  - "AvoidUnsealedAttributes"
  - "CA1813"
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1813: Evitar atributos no sellados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|Identificador de comprobación|CA1813|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo público hereda de <xref:System.Attribute?displayProperty=fullName>, no es abstracto y no está sellado \(`NotInheritable` en Visual Basic\).  
  
## Descripción de la regla  
 La biblioteca de clases de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] proporciona los métodos para recuperar los atributos personalizados.  De forma predeterminada, estos métodos buscan la jerarquía de herencia del atributo; por ejemplo, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> busca el tipo de atributo especificado o un tipo de atributo que extienda el tipo de atributo especificado.  Al sellar el atributo, se elimina la búsqueda a través de la jerarquía de herencia y puede mejorarse el rendimiento.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, selle el tipo de atributo o establézcalo como abstracto.  
  
## Cuándo suprimir advertencias  
 Es seguro suprimir una advertencia de esta regla.  Sólo debería realizar esto si está definiendo una jerarquía de atributo y no se puede sellar el atributo o establecerlo como abstracto.  
  
## Ejemplo  
 El ejemplo siguiente muestra un atributo personalizado que cumple esta regla.  
  
 [!code-cs[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## Reglas relacionadas  
 [CA1019: Definir descriptores de acceso para los argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018: Marcar atributos con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## Vea también  
 [Atributos](../Topic/Attributes1.md)