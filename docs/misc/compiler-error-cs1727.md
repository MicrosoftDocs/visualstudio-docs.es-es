---
title: "Error del compilador CS1727 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1727"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1727"
ms.assetid: 66478a58-e0f6-4886-b940-5473ad485a01
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1727
No se puede enviar el informe de errores automáticamente sin autorización. Visite '' para autorizar su envío.  
  
 En el sitio web indicado en el texto del error, se explica cómo habilitar los informes de errores automáticos de las herramientas de línea de comandos de [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)].  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1727.  
  
```  
// CS1727.cs // compile with: /errorreport:send // CS1727 expected class Test { static void Main(){} }  
```  
  
## Vea también  
 [\/errorreport \(Set Error Reporting Behavior\)](/dotnet/csharp/language-reference/compiler-options/errorreport-compiler-option)