---
title: "El par&#225;metro lambda &#39;&lt;par&#225;metro&gt;&#39; oculta una variable en un bloque de inclusi&#243;n, una variable de rango definida previamente o una variable declarada de forma impl&#237;cita en una expresi&#243;n de consulta. | Microsoft Docs"
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
  - "bc36641"
  - "vbc36641"
helpviewer_keywords: 
  - "BC36641"
ms.assetid: ee08c366-29d1-4abb-b14c-23ae2b9680e7
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro lambda &#39;&lt;par&#225;metro&gt;&#39; oculta una variable en un bloque de inclusi&#243;n, una variable de rango definida previamente o una variable declarada de forma impl&#237;cita en una expresi&#243;n de consulta.
Una variable en una expresión lambda tiene el mismo nombre que una variable definida anteriormente en el mismo ámbito. Puede ser una variable en un bloque de inclusión de código de una expresión lambda anidada, una variable de rango definida anteriormente en una consulta LINQ o una variable declarada de forma implícita para una consulta LINQ.  
  
 **Identificador de error:** BC36641  
  
### Para corregir este error  
  
-   Asegúrese de que todas las variables de la expresión lambda tienen nombres únicos que no duplican los nombres de variable existentes en el mismo ámbito.  
  
## Vea también  
 [Expresiones lambda](/dotnet/visual-basic/programming-guide/language-features/procedures/lambda-expressions)   
 [Introducción a LINQ en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [LINQ](/dotnet/visual-basic/programming-guide/language-features/linq/index)