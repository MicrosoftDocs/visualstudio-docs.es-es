---
title: "La variable de rango &lt;variable&gt; oculta una variable en un bloque de inclusi&#243;n o una variable de rango definida previamente en la expresi&#243;n de consulta. | Microsoft Docs"
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
  - "bc30978"
  - "vbc30978"
helpviewer_keywords: 
  - "BC30978"
ms.assetid: 806d94c1-653f-40c0-b1c4-95661c76a392
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La variable de rango &lt;variable&gt; oculta una variable en un bloque de inclusi&#243;n o una variable de rango definida previamente en la expresi&#243;n de consulta.
Una variable de rango en una consulta tiene el mismo nombre que una variable definida anteriormente en el mismo ámbito o una variable de rango definida anteriormente en la consulta.  
  
 **Identificador de error:** BC30978  
  
### Para corregir este error  
  
-   Asegúrese de que todas las variables de rango de la consulta tienen nombres únicos que no duplican los nombres de variable existentes en el mismo ámbito.  
  
-   Agregue consultas anidadas con nombres de variable de control duplicados entre paréntesis y separe el ámbito de cada variable de rango.  
  
## Vea también  
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)