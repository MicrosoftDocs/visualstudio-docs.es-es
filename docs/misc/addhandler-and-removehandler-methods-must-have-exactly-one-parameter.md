---
title: "Los m&#233;todos &#39;AddHandler&#39; y &#39;RemoveHandler&#39; deben tener exactamente un par&#225;metro | Microsoft Docs"
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
  - "vbc31133"
  - "bc31133"
helpviewer_keywords: 
  - "BC31133"
ms.assetid: f6295626-dd63-408c-ab5f-76367f94d6ca
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los m&#233;todos &#39;AddHandler&#39; y &#39;RemoveHandler&#39; deben tener exactamente un par&#225;metro
Una declaración de evento personalizado debe tener declaraciones `AddHandler` o `RemoveHandler`, cada una de las cuales toma un parámetro único del tipo delegado especificado por la cláusula `As` del evento personalizado.  
  
 **Identificador de error:** BC31133  
  
### Para corregir este error  
  
-   Quite los parámetros adicionales de la lista de parámetros y cambie el tipo de parámetro para que sea el mismo que el tipo delegado especificado por la cláusula `As` del evento personalizado.  
  
## Ejemplo  
 En este ejemplo se muestra un evento personalizado con los tipos de parámetro correctos para las declaraciones `AddHandler` y `RemoveHandler`.  
  
 [!CODE [VbVbalrEventError#1](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrEventError#1)]  
  
## Vea también  
 [Event \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [AddHandler \- delete](http://msdn.microsoft.com/es-es/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/es-es/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)