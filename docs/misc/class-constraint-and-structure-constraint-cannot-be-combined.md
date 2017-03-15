---
title: "La restricci&#243;n &#39;Class&#39; y la restricci&#243;n &#39;Structure&#39; no se pueden combinar | Microsoft Docs"
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
  - "vbc32104"
  - "bc32104"
helpviewer_keywords: 
  - "BC32104"
ms.assetid: f41a581b-afca-4173-bc82-b35ed49caba0
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La restricci&#243;n &#39;Class&#39; y la restricci&#243;n &#39;Structure&#39; no se pueden combinar
Una lista de restricciones incluye ambas restricciones [Class \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) y [Structure \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0).  
  
 Una lista de restricciones en un parámetro de tipo puede especificar que el argumento de tipo pasado a ese parámetro de tipo debe ser un tipo de valor \[con la restricción `Structure`\] o un tipo de referencia \[con la restricción `Class`\]. No se pueden especificar ambas restricciones en el mismo parámetro de tipo y ninguna de ellas se puede especificar más de una vez.  
  
 **Identificador de error:** BC32104  
  
### Para corregir este error  
  
1.  Decida si quiere requerir un tipo de valor o un tipo de referencia para el argumento de tipo.  
  
    -   Si quiere que el argumento de tipo sea un tipo de valor, quite la palabra clave `Class` de la lista de restricciones.  
  
    -   Si quiere que el argumento de tipo sea un tipo de referencia, quite la palabra clave `Structure` de la lista de restricciones.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)