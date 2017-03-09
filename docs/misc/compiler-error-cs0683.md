---
title: "Error del compilador CS0683 | Microsoft Docs"
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
  - "CS0683"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0683"
ms.assetid: 04cca66d-8a0b-469a-b157-9c8ece368c48
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0683
La implementación del método explícito 'explicitmethod' no puede implementar 'method' porque es un descriptor de acceso  
  
 El ejemplo siguiente genera la advertencia CS0683:  
  
```  
// CS0683.cs interface IExample { int Test { get; } } class CExample : IExample { int IExample.get_Test() { return 0; } // CS0683 int IExample.Test { get{ return 0; } } // correct }  
```