---
title: "El operando &#39;Using&#39; de tipo &#39;&lt;typename&gt;&#39; debe implementar System.IDisposable. | Microsoft Docs"
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
  - "vbc36010"
  - "bc36010"
helpviewer_keywords: 
  - "BC36010"
ms.assetid: ae9ed5d5-68ba-4950-bb7a-61327fa0e7d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operando &#39;Using&#39; de tipo &#39;&lt;typename&gt;&#39; debe implementar System.IDisposable.
Una instrucción `Using` especifica un recurso de un tipo que no implementa la interfaz <xref:System.IDisposable>.  
  
 El propósito de un bloque `Using` es garantizar la eliminación de un recurso del sistema al salir del bloque. Para satisfacer este propósito, el recurso debe exponer el método <xref:System.IDisposable.Dispose%2A> implementado desde <xref:System.IDisposable>.  
  
 **Identificador de error:** BC36010  
  
### Para corregir este error  
  
-   Quite el recurso de la lista de recursos de la instrucción `Using`, o reemplácelo por un recurso que implemente <xref:System.IDisposable>.  
  
## Vea también  
 <xref:System.IDisposable>   
 [Using \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [Cómo: Deshacerse de un recurso del sistema](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)