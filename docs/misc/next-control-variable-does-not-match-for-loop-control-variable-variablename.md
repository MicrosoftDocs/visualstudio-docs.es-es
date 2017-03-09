---
title: "La variable de control Next no coincide con la variable de control del bucle For &#39;&lt;nombreVariable&gt;&#39;. | Microsoft Docs"
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
  - "vbc30070"
  - "bc30070"
helpviewer_keywords: 
  - "BC30070"
ms.assetid: e9e96008-b053-4fa0-8966-decaad99fecd
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable de control Next no coincide con la variable de control del bucle For &#39;&lt;nombreVariable&gt;&#39;.
La variable de control en la instrucción `Next` de un bucle `For...Next` debe coincidir con la variable en la instrucción `For` correspondiente.  
  
 **Identificador de error:** BC30070  
  
### Para corregir este error  
  
1.  Compruebe la ortografía de la variable en la instrucción `Next` y en la instrucción `For` correspondiente para asegurarse de que coinciden.  
  
2.  Asegúrese de que ninguna parte del bucle envolvente se ha eliminado accidentalmente.  
  
3.  Si este bucle forma parte de un conjunto de bucles anidados, compruebe que cada bucle esté terminado correctamente.  
  
## Vea también  
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)