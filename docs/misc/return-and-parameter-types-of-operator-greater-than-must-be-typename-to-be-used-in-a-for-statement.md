---
title: "Los tipos de par&#225;metro y de valor devuelto de &#39;&lt;operador&gt;&#39; deben ser &#39;&lt;nombreDeTipo&gt;&#39; para usarse en una expresi&#243;n &#39;For&#39; | Microsoft Docs"
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
  - "vbc33039"
  - "bc33039"
helpviewer_keywords: 
  - "BC33039"
ms.assetid: 30e8cfa8-c086-474c-a4f0-ad01d01096e2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de par&#225;metro y de valor devuelto de &#39;&lt;operador&gt;&#39; deben ser &#39;&lt;nombreDeTipo&gt;&#39; para usarse en una expresi&#243;n &#39;For&#39;
Un bucle `For` especifica una variable de contador de un tipo que no define el operador `+` o `-` con parámetros y el valor devuelto de su propio tipo.  
  
 La variable de contador debe ser de un tipo que admita los operadores de suma \(`+`\) y resta \(`-`\) que funcionen plenamente en su tipo contenedor. Esto significa que ambos operandos y el valor devuelto deben ser del tipo de la variable de contador.  
  
 Si usa un tipo de datos numérico para la variable de contador, se admiten los operadores `+` y `-` en el tipo contenedor. Si usa una clase o una estructura definida por el usuario, debe definir ambos operadores con los operandos y el valor devuelto del tipo de dicha clase o estructura.  
  
 **Identificador de error:** BC33039  
  
### Para corregir este error  
  
1.  Asegúrese de que la ortografía del tipo de datos de la variable de contador sea correcta.  
  
2.  Si usa una clase o una estructura definida por el usuario para la variable de contador, defina los operadores `+` y `-` que funcionan plenamente en esa clase o estructura.  
  
## Vea también  
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)