---
title: "La propiedad &#39;ReadOnly&#39; &#39;&lt;propertyname&gt;&#39; no puede ser el destino de una asignaci&#243;n | Microsoft Docs"
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
  - "bc30098"
  - "vbc30098"
helpviewer_keywords: 
  - "BC30098"
ms.assetid: d0c6cdac-a49d-49d2-ba92-ddf01eed0620
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propiedad &#39;ReadOnly&#39; &#39;&lt;propertyname&gt;&#39; no puede ser el destino de una asignaci&#243;n
Aparece una propiedad `ReadOnly` en un contexto que le asigna un valor. Solo se pueden asignar valores durante la ejecución a variables, propiedades y elementos de matriz en los que se pueda escribir.  
  
 **Id. de error:** BC30098  
  
### Para corregir este error  
  
-   Quite la palabra clave `ReadOnly` de la instrucción `Property` que declara la variable o quite la instrucción que le asigna un valor.  
  
## Vea también  
 [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly)   
 [Property \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/property-statement)