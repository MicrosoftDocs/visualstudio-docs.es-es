---
title: "CA2136: Los miembros no deben tener anotaciones de transparencia en conflicto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2127"
  - "SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode"
  - "CA2136"
helpviewer_keywords: 
  - "CA2127"
  - "SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode"
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA2136: Los miembros no deben tener anotaciones de transparencia en conflicto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparencyAnnotationsShouldNotConflict|  
|Identificador de comprobación|CA2136|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Esta regla se desencadena cuando un miembro de tipo se marca con un atributo de seguridad <xref:System.Security> que tiene una transparencia diferente que el atributo de seguridad de un contenedor del miembro.  
  
## Descripción de la regla  
 Los atributos de transparencia se aplican de los elementos de código de ámbito mayor a los elementos de ámbito menor.  Los atributos de transparencia de los elementos de código con mayor ámbito tienen prioridad sobre los atributos de transparencia de los elementos de código incluidos en el primer elemento.  Por ejemplo, una clase marcada con el atributo <xref:System.Security.SecurityCriticalAttribute> no puede contener un método marcado con el atributo <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Cómo corregir infracciones  
 Para corregir esta infracción, quite el atributo de seguridad del elemento de código que tiene el ámbito más bajo o cambie su atributo para que sea igual que el elemento de código que contiene.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En el ejemplo siguiente, se marca un método con el atributo <xref:System.Security.SecuritySafeCriticalAttribute> y es un miembro de una clase marcada con el atributo <xref:System.Security.SecurityCriticalAttribute>.  Se debería quitar el atributo crítico para la seguridad.  
  
 [!code-cs[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]