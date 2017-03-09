---
title: "Advertencia del compilador (nivel 1) CS3015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3015"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3015"
ms.assetid: 58182215-0c2f-4497-8baf-ffb29f18d6c7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS3015
'signatura de método' no tiene constructores accesibles que solo usen tipos conforme a CLS  
  
 Para que sea conforme a Common Language Specification \(CLS\), la lista de argumentos de una clase de atributo no puede contener una matriz. Para obtener más información sobre la conformidad con CLS, vea [Escribir código conforme a CLS](http://msdn.microsoft.com/es-es/4c705105-69a2-4e5e-b24e-0633bc32c7f3) y [Independencia del lenguaje y componentes independientes del lenguaje](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3015.  
  
```  
// CS3015.cs // compile with: /target:library using System; [assembly:CLSCompliant(true)] public class MyAttribute : Attribute { public MyAttribute(int[] ai) {}   // CS3015 // try the following line instead // public MyAttribute(int ai) {} }  
```