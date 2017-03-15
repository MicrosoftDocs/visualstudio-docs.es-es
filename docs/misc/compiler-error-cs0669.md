---
title: "Error del compilador CS0669 | Microsoft Docs"
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
  - "CS0669"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0669"
ms.assetid: c7f81869-79d7-481f-a026-2cef0e87df4c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0669
Una clase con el atributo ComImport no puede tener un constructor definido por el usuario  
  
 La capa de interoperabilidad COM en Common Language Runtime ofrece el constructor para las clases [ComImport](frlrfSystemRuntimeInteropServicesComImportAttributeClassTopic). Por lo tanto, un objeto COM puede utilizarse como un objeto administrado en runtime.  
  
 El ejemplo siguiente genera la advertencia CS0669:  
  
```  
// CS0669.cs using System.Runtime.InteropServices; [ComImport, Guid("00000000-0000-0000-0000-000000000001")] class TestClass { TestClass()   // CS0669, delete constructor to resolve { } public static void Main() { } }  
```