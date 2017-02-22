---
title: "CA2004: Quitar las llamadas a GC.KeepAlive | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RemoveCallsToGCKeepAlive"
  - "CA2004"
helpviewer_keywords: 
  - "RemoveCallsToGCKeepAlive"
  - "CA2004"
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2004: Quitar las llamadas a GC.KeepAlive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|Identificador de comprobación|CA2004|  
|Categoría|Microsoft.Reliability|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Las clases utilizan `SafeHandle` pero aún contienen llamadas a `GC.KeepAlive`.  
  
## Descripción de la regla  
 Al efectuar la conversión para utilizar `SafeHandle`, quite todas las llamadas a `GC.KeepAlive` \(objeto\).  En este caso, las clases no deberían tener que llamar a `GC.KeepAlive`, `` puesto que se supone que no tienen un finalizador sino que dependen de `SafeHandle` para que se encargue de completar el identificador OS.  Aunque el costo de dejar una llamada a `GC.KeepAlive` puede ser mínimo en términos de rendimiento, la percepción de que una llamada a `GC.KeepAlive` resulta necesaria o suficiente para solucionar un problema de duración que ya no existe hace que el código sea más difícil de mantener.  
  
## Cómo corregir infracciones  
 Quite las llamadas a `GC.KeepAlive`.  
  
## Cuándo suprimir advertencias  
 Sólo puede suprimir esta advertencia si no es técnicamente correcto realizar la conversión para el uso de `SafeHandle` en la clase.