---
title: "Error del compilador CS0400 | Microsoft Docs"
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
  - "CS0400"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0400"
ms.assetid: 58f91f3b-30f4-433b-9a13-0cff258a2630
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0400
No se pudo encontrar el nombre de tipo o de espacio de nombres 'identificador' en el espacio de nombres global \(compruebe si falta una referencia de ensamblado\)  
  
 El identificador cuyo ámbito está delimitado por el operador de ámbito global \(`::`\) no se encontró en el espacio de nombres global. La causa puede ser la falta de una referencia de ensamblado que contiene el identificador o el identificador se haya declarado en una clase o un espacio de nombres distinto del espacio de nombres global. Este error también podría ocurrir si no se declara o se escribe incorrectamente un identificador de ámbito global.  
  
 Para evitar este error, busque la declaración del identificador, compruebe que esté escrita correctamente y, si la declaración está en un ensamblado independiente, asegúrese de que tiene la referencia de ensamblado adecuada. Si el identificador se declara dentro de otro tipo o espacio de nombres, use el nombre completo del operador "::". El ejemplo siguiente genera la advertencia CS0400:  
  
```  
// CS0400.cs class C { public static void Main() { // CS0400 - D could not be found // in the global namespace. global::D d = new global::D(); } }  
```