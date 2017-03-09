---
title: "&#39;&lt;nombreDeElemento&gt;&#39; no se puede declarar como &#39;Partial&#39; porque los m&#233;todos parciales deben ser Subs | Microsoft Docs"
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
  - "vbc31437"
  - "bc31437"
helpviewer_keywords: 
  - "BC31437"
ms.assetid: 31ca12ab-2c26-4907-a253-e7c57bb4f34b
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nombreDeElemento&gt;&#39; no se puede declarar como &#39;Partial&#39; porque los m&#233;todos parciales deben ser Subs
Solo los procedimientos `Sub` se pueden declarar como métodos parciales. Por ejemplo, el código siguiente genera este error porque `partialMethod` es una función.  
  
```  
' Partial Private Function partialMethod(ByVal n As Integer) As Integer ' End Function  
```  
  
 **Identificador de error:** BC31437  
  
### Para corregir este error  
  
-   Convierta lo que está declarando como método parcial a `Sub`.  
  
-   No use un método parcial en este caso.  
  
## Vea también  
 [Métodos Partial](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Procedimientos Sub](/dotnet/visual-basic/programming-guide/language-features/procedures/sub-procedures)