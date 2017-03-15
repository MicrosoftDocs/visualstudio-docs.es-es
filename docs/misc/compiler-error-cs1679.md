---
title: "Error del compilador CS1679 | Microsoft Docs"
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
  - "CS1679"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1679"
ms.assetid: c42e9bca-212a-458e-88f8-b81c812436bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1679
Alias externo no válido para '\/reference'; 'identifier' no es un identificador válido  
  
 Al usar la característica de alias de ensamblado externo de la opción **\/reference**, el texto que sigue a **\/reference:** y que precede a '\=' debe ser una palabra clave o un identificador de C\# válido de acuerdo con la especificación del lenguaje C\#.  
  
 Para corregir este error, cambie el texto delante de "\=" por una palabra clave o un identificador válido de C\#.  
  
## Ejemplo  
 El siguiente ejemplo genera el error CS1679.  
  
```  
// CS1679.cs // compile with: /reference:123$BadIdentifier%=System.dll class TestClass { static void Main() { } }  
```