---
title: "Las propiedades declaradas como &#39;WriteOnly&#39; no pueden tener una instrucci&#243;n &#39;Get&#39;. | Microsoft Docs"
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
  - "bc30023"
  - "vbc30023"
helpviewer_keywords: 
  - "BC30023"
ms.assetid: ac290f7d-cbc3-4979-a5d9-1ae1bb26e79d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las propiedades declaradas como &#39;WriteOnly&#39; no pueden tener una instrucci&#243;n &#39;Get&#39;.
El procedimiento `Get` lee el valor de una propiedad. No se pueden leer `WriteOnly` propiedades.  
  
 **Identificador de error:** BC30023  
  
### Para corregir este error  
  
-   Quite la palabra clave `WriteOnly` de la instrucción `Property` o quite el procedimiento `Get` del cuerpo de la propiedad.  
  
## Vea también  
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [WriteOnly](/dotnet/visual-basic/language-reference/modifiers/writeonly)