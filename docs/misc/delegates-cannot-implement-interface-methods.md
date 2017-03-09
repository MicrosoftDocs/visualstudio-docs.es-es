---
title: "Los delegados no pueden implementar m&#233;todos de interfaz | Microsoft Docs"
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
  - "bc30018"
  - "vbc30018"
helpviewer_keywords: 
  - "BC30018"
ms.assetid: 71851072-c0c7-4131-aaf7-f3e9e6a2a448
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los delegados no pueden implementar m&#233;todos de interfaz
Un delegado es un tipo de referencia que apunta a un procedimiento compartido o a un procedimiento de instancia en un objeto. Dado que el procedimiento al que apunta se puede cambiar por asignación, la instrucción `Delegate` no admite las cláusulas `Handles` o `Implements`.  
  
 **Identificador de error:** BC30018  
  
### Para corregir este error  
  
-   Quite la cláusula `Implements` de la instrucción `Delegate`.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Delegados y operador AddressOf](http://msdn.microsoft.com/es-es/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegate \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/delegate-statement)   
 [Handles](/dotnet/visual-basic/language-reference/statements/handles-clause)   
 [Implements \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/implements-statement)