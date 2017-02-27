---
title: "CA1712: No utilizar prefijos en valores de enumeraci&#243;n con el nombre del tipo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1712"
  - "DoNotPrefixEnumValuesWithTypeName"
helpviewer_keywords: 
  - "CA1712"
  - "DoNotPrefixEnumValuesWithTypeName"
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1712: No utilizar prefijos en valores de enumeraci&#243;n con el nombre del tipo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPrefixEnumValuesWithTypeName|  
|Identificador de comprobación|CA1712|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Una enumeración contiene un miembro cuyo nombre comienza con el nombre de tipo de la enumeración.  
  
## Descripción de la regla  
 Los nombres de los miembros de la enumeración no llevan el nombre de tipo como prefijo porque se espera que sean herramientas de desarrollo las que proporcionen la información de tipo.  
  
 Las convenciones de nomenclatura proporcionan una apariencia común para las bibliotecas destinadas a Common Language Runtime.  Esto reduce el tiempo de aprendizaje necesario para la nueva biblioteca de software y aumenta la confianza por parte del cliente en lo que respecta a que la biblioteca fue desarrollada por un especialista en desarrollo de código administrado.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el prefijo del nombre de tipo del miembro de la enumeración.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El ejemplo siguiente muestra una enumeración con nombre incorrecto seguida de la versión corregida.  
  
 [!code-cs[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]  
  
## Reglas relacionadas  
 [CA1711: Los identificadores no deberían tener el sufijo incorrecto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
 [CA1027: Marcar enumeraciones con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: No marcar enumeraciones con FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Vea también  
 <xref:System.Enum?displayProperty=fullName>