---
title: "CA1714: Las enumeraciones Flags deber&#237;an tener nombres en plural | Microsoft Docs"
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
  - "FlagsEnumsShouldHavePluralNames"
  - "CA1714"
helpviewer_keywords: 
  - "CA1714"
  - "FlagsEnumsShouldHavePluralNames"
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1714: Las enumeraciones Flags deber&#237;an tener nombres en plural
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|Identificador de comprobación|CA1714|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Una enumeración pública tiene <xref:System.FlagsAttribute?displayProperty=fullName> y su nombre no termina en 's'.  
  
## Descripción de la regla  
 Los tipos marcados con <xref:System.FlagsAttribute> tienen nombres en plural porque el atributo indica que se puede especificar más de un valor.  Por ejemplo, una enumeración que define los días de la semana podría usarse en una aplicación en la que se pueden especificar varios días.  Esta enumeración debería tener <xref:System.FlagsAttribute> y podría denominarse 'Días'.  Una enumeración similar que permite especificar sólo un día no tendría el atributo y se podría denominar 'Día'.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce la curva de aprendizaje necesaria para las nuevas bibliotecas de software y aumenta la confianza del cliente respecto a que la biblioteca se haya desarrollado por parte de un especialista en desarrollo de código administrado.  
  
## Cómo corregir infracciones  
 Cambie el nombre de la enumeración a una palabra en plural o quite el atributo <xref:System.FlagsAttribute> si no se deben especificar varios valores de enumeración simultáneamente.  
  
## Cuándo suprimir advertencias  
 Se puede suprimir una infracción de forma segura si el nombre es una palabra en plural pero no termina en 's'.  Por ejemplo, si la enumeración de varios días descrita anteriormente se denominara 'DíasDeLaSemana', esto infringiría la lógica de la regla pero no su intención.  Este tipo de infracciones debería suprimirse.  
  
## Reglas relacionadas  
 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Vea también  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Diseño de enumeraciones](../Topic/Enum%20Design.md)