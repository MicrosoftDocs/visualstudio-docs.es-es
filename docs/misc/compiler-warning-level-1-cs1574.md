---
title: "Advertencia del compilador (nivel 1) CS1574 | Microsoft Docs"
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
  - "CS1574"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1574"
ms.assetid: 4cd2b474-ab01-4397-aed7-63e5f0081649
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1574
El comentario XML sobre 'construct' tiene un atributo de cref sintácticamente incorrecto 'name'  
  
 Una cadena que se pasó a una etiqueta cref, por ejemplo, dentro de una etiqueta \<excepción\>, hacía referencia a un miembro que no está disponible en el entorno de compilación actual. La cadena pasada a una etiqueta cref debe ser el nombre sintácticamente correcto de un miembro o campo.  
  
 Para más información, consulte [Etiquetas recomendadas para los comentarios de documentación](/dotnet/csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments).  
  
 El ejemplo siguiente genera la advertencia CS1574:  
  
```  
// CS1574.cs // compile with: /W:1 /doc:x.xml using System; /// <exception cref="System.Console.WriteLin">An exception class.</exception>   // CS1574 // instead, uncomment and try the following line // /// <exception cref="System.Console.WriteLine">An exception class.</exception> class EClass : Exception { } class TestClass { public static void Main() { try { } catch(EClass) { } } }  
```