---
title: "Las instrucciones Declare de un m&#243;dulo no se pueden declarar como &#39;&lt;especificador&gt;&#39;. | Microsoft Docs"
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
  - "vbc30786"
  - "bc30786"
helpviewer_keywords: 
  - "BC30786"
ms.assetid: 488b855f-72ea-414b-bffc-a5b63e97d289
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las instrucciones Declare de un m&#243;dulo no se pueden declarar como &#39;&lt;especificador&gt;&#39;.
Una declaración `Declare` tiene un especificador que no es válido dentro de una declaración `Module`. Nunca se pueden crear instancias de módulos, no admiten herencia y no pueden implementar interfaces.  
  
 **Identificador de error:** BC30786  
  
### Para corregir este error  
  
-   Quite el especificador.  
  
## Vea también  
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Module \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/module-statement)