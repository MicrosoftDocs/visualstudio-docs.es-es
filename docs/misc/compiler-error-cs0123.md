---
title: "Error del compilador CS0123 | Microsoft Docs"
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
  - "CS0123"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0123"
ms.assetid: 57be2c58-6d87-40af-9376-cd7f91023044
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0123
Ninguna sobrecarga correspondiente a 'método' coincide con el delegado 'delegado'  
  
 Error al crear a un delegado porque no se usó la signatura correcta. Las instancias de un delegado deben declararse con la misma signatura que la declaración de delegado.  
  
 Puede resolver este error ajustando la signatura del método o del delegado. Para obtener más información, consulte [Delegados](/dotnet/csharp/programming-guide/delegates/index).  
  
 El ejemplo siguiente genera la advertencia CS0123.  
  
```  
// CS0123.cs delegate void D(); delegate void D2(int i); public class C { public static void f(int i) {} public static void Main() { D d = new D(f);   // CS0123 D2 d2 = new D2(f);   // OK } }  
```