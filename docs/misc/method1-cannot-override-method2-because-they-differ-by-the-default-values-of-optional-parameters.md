---
title: "&#39;&lt;m&#233;todo1&gt;&#39; no puede reemplazar a &#39;&lt;m&#233;todo2&gt;&#39; porque se diferencian en los valores predeterminados de los par&#225;metros opcionales | Microsoft Docs"
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
  - "vbc30307"
  - "bc30307"
helpviewer_keywords: 
  - "BC30307"
ms.assetid: c4cf6040-41c3-4650-8eb9-bff063756599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;todo1&gt;&#39; no puede reemplazar a &#39;&lt;m&#233;todo2&gt;&#39; porque se diferencian en los valores predeterminados de los par&#225;metros opcionales
Intentó reemplazar un método por otro método que es distinto del primero en los valores predeterminados de los parámetros opcionales, lo que significa que sus signaturas son diferentes. Un tipo puede reemplazar a un método reemplazable heredado. Para ello, debe declarar un método con el mismo nombre y la misma signatura, así como marcar la declaración con el modificador `Overrides`.  
  
 **Identificador de error:** BC30307  
  
### Para corregir este error  
  
-   Asegúrese de que los dos métodos tienen la misma signatura.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [NO ESTÁ EN LA COMPILACIÓN: Reemplazar modificadores](http://msdn.microsoft.com/es-es/18e8ef02-e79b-470e-837a-46a8f4163d32)