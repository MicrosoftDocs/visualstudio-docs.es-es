---
title: "Los m&#233;todos gen&#233;ricos no pueden usar la cl&#225;usula &#39;Handles&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32080"
  - "BC32080"
helpviewer_keywords: 
  - "BC32080"
ms.assetid: 88c62a1c-aee3-46b2-ad78-76790022c04c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los m&#233;todos gen&#233;ricos no pueden usar la cl&#225;usula &#39;Handles&#39;.
Un procedimiento `Sub` genérico incluye una cláusula [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause) en su declaración.  
  
 Una cláusula `Handles` especifica una lista de eventos que el procedimiento `Sub` controla. Para ser un controlador de eventos, el procedimiento `Sub` debe tener la misma firma que cada evento que se va a controlar. Un procedimiento genérico se puede crear más de una vez, con firmas que [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede predecir en tiempo de compilación. Por lo tanto, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] no puede garantizar una firma que coincida con la de los eventos en la cláusula `Handles`.  
  
 **Identificador de error:** BC32080  
  
### Para corregir este error  
  
-   Si el procedimiento `Sub` debe ser genérico, quite la cláusula `Handles` de su declaración. Use la [AddHandler \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/addhandler-statement) para asociar el controlador de eventos a un evento.  
  
-   Si el procedimiento `Sub` debe usar la cláusula `Handles` para asociar eventos, quite la cláusula [Of](/dotnet/visual-basic/language-reference/statements/of-clause) de su declaración. Debe usar un procedimiento no genérico con `Handles`.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NO ESTÁ EN LA COMPILACIÓN: Eventos y controladores de eventos](http://msdn.microsoft.com/es-es/95074a0d-1cbc-4221-a95a-964185c7f962)