---
title: "Error del compilador CS1917 | Microsoft Docs"
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
  - "CS1917"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1917"
ms.assetid: 05688706-e4b4-4273-9244-48cce1f7f9b9
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1917
Los miembros del campo de solo lectura 'name' de tipo 'struct name' no se pueden asignar con un inicializador de objeto porque es de un tipo de valor.  
  
 Los campos de solo lectura que son tipos de valor solo pueden asignarse en un constructor.  
  
### Para corregir este error  
  
-   Cambie la estructura a un tipo de clase.  
  
-   Inicialice la estructura con un constructor.  
  
## Ejemplo  
 El código siguiente genera el error CS1917:  
  
```  
// cs1917.cs class CS1917 { public struct TestStruct { public int i; } public class C { public readonly TestStruct str = new TestStruct(); public static int Main() { C c = new C { str = { i = 1 } }; // CS1917 return 0; } } }  
```