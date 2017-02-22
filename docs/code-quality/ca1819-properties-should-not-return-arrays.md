---
title: "CA1819: Las propiedades no deber&#237;an devolver matrices | Microsoft Docs"
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
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
helpviewer_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1819: Las propiedades no deber&#237;an devolver matrices
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotReturnArrays|  
|Identificador de comprobación|CA1819|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Una propiedad pública o protegida en un tipo público devuelve una matriz.  
  
## Descripción de la regla  
 Las matrices devueltas por las propiedades no están protegidas contra escritura, aun cuando la propiedad es de sólo lectura.  Para mantener la matriz inviolable, la propiedad debe devolver una copia de la matriz.  Por lo general, los usuarios no entienden las implicaciones de rendimiento adversas que se originan al llamar a este tipo de propiedad.  Específicamente, podrían utilizar la propiedad como una propiedad indizada.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, convierta la propiedad en un método o cambie la propiedad para que devuelva una colección.  
  
## Cuándo suprimir advertencias  
 Los atributos pueden contener propiedades que devuelven matrices, pero no pueden contener propiedades que devuelven colecciones.  Puede suprimir una advertencia provocada por una propiedad de un atributo que se deriva de la clase [System.Attribute](assetId:///System.Attribute?qualifyHint=False&autoUpgrade=True).  En caso contrario, no suprima ninguna advertencia de esta regla.  
  
## Infracción de ejemplo  
  
### Descripción  
 El siguiente ejemplo muestra una propiedad que infringe esta regla.  
  
### Código  
 [!code-cs[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### Comentarios  
 Para corregir una infracción de esta regla, convierta la propiedad en un método o cambie la propiedad para que devuelva una colección en lugar de una matriz.  
  
## Cambiar la propiedad a un ejemplo del método  
  
### Descripción  
 En el ejemplo siguiente se corrige la infracción cambiando la propiedad a un método.  
  
### Código  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-cs[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## Devolver un ejemplo de colección  
  
### Descripción  
 En el ejemplo siguiente se corrige la infracción cambiando la propiedad para que devuelva  
  
 <xref:System.Collection.ObjectModel.ReadOnlyCollection?displayProperty=fullName>.  
  
### Código  
 [!code-cs[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## Permitir a los usuarios modificar una propiedad  
  
### Descripción  
 Es posible que desee permitir al consumidor de la clase modificar una propiedad.  En el siguiente ejemplo se muestra una propiedad de lectura\/escritura que infringe esta regla.  
  
### Código  
 [!code-cs[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### Comentarios  
 En el ejemplo siguiente se corrige la infracción cambiando la propiedad para que devuelva <xref:System.Collection.ObjectModel.Collection?displayProperty=fullName>.  
  
### Código  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-cs[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## Reglas relacionadas  
 [CA1024: Utilizar las propiedades donde corresponda](../code-quality/ca1024-use-properties-where-appropriate.md)