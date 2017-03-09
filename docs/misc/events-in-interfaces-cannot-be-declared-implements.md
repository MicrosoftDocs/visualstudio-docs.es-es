---
title: "Los eventos de las interfaces no se pueden declarar como &#39;&lt;implementaciones&gt;&#39;. | Microsoft Docs"
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
  - "bc30688"
  - "vbc30688"
helpviewer_keywords: 
  - "BC30688"
ms.assetid: 577823c1-815c-4f1c-9177-4bbf73fa92db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los eventos de las interfaces no se pueden declarar como &#39;&lt;implementaciones&gt;&#39;.
Los eventos declarados en interfaces no pueden implementar los eventos de otras interfaces.  
  
 **Identificador de error:** BC30688  
  
### Para corregir este error  
  
1.  Quite la instrucción `Implements`.  
  
2.  Implemente el evento dentro de una clase o una estructura.  
  
## Vea también  
 [Interface \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/interface-statement)