---
title: "Los par&#225;metros de m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; y &#39;RaiseEvent&#39; no se pueden declarar como &#39;&lt;modifier&gt;&#39;. | Microsoft Docs"
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
  - "vbc31138"
  - "bc31138"
helpviewer_keywords: 
  - "BC31138"
ms.assetid: 6d8df92a-95fc-4a7d-ab1e-06d312155c55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los par&#225;metros de m&#233;todo &#39;AddHandler&#39;, &#39;RemoveHandler&#39; y &#39;RaiseEvent&#39; no se pueden declarar como &#39;&lt;modifier&gt;&#39;.
Los parámetros de los métodos `AddHandler`, `RemoveHandler` y `RaiseEvent` no se pueden declarar con los modificadores `Optional` o `ParamArray`.  
  
 Los modificadores `Optional` o `ParamArray` solo se permiten en parámetros en las declaraciones `Declare`, `Function`, `Property` y `Sub`.  
  
 **Identificador de error:** BC31138  
  
### Para corregir este error  
  
-   Quite la palabra clave `Optional` o `ParamArray` de la lista de parámetros.  
  
## Vea también  
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler: eliminar](http://msdn.microsoft.com/es-es/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler: eliminar](http://msdn.microsoft.com/es-es/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent: eliminar](http://msdn.microsoft.com/es-es/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)   
 [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)