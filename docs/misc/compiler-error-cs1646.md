---
title: "Error del compilador CS1646 | Microsoft Docs"
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
  - "CS1646"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1646"
ms.assetid: 5e4b0f1e-8de3-42b0-bde6-9f882677a409
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS1646
Se esperaba una palabra clave, un identificador o una cadena detrás del especificador textual: @  
  
 Vea los literales de cadena para saber cómo se usa el especificador textual '@'. El especificador textual solo se permite antes de una cadena, una palabra clave o un identificador. Para resolver este error, quite el símbolo @ de cualquier lugar inadecuado o agregue la cadena, la palabra clave o el identificador que corresponda.  
  
 El ejemplo siguiente genera la advertencia CS1646:  
  
```  
// CS1646 class C { int i = @5;  // CS1646 // Try this line instead: // int i = 5; }  
```