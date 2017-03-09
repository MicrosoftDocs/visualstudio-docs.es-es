---
title: "Los par&#225;metros de &lt;tipo&gt; no se pueden declarar como &#39;Optional&#39; | Microsoft Docs"
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
  - "bc33010"
  - "vbc33010"
helpviewer_keywords: 
  - "BC33010"
ms.assetid: ec4023e7-9ba6-4532-a6b9-4ae6b4f9063a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los par&#225;metros de &lt;tipo&gt; no se pueden declarar como &#39;Optional&#39;
Una definición de un delegado, evento u operador declara un parámetro [Optional](/dotnet/visual-basic/language-reference/modifiers/optional).  
  
 Los parámetros `Optional` solo se permiten en los parámetros `Declare`, `Function`, `Property` y `Sub`.  
  
 **Identificador de error:** BC33010  
  
### Para corregir este error  
  
-   Quite la palabra clave `Optional` de la lista de parámetros.  
  
-   Si va a definir un operador, quizás puede conseguir la función `Optional` con una serie de sobrecargas.  
  
-   Si está definiendo un delegado o un evento, debe rehacer toda la lógica de esta parte de la aplicación. No puede usar los parámetros `Optional` o [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray), ni versiones sobrecargadas, en parámetros de delegado o evento.  
  
## Vea también  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)