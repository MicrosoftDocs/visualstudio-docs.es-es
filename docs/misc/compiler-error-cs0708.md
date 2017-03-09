---
title: "Error del compilador CS0708 | Microsoft Docs"
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
  - "CS0708"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0708"
ms.assetid: 19e1907f-b78c-4c8b-b78c-eedfd57115f2
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0708
'field': no se pueden declarar miembros de instancia en una clase estática  
  
 Este error se produce si se declara un miembro no estático en una clase declarada como estática. No es posible crear instancias de clases estáticas, ya que las variables de instancia no tendrían sentido. La palabra clave **static** se debe aplicar a todos los miembros de las clases estáticas.  
  
 El ejemplo siguiente genera la advertencia CS0708:  
  
```  
// CS0708.cs // compile with: /target:library public static class C { int i;  // CS0708 static int j;  // OK }  
```