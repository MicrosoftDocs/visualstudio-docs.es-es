---
title: "No se pueden combinar las restricciones &#39;New&#39; y &#39;Structure&#39;. | Microsoft Docs"
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
  - "bc32103"
  - "vbc32103"
helpviewer_keywords: 
  - "BC32103"
ms.assetid: 5418b420-a014-4006-84aa-20ddac6739e6
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden combinar las restricciones &#39;New&#39; y &#39;Structure&#39;.
Una lista de restricciones incluye la restricción [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator) y la restricción [Structure \(Visual Basic\)](http://msdn.microsoft.com/es-es/263ce115-ac36-4c05-8cb7-0e0eead5c6d0).  
  
 Una lista de restricciones en un parámetro de tipo puede especificar que el argumento de tipo pasado a ese parámetro de tipo debe ser un tipo de valor \(con la restricción `Structure`\) o debe ser un tipo de referencia \(con la restricción [Class \(Visual Basic\)](http://msdn.microsoft.com/es-es/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)\). No se pueden especificar ambas restricciones en el mismo parámetro de tipo y no se puede especificar cualquiera de ellas más de una vez.  
  
 La restricción `New` especifica que el argumento de tipo debe exponer un constructor sin parámetros al que el código de creación pueda tener acceso. Sin embargo, una estructura no puede tener un constructor sin parámetros no compartido. Por lo tanto, las restricciones `New` y `Structure` están en conflicto.  
  
 **Identificador de error:** BC32103  
  
### Para corregir este error  
  
1.  Decida si quiere requerir un tipo de valor o un tipo de referencia para el argumento de tipo.  
  
2.  Si quiere que el argumento de tipo sea un tipo de valor, quite la palabra clave `New` de la lista de restricciones.  
  
3.  Si quiere que el argumento de tipo sea un tipo de referencia, quite la palabra clave `Structure` de la lista de restricciones.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Tipos de valor y tipos de referencia](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)