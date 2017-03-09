---
title: "Error del compilador CS0072 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0072"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0072"
ms.assetid: 9153cd52-f497-4128-a11f-a2820218b0e6
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0072
'evento': no se puede invalidar; 'método' no es un evento.  
  
 Un [evento](/dotnet/csharp/language-reference/keywords/event) solo puede reemplazar a otro evento. Para obtener más información, consulta [Eventos](/dotnet/csharp/programming-guide/events/index).  
  
 El ejemplo siguiente genera la advertencia CS0072:  
  
```  
// CS0072.cs delegate void MyDelegate(); class Test1 { public virtual event MyDelegate MyEvent; public virtual void VMeth() { } public void FireAway() { if (MyEvent != null) MyEvent(); } } class Test2 : Test1 { public override event MyDelegate VMeth   // CS0072 // uncomment the following lines to resolve // public override event MyDelegate MyEvent { add { VMeth += value; // MyEvent += value; } remove { VMeth -= value; // MyEvent -= value; } } public static void Main() { } }  
```