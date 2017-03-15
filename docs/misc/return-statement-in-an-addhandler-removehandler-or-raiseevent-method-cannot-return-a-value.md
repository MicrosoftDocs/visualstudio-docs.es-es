---
title: "La instrucci&#243;n &#39;Return&#39; en un m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; o &#39;RaiseEvent&#39; no puede devolver un valor. | Microsoft Docs"
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
  - "bc30940"
  - "vbc30940"
helpviewer_keywords: 
  - "BC30940"
ms.assetid: 0e4d037a-2d20-40e4-8ead-6d709d1c9c7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n &#39;Return&#39; en un m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; o &#39;RaiseEvent&#39; no puede devolver un valor.
Los métodos `AddHandler`, `RemoveHandler` y `RaiseEvent` en una declaración `Custom Event` puede contener instrucciones `Return` para salir de los métodos. Sin embargo, la instrucción `Return` no puede especificar un valor devuelto porque los métodos no pueden devolver valores.  
  
 **Identificador de error:** BC30940  
  
### Para corregir este error  
  
-   Quite la expresión que sigue a la instrucción `Return`.  
  
## Vea también  
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler: eliminar](http://msdn.microsoft.com/es-es/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler: eliminar](http://msdn.microsoft.com/es-es/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent: eliminar](http://msdn.microsoft.com/es-es/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Return \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/return-statement)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)