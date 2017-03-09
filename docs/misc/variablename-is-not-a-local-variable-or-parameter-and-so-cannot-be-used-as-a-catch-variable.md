---
title: "&#39;&lt;variablename&gt;&#39; no es una variable local ni un par&#225;metro y, por tanto, no se puede usar como variable Catch. | Microsoft Docs"
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
  - "bc31082"
  - "vbc31082"
helpviewer_keywords: 
  - "BC31082"
ms.assetid: de197563-5848-4c1a-a519-cc4b5ea9a4c9
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;variablename&gt;&#39; no es una variable local ni un par&#225;metro y, por tanto, no se puede usar como variable Catch.
Las variables en instrucciones `Try...Catch...Finally` deben declararse de forma local, o bien ser parámetros del procedimiento actual.  
  
 **Identificador de error:** BC31082  
  
### Para corregir este error  
  
1.  Declare las variables locales o los parámetros de las instrucciones `Try...Catch...Finally`.  
  
## Vea también  
 [Try...Catch...Finally \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)