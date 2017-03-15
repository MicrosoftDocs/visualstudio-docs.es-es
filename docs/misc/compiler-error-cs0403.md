---
title: "Error del compilador CS0403 | Microsoft Docs"
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
  - "CS0403"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0403"
ms.assetid: 6e5d55ce-d6bf-419d-aded-aaa2e5963bb6
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0403
No se puede convertir NULL en el parámetro de tipo 'name' porque podría ser un tipo de valor que no acepta valores NULL. Considere el uso de default\('T'\) en su lugar.  
  
 No se puede asignar null al tipo desconocido indicado porque podría ser un tipo de valor que no permite la asignación de null. Si la clase genérica no está diseñada para aceptar tipos de valor, use la restricción de tipo de clase. Si puede aceptar tipos de valor, como los tipos integrados, es posible que pueda reemplazar la asignación a null por la expresión `default(T)`, tal como se muestra en el ejemplo siguiente.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS0403:  
  
```  
// CS0403.cs // compile with: /target:library class C<T> { public void f() { T t = null;  // CS0403 T t2 = default(T);   // OK } } class D<T> where T : class { public void f() { T t = null;  // OK } }  
```