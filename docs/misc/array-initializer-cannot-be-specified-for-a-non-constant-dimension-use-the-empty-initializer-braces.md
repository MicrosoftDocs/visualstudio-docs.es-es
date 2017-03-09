---
title: "No se puede especificar el inicializador de matriz para una dimensi&#243;n no constante; use el inicializador vac&#237;o &#39;{}&#39;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30949"
  - "bc30949"
helpviewer_keywords: 
  - "BC30949"
ms.assetid: b3d27d9c-7a1f-4bac-ad71-388b24b807b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede especificar el inicializador de matriz para una dimensi&#243;n no constante; use el inicializador vac&#237;o &#39;{}&#39;.
Una matriz inicializa una dimensión que no se conoce en tiempo de compilación.  
  
 El código siguiente genera este error.  
  
```  
Dim j As Integer Dim intArray As Integer = New Integer(1, j) {{0, 100}, {1,101}}  
```  
  
 El código siguiente evita el error.  
  
```  
Dim intArray As Integer = New Integer(1, j) {} For i As Integer = 0 To j intArray(0, i) = i intArray(1, i) = 100 + i Next i  
```  
  
 **Identificador de error:** BC30949  
  
### Para corregir este error  
  
-   Si es posible, especifique una dimensión constante en la declaración de matriz.  
  
-   Si no se puede especificar una dimensión constante, debe inicializar la matriz mediante un bucle cuando se conoce la dimensión no constante.  
  
## Vea también  
 [For Each...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [NO ESTÁ EN LA COMPILACIÓN Información general sobre matrices en Visual Basic](http://msdn.microsoft.com/es-es/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8)   
 [Cómo: Inicializar una variable de matriz en Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)   
 [NO ESTÁ EN LA COMPILACIÓN: Cómo: Inicializar una matriz multidimensional](http://msdn.microsoft.com/es-es/502dcf8b-d86c-46f1-ad7d-3ce809645774)