---
title: "Error del compilador CS0726 | Microsoft Docs"
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
  - "CS0726"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0726"
ms.assetid: 9ea5f004-cf25-4e6e-b9e5-6b53e4a7e1ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0726
'format specifier' no es un especificador de formato válido  
  
 Este error se produce en el depurador. Cuando escriba un nombre de variable en una de las ventanas del depurador, puede agregarle una coma y luego un especificador de formato. Algunos ejemplos de ello son `myInt, h` y `myString,nq`. Este error se produce cuando el compilador no reconoce el elemento [Especificadores de formato en C\#](../debugger/format-specifiers-in-csharp.md).