---
title: "Los delegados no pueden administrar eventos | Microsoft Docs"
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
  - "bc30019"
  - "vbc30019"
helpviewer_keywords: 
  - "BC30019"
ms.assetid: 7f0c7bb9-8e81-44bf-acc5-80d9785708aa
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los delegados no pueden administrar eventos
Un delegado es un tipo de referencia que apunta a un procedimiento compartido o a un procedimiento de instancia en un objeto. Dado que el procedimiento al que apunta se puede cambiar por asignación, la instrucción `Delegate` no admite las cláusulas `Handles` o `Implements`.  
  
 **Identificador de error:** BC30019  
  
### Para corregir este error  
  
-   Quite la cláusula `Handles` de la instrucción `Delegate`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Delegados y el operador AddressOf](http://msdn.microsoft.com/es-es/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)