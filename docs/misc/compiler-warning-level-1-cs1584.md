---
title: "Advertencia del compilador (nivel 1) CS1584 | Microsoft Docs"
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
  - "CS1584"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1584"
ms.assetid: 56c8f9bf-4cce-4269-b573-d60e5b11f9ab
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1584
El comentario XML en 'miembro' tiene un atributo cref con sintaxis incorrecta 'sintaxis\_no\_válida'.  
  
 Uno de los parámetros pasados a una etiqueta para comentarios de documentación tiene una sintaxis no válida. Para obtener más información, consulta [Etiquetas recomendadas para los comentarios de documentación](/dotnet/csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia CS1584.  
  
```  
// CS1584.cs // compile with: /W:1 /doc:CS1584.xml /// <remarks>Test class</remarks> public class Test { /// <remarks>Called in <see cref="Test.Mai()n"/>.</remarks>   // CS1584 // try the following line instead // /// <remarks>Called in <see cref="Test.Main()"/>.</remarks> public static void Test2() {} /// <remarks>Main method</remarks> public static void Main() {} }  
```