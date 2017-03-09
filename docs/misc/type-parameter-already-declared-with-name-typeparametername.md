---
title: "Ya se declar&#243; el par&#225;metro de tipo con el nombre &#39;&lt;typeparametername&gt;&#39; | Microsoft Docs"
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
  - "vbc32049"
  - "bc32049"
helpviewer_keywords: 
  - "BC32049"
ms.assetid: d7affad0-0c3d-4fce-a1c2-a17f65514471
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ya se declar&#243; el par&#225;metro de tipo con el nombre &#39;&lt;typeparametername&gt;&#39;
Un parámetro de tipo de un tipo genérico se declara con el mismo nombre que un parámetro de otro tipo de dicho tipo genérico.  
  
 En la lista de parámetros de tipo de un tipo genérico, cada parámetro de tipo debe tener un nombre distinto a todos los nombres siguientes:  
  
-   Cada uno de los demás parámetros de tipo de la misma lista de parámetros de tipo.  
  
-   Cada parámetro de tipo de la lista de parámetros de tipo de cualquier tipo genérico contenedor.  
  
-   Nombre del parámetro de tipo genérico.  
  
 **Identificador de error:** BC32049  
  
### Para corregir este error  
  
-   Cambie el nombre del parámetro de tipo para que sea distinto de los nombres mencionados en la lista de esta página de ayuda.  
  
## Vea también  
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Lista de tipos](/dotnet/visual-basic/language-reference/statements/type-list)