---
title: "Una expresi&#243;n &#39;AddressOf&#39; no se puede convertir a &#39;&lt;nombreDeTipo&gt;&#39; porque &#39;&lt;nombreDeTipo&gt;&#39; no es un tipo delegado | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30581"
  - "bc30581"
helpviewer_keywords: 
  - "BC30581"
ms.assetid: 5db7589a-5456-4b3a-9d6b-93d9157f0484
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Una expresi&#243;n &#39;AddressOf&#39; no se puede convertir a &#39;&lt;nombreDeTipo&gt;&#39; porque &#39;&lt;nombreDeTipo&gt;&#39; no es un tipo delegado
Una instrucción intenta convertir una expresión `AddressOf` a un tipo que no es un tipo delegado.  
  
 El operador `AddressOf` crea una instancia de delegado de procedimiento que hace referencia a un procedimiento específico.`AddressOf` se puede usar como operando de un constructor de delegado o en un contexto en el que el compilador puede determinar el tipo del delegado.  
  
 **Identificador de error:** BC30581  
  
### Para corregir este error  
  
-   Cambie el tipo de destino a un tipo delegado.  
  
## Vea también  
 [AddressOf \(Operador\)](/dotnet/visual-basic/language-reference/operators/addressof-operator)   
 [NO ESTÁ EN LA COMPILACIÓN: Los delegados y el operador AddressOf](http://msdn.microsoft.com/es-es/7b2ed932-8598-4355-b2f7-5cedb23ee86f)