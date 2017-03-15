---
title: "CA2106: Asegurar aserciones | Microsoft Docs"
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
  - "CA2106"
  - "SecureAsserts"
helpviewer_keywords: 
  - "CA2106"
  - "SecureAsserts"
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2106: Asegurar aserciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecureAsserts|  
|Identificador de comprobación|CA2106|  
|Categoría|Microsoft.Security|  
|Cambio problemático|Problemático|  
  
## Motivo  
 Un método valida un permiso y no se realiza ninguna comprobación de seguridad en el llamador.  
  
## Descripción de la regla  
 Validar un permiso de seguridad sin realizar ninguna comprobación de seguridad puede dejar una debilidad de seguridad explotable en el código.  Un recorrido de pila de seguridad se detiene cuando se somete a aserción un permiso de seguridad.  Si valida un permiso sin realizar ninguna comprobación en el llamador, éste último podría ejecutar código indirectamente utilizando los permisos del usuario.  Las aserciones sin comprobaciones de seguridad solo se permiten si está seguro de que la aserción no se puede utilizar de una manera dañina.  Una aserción es inocua si el código al que llama es inocuo, o los usuarios no pueden pasar información arbitraria al código al que llama.  
  
## Cómo corregir infracciones  
 Para corregir una infracción de esta regla, agregue una demanda de seguridad al método o a su tipo declarativo.  
  
## Cuándo suprimir advertencias  
 Suprima una advertencia de esta regla solo después de una revisión exhaustiva de la seguridad.  
  
## Vea también  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)