---
title: "Error del compilador CS0594 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0594"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0594"
ms.assetid: a3d6bde1-db63-4c5c-a425-8c6a39e00999
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0594
La constante de punto flotante está fuera del intervalo del tipo 'type'  
  
 Se asignó un valor a una variable de punto flotante que es demasiado grande para las variables de este tipo de datos. Consulte [Tabla de tipos integrales](/dotnet/csharp/language-reference/keywords/integral-types-table) para obtener información sobre el intervalo de valores permitido en los tipos de datos.  
  
 El ejemplo siguiente genera la advertencia CS0594:  
  
```  
// CS0594.cs namespace MyNamespace { public class MyClass { public static void Main() { float f = 6.77777777777E400;   // CS0594, value too large } } }  
```