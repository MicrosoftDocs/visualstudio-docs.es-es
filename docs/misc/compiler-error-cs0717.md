---
title: "Error del compilador CS0717 | Microsoft Docs"
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
  - "CS0717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0717"
ms.assetid: 1976e82a-d048-4f13-a95a-a7f4e3cd7038
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0717
'clase estática': las clases estáticas no se pueden usar como restricciones  
  
 No se pueden extender las clases estáticas porque contienen solo miembros estáticos y no miembros de instancia. Dado que no se pueden extender, no sirven como parámetros de tipo ni restricciones, ya que no puede existir ningún tipo que sea una especialización de una clase estática.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0717:  
  
```  
// CS0717.cs public static class SC { public static void F() { } } public class G<T> where T : SC  // CS0717 { public static void Main() { } }  
```