---
title: "Error del compilador CS1032 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1032"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1032"
ms.assetid: fe318a6c-4403-4b9b-b3d8-753ec31c00ff
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1032
No se puede definir o anular la definición de símbolos de preprocesador después del primer token del archivo  
  
 Las [directivas de preprocesador](/dotnet/csharp/language-reference/preprocessor-directives/index)`#define` y `#undef` deben usarse al principio de un programa, antes que cualquier otra palabra clave, como las usadas en la declaración de espacio de nombres.  
  
 El ejemplo siguiente genera la advertencia CS1032:  
  
```  
// CS1032.cs namespace x { public class clx { #define a   // CS1032, put before namespace public static void Main() { } } }  
```