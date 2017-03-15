---
title: "Error del compilador CS0250 | Microsoft Docs"
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
  - "CS0250"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0250"
ms.assetid: a994f361-6287-4db0-9ce1-e293a8190049
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0250
No llame directamente a su método de clase base Finalize. Este se llama automáticamente desde el destructor.  
  
 Un programa no puede intentar forzar la eliminación de recursos de clase base.  
  
 Para obtener más información, vea [Métodos de finalización y destructores](http://msdn.microsoft.com/es-es/fd376774-1643-499b-869e-9546a3aeea70).  
  
 El ejemplo siguiente genera la advertencia CS0250:  
  
```  
// CS0250.cs class B { } class C : B { ~C() { base.Finalize();   // CS0250 } public static void Main() { } }  
```