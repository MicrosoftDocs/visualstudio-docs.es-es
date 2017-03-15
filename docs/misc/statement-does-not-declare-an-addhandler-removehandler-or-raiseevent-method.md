---
title: "La instrucci&#243;n no declara un m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; o &#39;RaiseEvent&#39; | Microsoft Docs"
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
  - "vbc31113"
  - "bc31113"
helpviewer_keywords: 
  - "BC31113"
ms.assetid: f8299c9d-6030-43e5-878e-8d2b042191b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La instrucci&#243;n no declara un m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; o &#39;RaiseEvent&#39;
La instrucción no proporciona una instrucción de declaración `AddHandler`, `RemoveHandler` o `RaiseEvent` alrededor de un procedimiento `Custom Event`. Una declaración de evento personalizado es un bloque de código delimitado por las instrucciones `Custom Event` y `End Event`. Dentro de este bloque, cada procedimiento `Custom Event` aparece como un bloque interno delimitado por una instrucción de declaración y una instrucción `End`.  
  
 **Identificador de error:** BC31113  
  
### Para corregir este error  
  
-   Proporcione una instrucción de declaración `AddHandler`, `RemoveHandler` o `RaiseEvent`.  
  
## Vea también  
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- delete](http://msdn.microsoft.com/es-es/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/es-es/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/es-es/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)