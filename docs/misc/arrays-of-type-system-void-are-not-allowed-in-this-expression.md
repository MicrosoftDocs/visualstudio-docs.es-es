---
title: "En esta expresi&#243;n no se permiten matrices de tipo &#39;System.Void&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31428"
  - "bc31428"
helpviewer_keywords: 
  - "BC31428"
ms.assetid: 21d77b56-585f-4107-b7ec-21933ba58017
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# En esta expresi&#243;n no se permiten matrices de tipo &#39;System.Void&#39;
Una expresión en una instrucción de asignación o una declaración especifica una matriz de tipo <xref:System.Void>.  
  
 La estructura <xref:System.Void> es un tipo especializado que se usa internamente en .NET Framework y particularmente en Visual C\# y Visual C\+\+. Representa un tipo de valor devuelto para un método que no devuelve un valor. Visual Basic usa un procedimiento `Sub` cuando no se devuelve un valor y un procedimiento `Function` cuando se devuelve un valor.  
  
 Las matrices de tipo <xref:System.Void> no son significativas y no se permiten en ningún contexto.  
  
 **Identificador de error:** BC31428  
  
### Para corregir este error  
  
1.  Quite los paréntesis que designan una matriz.  
  
2.  A menos que tenga un motivo concreto para comparar un tipo en tiempo de ejecución con <xref:System.Void>, quite la referencia a este por completo.  
  
## Vea también  
 <xref:System.Void>