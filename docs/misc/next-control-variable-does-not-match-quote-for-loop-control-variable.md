---
title: "La variable de control &#39;Next&#39; no coincide con la variable de control del bucle &#39;For&#39; | Microsoft Docs"
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
  - "vbc30976"
  - "bc30976"
helpviewer_keywords: 
  - "BC30976"
ms.assetid: 87c2d464-43bf-426f-b78b-7bc07ba171e6
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable de control &#39;Next&#39; no coincide con la variable de control del bucle &#39;For&#39;
La variable de control en la instrucción `Next` de un bucle `For...Next` debe coincidir con la variable en la instrucción `For` correspondiente.  
  
 **Identificador de error:** BC30976  
  
### Para corregir este error  
  
-   Compruebe la ortografía de la variable en la instrucción `Next` y en la instrucción `For` correspondiente para asegurarse de que coinciden.  
  
-   Asegúrese de que ninguna parte del bucle envolvente se eliminó accidentalmente.  
  
-   Si este bucle forma parte de un conjunto de bucles anidados, compruebe que cada bucle esté terminado correctamente.  
  
## Vea también  
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)