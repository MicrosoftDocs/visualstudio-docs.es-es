---
title: "CA2141: Los m&#233;todos transparentes no deben satisfacer LinkDemands | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2141"
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2141: Los m&#233;todos transparentes no deben satisfacer LinkDemands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|Identificador de comprobación|CA2141|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método de seguridad transparente llama a un método de un ensamblado que no está marcado con el atributo <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\), o un método de seguridad transparente satisface una <xref:System.Security.Permissions.SecurityAction>`.LinkDemand` para un tipo o un método.  
  
## Descripción de la regla  
 Satisfacer un LinkDemand es una operación sensible a la seguridad que puede dar lugar a una elevación de privilegios involuntaria.  El código transparente de seguridad no debe satisfacer LinkDemand, porque no está sujeto a los mismos requisitos de auditoría de seguridad que el código crítico para la seguridad.  Los métodos transparentes en los ensamblados con un conjunto de reglas de seguridad de nivel 1 harán que todas las LinkDemands que satisfacen se conviertan peticiones completas en tiempo de ejecución, los cual puede producir problemas de rendimiento.  En los ensamblados con el conjunto de reglas de seguridad de nivel 2, los métodos transparentes no se compilan en el compilador Just\-In\-Time \(JIT\) si intentan satisfacer una LinkDemand.  
  
 En ensamblados que usan seguridad de Nivel 2, los intentos de un método con seguridad transparente de satisfacer una LinkDemand o llamar a un método en un ensamblado no APTCA genera la <xref:System.MethodAccessException>; en ensamblados de Nivel 1 LinkDemand se vuelve una Demanda completa.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, marque el método que obtiene acceso con el atributo <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityCriticalAttribute>, o quite LinkDemand del método al que se obtiene acceso.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En este ejemplo, un método transparente intenta llamar a un método que tiene una LinkDemand.  Esta regla se desencadenará en este código.  
  
 [!code-cs[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]