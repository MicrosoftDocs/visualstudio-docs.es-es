---
title: "Los especificadores no son v&#225;lidos en los m&#233;todos &#39;AddHandler&#39;, &#39;RemoveHandler&#39; y &#39;RaiseEvent&#39; | Microsoft Docs"
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
  - "vbc31135"
  - "bc31135"
helpviewer_keywords: 
  - "BC31135"
ms.assetid: 2eaf5a6f-d201-4f9b-bcdf-12170cb44791
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los especificadores no son v&#225;lidos en los m&#233;todos &#39;AddHandler&#39;, &#39;RemoveHandler&#39; y &#39;RaiseEvent&#39;
Las declaraciones de los métodos `AddHandler`, `RemoveHandler` y `RaiseEvent` no se pueden modificar con palabras clave como `Public` o `ReadOnly`. Solo las declaraciones modificables pueden contener tales palabras clave.  
  
 **Identificador de error:** BC31135  
  
### Para corregir este error  
  
-   Quite la palabra clave de la declaración de método.  
  
## Vea también  
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler: eliminar](http://msdn.microsoft.com/es-es/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler: eliminar](http://msdn.microsoft.com/es-es/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent: eliminar](http://msdn.microsoft.com/es-es/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [NO ESTÁ EN LA COMPILACIÓN Palabras clave \(Visual Basic\)](http://msdn.microsoft.com/es-es/3a6fda51-6ade-4862-a407-1c305c3906ec)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)