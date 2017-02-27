---
title: "CA2149: Los m&#233;todos transparentes no deben llamar a c&#243;digo nativo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2149"
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2149: Los m&#233;todos transparentes no deben llamar a c&#243;digo nativo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallNativeCode|  
|Identificador de comprobación|CA2149|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método llama a una función nativa a través de un código auxiliar de método como P\/Invoke.  
  
## Descripción de la regla  
 Esta regla se desencadena en cualquier método transparente que llame directamente a código nativo, por ejemplo, a través de P\/Invoke.  Las infracciones de esta regla conducen a una <xref:System.MethodAccessException> en el modelo de transparencia de nivel 2, y a una petición completa de <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> en el modelo de transparencia de nivel 1.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, marque el método que llama al código nativo con el atributo <xref:System.Security.SecuritySafeCriticalAttribute> o <xref:System.Security.SecurityCriticalAttribute>.  
  
## Cuándo suprimir advertencias  
 No suprima las advertencias de esta regla.  
  
## Ejemplo  
 [!code-cs[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]