---
title: "Error del compilador CS0689 | Microsoft Docs"
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
  - "CS0689"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0689"
ms.assetid: 5c555c2e-8e71-4097-8dbf-52dbafe7bf57
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0689
No se puede derivar de 'identificador' porque es un parámetro de tipo  
  
 Las clases base o las interfaces para clases genéricas no se puede especificar mediante un parámetro de tipo. Se debe derivar de una determinada interfaz o clase o de una clase genérica específica, o bien incluir el tipo desconocido como miembro.  
  
 El ejemplo siguiente genera la advertencia CS0689:  
  
```  
// CS0689.cs class A<T> : T   // CS0689 { }  
```