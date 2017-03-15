---
title: "Advertencia del compilador (nivel 1) CS0626 | Microsoft Docs"
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
  - "CS0626"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0626"
ms.assetid: 2cd5061c-80e7-48d3-8d14-be7fc642af94
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS0626
El método, el operador o el descriptor de acceso 'método' está marcado como externo y no tiene atributos. Considere la posibilidad de agregar un atributo DllImport para especificar la implementación externa.  
  
 Un método marcado como `extern` también debe marcarse con un atributo \(por ejemplo, el atributo [DllImport](frlrfSystemRuntimeInteropServicesDllImportAttributeClassTopic)\).  
  
 El atributo especifica dónde se implementa el método. En tiempo de ejecución, el programa necesitará esta información.  
  
 El ejemplo siguiente genera la advertencia CS0626:  
  
```  
// CS0626.cs // compile with: /warnaserror using System.Runtime.InteropServices; public class MyClass { static extern public void M(); // CS0626 // try the following line // [DllImport("mydll.dll")] static extern public void M(); public static void Main() { } }  
```