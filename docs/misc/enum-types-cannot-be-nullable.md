---
title: "Los tipos de enumeraci&#243;n no pueden aceptar valores NULL | Microsoft Docs"
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
  - "vbc32129"
  - "bc32129"
helpviewer_keywords: 
  - "BC32129"
ms.assetid: 9e0fe5c9-72c7-4905-b177-d00cc3469ea9
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los tipos de enumeraci&#243;n no pueden aceptar valores NULL
El tipo subyacente que se utiliza para declarar una enumeración no puede tener valores NULL. Por ejemplo, el código siguiente provoca este error:  
  
```vb#  
'' Not valid. ' Enum exampleEnum As Integer? '     Member declarations. ' End Enum  
```  
  
 **Id. de error:** BC32129  
  
### Para corregir este error  
  
-   No utilice un tipo subyacente que acepte valores NULL en una declaración `Enum`.  
  
## Vea también  
 [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)   
 [Enum \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/enum-statement)