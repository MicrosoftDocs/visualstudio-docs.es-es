---
title: "El tipo de restricci&#243;n &#39;&lt;typename&gt;&#39; ya se ha especificado para este par&#225;metro de tipo. | Microsoft Docs"
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
  - "BC32071"
  - "vbc32071"
helpviewer_keywords: 
  - "BC32071"
ms.assetid: 6b0e85e9-3ac8-4181-97de-ca690b95a63c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo de restricci&#243;n &#39;&lt;typename&gt;&#39; ya se ha especificado para este par&#225;metro de tipo.
Una lista de restricciones incluye una restricción de clase o interfaz más de una vez.  
  
 Una lista de restricciones impone requisitos al argumento de tipo pasado al parámetro de tipo. Puede especificar los requisitos siguientes en cualquier combinación:  
  
-   El argumento de tipo debe implementar una o varias interfaces  
  
-   El argumento de tipo debe heredar de al menos una clase  
  
 Un tipo no puede implementar o heredar del mismo tipo más de una vez y no se puede especificar un tipo más de una vez en la misma lista de restricción.  
  
 **Identificador de error:** BC32071  
  
### Para corregir este error  
  
-   Quite las especificaciones redundantes de la misma clase o interfaz. Debe aparecer solo una vez en la lista de restricciones.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)