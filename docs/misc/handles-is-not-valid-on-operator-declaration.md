---
title: "&#39;Handles&#39; no es v&#225;lido en la declaraci&#243;n del operador | Microsoft Docs"
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
  - "bc33003"
  - "vbc33003"
helpviewer_keywords: 
  - "BC33003"
ms.assetid: 8336402c-9393-4e8e-834d-55c2268f24f6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Handles&#39; no es v&#225;lido en la declaraci&#243;n del operador
Una [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement) especifica la palabra clave [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause).  
  
 Solo un procedimiento `Sub` puede controlar eventos. Un procedimiento `Operator` no puede. Para más información sobre los controladores de eventos, vea [Cómo: Llamar a un controlador de eventos en Visual Basic](../Topic/How%20to:%20Call%20an%20Event%20Handler%20in%20Visual%20Basic.md).  
  
 Un procedimiento `Operator` requiere ambas palabras clave `Public` y `Shared`, y un operador de conversión requiere la palabra clave `Widening` o `Narrowing`. Para obtener más información, consulta [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures).  
  
 **Identificador de error:** BC33003  
  
### Para corregir este error  
  
-   Si tiene previsto que este procedimiento controle eventos, vuelva a escribirlo como un procedimiento `Sub`.  
  
-   Si tiene previsto que este procedimiento defina un operador, quite la palabra clave `Handles` de su declaración.  
  
## Vea también  
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)