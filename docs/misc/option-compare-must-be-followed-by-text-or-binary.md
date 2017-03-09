---
title: "&#39;Option Compare&#39; debe ir seguida de &#39;Text&#39; o &#39;Binary&#39;. | Microsoft Docs"
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
  - "vbc30207"
  - "bc30207"
helpviewer_keywords: 
  - "BC30207"
ms.assetid: e59cf10d-47ce-401d-8474-3b69a3a5f5db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Option Compare&#39; debe ir seguida de &#39;Text&#39; o &#39;Binary&#39;.
Una instrucción `Option Compare` contiene un valor incorrecto o no contiene ningún valor. Los únicos valores permitidos en `Option Compare` son `Text` y `Binary`.  
  
 **Identificador de error:** BC30207  
  
### Para corregir este error  
  
1.  Compruebe si el especificador de valores está mal escrito.  
  
2.  Agregue `Text` o `Binary` a la instrucción `Option Compare`; por ejemplo, `Option Compare Text`.  
  
## Vea también  
 [Option Compare \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/option-compare-statement)