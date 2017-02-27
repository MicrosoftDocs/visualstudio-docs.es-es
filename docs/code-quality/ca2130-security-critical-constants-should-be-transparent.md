---
title: "CA2130: Las constantes cr&#237;ticas para la seguridad deben ser transparentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2130"
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2130: Las constantes cr&#237;ticas para la seguridad deben ser transparentes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConstantsShouldBeTransparent|  
|Identificador de comprobación|CA2130|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un campo constante o un miembro de enumeración se marca con <xref:System.Security.SecurityCriticalAttribute>.  
  
## Descripción de la regla  
 El cumplimiento de la transparencia no se exige para los valores constantes porque los compiladores alinean los valores constantes para que no se requiera ninguna búsqueda en tiempo de ejecución.  Los campos constantes deberían ser transparentes en seguridad de modo que los revisores del código no supongan que el código transparente no puede tener acceso a la constante.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el atributo SecurityCritical del campo o valor.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En los ejemplos siguientes, el valor de enumeración `EnumWithCriticalValues.CriticalEnumValue` y la constante `CriticalConstant` producen esta advertencia.  Para corregir los problemas, quite el atributo \[`SecurityCritical`\] para que tengan seguridad transparente.  
  
 [!code-cs[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]