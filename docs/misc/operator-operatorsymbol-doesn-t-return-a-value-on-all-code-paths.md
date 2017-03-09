---
title: "El operador &lt;s&#237;mboloDeOperador&gt; no devuelve un valor en todas las rutas de c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42106"
  - "bc42106"
helpviewer_keywords: 
  - "BC42106"
ms.assetid: 175b2bc9-5233-462d-97de-9d97b003cc46
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operador &lt;s&#237;mboloDeOperador&gt; no devuelve un valor en todas las rutas de c&#243;digo
El operador \<símboloDeOperador\> no devuelve un valor en todas las rutas de código. Podría producirse una excepción de referencia nula en tiempo de ejecución al usar el resultado.  
  
 Un procedimiento de operador tiene al menos una ruta posible en el código que no devuelve un valor.  
  
 Puede devolver un valor desde un procedimiento de operador incluyéndolo simplemente en una [Return \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/return-statement).  
  
 Si el control se pasa a la instrucción `End Operator`, el procedimiento de operador devuelve el valor predeterminado del tipo de datos de la propiedad. Para más información, vea "Comportamiento" en [Function \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/function-statement).  
  
 De forma predeterminada, este mensaje es una advertencia. Para obtener más información sobre cómo ocultar las advertencias o cómo tratarlas como errores, vea [Configurar advertencias en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Identificador de error:** BC42106  
  
### Para corregir este error  
  
-   Compruebe la lógica del flujo de control y asegúrese de que cada ruta posible finaliza con una instrucción `Return`. En particular, la última instrucción antes de `End Operator` debe ser una instrucción `Return`.  
  
## Vea también  
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)