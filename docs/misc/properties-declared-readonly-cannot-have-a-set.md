---
title: "Las propiedades declaradas como &#39;ReadOnly&#39; no pueden tener una instrucci&#243;n &#39;Set&#39; | Microsoft Docs"
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
  - "vbc30022"
  - "bc30022"
helpviewer_keywords: 
  - "BC30022"
ms.assetid: a22eff96-8c18-47c4-9ef0-f98b2ab8a5d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las propiedades declaradas como &#39;ReadOnly&#39; no pueden tener una instrucci&#243;n &#39;Set&#39;
El procedimiento `Set` escribe el valor de una propiedad. No se pueden leer propiedades `ReadOnly`.  
  
 **Id. de error:** BC30022  
  
### Para corregir este error  
  
-   Quite la palabra clave `ReadOnly` de la instrucción `Property` o quite el procedimiento `Set` del cuerpo de la propiedad.  
  
## Vea también  
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)   
 [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement)   
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)