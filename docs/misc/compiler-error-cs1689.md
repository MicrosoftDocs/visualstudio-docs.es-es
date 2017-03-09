---
title: "Error del compilador CS1689 | Microsoft Docs"
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
  - "CS1689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1689"
ms.assetid: 5fa6e845-40ef-4451-81ee-acbe2665527a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1689
El atributo 'Nombre del atributo' solo es válido en métodos o clases de atributos  
  
 Este error se produce solo con el atributo **ConditionalAttribute**. Como indica el mensaje, este atributo únicamente se puede usar en métodos o clases de atributos. Por ejemplo, se genera el error si se intenta aplicar este atributo a una clase.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1689.  
  
```  
// CS1689.cs // compile with: /target:library [System.Diagnostics.Conditional("A")]   // CS1689 class MyClass {}  
```