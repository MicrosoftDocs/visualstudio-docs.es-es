---
title: "No se puede especificar la restricci&#243;n &#39;Class&#39; varias veces para el mismo par&#225;metro de tipo | Microsoft Docs"
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
  - "bc32101"
  - "vbc32101"
helpviewer_keywords: 
  - "BC32101"
ms.assetid: fac2330a-e397-4bd9-8166-934407575f9e
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede especificar la restricci&#243;n &#39;Class&#39; varias veces para el mismo par&#225;metro de tipo
Una lista de restricciones incluye la restricción [Class \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7) más de una vez.  
  
 Una lista de restricciones en un parámetro de tipo puede especificar que el argumento de tipo pasado a ese parámetro de tipo debe ser un tipo de valor \[con la restricción [Structure \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)\] o debe ser un tipo de referencia \(con la restricción `Class`\). No se pueden especificar ambas restricciones en el mismo parámetro de tipo y ninguna de ellas se puede especificar más de una vez.  
  
 Identificador de error: BC32101  
  
### Para corregir este error  
  
-   Quite las palabras clave `Class` redundantes. Debe tener solo una en la lista de restricciones.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)