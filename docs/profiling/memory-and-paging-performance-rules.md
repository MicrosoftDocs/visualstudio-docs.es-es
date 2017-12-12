---
title: "Reglas de rendimiento de memoria y paginación | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15b9963d10a2a51d34ef3a426ac7a2aba17c2430
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="memory-and-paging-performance-rules"></a>Reglas de rendimiento de memoria y paginación
Las reglas de rendimiento en la categoría de paginación y memoria identifican la actividad de paginación en una generación de perfiles que puede afectar al rendimiento y la capacidad de respuesta de la aplicación.  
  
|||  
|-|-|  
|[DA0014: Frecuencia extremadamente alta de paginación de memoria activa en el disco](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Se ha producido una tasa muy alta de paginación de memoria activa hacia el disco y desde el disco durante la generación de perfiles. Las tasas de paginación en este nivel normalmente afectan al rendimiento y la capacidad de respuesta de la aplicación. Considere la posibilidad de reducir las asignaciones de memoria mediante la revisión de los algoritmos. También es posible que deba tener en cuenta los requisitos de memoria de la aplicación. Intente ejecutar de nuevo la generación de perfiles en un equipo con más memoria. Se activa esta regla cuando la cantidad de actividad de paginación supera el umbral de regla D0017.|  
|[DA0017: Alta frecuencia de paginación de memoria activa en el disco](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Se produjo una tasa relativamente alta de paginación de memoria activa hacia y desde el disco durante la generación de perfiles. Las tasas de paginación en este nivel normalmente afectan al rendimiento y la capacidad de respuesta de la aplicación. Considere la posibilidad de reducir las asignaciones de memoria mediante la revisión de los algoritmos. También es posible que deba tener en cuenta los requisitos de memoria de la aplicación. Intente ejecutar de nuevo la generación de perfiles en un equipo con más memoria.|