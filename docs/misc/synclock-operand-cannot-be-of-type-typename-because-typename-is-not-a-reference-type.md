---
title: "El operando de &#39;SyncLock&#39; no puede ser del tipo &#39;&lt;nombreTipo&gt;&#39; debido a que &#39;&lt;nombreTipo&gt;&#39; no es un tipo de referencia. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30582"
  - "bc30582"
helpviewer_keywords: 
  - "BC30582"
ms.assetid: 953aecf2-629a-4272-94bd-abf88f785e63
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El operando de &#39;SyncLock&#39; no puede ser del tipo &#39;&lt;nombreTipo&gt;&#39; debido a que &#39;&lt;nombreTipo&gt;&#39; no es un tipo de referencia.
La instrucción `SyncLock` permite que las instrucciones se sincronicen en una sola expresión ya que garantiza que varios subprocesos no ejecuten las mismas instrucciones al mismo tiempo. El tipo de expresión en una instrucción `SyncLock` debe ser un tipo de referencia, como una clase, un módulo, una interfaz, una matriz o un delegado.  
  
 **Identificador de error:** BC30582  
  
### Para corregir este error  
  
-   Cambie el tipo a un tipo de referencia adecuado.  
  
## Vea también  
 [SyncLock \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/synclock-statement)   
 [NO ESTÁ EN LA COMPILACIÓN: Multithreading en Visual Basic](http://msdn.microsoft.com/es-es/c731a50c-09c1-4468-9646-54c86b75d269)