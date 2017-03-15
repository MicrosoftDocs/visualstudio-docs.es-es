---
title: "&#39;System.Void&#39; solo se puede usar en una expresi&#243;n GetType | Microsoft Docs"
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
  - "bc31422"
  - "vbc31422"
helpviewer_keywords: 
  - "BC31422"
ms.assetid: 84e45194-cb46-41f6-8420-a1498baeaaba
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Void&#39; solo se puede usar en una expresi&#243;n GetType
Una expresión en una instrucción de asignación o una declaración que usa <xref:System.Void> como tipo de un variable, parámetro de procedimiento, valor devuelto de función o argumento de tipo.  
  
 La estructura <xref:System.Void> es un tipo especializado que se usa internamente en .NET Framework y particularmente en Visual C\# y Visual C\+\+. Representa un tipo de valor devuelto para un método que no devuelve un valor. Visual Basic usa un procedimiento `Sub` cuando no se devuelve un valor y un procedimiento `Function` cuando se devuelve un valor.  
  
 Puede probar una variable de referencia con el operador [GetType \(Operador\)](/dotnet/visual-basic/language-reference/operators/gettype-operator) para ver si su tipo en tiempo de ejecución es <xref:System.Void>, pero no puede usar <xref:System.Void> en ningún otro contexto.  
  
 **Identificador de error:** BC31422  
  
### Para corregir este error  
  
1.  Si desea comparar el tipo en tiempo de ejecución de una variable con <xref:System.Void>, use el operador `GetType`.  
  
2.  A menos que tenga un motivo concreto para comparar un tipo en tiempo de ejecución con <xref:System.Void>, quite la referencia a este por completo.  
  
## Vea también  
 <xref:System.Void>   
 [GetType \(Operador\)](/dotnet/visual-basic/language-reference/operators/gettype-operator)