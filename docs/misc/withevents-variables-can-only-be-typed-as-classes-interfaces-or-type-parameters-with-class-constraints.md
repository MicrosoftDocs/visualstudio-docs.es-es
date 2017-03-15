---
title: "Las variables &#39;WithEvents&#39; solo se pueden escribir como clases, interfaces o par&#225;metros de tipo con restricciones de clase. | Microsoft Docs"
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
  - "vbc30413"
  - "bc30413"
helpviewer_keywords: 
  - "BC30413"
ms.assetid: 11ddf207-2760-425f-b4c2-bb9fe6da36ea
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las variables &#39;WithEvents&#39; solo se pueden escribir como clases, interfaces o par&#225;metros de tipo con restricciones de clase.
Declara una variable que se escribe como una estructura con `WithEvents`, que no es un uso válido del modificador `WithEvents`.  
  
 **Id. de error:** BC30413  
  
### Para corregir este error  
  
1.  Use `AddHandler` para controlar los eventos definidos en una estructura.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: WithEvents y la cláusula Handles](http://msdn.microsoft.com/es-es/072b9cf6-6298-46f1-849e-4edc1631564c)   
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [AddHandler \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/addhandler-statement)