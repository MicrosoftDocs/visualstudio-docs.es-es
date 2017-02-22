---
title: "DA0010: GetHashCode consume muchos recursos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAExpensiveGetHashCode"
  - "vs.performance.DA0010"
  - "vs.performance.rules.DA0010"
  - "vs.performance.10"
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0010: GetHashCode consume muchos recursos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Identificador de regla|DA0010|  
|Categoría|Uso de .NET Framework|  
|Métodos de generación de perfiles|Muestreo<br /><br /> Memoria de .NET|  
|Mensaje|Las funciones GetHashCode deben consumir pocos recursos y no asignar ninguna memoria.  Reduzca la complejidad de la función de código hash si es posible.|  
|Tipo de mensaje|Advertencia|  
  
## Motivo  
 Las llamadas al método GetHashCode del tipo constituyen una proporción considerable de los datos de generación de perfiles o el método asigna memoria.  
  
## Descripción de la regla  
 Aplicar un algoritmo hash es una técnica para buscar rápidamente un elemento determinado en una colección grande.  Dado que las tablas hash pueden ser muy grandes y tener que admitir tasas muy altas de acceso, las tablas hash deberían ser sumamente eficaces.  Una implicación de este requisito es que los métodos GetHashCode en el .NET Framework no deberían asignar la memoria.  La asignación de memoria incrementa la carga en el recolector de elementos no utilizados y expone el método a posibles retrasos si se hace necesario ejecutar la recolección de elementos no utilizados como resultado de la solicitud de asignación.  
  
## Cómo corregir infracciones  
 Reduzca la complejidad del método.