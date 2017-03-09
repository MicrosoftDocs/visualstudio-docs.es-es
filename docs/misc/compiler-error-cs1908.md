---
title: "Error del compilador CS1908 | Microsoft Docs"
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
  - "CS1908"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1908"
ms.assetid: d7da31c2-48ef-4401-b885-3459b4d7f6f6
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1908
El tipo de argumento para el atributo DefaultValue debe coincidir con el tipo de parámetro  
  
 Este error se genera cuando se usa el argumento incorrecto para el valor de atributo <xref:System.ComponentModel.DefaultValueAttribute>. Use un valor que coincida con el tipo de parámetro.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1908.  
  
```  
// CS1908.cs // compile with: /target:library using System.Runtime.InteropServices; public interface ISomeInterface { void Bad([Optional] [DefaultParameterValue("true")] bool b);   // CS1908 void Good([Optional] [DefaultParameterValue(true)] bool b);   // OK }  
```