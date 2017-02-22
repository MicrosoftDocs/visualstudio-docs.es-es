---
title: "CA2138: Los m&#233;todos transparentes no deben llamar a m&#233;todos con el atributo SuppressUnmanagedCodeSecurity | Microsoft Docs"
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
  - "CA2138"
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2138: Los m&#233;todos transparentes no deben llamar a m&#233;todos con el atributo SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|Identificador de comprobación|CA2138|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método de seguridad transparente llama a un método que está marcado con el atributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.  
  
## Descripción de la regla  
 Esta regla se desencadena en cualquier método transparente que llame directamente a código nativo, por ejemplo, utilizando una llamada a P\/Invoke \(invocación de plataforma\).  Los métodos de interoperabilidad COM y P\/Invoke que están marcados con el atributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> hacen que se ejecute LinkDemand respecto al método de llamada.  Debido a que el código transparente en seguridad no puede satisfacer LinkDemands, el código tampoco puede llamar a los métodos que están marcados con el atributo SuppressUnmanagedCodeSecurity, ni a los métodos de clase que están marcados con el atributo SuppressUnmanagedCodeSecurity.  Se producirá un error en el método, o la demanda se convertirá en una demanda completa.  
  
 Las infracciones de esta regla conducen a una <xref:System.MethodAccessException> en el modelo de transparencia de seguridad de nivel 2, y a una petición completa de <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> en el modelo de transparencia de nivel 1.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el atributo <xref:System.Security.SecurityCriticalAttribute> y marque el método con el atributo <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 [!code-cs[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]