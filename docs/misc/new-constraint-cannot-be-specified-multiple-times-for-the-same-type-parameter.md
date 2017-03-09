---
title: "La restricci&#243;n &#39;New&#39; no se puede especificar varias veces para el mismo par&#225;metro de tipo. | Microsoft Docs"
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
  - "vbc32081"
  - "BC32081"
helpviewer_keywords: 
  - "BC32081"
ms.assetid: afcb30da-3973-4452-9cf3-c027f9866589
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La restricci&#243;n &#39;New&#39; no se puede especificar varias veces para el mismo par&#225;metro de tipo.
Una lista de restricciones incluye la restricción [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator) más de una vez.  
  
 Una lista de restricciones en un parámetro de tipo puede especificar que el argumento de tipo pasado a ese parámetro de tipo debe exponer un constructor sin parámetros que pueda tener acceso al código de creación. Un tipo no puede tener más de un constructor sin parámetros y no puede especificar más de una vez este requisito.  
  
 **Identificador de error:** BC32081  
  
### Para corregir este error  
  
-   Quite las palabras clave `New` redundantes. Debe tener solo una en la lista de restricciones.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)