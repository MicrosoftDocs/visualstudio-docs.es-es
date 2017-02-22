---
title: "CA1027: Marcar enumeraciones con FlagsAttribute | Microsoft Docs"
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
  - "MarkEnumsWithFlags"
  - "CA1027"
helpviewer_keywords: 
  - "CA1027"
  - "MarkEnumsWithFlags"
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1027: Marcar enumeraciones con FlagsAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkEnumsWithFlags|  
|Identificador de comprobación|CA1027|  
|Categoría|Microsoft.Design|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Los valores de una enumeración pública son potencias de dos o combinaciones de otros valores definidos en la enumeración, pero el atributo <xref:System.FlagsAttribute?displayProperty=fullName> no está presente.  Para reducir los positivos falsos, esta regla no informa de una infracción para las enumeraciones que tienen valores contiguos.  
  
## Descripción de la regla  
 Una enumeración es un tipo de valor que define un conjunto de constantes con nombre relacionadas.  Aplique <xref:System.FlagsAttribute> a una enumeración cuando se pueden combinar con sentido sus constantes con nombre.  Por ejemplo, tenga en cuenta una enumeración de los días de la semana en una aplicación que realiza el seguimiento de qué recursos del día hay disponibles.  Si la disponibilidad de cada recurso se codifica utilizando la enumeración con <xref:System.FlagsAttribute> presente, se puede representar cualquier combinación de días.  Sin el atributo, sólo se puede representar uno día de la semana.  
  
 Para campos que almacenan las enumeraciones combinables, los valores de enumeración individuales se tratan como grupos de bits en el campo.  Por consiguiente, a veces se les denomina *campos de bits*.  Para combinar los valores de enumeración para el almacenamiento en un campo de bits, utilice los operadores condicionales de tipo Boolean.  Para probar un campo de bits para determinar si un valor de enumeración concreto está presente, utilice los operadores lógicos de tipo Boolean.  Para almacenar un campo de bits y recuperar correctamente los valores de enumeración combinados, cada valor definido en la enumeración debe ser una potencia de dos.  A menos que esto sea así, los operadores lógicos de tipo Boolean no podrán extraer los valores de enumeración individuales almacenados en el campo.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue <xref:System.FlagsAttribute> a la enumeración.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla si no desea que los valores de enumeración sean combinables.  
  
## Ejemplo  
 En el ejemplo siguiente, `DaysEnumNeedsFlags` es una enumeración que cumple los requisitos para utilizar <xref:System.FlagsAttribute>, pero no lo tiene.  La enumeración `ColorEnumShouldNotHaveFlag` no tiene valores que sean potencias de dos, y especifica <xref:System.FlagsAttribute> incorrectamente.  Esto infringe la regla [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).  
  
 [!code-cs[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]  
  
## Reglas relacionadas  
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Vea también  
 <xref:System.FlagsAttribute?displayProperty=fullName>