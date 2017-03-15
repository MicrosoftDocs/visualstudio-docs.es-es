---
title: "DA0011: CompareTo consume muchos recursos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0011"
  - "vs.performance.rules.DAExpensiveCompareTo"
  - "vs.performance.11"
  - "vs.performance.rules.DA0011"
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DA0011: CompareTo consume muchos recursos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0011|  
|Categoría|Uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo<br /><br /> Memoria de .NET|  
|Mensaje|Las funciones CompareTo deben consumir pocos recursos y no asignar ninguna memoria.  Reduzca la complejidad de la función CompareTo si es posible.|  
|Tipo de regla|Advertencia|  
  
## Motivo  
 El método CompareTo del tipo consume muchos recursos o asigna memoria.  
  
## Descripción de la regla  
 Los métodos CompareTo deben ser eficaces y no deben asignar memoria.  
  
## Cómo corregir infracciones  
 Reduzca la complejidad del método CompareTo.