---
title: "CA1719: Los nombres de par&#225;metro no deber&#237;an coincidir con los nombres de miembro | Microsoft Docs"
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
  - "ParameterNamesShouldNotMatchMemberNames"
  - "CA1719"
helpviewer_keywords: 
  - "CA1719"
  - "ParameterNamesShouldNotMatchMemberNames"
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1719: Los nombres de par&#225;metro no deber&#237;an coincidir con los nombres de miembro
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|Identificador de comprobación|CA1719|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 El nombre de un miembro visible externamente, en una comparación sin distinción entre mayúsculas y minúsculas, coincide con el nombre de uno de sus parámetros.  
  
## Descripción de la regla  
 Un nombre de parámetro debe comunicar el significado del parámetro y un nombre de miembro debe comunicar el significado del miembro.  Sería un diseño extraño si éstos fueran los mismos.  Denominar un parámetro igual que el nombre del miembro no es intuitivo y dificulta el uso de la biblioteca.  
  
## Cómo corregir infracciones  
 Seleccione un nombre de parámetro que no coincida con el nombre de miembro.  
  
## Cuándo suprimir advertencias  
 Para el nuevo desarrollo, no se da ningún escenario conocido donde se deba suprimir ninguna advertencia de esta regla.  Para enviar las bibliotecas, quizá deba suprimir una advertencia de esta regla.  
  
## Reglas relacionadas  
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Los identificadores se deberían diferenciar en algo más que en el uso de mayúsculas y minúsculas](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Los identificadores no deberían contener subrayado](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)