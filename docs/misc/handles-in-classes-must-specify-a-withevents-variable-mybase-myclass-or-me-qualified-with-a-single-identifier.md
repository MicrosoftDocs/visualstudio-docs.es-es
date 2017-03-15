---
title: "&#39;Handles&#39; debe especificar una variable &#39;WithEvents&#39;, &#39;MyBase&#39;, &#39;MyClass&#39; o &#39;Me&#39; calificada con un solo identificador cuando aparece en las clases. | Microsoft Docs"
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
  - "bc31412"
  - "vbc31412"
helpviewer_keywords: 
  - "BC31412"
ms.assetid: acbefc38-448a-4afa-90c2-77389415d618
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Handles&#39; debe especificar una variable &#39;WithEvents&#39;, &#39;MyBase&#39;, &#39;MyClass&#39; o &#39;Me&#39; calificada con un solo identificador cuando aparece en las clases.
Para especificar un controlador de eventos, las instrucciones `Handles` deben especificar una variable de objeto declarada con la palabra clave `WithEvents` o un miembro calificado con la palabra clave `MyBase`.  
  
 **Id. de error:** BC31412  
  
### Para corregir este error  
  
1.  Utilice el modificador `WithEvents` para declarar las variables para su uso con la instrucción `Handles`.  
  
2.  Especifique el nombre de un evento para la clase actual de la clase base.  
  
## Vea también  
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [WithEvents](/dotnet/visual-basic/language-reference/modifiers/withevents)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)