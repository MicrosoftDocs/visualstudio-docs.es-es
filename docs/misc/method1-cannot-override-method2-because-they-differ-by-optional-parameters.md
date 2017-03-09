---
title: "&#39;&lt;m&#233;todo1&gt;&#39; no puede reemplazar a &#39;&lt;m&#233;todo2&gt;&#39; porque se diferencian en los par&#225;metros opcionales | Microsoft Docs"
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
  - "vbc30308"
  - "bc30308"
helpviewer_keywords: 
  - "BC30308"
ms.assetid: 591dc351-4b87-4e92-81e1-2c1ff51da295
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;todo1&gt;&#39; no puede reemplazar a &#39;&lt;m&#233;todo2&gt;&#39; porque se diferencian en los par&#225;metros opcionales
Ha intentado reemplazar un método con otro método que es distinto del primero respecto de los valores de los parámetros opcionales, lo que significa que sus signaturas son diferentes. Un tipo puede reemplazar a un método reemplazable heredado declarar un método con el mismo nombre y la misma signatura y al marcar la declaración con el modificador `Overrides`.  
  
 **Identificador de error:** BC30308  
  
### Para corregir este error  
  
-   Asegúrese de que los dos métodos tienen la misma signatura.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Invalidar propiedades y métodos](http://msdn.microsoft.com/es-es/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)