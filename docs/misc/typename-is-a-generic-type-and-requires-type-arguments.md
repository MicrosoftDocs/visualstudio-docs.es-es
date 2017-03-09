---
title: "&#39;&lt;nombreDeTipo&gt;&#39; es un tipo gen&#233;rico y requiere argumentos de tipo | Microsoft Docs"
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
  - "BC32076"
  - "vbc32076"
helpviewer_keywords: 
  - "BC32076"
ms.assetid: 57f63727-c544-4012-8f03-5d77fbdd1135
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeTipo&gt;&#39; es un tipo gen&#233;rico y requiere argumentos de tipo
Se declaró una variable, un parámetro de procedimiento o un valor devuelto de función para que tenga el tipo de una clase o una estructura genérica, pero la declaración no proporciona ningún argumento de tipo.  
  
 Por su naturaleza, cada clase y estructura genérica se define con al menos un parámetro de tipo. Cuando se usa un tipo genérico para declarar una clase o un estructura construida, se debe proporcionar un argumento de tipo para cada parámetro de tipo definido por el tipo genérico.  
  
 **Identificador de error:** BC32076  
  
### Para corregir este error  
  
-   Agregue una lista de tipos a la declaración, entre paréntesis y comenzando con la palabra clave `Of`.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Of](/dotnet/visual-basic/language-reference/statements/of-clause)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)