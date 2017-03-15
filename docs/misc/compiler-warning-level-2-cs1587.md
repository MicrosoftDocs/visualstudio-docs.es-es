---
title: "Advertencia del compilador (nivel 2) CS1587 | Microsoft Docs"
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
  - "CS1587"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1587"
ms.assetid: b27c2009-d485-43fd-a649-fbc15570d256
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 2) CS1587
El comentario XML no está situado en un elemento de idioma válido  
  
 Las etiquetas recomendadas para comentarios de documentación no se permiten en todos los elementos del lenguaje. Por ejemplo, no se permite una etiqueta en un espacio de nombres. Para más información sobre los comentarios XML, vea [Etiquetas recomendadas para los comentarios de documentación](/dotnet/csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1587:  
  
```  
// CS1587.cs // compile with: /W:2 /doc:x.xml /// <summary>test</summary>   // CS1587, tag not allowed on namespace namespace MySpace { class MyClass { public static void Main() { } } }  
```