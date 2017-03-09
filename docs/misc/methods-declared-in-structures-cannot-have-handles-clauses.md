---
title: "Los m&#233;todos declarados en estructuras no pueden tener cl&#225;usulas &#39;Handles&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30728"
  - "bc30728"
helpviewer_keywords: 
  - "BC30728"
ms.assetid: 64c70bb5-3696-4865-8194-328394c2b4b1
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los m&#233;todos declarados en estructuras no pueden tener cl&#225;usulas &#39;Handles&#39;
Los métodos de estructura no pueden utilizar la palabra clave `Handles` para controlar eventos.  
  
 **Id. de error:** BC30728  
  
### Para corregir este error  
  
-   Considere la posibilidad de volver a diseñar la estructura como una clase.  
  
     Puede usar `AddHandler` para asociar un evento a un controlador de eventos de una estructura, siempre que la estructura implemente un controlador de eventos definido en una interfaz.  
  
## Vea también  
 [Estructuras y clases](/dotnet/visual-basic/programming-guide/language-features/data-types/structures-and-classes)   
 [NO ESTÁ EN LA COMPILACIÓN: Clases: planos para objetos](http://msdn.microsoft.com/es-es/2c86373d-0333-4616-a7d8-4790c4e89f7b)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)   
 [NO ESTÁ EN LA COMPILACIÓN: AddHandler y RemoveHandler](http://msdn.microsoft.com/es-es/a7a24bd2-519a-46fe-8a2c-2b9df2ca28ef)