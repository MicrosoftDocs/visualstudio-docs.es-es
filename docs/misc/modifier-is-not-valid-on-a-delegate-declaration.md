---
title: "&#39;&lt;modifier&gt;&#39; no es v&#225;lido en una declaraci&#243;n Delegate | Microsoft Docs"
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
  - "bc30385"
  - "vbc30385"
helpviewer_keywords: 
  - "BC30385"
ms.assetid: cacbcdc7-dca9-4a22-b3bf-7e264308c031
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;modifier&gt;&#39; no es v&#225;lido en una declaraci&#243;n Delegate
Ha intentado utilizar un modificador, como `Shared`, en una declaración de delegado. Los delegados son objetos que se utilizan para llamar a los métodos de otros objetos, mediante la definición de un constructor al que se le pasa la especificación de un método de objeto. No es válido para especificar un modificador en una declaración de delegado.  
  
 **Id. de error:** BC30385  
  
### Para corregir este error  
  
1.  Quite el modificador.  
  
## Vea también  
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Cómo: Invocar un método delegado](../Topic/How%20to:%20Invoke%20a%20Delegate%20Method%20\(Visual%20Basic\).md)