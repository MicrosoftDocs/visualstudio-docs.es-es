---
title: "Los par&#225;metros &#39;&lt;tipo&gt;&#39; no se pueden declarar &#39;ParamArray&#39; | Microsoft Docs"
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
  - "bc33009"
  - "vbc33009"
helpviewer_keywords: 
  - "BC33009"
ms.assetid: faba9aef-ca4e-4c4d-934c-a3e3d3fa3c3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los par&#225;metros &#39;&lt;tipo&gt;&#39; no se pueden declarar &#39;ParamArray&#39;
Una definición de un delegado, evento u operador declara un parámetro [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray).  
  
 Los parámetros `ParamArray` solo se permiten en los parámetros `Declare`, `Function`, `Property` y `Sub`.  
  
 **Identificador de error:** BC33009  
  
### Para corregir este error  
  
-   Quite la palabra clave `ParamArray` de la lista de parámetros.  
  
-   Si está definiendo un operador, quizás puede conseguir la función `ParamArray` con una serie de sobrecargas.  
  
-   Si está definiendo un delegado o un evento, debe rehacer toda la lógica de esta parte de la aplicación. No puede usar los parámetros [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) o `ParamArray`, ni versiones sobrecargadas, en parámetros de delegado o evento.  
  
## Vea también  
 [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)   
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)