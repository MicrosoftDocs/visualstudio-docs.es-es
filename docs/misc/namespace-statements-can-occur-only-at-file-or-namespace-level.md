---
title: "Las instrucciones &#39;Namespace&#39; solo pueden ocurrir en el nivel de archivo o de espacio de nombres | Microsoft Docs"
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
  - "bc30618"
  - "vbc30618"
helpviewer_keywords: 
  - "BC30618"
ms.assetid: bcd365a4-5d84-4c3c-83dc-40cb4c47f73b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las instrucciones &#39;Namespace&#39; solo pueden ocurrir en el nivel de archivo o de espacio de nombres
Las instrucciones `Namespace` deben aparecer después de las instrucciones `Option`, las instrucciones `Imports` y los atributos globales, pero antes del resto de declaraciones del archivo de código fuente.  
  
 **Identificador de error:** BC30618  
  
### Para corregir este error  
  
-   Mueva la instrucción `Namespace` a la parte superior de la declaración del espacio de nombres o el archivo de código fuente.  
  
## Vea también  
 [Namespace \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/namespace-statement)   
 [Espacios de nombres en Visual Basic](/dotnet/visual-basic/programming-guide/program-structure/namespaces)