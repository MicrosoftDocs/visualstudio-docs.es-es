---
title: "Error del compilador CS0430 | Microsoft Docs"
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
  - "CS0430"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0430"
ms.assetid: b63c4f9a-b1cd-41d2-a02e-2ed0f177450f
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0430
El alias externo 'alias' no se especificó en una opción \/reference.  
  
 Este error se produce cuando se encuentra alias externo pero no se especificó un alias como referencia en la línea de comandos. Para resolver el error CS0430, compile con **\/reference**.  
  
## Ejemplo  
  
```  
// CS0430_a.cs // compile with: /target:library public class MyClass {}  
```  
  
## Ejemplo  
 Compilar con **\/reference:MyType\=cs0430\_a.dll** para hacer referencia a la DLL creada en el ejemplo anterior resuelve este error. El ejemplo siguiente genera la advertencia CS0430.  
  
```  
// CS0430_b.cs extern alias MyType;   // CS0430 public class Test { public static void Main() {} }  
  
```