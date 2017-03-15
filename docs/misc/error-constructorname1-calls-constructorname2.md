---
title: "&lt;error&gt;: &#39;&lt;constructorname1&gt;&#39; llama a &#39;&lt;constructorname2&gt;&#39; | Microsoft Docs"
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
  - "vbc30297"
  - "bc30297"
helpviewer_keywords: 
  - "BC30297"
ms.assetid: dfca67d7-f4d7-4451-a937-68f22b8527d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;error&gt;: &#39;&lt;constructorname1&gt;&#39; llama a &#39;&lt;constructorname2&gt;&#39;
Se produce una llamada de constructor circular. Un constructor realiza una llamada a `Me.New()` o `MyClass.New()`. Una posible causa es un intento de llamar a un constructor sobrecargado con diferentes listas de argumentos.  
  
 **Identificador de error:** BC30297  
  
### Para corregir este error  
  
-   Use una lista de argumentos diferente para llamar a un constructor sobrecargado.  
  
-   Si no hay sobrecargas accesibles, quite la llamada a `Me.New()` o `MyClass.New()`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Usar constructores y destructores](http://msdn.microsoft.com/es-es/548eebe1-86c4-4377-b2f5-447cb8be3d90)