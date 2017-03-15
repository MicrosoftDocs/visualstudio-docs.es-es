---
title: "Las variables de los m&#243;dulos no se pueden declarar como &#39;&lt;especificador&gt;&#39;. | Microsoft Docs"
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
  - "bc30593"
  - "vbc30593"
helpviewer_keywords: 
  - "BC30593"
ms.assetid: 2500b776-7fa4-4272-8cc7-204593706651
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las variables de los m&#243;dulos no se pueden declarar como &#39;&lt;especificador&gt;&#39;.
Se ha usado un especificador, como `MustInherit`, en una variable de una instrucción `Module`. Nunca se pueden crear instancias de módulos, no admiten herencia y no pueden implementar interfaces.  
  
 **Identificador de error:** BC30593  
  
### Para corregir este error  
  
-   Quite el especificador.  
  
## Vea también  
 [Module \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/module-statement)