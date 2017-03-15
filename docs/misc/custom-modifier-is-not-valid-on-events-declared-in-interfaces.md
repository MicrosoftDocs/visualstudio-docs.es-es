---
title: "El modificador &#39;Custom&#39; no es v&#225;lido en los eventos declarados en interfaces. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31121"
  - "vbc31121"
helpviewer_keywords: 
  - "BC31121"
ms.assetid: b5687034-a2b2-4961-88b7-0ba73023573e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El modificador &#39;Custom&#39; no es v&#225;lido en los eventos declarados en interfaces.
No se puede declarar un evento personalizado en una interfaz porque un evento personalizado debe proporcionar una implementación de sus métodos `AddHandler`, `RemoverHandler` y `RaiseEvent`.  
  
 La palabra clave `Custom` puede usarse en una clase derivada que implementa el evento.  
  
 **Identificador de error:** BC31121  
  
### Para corregir este error  
  
-   Quite la palabra clave `Custom` de la declaración del evento en la interfaz.  
  
## Ejemplo  
 En este ejemplo se muestra cómo implementar un evento declarado en una interfaz como un evento personalizado.  
  
 [!code-vb[VbVbalrEventError#3](../misc/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-in-interfaces_1.vb)]  
  
## Vea también  
 [Custom: eliminar](http://msdn.microsoft.com/es-es/dc62be07-c896-4866-a533-982a661d143f)   
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Class \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)