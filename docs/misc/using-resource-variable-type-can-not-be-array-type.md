---
title: "El tipo de variable de recurso &#39;using&#39; no puede ser un tipo de matriz | Microsoft Docs"
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
  - "vbc36012"
  - "bc36012"
helpviewer_keywords: 
  - "BC36012"
ms.assetid: f98c54b0-6ede-48b6-aa31-438664c219f3
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo de variable de recurso &#39;using&#39; no puede ser un tipo de matriz
Una instrucción `Using` especifica una variable de matriz para un recurso.  
  
 La clase <xref:System.Array> no implementa la interfaz <xref:System.IDisposable>, por lo que el bloque `Using` no puede llamar al método <xref:System.IDisposable.Dispose%2A> en un recurso de matriz.  
  
 **Identificador de error:** BC36012  
  
### Para corregir este error  
  
-   Use otro tipo de recurso del sistema en el bloque `Using`.  
  
## Vea también  
 [Using \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/using-statement)   
 [Cómo: Deshacerse de un recurso del sistema](../Topic/How%20to:%20Dispose%20of%20a%20System%20Resource%20\(Visual%20Basic\).md)   
 [NO ESTÁ EN LA COMPILACIÓN Información general sobre matrices en Visual Basic](http://msdn.microsoft.com/es-es/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)