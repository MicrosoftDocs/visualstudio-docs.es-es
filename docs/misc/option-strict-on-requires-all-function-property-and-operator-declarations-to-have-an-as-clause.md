---
title: "Option Strict On requiere que todas las declaraciones Function, Property y Operator tengan una cl&#225;usula &#39;As&#39; | Microsoft Docs"
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
  - "vbc30210"
  - "bc30210"
helpviewer_keywords: 
  - "BC30210"
ms.assetid: 4d217e56-0eac-4834-bcad-234a69809390
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On requiere que todas las declaraciones Function, Property y Operator tengan una cl&#225;usula &#39;As&#39;
Una declaración contiene una propiedad declarada o un valor devuelto de función sin una cláusula `As`. Si `Option Strict` es `On`, todas las variables, las propiedades, los argumentos de procedimiento y los valores devueltos de funciones deben declararse con una cláusula `As` para especificar su tipo de datos; por ejemplo, `Dim MyNum As Short`.  
  
 **Identificador de error:** BC30210  
  
### Para corregir este error  
  
1.  Compruebe si la palabra clave `As` está mal escrita.  
  
2.  Proporcione una cláusula `As` para la propiedad declarada o el valor devuelto de función, o bien ajuste `Option Strict Off`.  
  
## Vea también  
 [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Procedimientos de propiedad](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Procedimientos Function](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)