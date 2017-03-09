---
title: "&#39;Next&#39; debe ir precedida de la instrucci&#243;n &#39;For&#39; correspondiente | Microsoft Docs"
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
  - "vbc30092"
  - "bc30092"
helpviewer_keywords: 
  - "BC30092"
ms.assetid: 4bf49bb2-c69b-443d-aa58-cb40fcfb1370
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Next&#39; debe ir precedida de la instrucci&#243;n &#39;For&#39; correspondiente
Una instrucción `Next` aparece sin una instrucción `For` o `For Each` correspondiente.`Next` debe ir precedida de una instrucción `For` o `For Each` correspondiente.  
  
 **Identificador de error:** BC30092  
  
### Para corregir este error  
  
1.  Si este bucle `For` forma parte de un conjunto de bucles `For` anidados, asegúrese de que cada bucle esté terminado correctamente.  
  
2.  Compruebe que el resto de estructuras de control dentro del bucle `For` terminen correctamente.  
  
3.  Asegúrese de que este bucle `For` tenga el formato correcto.  
  
## Vea también  
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [For Each...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)