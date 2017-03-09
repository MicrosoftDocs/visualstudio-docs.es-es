---
title: "No se puede usar aqu&#237; el car&#225;cter &#39;?&#39; | Microsoft Docs"
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
  - "bc36637"
  - "vbc36637"
helpviewer_keywords: 
  - "BC36637"
ms.assetid: a54c46e7-8fd8-4941-9fce-72f2b41b5e24
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede usar aqu&#237; el car&#225;cter &#39;?&#39;
El carácter '?' puede usarse para especificar que un tipo de valor o una estructura acepta valores NULL. Su uso en otras circunstancias es limitado. Por ejemplo, el código siguiente generará esta excepción.  
  
```  
' Not valid. ' #Const found = True?  
```  
  
 **Identificador de error:** BC36637  
  
### Para corregir este error  
  
-   Quite el carácter '?' de la declaración.  
  
## Vea también  
 [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)