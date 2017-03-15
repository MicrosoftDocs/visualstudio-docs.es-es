---
title: "Advertencia del compilador (nivel 1) CS1589 | Microsoft Docs"
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
  - "CS1589"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1589"
ms.assetid: bdc47124-93ae-4c6a-81b2-dde8ec4d0ab1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Advertencia del compilador (nivel 1) CS1589
No se puede incluir el fragmento de código XML 'fragment' del archivo 'file' \-\- motivo  
  
 La sintaxis \(*fragment*\) de una etiqueta [\<include\>](../Topic/%3Cinclude%3E%20\(C%23%20Programming%20Guide\).md), que hace referencia a un archivo \(`file`\), era incorrecta por el ***motivo*** especificado.  
  
 Aparecerá una línea con formato incorrecto en el archivo XML generado.  
  
 El ejemplo siguiente genera la advertencia CS1589:  
  
```  
// CS1589.cs // compile with: /W:1 /doc:CS1589_out.xml /// <include file='CS1589.doc' path='MyDocs/MyMembers[@name="test"]/' />   // CS1589 // try the following line instead // /// <include file='CS1589.doc' path='MyDocs/MyMembers[@name="test"]/*' /> class Test { public static void Main() { } }  
```