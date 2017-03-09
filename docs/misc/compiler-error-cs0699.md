---
title: "Error del compilador CS0699 | Microsoft Docs"
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
  - "CS0699"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0699"
ms.assetid: 1dff310b-6b8d-46b4-a649-bbf23282ff1f
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Error del compilador CS0699
'generic' no define el parámetro de tipo 'identifier'  
  
 Se usó un parámetro de tipo en una definición genérica que no se encontró en la lista de declaración de los parámetros de tipo de ese genérico. Esto puede ocurrir si el nombre usado para el parámetro de tipo es incoherente.  
  
 El ejemplo siguiente genera la advertencia CS0699:  
  
```  
// CS0699.cs class C<T> where U : I   // CS0699 – U is not a valid type parameter { }  
```