---
title: "&#39;End Property&#39; debe ir precedida de la instrucci&#243;n &#39;Property&#39; correspondiente. | Microsoft Docs"
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
  - "vbc30431"
  - "bc30431"
helpviewer_keywords: 
  - "BC30431"
ms.assetid: b1e02d97-b38a-4acf-b351-1726f17a0051
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Property&#39; debe ir precedida de la instrucci&#243;n &#39;Property&#39; correspondiente.
Una instrucción `End Property` aparece en el código sin ninguna declaración `Property` anterior.  
  
 **Identificador de error:** BC30431  
  
### Para corregir este error  
  
-   Quite la instrucción `End Property` si es redundante.  
  
-   Facilite el procedimiento `Property` si falta alguno.  
  
-   Mueva la instrucción `End Property` al lugar adecuado del código.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Propiedades y procedimientos de propiedad](http://msdn.microsoft.com/es-es/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [End \<palabra clave\> \(Instrucción\)](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)