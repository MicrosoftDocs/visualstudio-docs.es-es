---
title: "Las etiquetas no son v&#225;lidas fuera de m&#233;todos o lambdas de varias l&#237;neas | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30016"
  - "bc30016"
helpviewer_keywords: 
  - "BC30016"
ms.assetid: 17d12a96-d759-4df9-882c-5e45c1d814a5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Las etiquetas no son v&#225;lidas fuera de m&#233;todos o lambdas de varias l&#237;neas
Puede agregar una etiqueta a una instrucción solo dentro de un procedimiento `Sub`, `Function`, propiedad `Get` o propiedad `Set`. Solo una instrucción ejecutable puede tener una etiqueta, y todas las instrucciones ejecutables deben estar dentro de procedimientos.  
  
 **Identificador de error:** BC30016  
  
### Para corregir este error  
  
1.  Quite la etiqueta de la instrucción o mueva la instrucción dentro de un procedimiento.  
  
## Vea también  
 [Cómo: Aplicar etiquetas a las instrucciones](../Topic/How%20to:%20Label%20Statements%20\(Visual%20Basic\).md)   
 [Sub \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/sub-statement)   
 [Function \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/function-statement)   
 [Get \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/get-statement)   
 [Set \(Instrucción\)](/dotnet/visual-basic/language-reference/statements/set-statement)