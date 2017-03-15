---
title: "Los par&#225;metros de m&#233;todo &#39;AddHandler&#39; y &#39;RemoveHandler&#39; no se pueden declarar como &#39;ByRef&#39;. | Microsoft Docs"
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
  - "vbc31134"
  - "bc31134"
helpviewer_keywords: 
  - "BC31134"
ms.assetid: 942f0b91-e71a-499a-ad10-a5dfcb4e72b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los par&#225;metros de m&#233;todo &#39;AddHandler&#39; y &#39;RemoveHandler&#39; no se pueden declarar como &#39;ByRef&#39;.
Los parámetros de los métodos `AddHandler` y `RemoveHandler` no se pueden declarar con el modificador `ByRef`.  
  
 **Identificador de error:** BC31134  
  
### Para corregir este error  
  
-   Quite la palabra clave `ByRef` del parámetro.  
  
## Vea también  
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler: eliminar](http://msdn.microsoft.com/es-es/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler: eliminar](http://msdn.microsoft.com/es-es/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)