---
title: "CA1821: Quitar los finalizadores vac&#237;os | Microsoft Docs"
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
  - "RemoveEmptyFinalizers"
  - "CA1821"
helpviewer_keywords: 
  - "CA1821"
ms.assetid: 3f4855a0-e4a0-46e6-923c-4c3b7074048d
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1821: Quitar los finalizadores vac&#237;os
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveEmptyFinalizers|  
|Identificador de comprobación|CA1821|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un tipo implementa un finalizador que está vacío, llama sólo al finalizador del tipo base o llama sólo a los métodos emitidos condicionalmente.  
  
## Descripción de la regla  
 Siempre que pueda, evite los finalizadores debido a la sobrecarga de rendimiento adicional necesaria para el seguimiento de la duración del objeto.  El recolector de elementos no utilizados ejecutará el finalizador antes de recopilar el objeto.  Esto significa que se requerirán dos colecciones para recopilar el objeto.  Un finalizador vacío no obtiene ningún beneficio de esta sobrecarga adicional.  
  
## Cómo corregir infracciones  
 Quite el finalizador vacío.  Si se requiere un finalizador para depurar, enciérrelo en directivas `#if DEBUG / #endif`.  
  
## Cuándo suprimir advertencias  
 No suprima los mensajes de esta regla.  El error para suprimir la finalización disminuye el rendimiento y no proporciona ventajas.  
  
## Ejemplo  
 El ejemplo siguiente muestra un finalizador vacío que se debería quitar, un finalizador que se debería encerrar en directivas `#if DEBUG / #endif` y un finalizador que utiliza correctamente las directivas `#if DEBUG / #endif`.  
  
 [!code-cs[FxCop.Performance.RemoveEmptyFinalizers#1](../code-quality/codesnippet/CSharp/ca1821-remove-empty-finalizers_1.cs)]