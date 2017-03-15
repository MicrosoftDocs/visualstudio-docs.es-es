---
title: "Los tipos de par&#225;metro de &#39;&lt;operador&gt;&#39; deben ser &#39;&lt;nombreDeTipo&gt;&#39; para usarse en una expresi&#243;n &#39;For&#39; | Microsoft Docs"
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
  - "BC33040"
  - "vbc33040"
helpviewer_keywords: 
  - "BC33040"
ms.assetid: bffbb812-0d69-47e4-96c5-01882722ccdb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de par&#225;metro de &#39;&lt;operador&gt;&#39; deben ser &#39;&lt;nombreDeTipo&gt;&#39; para usarse en una expresi&#243;n &#39;For&#39;
Un bucle `For` especifica una variable de contador de un tipo que no define el operador `>=` o `<=` con parámetros de su propio tipo.  
  
 La variable de contador debe ser de un tipo que admita operadores mayor o igual \(`>=`\) y menor o igual \(`<=`\) que comparen su tipo contenedor. Esto significa que ambos operandos deben ser del tipo de la variable de contador.  
  
 Si usa un tipo de datos numérico para la variable de contador, se admiten los operadores `>=` y `<=` en el tipo contenedor. Si usa una clase o estructura definida por el usuario, debe definir ambos operadores con los operandos del tipo de la clase o estructura.  
  
 **Identificador de error:** BC33040  
  
### Para corregir este error  
  
1.  Asegúrese de que la ortografía del tipo de datos de la variable de contador sea correcta.  
  
2.  Si usa una clase o estructura definida por el usuario para la variable de contador, defina los operadores `>=` y `<=` que comparan esa clase o estructura.  
  
## Vea también  
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)