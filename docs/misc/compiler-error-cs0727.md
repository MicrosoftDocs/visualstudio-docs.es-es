---
title: "Error del compilador CS0727 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0727"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0727"
ms.assetid: 54bfb87e-d759-4310-a8ab-02dccd06337c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0727
Especificador de formato no válido  
  
 Este error se produce en el depurador. Cuando escriba un nombre de variable en una de las ventanas del depurador, puede agregarle una coma y, a continuación, un especificador de formato. Algunos ejemplos son: myInt, h; o myString, nq. Este error se produce cuando el compilador no puede analizar completamente lo que ha escrito. Para resolver este error, vuelva a escribir el nombre de variable, seguido opcionalmente por una coma y un [especificador de formato válido](../debugger/format-specifiers-in-csharp.md).