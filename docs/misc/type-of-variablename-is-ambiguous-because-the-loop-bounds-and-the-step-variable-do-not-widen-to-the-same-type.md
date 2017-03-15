---
title: "El tipo de &#39;&lt;variablename&gt;&#39; es ambiguo porque los l&#237;mites del bucle y la variable step no se convierten en el mismo tipo | Microsoft Docs"
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
  - "vbc30983"
  - "bc30983"
helpviewer_keywords: 
  - "BC30983"
ms.assetid: 6b97153c-dee3-4429-b92a-2e5a212c864b
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo de &#39;&lt;variablename&gt;&#39; es ambiguo porque los l&#237;mites del bucle y la variable step no se convierten en el mismo tipo
El código contiene un bucle `For...Next` en el que el compilador no puede inferir un tipo de datos para la variable de control de bucle porque las siguientes condiciones son true:  
  
-   El tipo de datos de la variable de control de bucle no se especifica con una cláusula `As`.  
  
-   Los límites del bucle y la variable step contienen al menos dos tipos de datos.  
  
-   Existe más de una conversión posibles entre los tipos de datos.  
  
-   No hay ningún tipo mejor entre los candidatos, por lo que la elección del tipo de la variable de control de bucle es ambigua.  
  
 Por ejemplo, el siguiente bucle tiene un límite de bucle del tipo de `Integer` y un bucle enlazado de tipo `UInteger`:  
  
```vb#  
Dim m As Integer = 1 Dim n As UInteger = 10 ' Not valid. ' For i = m To n ' Loop processing. ' Next  
```  
  
 Hay una conversión posible entre `Integer` y `UInteger`, y una conversión posible entre `UInteger` y `Integer`, pero ambas son conversiones de restricción, por lo que ninguna es la mejor opción.  
  
 En el ejemplo siguiente, se agrega una tercera variable de tipo `Double`. Ambas `Integer` y `UInteger` tienen conversiones de ampliación estándar a `Double`, que realiza la conversión a la mejor opción de `Double`. La inferencia de tipos se asigna para crear un bucle de la variable de control de bucle `i` con el tipo de datos `Double`.  
  
```vb#  
Dim stepVar As Double = 1 ' Valid. For i = m To n Step stepVar ' Loop processing. Next  
```  
  
 **Identificador de error:** BC30983  
  
### Para corregir este error  
  
-   Convierta de forma explícita una de las variables a un tipo para el que los otros tienen una conversión de ampliación, por ejemplo:  
  
    ```  
    For i = m To CLng(n)  
    ```  
  
-   Use una cláusula `As` para especificar el tipo de la variable de control:  
  
    ```  
    For i As Double = m To n   
    ```  
  
## Vea también  
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Conversiones implícitas y explícitas](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions)   
 [Inferencia de tipo de variable local](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer \(instrucción\)](/dotnet/visual-basic/language-reference/statements/option-infer-statement)   
 [Conversiones de ampliación y de restricción](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)