---
title: "CA2111: Los punteros no deber&#237;an estar visibles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PointersShouldNotBeVisible"
  - "CA2111"
helpviewer_keywords: 
  - "CA2111"
  - "PointersShouldNotBeVisible"
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2111: Los punteros no deber&#237;an estar visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PointersShouldNotBeVisible|  
|Identificador de comprobación|CA2111|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un <xref:System.IntPtr?displayProperty=fullName> público o protegido o el campo <xref:System.UIntPtr?displayProperty=fullName> no son de sólo lectura.  
  
## Descripción de la regla  
 <xref:System.IntPtr> y <xref:System.UIntPtr> son tipos de punteros que se utilizan para tener acceso a la memoria no administrada.  Si un puntero no es privado, interno o de sólo lectura, el código malintencionado puede cambiar el valor del puntero, permitiendo de forma potencial el acceso a ubicaciones arbitrarias o provocando errores de sistema o de aplicación.  
  
 Si desea obtener acceso de forma segura al tipo que contiene el campo de puntero, vea [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md).  
  
## Cómo corregir infracciones  
 Proteja el puntero marcándolo como de sólo lectura, interno o privado.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla si no confía en el valor del puntero.  
  
## Ejemplo  
 El código siguiente muestra punteros que infringen y cumplen la regla.  Observe que los punteros no privados también infringen la regla [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).  
  
 [!code-cs[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]  
  
## Reglas relacionadas  
 [CA2112: Los tipos seguros no deberían exponer campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA1051: No declarar campos de instancia visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)  
  
## Vea también  
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>