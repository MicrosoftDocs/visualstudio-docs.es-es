---
title: "CA2145: Los m&#233;todos transparentes no deben ser representativos con el atributo SuppressUnmanagedCodeSecurityAttribute | Microsoft Docs"
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
  - "CA2145"
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2145: Los m&#233;todos transparentes no deben ser representativos con el atributo SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|Identificador de comprobación|CA2145|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método transparente, un método que está marcado con el método <xref:System.Security.SecuritySafeCriticalAttribute>, o un tipo que contiene un método que está marcado con el atributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.  
  
## Descripción de la regla  
 Los métodos decorados con el atributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> tienen una LinkDemand implícita colocada en cualquier método que la llame.  Esta LinkDemand requiere que el código de llamada sea crítico para la seguridad.  Marcar el método que utiliza SuppressUnmanagedCodeSecurity con el atributo <xref:System.Security.SecurityCriticalAttribute> hace este requisito más obvio para los llamadores del método.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, marque el método o tipo con el atributo <xref:System.Security.SecurityCriticalAttribute>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
### Código  
 [!code-cs[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### Comentarios