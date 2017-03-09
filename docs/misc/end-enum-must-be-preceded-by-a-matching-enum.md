---
title: "&#39;End Enum&#39; debe ir precedida de la instrucci&#243;n &#39;Enum&#39; correspondiente | Microsoft Docs"
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
  - "bc30184"
  - "vbc30184"
helpviewer_keywords: 
  - "BC30184"
ms.assetid: b7f5ebf0-10c8-4320-8caf-dffc24ae8a71
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Enum&#39; debe ir precedida de la instrucci&#243;n &#39;Enum&#39; correspondiente
Una instrucción `End Enum` se produce sin una instrucción `Enum` correspondiente. La instrucción `End Enum` debe ir precedida de una instrucción `Enum` correspondiente.  
  
 **Identificador de error:** BC30184  
  
### Para corregir este error  
  
1.  Compruebe si una instrucción `Enum` anterior está mal escrita o no es válida.  
  
2.  Compruebe que los miembros `Enum` tengan el formato correcto.  
  
## Vea también  
 [Enum \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/enum-statement)