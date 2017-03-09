---
title: "&#39;Implements&#39; no es v&#225;lida en declaraciones de operadores. | Microsoft Docs"
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
  - "vbc33004"
  - "bc33004"
helpviewer_keywords: 
  - "BC33004"
ms.assetid: 22f27f4d-4bbd-4f8f-a6e8-0fc10efb268d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Implements&#39; no es v&#225;lida en declaraciones de operadores.
Una [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement) especifica la palabra clave [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause).  
  
 Solo un procedimiento `Function` o `Sub`, una propiedad o un evento puede implementar un miembro de interfaz. Para obtener más información sobre la implementación, vea [NO ESTÁ EN LA COMPILACIÓN: Ejemplos de implementación de interfaz en Visual Basic](http://msdn.microsoft.com/es-es/50bf2a30-73b6-4126-a921-075fd6eec278).  
  
 Un procedimiento `Operator` necesita las palabras clave `Public` y `Shared`, y un operador de conversión necesita la palabra clave `Widening` o `Narrowing`. Para obtener más información, consulta [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures).  
  
 **Identificador de error:** BC33004  
  
### Para corregir este error  
  
-   Si tiene la intención de que este procedimiento implemente un miembro de interfaz, vuelva a escribirlo como un procedimiento `Function` o `Sub`, una propiedad o un evento.  
  
-   Si tiene la intención de que este procedimiento defina un operador, quite la palabra clave `Implements` de su declaración.  
  
## Vea también  
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)