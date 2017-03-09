---
title: "Option Strict On requiere que todas las declaraciones de variables tengan una cl&#225;usula &#39;As&#39; | Microsoft Docs"
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
  - "bc30209"
  - "vbc30209"
helpviewer_keywords: 
  - "BC30209"
ms.assetid: 69c2e32a-86aa-4075-a142-440605a7063a
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On requiere que todas las declaraciones de variables tengan una cl&#225;usula &#39;As&#39;
Una declaración contiene una variable declarada sin una cláusula `As`. Si `Option Strict` es `On`, todas las variables, las propiedades, los argumentos de procedimiento y los valores devueltos de funciones deben declararse con una cláusula `As` para especificar su tipo de datos; por ejemplo, `Dim MyNum As Short`.  
  
 **Id. de error:** BC30209  
  
### Para corregir este error  
  
1.  Compruebe si la palabra clave `As` está mal escrita.  
  
2.  Facilite una cláusula `As` para la variable declarada o active `Option Strict Off`.  
  
## Vea también  
 [Option Strict \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Declaración de variable](/dotnet/visual-basic/programming-guide/language-features/variables/variable-declaration)