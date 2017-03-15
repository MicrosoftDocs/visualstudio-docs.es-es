---
title: "Error del compilador CS1688 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1688"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1688"
ms.assetid: e15672a1-2570-4e65-99fc-7acc190ae643
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1688
No se puede convertir el bloque de método anónimo sin una lista de parámetros en el tipo delegado 'delegate' porque tiene uno o varios parámetros out.  
  
 El compilador permite omitir parámetros desde un bloque de método anónimo en la mayoría de los casos. Este error se genera cuando el bloque de método anónimo no tiene una lista de parámetros, pero el delegado tiene un parámetro `out`. El compilador no permite esta situación porque necesitaría ignorar la presencia del parámetro `out`, que es poco probable que tenga el comportamiento correcto.  
  
## Ejemplo  
 El código siguiente genera el error CS1688.  
  
```  
// CS1688.cs using System; delegate void OutParam(out int i); class ErrorCS1676 { static void Main() { OutParam o; o = delegate  // CS1688 // Try this instead: // o = delegate(out int i) { Console.WriteLine(""); }; } }  
```