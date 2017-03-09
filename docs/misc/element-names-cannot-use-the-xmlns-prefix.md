---
title: "Los nombres de elemento no pueden usar el prefijo &#39;xmlns&#39;. | Microsoft Docs"
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
  - "vbc31189"
  - "bc31189"
helpviewer_keywords: 
  - "BC31189"
ms.assetid: 88716bb5-6766-4180-b2ed-1d1bee0ff7a6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los nombres de elemento no pueden usar el prefijo &#39;xmlns&#39;.
Se ha especificado un literal de elemento XML con un prefijo de espacio de nombres XML de `xmlns`. Por ejemplo:  
  
```vb#  
Dim elem = <xmlns:ElementName>  
```  
  
 La especificación XML 1.0 identifica `xmlns` como una palabra reservada.  
  
 **Identificador de error:** BC31189  
  
### Para corregir este error  
  
-   Cambie el prefijo de espacio de nombres XML por un valor válido, o quite el prefijo.  
  
## Vea también  
 [Literales XML](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [Imports \(Instrucción, Espacio de nombres XML\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)