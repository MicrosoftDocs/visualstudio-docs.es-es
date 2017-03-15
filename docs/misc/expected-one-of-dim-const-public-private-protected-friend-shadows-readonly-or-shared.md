---
title: "Se esperaba &#39;Dim&#39;, &#39;Const&#39;, &#39;Public&#39;, &#39;Private&#39;, &#39;Protected&#39;, &#39;Friend&#39;, &#39;Shadows&#39;, &#39;ReadOnly&#39; o &#39;Shared&#39;. | Microsoft Docs"
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
  - "bc30195"
  - "vbc30195"
helpviewer_keywords: 
  - "BC30195"
ms.assetid: 95684eaa-5aa2-4ae4-9a73-5f97c491e02c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se esperaba &#39;Dim&#39;, &#39;Const&#39;, &#39;Public&#39;, &#39;Private&#39;, &#39;Protected&#39;, &#39;Friend&#39;, &#39;Shadows&#39;, &#39;ReadOnly&#39; o &#39;Shared&#39;.
Falta una palabra clave de declaración en una instrucción de declaración. Una posible causa es que una declaración de atributo llama a un método.  
  
 **Identificador de error:** BC30195  
  
### Para corregir este error  
  
1.  Compruebe si un método se declara dentro de una declaración de atributo.  
  
2.  Inicie la instrucción con la palabra clave de declaración adecuada.  
  
## Vea también  
 [Elementos declarados](/dotnet/visual-basic/programming-guide/language-features/declared-elements/index)   
 [Las matrices no se pueden declarar con 'New'.](../misc/arrays-cannot-be-declared-with-new.md)