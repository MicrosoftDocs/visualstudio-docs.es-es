---
title: "CA1717: Solo las enumeraciones FlagsAttribute deber&#237;an tener nombres en plural | Microsoft Docs"
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
  - "CA1717"
  - "OnlyFlagsEnumsShouldHavePluralNames"
helpviewer_keywords: 
  - "OnlyFlagsEnumsShouldHavePluralNames"
  - "CA1717"
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1717: Solo las enumeraciones FlagsAttribute deber&#237;an tener nombres en plural
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|  
|Identificador de comprobación|CA1717|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El nombre de una enumeración visible externamente termina con una palabra en plural y la enumeración no está marcada con el atributo <xref:System.FlagsAttribute?displayProperty=fullName>.  
  
## Descripción de la regla  
 Las convenciones de nomenclatura dictan que un nombre en plural para una enumeración indica que se pueden especificar varios valores de enumeración simultáneamente.  <xref:System.FlagsAttribute> indica a los compiladores que la enumeración debe tratarse como un campo de bits que habilita operaciones bit a bit en la enumeración.  
  
 Si sólo se puede especificar un valor de enumeración a la vez, el nombre de la enumeración debe ser una palabra en singular.  Por ejemplo, una enumeración que define los días de la semana podría usarse en una aplicación en la que se pueden especificar varios días.  Esta enumeración debería tener <xref:System.FlagsAttribute> y podría denominarse 'Días'.  Una enumeración similar que permite especificar sólo un día no tendría el atributo y se podría denominar 'Día'.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce el tiempo de aprendizaje necesario para la nueva biblioteca de software y aumenta la confianza por parte del cliente en lo que respecta a que la biblioteca fue desarrollada por un especialista en desarrollo de código administrado.  
  
## Cómo corregir infracciones  
 Cambie el nombre de la enumeración a una palabra en singular o agregue <xref:System.FlagsAttribute>.  
  
## Cuándo suprimir advertencias  
 Puede suprimir de forma segura una advertencia de la regla si el nombre termina con una palabra en singular.  
  
## Reglas relacionadas  
 [CA1714: Las enumeraciones Flags deberían tener nombres en plural](../code-quality/ca1714-flags-enums-should-have-plural-names.md)  
  
 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Vea también  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Diseño de enumeraciones](../Topic/Enum%20Design.md)