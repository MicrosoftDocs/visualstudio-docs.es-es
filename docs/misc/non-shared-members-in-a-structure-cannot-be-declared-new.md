---
title: "Los miembros no compartidos de una estructura no se pueden declarar como &#39;New&#39;. | Microsoft Docs"
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
  - "vbc30795"
  - "BC30795"
helpviewer_keywords: 
  - "BC30795"
ms.assetid: 8e4e1ad8-3bac-475f-82e8-e4f134692204
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los miembros no compartidos de una estructura no se pueden declarar como &#39;New&#39;.
Una variable no compartida de una estructura se declara con una cláusula `New`.  
  
 Puede inicializar una variable de referencia compartida en una estructura, y puede haber una variable de referencia no compartida sin inicialización, como muestran las siguientes líneas de código.  
  
 `Shared structVar1 As New System.ApplicationException`  
  
 `Dim structVar2 As System.ApplicationException`  
  
 Sin embargo, no se puede inicializar una variable de referencia no compartida en una estructura. La siguiente línea de código no es válida.  
  
 `Dim structVar3 As New System.ApplicationException ' INVALID IN A STRUCTURE`  
  
 **Identificador de error:** BC30795  
  
### Para corregir este error  
  
-   Quite el modificador `Shared` o la palabra clave `New` de la declaración de variable de referencia.  
  
## Vea también  
 [Structure \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/structure-statement)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator)