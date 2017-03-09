---
title: "Se necesita una expresi&#243;n constante. | Microsoft Docs"
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
  - "bc30059"
  - "vbc30059"
helpviewer_keywords: 
  - "BC30059"
ms.assetid: fdd5e7bb-6370-4a63-bbb6-23b15badb4c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Se necesita una expresi&#243;n constante.
Una instrucción `Const` no inicializa correctamente una constante o una declaración de matriz usa una variable para especificar el número de elementos.  
  
 **Identificador de error:** BC30059  
  
### Para corregir este error  
  
1.  Si la declaración es una instrucción `Const`, compruebe que la constante se inicializa con un literal, una constante declarada anteriormente, un miembro de enumeración o una combinación de literales, constantes y miembros de enumeración con operadores.  
  
2.  Si la declaración especifica una matriz, compruebe si se usa una variable para especificar el número de elementos. Si es así, reemplace la variable con una expresión constante.  
  
## Vea también  
 [Const \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [NOTINBUILD Una variable de matriz](http://msdn.microsoft.com/es-es/c2da78bd-6928-46ba-805f-44f819dfaf93)