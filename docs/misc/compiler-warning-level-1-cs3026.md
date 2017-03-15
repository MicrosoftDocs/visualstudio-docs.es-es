---
title: "Advertencia del compilador (nivel 1) CS3026 | Microsoft Docs"
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
  - "CS3026"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3026"
ms.assetid: 6c57b2e3-3011-42db-b450-ce9e04c4b4ca
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3026
El campo 'field' conforme a CLS no puede ser volátil  
  
 Una variable volátil no debe ser compatible con CLS.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS3026.  
  
```  
// CS3026.cs [assembly:System.CLSCompliant(true)] public class Test { public volatile int v0 =0;   // CS3026 // To resolve remove the CLS-CComplient attribute. public static void Main() { } }  
  
```