---
title: "Se esperaba &#39;Sub&#39; o &#39;Function&#39; | Microsoft Docs"
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
  - "vbc30215"
  - "bc30215"
helpviewer_keywords: 
  - "BC30215"
ms.assetid: 013f4200-b3cf-4cd8-a235-15067ca773fc
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;Sub&#39; o &#39;Function&#39;
Una instrucción `Declare` no especifica `Sub` o `Function`.`Declare` identifica un procedimiento externo y debe especificar qué tipo de procedimiento.  
  
 **Identificador de error:** BC30215  
  
### Para corregir este error  
  
-   Agregue la palabra clave `Sub` o `Function` a la instrucción `Declare`.  
  
## Vea también  
 [Declare \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/declare-statement)