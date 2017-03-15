---
title: "Se requiere &#39;Of&#39; cuando se especifican argumentos de tipo para un tipo o un m&#233;todo gen&#233;ricos | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32093"
  - "vbc32093"
helpviewer_keywords: 
  - "BC32093"
ms.assetid: 9a1baf12-a4a4-442d-9baa-852ad30a956b
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se requiere &#39;Of&#39; cuando se especifican argumentos de tipo para un tipo o un m&#233;todo gen&#233;ricos
Una instrucción intenta construir un tipo a partir de un tipo genérico, o llama a un método genérico, sin usar una cláusula [Of](/dotnet/visual-basic/language-reference/statements/of-clause).  
  
 La sintaxis de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] para los tipos genéricos llama a los parámetros de tipo y los argumentos de tipo que se introducen mediante la palabra clave `Of`. Además, la lista de parámetros de tipo o la lista de argumentos de tipo se debe incluir entre paréntesis.  
  
 **Identificador de error:** BC32093  
  
### Para corregir este error  
  
-   Incluya la palabra clave `Of` al principio de la lista de argumentos de tipo y agregue la lista completa entre paréntesis.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Cómo: Utilizar una clase genérica](../Topic/How%20to:%20Use%20a%20Generic%20Class%20\(Visual%20Basic\).md)