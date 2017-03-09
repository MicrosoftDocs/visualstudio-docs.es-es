---
title: "Error del compilador CS0167 | Microsoft Docs"
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
  - "CS0167"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0167"
ms.assetid: e6901b40-11a0-422c-9ea3-3b25c0ad7791
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0167
Falta el método Invoke en el delegado 'delegado'.  
  
 Ha importado y usado un programa administrado \(uno que usa .NET Framework Common Language Runtime\) que se creó con otro compilador. Ese compilador permitía un [delegado](/dotnet/csharp/language-reference/keywords/delegate) formado incorrectamente. Por lo tanto, el método `Invoke` no estaba disponible. Para obtener más información, consulta [Delegados](/dotnet/csharp/programming-guide/delegates/index).