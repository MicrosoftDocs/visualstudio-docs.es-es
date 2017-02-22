---
title: "CA1401: Los elementos P/Invoke no deben estar visibles | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PInvokesShouldNotBeVisible"
  - "CA1401"
helpviewer_keywords: 
  - "CA1401"
  - "PInvokesShouldNotBeVisible"
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1401: Los elementos P/Invoke no deben estar visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokesShouldNotBeVisible|  
|Identificador de comprobación|CA1401|  
|Categoría|Microsoft.Interoperability|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método público o protegido en un tipo público tiene el atributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> \(también se implementa por la palabra clave `Declare` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Descripción de la regla  
 Los métodos marcados con el atributo <xref:System.Runtime.InteropServices.DllImportAttribute> \(o los métodos definidos utilizando la palabra clave `Declare` en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) utilizan los servicios de invocación de plataforma para tener acceso al código no administrado.  No se deberían exponer estos métodos.  Al mantener estos métodos como privados e internos se garantiza que la biblioteca no se puede utilizar para poner en peligro la seguridad permitiendo que los llamadores obtengan acceso a las API no administradas que, de lo contrario, no pueden llamar.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, cambie el nivel de acceso del método.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 El siguiente ejemplo declara un método que infringe esta regla.  
  
 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]