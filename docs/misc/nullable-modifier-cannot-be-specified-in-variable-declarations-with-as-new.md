---
title: "No se puede especificar un modificador que acepte valores NULL en declaraciones de variable con &#39;As New&#39;. | Microsoft Docs"
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
  - "bc33109"
  - "vbc33109"
helpviewer_keywords: 
  - "BC33109"
ms.assetid: 135def20-3535-4239-bffb-43208d1b3f63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede especificar un modificador que acepte valores NULL en declaraciones de variable con &#39;As New&#39;.
Se ha incluido el modificador de tipo que acepta valores NULL \(?\) en una declaración de variable donde se ha especificado `As New`. El ejemplo siguiente causa este error:  
  
```vb#  
Dim num? As New ExampleStructure  
```  
  
 **Identificador de error:** BC33109  
  
### Para corregir este error  
  
1.  Quite la palabra clave `New` de la declaración de variable que acepta valores NULL, como se muestra en el ejemplo siguiente:  
  
    ```vb#  
    Dim num? As ExampleStructure  
    ```  
  
## Vea también  
 [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)