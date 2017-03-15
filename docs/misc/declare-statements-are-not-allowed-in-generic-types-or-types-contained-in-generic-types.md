---
title: "No se permiten las instrucciones &#39;Declare&#39; en tipos gen&#233;ricos o tipos contenidos en tipos gen&#233;ricos | Microsoft Docs"
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
  - "BC32075"
  - "vbc32075"
helpviewer_keywords: 
  - "BC32075"
ms.assetid: c620b67e-70f8-42ac-8292-e9ea484904c3
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se permiten las instrucciones &#39;Declare&#39; en tipos gen&#233;ricos o tipos contenidos en tipos gen&#233;ricos
Una instrucción `Declare` aparece como parte de una estructura o una clase genérica, o una clase o estructura declaras dentro de una estructura o una clase genérica.  
  
 Visual Basic y .NET Framework no admiten actualmente ninguna combinación de referencias externas y tipos genéricos. El compilador necesita todos los parámetros y el tipo de valor devuelto de un procedimiento externo para que se llame correctamente.  
  
 **Id. de error:** BC32075  
  
### Para corregir este error  
  
-   Mueva la instrucción `Declare` fuera del ámbito de los tipos genéricos o quite ambos.  
  
## Vea también  
 [Declare \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/declare-statement)   
 [Tipos genéricos en Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)