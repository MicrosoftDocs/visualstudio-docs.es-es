---
title: "El tipo &#39;&lt;nombreDeTipo&gt;&#39; no puede heredar de un tipo anidado en este | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30908"
  - "vbc30908"
helpviewer_keywords: 
  - "BC30908"
ms.assetid: bca164b2-a4a9-4ed4-9f71-a9a5a42f181a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;nombreDeTipo&gt;&#39; no puede heredar de un tipo anidado en este
Una definición de clase o interfaz incluye [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement) que especifica un tipo anidado en este.  
  
 La herencia debe ser lineal, no circular. Un tipo no puede heredar de un tipo que herede de este.  
  
 Una restricción relacionada es que un tipo no puede heredar de un tipo que todavía no está definido. La herencia implica la capacidad de volver a usar los miembros de la clase base, lo que a su vez requiere que estos miembros estén definidos. Por lo tanto, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede compilar código como el del siguiente ejemplo.  
  
```  
Public Class outerClass ' The following statement is INVALID because innerClass is not defined. Inherits innerClass Public Class innerClass Public Sub doSomething() End Sub End Class End Class  
```  
  
 **Identificador de error:** BC30908  
  
### Para corregir este error  
  
-   Si el tipo que hereda \(el tipo externo del anidamiento\) debe heredar del tipo interno, mueva el tipo interno al tipo externo.  
  
-   Si el tipo interno debe estar anidado dentro del tipo externo, el tipo externo no puede heredar de este. Quite [Inherits \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/inherits-statement).  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Herencia en Visual Basic](http://msdn.microsoft.com/es-es/e5e6e240-ed31-4657-820c-079b7c79313c)