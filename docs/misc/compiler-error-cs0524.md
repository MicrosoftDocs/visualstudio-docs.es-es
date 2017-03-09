---
title: "Error del compilador CS0524 | Microsoft Docs"
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
  - "CS0524"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0524"
ms.assetid: a5cd8fb0-f5df-4580-9116-a6be4dffd1cb
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0524
'type': las interfaces no pueden declarar tipos  
  
 Una [interfaz](/dotnet/csharp/language-reference/keywords/interface) no puede contener un tipo definido por el usuario; debe contener solo los métodos y las propiedades.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0524:  
  
```  
// CS0524.cs public interface Clx { public class Cly   // CS0524, delete user-defined type { } }  
  
```