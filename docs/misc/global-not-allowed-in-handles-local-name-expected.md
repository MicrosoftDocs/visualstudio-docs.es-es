---
title: "&#39;Global&#39; no se permite en identificadores; se esperaba el nombre local | Microsoft Docs"
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
  - "bc36002"
  - "vbc36002"
helpviewer_keywords: 
  - "BC36002"
ms.assetid: 7b4602a9-84c9-4068-81bc-e8df03ffc130
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Global&#39; no se permite en identificadores; se esperaba el nombre local
Una cláusula `Handles` debe hacer referencia a un evento local. La palabra clave `Global` proporciona acceso a elementos de programación globales.  
  
 **Identificador de error:** BC36002  
  
### Para corregir este error  
  
-   Cambie la cláusula `Handles` para que haga referencia a una instancia local del evento en lugar de a la instancia global.  
  
## Vea también  
 [Global \- delete](http://msdn.microsoft.com/es-es/18c8ba14-40f6-4978-8096-6a5852324635)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Eventos](/dotnet/visual-basic/programming-guide/language-features/events/events)