---
title: "La palabra clave &#39;Loop&#39; debe ir precedida de una instrucci&#243;n &#39;Do&#39; correspondiente | Microsoft Docs"
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
  - "vbc30091"
  - "bc30091"
helpviewer_keywords: 
  - "BC30091"
ms.assetid: 05f47b2f-4eaa-4911-981e-3fce737d249f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La palabra clave &#39;Loop&#39; debe ir precedida de una instrucci&#243;n &#39;Do&#39; correspondiente
Una instrucción `Loop` aparece sin una instrucción `Do` correspondiente. La palabra clave `Loop` debe ir precedida de una instrucción `Do` correspondiente.  
  
 **Id. de error:** BC30091  
  
### Para corregir este error  
  
1.  Si este bucle `Do` forma parte de un conjunto de bucles `Do` anidados, asegúrese de que cada bucle esté terminado correctamente.  
  
2.  Compruebe que el resto de estructuras de control dentro del bucle `Do` terminen correctamente.  
  
3.  Asegúrese de que este bucle `Do` tenga el formato correcto.  
  
## Vea también  
 [Do...Loop \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/do-loop-statement)