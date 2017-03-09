---
title: "Los par&#225;metros de m&#233;todo &#39;AddHandler&#39; y &#39;RemoveHandler&#39; deben tener el mismo tipo delegado que el evento que los contiene | Microsoft Docs"
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
  - "bc31136"
  - "vbc31136"
helpviewer_keywords: 
  - "BC31136"
ms.assetid: 199b2f7b-a85e-465d-9853-0995156e7ab6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los par&#225;metros de m&#233;todo &#39;AddHandler&#39; y &#39;RemoveHandler&#39; deben tener el mismo tipo delegado que el evento que los contiene
Una declaración `Custom Event` debe tener declaraciones `AddHandler` o `RemoveHandler`, cada una de las cuales toma un parámetro único del tipo delegado especificado por la cláusula `As` del evento personalizado.  
  
 **Identificador de error:** BC31136  
  
### Para corregir este error  
  
-   Cambie el tipo del parámetro para que coincida con el tipo delegado especificado por la cláusula `As` del evento personalizado.  
  
## Ejemplo  
 En este ejemplo se muestra un evento personalizado con los tipos de parámetro correctos para las declaraciones `AddHandler` y `RemoveHandler`.  
  
 [!code-vb[VbVbalrEventError#1](../misc/codesnippet/VisualBasic/addhandler-and-removehandler-method-parameters-must-have-the-same-delegate-type-as-the-containing-event_1.vb)]  
  
## Vea también  
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- delete](http://msdn.microsoft.com/es-es/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/es-es/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)