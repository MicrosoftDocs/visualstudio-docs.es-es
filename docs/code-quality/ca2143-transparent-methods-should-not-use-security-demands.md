---
title: "CA2143: Los m&#233;todos transparentes no deben usar peticiones de seguridad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2143"
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA2143: Los m&#233;todos transparentes no deben usar peticiones de seguridad
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|Identificador de comprobación|CA2143|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un tipo o método transparente se marca mediante declaración con una demanda <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>`.Demand` o las llamadas al método del método <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>.  
  
## Descripción de la regla  
 El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos.  El código transparente en seguridad debería utilizar peticiones completas para tomar decisiones de seguridad y el código crítico para la seguridad no debió confiar en el código transparente al realizar la petición completa.  Cualquier código que realice comprobaciones de seguridad, como las demandas de seguridad, debería ser crítico para la seguridad.  
  
## Cómo corregir infracciones  
 En general, para corregir una infracción de esta regla, marque el método con el atributo <xref:System.Security.SecuritySafeCriticalAttribute>.  También puede quitar la petición.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 La regla se desencadena en el código siguiente porque un método transparente hace una demanda de seguridad declarativa.  
  
 [!code-cs[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## Vea también  
 [CA2142: El código transparente no se debería proteger con LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)