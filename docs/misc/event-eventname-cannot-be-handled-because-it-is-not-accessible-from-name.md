---
title: "No se puede controlar el evento &#39;&lt;nombreEvento&gt;&#39; porque no es accesible desde &#39;&lt;nombre&gt;&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30585"
  - "vbc30585"
helpviewer_keywords: 
  - "BC30585"
ms.assetid: fe039f8f-be6f-4b52-86bd-d551c54b85cd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede controlar el evento &#39;&lt;nombreEvento&gt;&#39; porque no es accesible desde &#39;&lt;nombre&gt;&#39;.
Ha intentado controlar un evento que no es accesible. Por ejemplo, si se comparte una variable `Handles`, el método que controla los eventos también se comparte.  
  
 **Identificador de error:** BC30585  
  
### Para corregir este error  
  
1.  Asegúrese de que el evento esté accesible.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Eventos y controladores de eventos](http://msdn.microsoft.com/es-es/95074a0d-1cbc-4221-a95a-964185c7f962)