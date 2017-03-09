---
title: "No se pueden especificar par&#225;metros de tipo en esta declaraci&#243;n. | Microsoft Docs"
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
  - "vbc32065"
  - "bc32065"
helpviewer_keywords: 
  - "BC32065"
ms.assetid: 94cfe3de-74fd-4a2c-9246-ec4a05b73d55
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se pueden especificar par&#225;metros de tipo en esta declaraci&#243;n.
Un elemento de programación se declara con una lista de parámetros de tipo, pero el elemento de programación no es apto para ser un tipo genérico.  
  
 Los elementos de programación que no son válidos como genéricos incluyen propiedades, operadores, eventos y constructores. La declaración de cualquiera de estos elementos con una lista de parámetros de tipo generará este error.  
  
 **Identificador de error:** BC32065  
  
### Para corregir este error  
  
-   Quite la palabra clave `Of` y los parámetros de tipo de la declaración.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)