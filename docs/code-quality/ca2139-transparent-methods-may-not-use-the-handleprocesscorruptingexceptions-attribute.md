---
title: "CA2139: Los m&#233;todos transparentes no pueden usar el atributo HandleProcessCorruptingExceptions | Microsoft Docs"
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
  - "CA2139"
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2139: Los m&#233;todos transparentes no pueden usar el atributo HandleProcessCorruptingExceptions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|  
|Identificador de comprobación|CA2139|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método transparente está marcado con el atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>.  
  
## Descripción de la regla  
 Esta regla desencadena cualquier método que sea transparente e intenta controlar una excepción de daño de proceso utilizando el atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>.  Una excepción de daño de proceso en la versión 4.0 de CLR es una clasificación de excepciones como <xref:System.AccessViolationException>.  El atributo HandleProcessCorruptedStateExceptionsAttribute solo lo pueden utilizar los métodos críticos para la seguridad, y se omitirá si se aplica a un método transparente.  Para controlar las excepciones de daño de proceso, este método debe volverse crítico de seguridad o crítico para la seguridad.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, quite el atributo <xref:System.Security.SecurityCriticalAttribute>, o marque el método con el atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 En este ejemplo, un método transparente se marca con el atributo <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> y no cumplirá la regla.  El método también se debería marcar con el atributo <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityCriticalAttribute>.  
  
 [!code-cs[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]