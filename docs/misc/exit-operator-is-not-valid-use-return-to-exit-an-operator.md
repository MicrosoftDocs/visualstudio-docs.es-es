---
title: "&#39;Exit Operator&#39; no es v&#225;lido. Use &#39;Return&#39; para salir de un operador. | Microsoft Docs"
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
  - "bc33008"
  - "vbc33008"
helpviewer_keywords: 
  - "BC33008"
ms.assetid: 8c44456b-8fd2-4168-ad8c-b6da129242ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit Operator&#39; no es v&#225;lido. Use &#39;Return&#39; para salir de un operador.
Una instrucción `Exit Operator` aparece en un procedimiento `Operator`.  
  
 Debe usar una [Return \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/return-statement) para volver de un procedimiento `Operator`. La [Exit \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/exit-statement) no acepta la palabra clave `Operator` y la instrucción `End Operator` no devuelve el control al código de llamada.  
  
 **Identificador de error:** BC33008  
  
### Para corregir este error  
  
-   Reemplace la instrucción `Exit Operator` por una instrucción `Return`.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)