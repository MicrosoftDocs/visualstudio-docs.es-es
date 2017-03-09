---
title: "No se declar&#243; &#39;&lt;lsetstmt&gt;&#39; | Microsoft Docs"
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
  - "bc30820"
  - "vbc30820"
helpviewer_keywords: 
  - "BC30820"
ms.assetid: 8666dd52-58ea-4b84-b59a-8ebd8b2cb23b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se declar&#243; &#39;&lt;lsetstmt&gt;&#39;
No se declaró '\<lsetstmt\>'. Ya no se admiten instrucciones LSet; use Microsoft.VisualBasic.LSet en su lugar.  
  
 Varias funciones que eran intrínsecas de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] en versiones anteriores se movieron al espacio de nombres <xref:Microsoft.VisualBasic?displayProperty=fullName>. Esto hace que sus funciones estén disponibles de manera más general para todos los lenguajes de programación.  
  
 **Identificador de error:** BC30820  
  
### Para corregir este error  
  
-   Use la función `LSet` del espacio de nombres `Microsoft.VisualBasic` en su lugar.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Función LSet](http://msdn.microsoft.com/es-es/591d286c-6b7a-4350-ae74-99fee00fd964)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/es-es/0483590a-6309-449c-a2fa-effa26a03b95)