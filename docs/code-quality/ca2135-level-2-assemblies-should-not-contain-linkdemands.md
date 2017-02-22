---
title: "CA2135: Los ensamblados de nivel 2 no deben contener LinkDemands | Microsoft Docs"
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
  - "CA2135"
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2135: Los ensamblados de nivel 2 no deben contener LinkDemands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|  
|Identificador de comprobación|CA2135|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Una clase o miembro de clase está utilizando <xref:System.Security.Permissions.SecurityAction> en una aplicación que está utilizando seguridad de Nivel 2.  
  
## Descripción de la regla  
 LinkDemands está desusado en el conjunto de reglas de seguridad de nivel 2.  En lugar de utilizar LinkDemands para exigir la seguridad en el momento de la compilación Just\-In\-Time \(JIT\), marque los métodos, tipos y campos con el atributo <xref:System.Security.SecurityCriticalAttribute>.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite <xref:System.Security.SecurityCriticalAttribute> y marque el tipo o miembro con el atributo <xref:System.Security.Permissions.SecurityAction>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En el ejemplo siguiente, <xref:System.Security.Permissions.SecurityAction> se debería quitar, así como el método marcado con el atributo <xref:System.Security.SecurityCriticalAttribute>.  
  
 [!code-cs[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]