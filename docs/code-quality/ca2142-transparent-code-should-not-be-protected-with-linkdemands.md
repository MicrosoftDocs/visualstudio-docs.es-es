---
title: "CA2142: El c&#243;digo transparente no se deber&#237;a proteger con LinkDemands | Microsoft Docs"
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
  - "CA2142"
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2142: El c&#243;digo transparente no se deber&#237;a proteger con LinkDemands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|Identificador de comprobación|CA2142|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método transparente requiere una <xref:System.Security.Permissions.SecurityAction> u otra demanda de seguridad.  
  
## Descripción de la regla  
 Esta regla se desencadena en los métodos transparentes que requieren que las LinkDemand tengan acceso a ellos.  El código transparente en seguridad no debería ser responsable de comprobar la seguridad de una operación y, por consiguiente, no debería exigir permisos.  Como se supone que los métodos transparentes tienen una seguridad neutra, no deberían tomar ninguna decisión de seguridad.  Además, el código crítico para la seguridad, que toma las decisiones de seguridad, no debería basarse en el código transparente para haber tomado este tipo de decisión previamente.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite la petición de vínculo en el método transparente o marque el método con el atributo <xref:System.Security.SecuritySafeCriticalAttribute> si está realizando comprobaciones de seguridad, por ejemplo demandas de seguridad.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En el ejemplo siguiente, la regla desencadena en el método porque este es transparente y se marca con una LinkDemand <xref:System.Security.PermissionSet> que contiene <xref:System.Security.Permissions.SecurityAction>.  
  
 [!code-cs[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 No suprima las advertencias de esta regla.