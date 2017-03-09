---
title: "Cadena de patr&#243;n no v&#225;lida | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cadena de patr&#243;n no v&#225;lida
La cadena de patrón especificada en la operación `Like` de una búsqueda no es válida.  
  
### Para corregir este error  
  
1.  Revise los caracteres válidos para las expresiones de lista.  
  
2.  En el intervalo de patrones, asegúrese de que el carácter inicial del intervalo es menor que el carácter final del intervalo, como en `[a-z]`.  
  
3.  En el intervalo de patrones, asegúrese de que no hay varios guiones uno junto a otro, como en `[a--z]`.  
  
4.  Finalice los intervalos de patrones con un corchete de cierre.  
  
## Vea también  
 [Like \(Operador\)](/dotnet/visual-basic/language-reference/operators/like-operator)