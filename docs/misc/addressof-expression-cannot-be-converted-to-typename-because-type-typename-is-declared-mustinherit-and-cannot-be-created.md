---
title: "La expresi&#243;n &#39;AddressOf&#39; no se puede convertir a &#39;&lt;nombreTipo&gt;&#39; porque el tipo &#39;&lt;nombreTipo&#39; se ha declarado como &#39;MustInherit&#39; y no se puede crear. | Microsoft Docs"
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
  - "vbc30939"
  - "bc30939"
helpviewer_keywords: 
  - "BC30939"
ms.assetid: e8edef15-0df5-46d7-aba6-89e26a2aa506
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La expresi&#243;n &#39;AddressOf&#39; no se puede convertir a &#39;&lt;nombreTipo&gt;&#39; porque el tipo &#39;&lt;nombreTipo&#39; se ha declarado como &#39;MustInherit&#39; y no se puede crear.
Una instrucción intenta convertir una expresión `AddressOf` a un tipo que solo puede ser una clase base y no se puede usar para crear una instancia.  
  
 El operador `AddressOf` crea una instancia de delegado de procedimiento que hace referencia a un procedimiento específico.  
  
 **Identificador de error:** BC30939  
  
### Para corregir este error  
  
-   Asigne la expresión `AddressOf` a un tipo delegado específico.  
  
## Vea también  
 [AddressOf \(Operador\)](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [NO ESTÁ EN LA COMPILACIÓN: Delegados y el operador AddressOf](http://msdn.microsoft.com/es-es/7b2ed932-8598-4355-b2f7-5cedb23ee86f)   
 [Delegados](/dotnet/visual-basic/programming-guide/language-features/delegates/delegates)