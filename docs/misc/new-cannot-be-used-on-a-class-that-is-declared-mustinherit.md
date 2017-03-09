---
title: "&#39;New&#39; no se puede usar en una clase declarada como &#39;MustInherit&#39;. | Microsoft Docs"
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
  - "vbc30569"
  - "bc30569"
helpviewer_keywords: 
  - "BC30569"
ms.assetid: 94c9e6a3-6489-4d58-b7e5-7b4203677e3b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;New&#39; no se puede usar en una clase declarada como &#39;MustInherit&#39;.
No se puede crear una instancia de una clase `MustInherit` directamente y, por tanto, el operador `New` no puede usarse en una clase`MustInherit`. Aunque es posible que hayan variables y valores cuyos tipos en tiempo de compilación sean `MustInherit`, tales variables y valores serán necesariamente un valor NULL o contendrán referencias a instancias de clases regulares derivadas de los tipos `MustInherit`.  
  
 **Identificador de error:** BC30569  
  
### Para corregir este error  
  
-   Quite el operador `New`.  
  
## Vea también  
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [New \(Operador\)](/dotnet/visual-basic/language-reference/operators/new-operator)