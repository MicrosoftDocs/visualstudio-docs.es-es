---
title: "El tipo &#39;&lt;nombreTipo&gt;&#39; debe definir el operador &#39;&lt;operador&gt;&#39; que se va a usar en una instrucci&#243;n &#39;For&#39;. | Microsoft Docs"
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
  - "vbc33038"
  - "BC33038"
helpviewer_keywords: 
  - "BC33038"
ms.assetid: b1c9d87f-80f9-4c8c-8908-f8400b9fe4c5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo &#39;&lt;nombreTipo&gt;&#39; debe definir el operador &#39;&lt;operador&gt;&#39; que se va a usar en una instrucci&#243;n &#39;For&#39;.
Un bucle `For` especifica una variable de contador de un tipo que no admite un operador necesario.  
  
 La variable de contador en un bucle `For` puede ser de cualquier tipo de datos que admita todos los operadores siguientes:  
  
-   Mayor o igual que \(`>=`\)  
  
-   Menor o igual que \(`<=`\)  
  
-   Adición \(`+`\)  
  
-   Resta \(`-`\)  
  
 Si usa un tipo de datos numérico para la variable de contador, se admiten todos los operadores anteriores. Si usa una clase o estructura definida por el usuario, debe definir todos los operadores anteriores en dicha clase o estructura.  
  
 Tenga en cuenta también que los tipos de datos de las expresiones `start`, `end` y `step` de la instrucción `For` deben ampliarse al tipo de datos de la variable de contador. Si la variable de contador es una estructura o clase definida por el usuario y la expresión `start`, `end` o `step` es de un tipo diferente, debe definir el operador de conversión `CType` para que realice la conversión necesaria.  
  
 **Identificador de error:** BC33038  
  
### Para corregir este error  
  
1.  Asegúrese de que la ortografía del tipo de datos de variable de contador es correcta.  
  
2.  Si usa una clase o estructura definida por el usuario para la variable de contador, defina todos los operadores necesarios en dicha clase o estructura.  
  
3.  En función de los tipos de datos de las expresiones `start`, `end` y `step`, es posible que deba definir uno o varios operadores de conversión `CType` para convertirlas en el tipo de datos de la variable de contador.  
  
## Vea también  
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Procedimientos de operador](/dotnet/visual-basic/programming-guide/language-features/procedures/operator-procedures)   
 [Operator \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/operator-statement)   
 [Cómo: Definir un operador](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [Cómo: Definir un operador de conversión](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [CType \(Función\)](/dotnet/visual-basic/language-reference/functions/ctype-function)