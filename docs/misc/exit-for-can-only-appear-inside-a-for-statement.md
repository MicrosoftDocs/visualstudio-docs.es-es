---
title: "&#39;Exit For&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;For&#39;. | Microsoft Docs"
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
  - "bc30096"
  - "vbc30096"
helpviewer_keywords: 
  - "BC30096"
ms.assetid: 1062a329-9364-4234-9175-4c70a51cb7ae
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Exit For&#39; solo puede aparecer dentro de una instrucci&#243;n &#39;For&#39;.
Una instrucción `Exit For` aparece fuera de un bucle `For`.`Exit For` solo es válida entre una instrucción `For` o `For Each` y su instrucción `Next` correspondiente.  
  
 **Identificador de error:** BC30096  
  
### Para corregir este error  
  
1.  Asegúrese de que una instrucción `For` o `For Each` válida precede a `Exit For`, y de que una instrucción `Next` válida aparece después.  
  
2.  Compruebe que el resto de estructuras de control dentro del bucle `For` terminen correctamente.  
  
## Vea también  
 [For...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-next-statement)   
 [For Each...Next \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/for-each-next-statement)