---
title: "CA2217: No marcar enumeraciones con FlagsAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotMarkEnumsWithFlags"
  - "CA2217"
helpviewer_keywords: 
  - "CA2217"
  - "DoNotMarkEnumsWithFlags"
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA2217: No marcar enumeraciones con FlagsAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotMarkEnumsWithFlags|  
|Identificador de comprobación|CA2217|  
|Categoría|Microsoft.Usage|  
|Cambio problemático|No|  
  
## Motivo  
 Una enumeración visible externamente está marcada con <xref:System.FlagsAttribute> y tiene uno o varios valores que no son potencias de dos o una combinación de los otros valores definidos en la enumeración.  
  
## Descripción de la regla  
 Una enumeración debe tener un atributo <xref:System.FlagsAttribute> presente sólo si cada valor definido en la enumeración es una potencia de dos o una combinación de valores definidos.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite <xref:System.FlagsAttribute> de la enumeración.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra una enumeración, Color, que contiene el valor 3, que no es una potencia de dos ni una combinación de ninguno de los valores definidos.  La enumeración Color no debe marcarse con <xref:System.FlagsAttribute>.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]  
  
## Ejemplo  
 En el ejemplo siguiente se muestra una enumeración, Days, que cumple los requisitos necesarios para que pueda marcarse con System.FlagsAttribute.  
  
 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-cs[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]  
  
## Reglas relacionadas  
 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## Vea también  
 <xref:System.FlagsAttribute?displayProperty=fullName>