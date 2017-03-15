---
title: "Las expresiones &#39;AddressOf&#39; no son v&#225;lidas en la primera expresi&#243;n de una instrucci&#243;n &#39;Select Case&#39; | Microsoft Docs"
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
  - "bc36636"
  - "vbc36636"
helpviewer_keywords: 
  - "BC36636"
ms.assetid: 2ccc0ccc-d4d0-4910-8859-dedfa57c8126
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las expresiones &#39;AddressOf&#39; no son v&#225;lidas en la primera expresi&#243;n de una instrucci&#243;n &#39;Select Case&#39;
No se puede usar un expresión `AddressOf` para la expresión de prueba en una instrucción `Select Case`. Las expresiones `AddressOf` devuelven delegados de función, y la expresión de prueba de una instrucción `Select Case` debe ser un tipo de datos básico.  
  
 **Identificador de error:** BC36636  
  
### Para corregir este error  
  
-   Examine el código para determinar si podría funcionar una construcción condicional diferente como, por ejemplo, una instrucción `If...Then...Else`.  
  
## Vea también  
 [AddressOf \(Operador\)](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [If...Then...Else \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)   
 [Select...Case \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/select-case-statement)