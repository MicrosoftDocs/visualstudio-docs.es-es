---
title: "Error del compilador CS1910 | Microsoft Docs"
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
  - "CS1910"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1910"
ms.assetid: 0fef9727-e56f-451c-9255-ca4e5a26d7c6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1910
El argumento de tipo 'type' no se puede aplicar al atributo DefaultValue.  
  
 Para los parámetros cuyo tipo sea de objeto, el argumento de <xref:System.Runtime.InteropServices.DefaultParameterValueAttribute> debe ser `null`, un tipo integral, un punto flotante, `bool`, `string`, `enum` o `char`. El argumento no puede ser de tipo <xref:System.Type> o cualquier tipo de matriz.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1910.  
  
```  
// CS1910.cs // compile with: /target:library using System.Runtime.InteropServices; public interface MyI { void Test([DefaultParameterValue(typeof(object))] object o);   // CS1910 }  
```