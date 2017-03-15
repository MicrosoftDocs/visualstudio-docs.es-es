---
title: "Error del compilador CS0611 | Microsoft Docs"
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
  - "CS0611"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0611"
ms.assetid: bbd857a0-9454-4438-a21c-fef5bc7eee06
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0611
Los elementos de matriz no pueden ser del tipo 'type'  
  
 Existen algunos tipos que no pueden usarse como el tipo de una matriz. Estos tipos incluyen **System.TypedReference** y **System.ArgIterator**.  
  
 El ejemplo siguiente genera la advertencia CS0611 como resultado del uso de **System.TypedReference** como un elemento de matriz:  
  
```  
// CS0611.cs public class a { public static void Main() { System.TypedReference[] ao = new System.TypedReference [10];   // CS0611 // try the following line instead // int[] ao = new int[10]; } }  
```