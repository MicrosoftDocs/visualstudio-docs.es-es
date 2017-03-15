---
title: "El tipo de &#39;&lt;nombreVariable&gt;&#39; no se puede inferir de una expresi&#243;n que contiene &#39;&lt;nombreVariable&gt;&#39;. | Microsoft Docs"
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
  - "vbc30980"
  - "bc30980"
helpviewer_keywords: 
  - "BC30980"
ms.assetid: 43a5d008-5362-481b-845b-b9bb00a61a83
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El tipo de &#39;&lt;nombreVariable&gt;&#39; no se puede inferir de una expresi&#243;n que contiene &#39;&lt;nombreVariable&gt;&#39;.
El compilador no puede inferir el tipo de datos de una variable si la variable se usa para establecer su valor inicial en la declaración.  
  
 Por ejemplo, si se establece `Option Infer` en `On`, no se compilan los ejemplos siguientes:  
  
-   Declaraciones  
  
    ```  
    ' Does not compile with Option Infer on. Dim m = m Dim d = someFunction(d)  
    ```  
  
-   Bucle `For`  
  
    ```  
    ' Does not compile with Option Infer on. For j = 1 To j Next  
    ```  
  
-   Bucle `For Each`  
  
    ```  
    ' Does not compile with Option Infer on. For Each customer In customer.Orders Next  
    ```  
  
 **Identificador de error:** BC30980  
  
### Para corregir este error  
  
-   Si las dos variables estaban previstas para hacer referencia a valores diferentes, cambie el nombre de la variable que declara.  
  
-   Use un valor literal en lugar del nombre de variable en el valor inicial, en el lado derecho de la asignación.  
  
-   Use una cláusula `As` para especificar el tipo de la variable que declara.  
  
## Vea también  
 [Dim \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/dim-statement)   
 [For Each...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)   
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [Inferencia de tipo de variable local](/dotnet/visual-basic/programming-guide/language-features/variables/local-type-inference)   
 [Option Infer \(instrucción\)](/dotnet/visual-basic/language-reference/statements/option-infer-statement)