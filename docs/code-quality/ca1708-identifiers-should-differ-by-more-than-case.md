---
title: "CA1708: Los identificadores se deber&#237;an diferenciar en algo m&#225;s que en el uso de may&#250;sculas y min&#250;sculas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldDifferByMoreThanCase"
  - "CA1708"
helpviewer_keywords: 
  - "CA1708"
  - "IdentifiersShouldDifferByMoreThanCase"
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1708: Los identificadores se deber&#237;an diferenciar en algo m&#225;s que en el uso de may&#250;sculas y min&#250;sculas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|Identificador de comprobación|CA1708|  
|Categoría|Microsoft.Naming|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Los nombres de dos tipos, los miembros, los parámetros o los espacios de nombres completos son idénticos cuando se convierten a letras minúsculas.  
  
## Descripción de la regla  
 Los identificadores de los espacios de nombres, miembros y parámetros no puede distinguirse sólo por mayúsculas o minúsculas porque los lenguajes que tienen como destino el Common Language Runtime no necesitan distinguir entre mayúsculas y minúsculas.  Por ejemplo, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] es un lenguaje sin distinción entre mayúsculas y minúsculas muy utilizado.  
  
 Esta regla sólo se desencadena en miembros visibles públicamente.  
  
## Cómo corregir infracciones  
 Seleccione un nombre que sea único cuando realice la comparación con otros identificadores en el modo sin distinción entre mayúsculas y minúsculas.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  La biblioteca no podría utilizarse en todos los lenguajes disponibles en [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
## Ejemplo de infracción  
 En el ejemplo siguiente se muestra una infracción de esta regla.  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## Reglas relacionadas  
 [CA1709: Los identificadores deberían utilizar las mayúsculas y minúsculas correctamente](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)