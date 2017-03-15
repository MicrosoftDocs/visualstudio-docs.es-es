---
title: "El m&#233;todo &#39;RaiseEvent&#39; debe tener la misma firma que el tipo delegado del evento &#39;&lt;signature&gt;&#39; que lo contiene | Microsoft Docs"
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
  - "bc31137"
  - "vbc31137"
helpviewer_keywords: 
  - "BC31137"
ms.assetid: 9db77546-9205-4fd2-baf6-6eb1b46b1f1a
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El m&#233;todo &#39;RaiseEvent&#39; debe tener la misma firma que el tipo delegado del evento &#39;&lt;signature&gt;&#39; que lo contiene
Una declaración `Custom Event` debe tener una declaración `RaiseEvent` con la misma firma que el tipo delegado que especifica la cláusula `As` del evento personalizado.  
  
 Para que las firmas coincidan, la declaración `RaiseEvent` y el delegado deben tener el número de parámetros y los tipos de parámetros deben coincidir.  
  
 **Id. de error:** BC31137  
  
### Para corregir este error  
  
-   Cambie los parámetros de la declaración `RaiseEvent` para que coincidan con los parámetros del tipo delegado.  
  
## Ejemplo  
 En este ejemplo se muestra un evento personalizado con los tipos de parámetro correctos para la declaración `RaiseEvent`.  
  
 [!code-vb[VbVbalrEventError#2](../misc/codesnippet/VisualBasic/raiseevent-method-must-have-the-same-signature-as-the-containing-event-s-delegate-type-signature_1.vb)]  
  
## Vea también  
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [RaiseEvent: eliminar](http://msdn.microsoft.com/es-es/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)