---
title: "El constructor de atributo tiene un par&#225;metro &#39;ByRef&#39; del tipo &#39;&lt;nombreDeTipo&gt;&#39;; no se pueden usar constructores con par&#225;metros byref para aplicar el atributo | Microsoft Docs"
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
  - "bc36006"
  - "vbc36006"
helpviewer_keywords: 
  - "BC36006"
ms.assetid: 4c4e991f-3839-4196-bcfb-eb8464aa55e5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El constructor de atributo tiene un par&#225;metro &#39;ByRef&#39; del tipo &#39;&lt;nombreDeTipo&gt;&#39;; no se pueden usar constructores con par&#225;metros byref para aplicar el atributo
Un atributo se aplica a un elemento de programación mediante un constructor de atributo que toma un parámetro `ByRef`.  
  
 Los atributos se aplican en tiempo de compilación y el compilador necesita valores concretos que pasar al constructor de atributo. Un parámetro `ByRef` toma un puntero para un valor, que no se puede evaluar en tiempo de compilación.  
  
 Puede definir un constructor de atributo que tome un parámetro `ByRef` y usarlo con fines como la herencia, pero al aplicar el atributo debe usar un constructor que no tome ningún parámetro `ByRef`.  
  
 **Identificador de error:** BC36006  
  
### Para corregir este error  
  
-   Aplique el atributo mediante un constructor que no tome ningún parámetro `ByRef`, o no aplique el atributo de ningún modo.  
  
## Vea también  
 [NO ESTÁ EN LA COMPILACIÓN: Información general de atributos en Visual Basic](http://msdn.microsoft.com/es-es/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [NO ESTÁ EN LA COMPILACIÓN: Aplicación de atributos](http://msdn.microsoft.com/es-es/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Pasar argumentos por valor y por referencia](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)   
 [ByRef](/dotnet/visual-basic/language-reference/modifiers/byref)