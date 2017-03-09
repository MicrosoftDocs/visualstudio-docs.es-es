---
title: "Error del compilador CS0839 | Microsoft Docs"
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
  - "CS0839"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0839"
ms.assetid: 6f2f1062-8551-4125-8880-68bfbfbcf061
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0839
Falta un argumento.  
  
 Falta algún argumento en la llamada del método.  
  
### Para corregir este error  
  
1.  Vuelva a comprobar la firma del método, busque y proporcione el argumento que falta.  
  
## Ejemplo  
 El ejemplo siguiente genera el error CS0839:  
  
```  
// cs0839.cs using System; namespace TestNamespace { class Test { static int Add(int i, int j) { return i + j; } static int Main() { int i = Test.Add( , 5); // CS0839 return 1; } } }  
```