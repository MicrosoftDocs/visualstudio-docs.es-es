---
title: "El par&#225;metro de tipo no puede tener el mismo nombre que la funci&#243;n que lo define. | Microsoft Docs"
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
  - "vbc32090"
  - "bc32090"
helpviewer_keywords: 
  - "BC32090"
ms.assetid: 02f4d82c-dcd7-44cc-b725-81e235f680f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro de tipo no puede tener el mismo nombre que la funci&#243;n que lo define.
Hay un parámetro de tipo de un tipo genérico declarado con el mismo nombre que el tipo genérico.  
  
 En la lista de parámetros de tipo de un tipo genérico, cada parámetro de tipo debe tener un nombre distinto a todos los nombres siguientes:  
  
-   cada uno de los demás parámetros de tipo de la misma lista de parámetros de tipo;  
  
-   cada parámetro de tipo de la lista de parámetros de tipo de cualquier tipo genérico contenedor; y  
  
-   el nombre del parámetro de tipo genérico en sí.  
  
 **Identificador de error:** BC32090  
  
### Para corregir este error  
  
-   Cambie el nombre del parámetro de tipo para que sea distinto de los nombres mencionados en la lista de esta página de ayuda.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)