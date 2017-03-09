---
title: "El par&#225;metro de tipo &#39;&lt;typeparametername&gt;&#39; no se puede restringir a s&#237; mismo: &#39;&lt;errormessage&gt;&#39; | Microsoft Docs"
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
  - "bc32113"
  - "vbc32113"
helpviewer_keywords: 
  - "BC32113"
ms.assetid: a74128ae-11d0-46bf-8c0b-c7a2bf881d17
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro de tipo &#39;&lt;typeparametername&gt;&#39; no se puede restringir a s&#237; mismo: &#39;&lt;errormessage&gt;&#39;
Una lista de restricciones para un parámetro de tipo incluye ese mismo parámetro de tipo.  
  
 Una lista de restricciones de un parámetro de tipo puede especificar cualquier número de interfaces y al menos una clase. Un argumento de tipo proporcionado para ese parámetro de tipo debe implementar cada interfaz especificada y heredar de la clase especificada. El compilador requiere las interfaces y clases que ya están definidas cuando se encuentra una lista de restricciones. Un parámetro de tipo no se considera como tipo definido hasta que se reemplace por un argumento de tipo adecuado proporcionado por el código que crea el tipo genérico.  
  
 **Identificador de error:** BC32113  
  
### Para corregir este error  
  
1.  Compruebe la ortografía del parámetro de tipo y las restricciones en su lista de restricciones.  
  
2.  Si no hay ningún error de ortografía, quite el nombre del parámetro de tipo de su lista de restricciones. No se puede restringir a sí mismo.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)