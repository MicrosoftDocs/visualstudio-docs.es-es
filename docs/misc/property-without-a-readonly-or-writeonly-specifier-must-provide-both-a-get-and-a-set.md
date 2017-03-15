---
title: "La propiedad sin un especificador &#39;ReadOnly&#39; o &#39;WriteOnly&#39; debe proporcionar una instrucci&#243;n &#39;Get&#39; y una instrucci&#243;n &#39;Set&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30124"
  - "vbc30124"
helpviewer_keywords: 
  - "BC30124"
ms.assetid: b24fc997-9a6b-44d1-b712-dab498a6fc72
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propiedad sin un especificador &#39;ReadOnly&#39; o &#39;WriteOnly&#39; debe proporcionar una instrucci&#243;n &#39;Get&#39; y una instrucci&#243;n &#39;Set&#39;.
Si no se declara una propiedad como `ReadOnly` o `WriteOnly`, debe proporcionar procedimientos para leer y escribir su valor.  
  
 **Identificador de error:** BC30124  
  
### Para corregir este error  
  
1.  Asegúrese de incluir un procedimiento `Get` y un procedimiento `Set` entre la instrucción `Property` y la instrucción `End Property`.  
  
2.  Compruebe que otros procedimientos de la declaración `Property` finalicen correctamente.  
  
## Vea también  
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement)