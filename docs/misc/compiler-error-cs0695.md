---
title: "Error del compilador CS0695 | Microsoft Docs"
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
  - "CS0695"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0695"
ms.assetid: 05f6c8cf-6147-4ac7-84ea-e1f34f8ef9f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0695
'generic type' no puede implementar tanto 'generic inerface' como 'generic interface' porque se pueden unificar para algunas sustituciones de parámetros de tipo  
  
 Este error se produce cuando una clase genérica implementa más de una parametrización de la misma interfaz genérica y existe una sustitución de parámetros de tipo que haría que las dos interfaces fuesen idénticas. Para evitar este error, implemente solo una de las interfaces o cambie los parámetros de tipo para evitar el conflicto.  
  
 El ejemplo siguiente genera la advertencia CS0695:  
  
```  
// CS0695.cs // compile with: /target:library interface I<T> { } class G<T1, T2> : I<T1>, I<T2>  // CS0695 { }  
```