---
title: "Advertencia del compilador (nivel 1) CS1570 | Microsoft Docs"
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
  - "CS1570"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1570"
ms.assetid: a121d5c4-8b90-4cda-af5b-6ba8f23b2b1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1570
El comentario XML de 'construct' tiene código XML con formato incorrecto: 'reason'  
  
 Al usar [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option), los comentarios del código fuente deben estar en XML. Cualquier error con el formato XML generará la advertencia CS1570. Por ejemplo:  
  
-   Si pasa una cadena a un elemento **cref**, como en una etiqueta [\<exception\>](../Topic/%3Cexception%3E%20\(C%23%20Programming%20Guide\).md), la cadena debe incluirse entre comillas dobles.  
  
-   Si usa una etiqueta, como [\<seealso\>](../Topic/%3Cseealso%3E%20\(C%23%20Programming%20Guide\).md), que no tenga una etiqueta de cierre, debe especificar una barra diagonal antes del corchete angular de cierre.  
  
-   Si necesita usar símbolo de mayor que o menor que en el texto de la descripción, deberá representarlos con **&gt;** o **&lt;**.  
  
-   El atributo de ruta de acceso o archivo de una etiqueta [\<include\>](../Topic/%3Cinclude%3E%20\(C%23%20Programming%20Guide\).md) faltaba o estaba mal formado.  
  
 El ejemplo siguiente genera la advertencia CS1570:  
  
```  
// CS1570.cs // compile with: /W:1 namespace ns { // the following line generates CS1570 /// <summary> returns true if < 5 </summary> // try this instead // /// <summary> returns true if <5 </summary> public class MyClass { public static void Main () { } } }  
```