---
title: "&#39;Exit AddHandler&#39;, &#39;Exit RemoveHandler&#39; y &#39;Exit RaiseEvent&#39; no son v&#225;lidos | Microsoft Docs"
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
  - "vbc31111"
  - "bc31111"
helpviewer_keywords: 
  - "BC31111"
ms.assetid: e02264f3-0645-4de5-b622-8a2a74496b64
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit AddHandler&#39;, &#39;Exit RemoveHandler&#39; y &#39;Exit RaiseEvent&#39; no son v&#225;lidos
'Exit AddHandler', 'Exit RemoveHandler' y 'Exit RaiseEvent' no son válidos. Use 'Return' para salir de los miembros de evento.  
  
 La instrucción `Exit` no se puede usar para salir de los métodos `AddHandler`, `RemoveHandler` o `RaiseEvent` en una declaración `Custom Event`. En su lugar, use la instrucción `Return` sin especificar ninguna expresión de devolución, para salir del método.  
  
 **Identificador de error:** BC31111  
  
### Para corregir este error  
  
-   Reemplace la instrucción `Exit` por una instrucción `Return`.  
  
     Asegúrese de que la instrucción `Return` no especifica una expresión de devolución.  
  
## Vea también  
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler: eliminar](http://msdn.microsoft.com/es-es/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler: eliminar](http://msdn.microsoft.com/es-es/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent: eliminar](http://msdn.microsoft.com/es-es/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Return \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)