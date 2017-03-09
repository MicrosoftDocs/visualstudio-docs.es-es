---
title: "Error del compilador CS0126 | Microsoft Docs"
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
  - "CS0126"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0126"
ms.assetid: 15fb0f38-ac9d-4c09-a69f-398a4903d790
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0126
Se requiere un objeto cuyo tipo se pueda convertir en 'tipo'  
  
 Una instrucción return está presente, pero no devuelve un valor del tipo esperado. Para obtener más información, consulta [Propiedades](/dotnet/csharp/programming-guide/classes-and-structs/properties).  
  
 El ejemplo siguiente genera la advertencia CS0126:  
  
```  
// CS0126.cs public class a { public int i { set { } get { return;   // CS0126, specify a value to return } } }  
```