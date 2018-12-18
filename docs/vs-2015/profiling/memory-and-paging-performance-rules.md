---
title: Reglas de rendimiento de memoria y paginación | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f37972b2-efe4-4a1c-a5d1-a246ccd76817
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d10d423c544a1117a56a954bacfa00f0ce439b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808653"
---
# <a name="memory-and-paging-performance-rules"></a>Reglas de rendimiento de memoria y paginación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las reglas de rendimiento en la categoría de paginación y memoria identifican la actividad de paginación en una generación de perfiles que puede afectar al rendimiento y la capacidad de respuesta de la aplicación.  
  
|||  
|-|-|  
|[DA0014: Frecuencia extremadamente alta de paginación de memoria activa en el disco](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)|Se ha producido una tasa muy alta de paginación de memoria activa hacia el disco y desde el disco durante la generación de perfiles. Las tasas de paginación en este nivel normalmente afectan al rendimiento y la capacidad de respuesta de la aplicación. Considere la posibilidad de reducir las asignaciones de memoria mediante la revisión de los algoritmos. También es posible que deba tener en cuenta los requisitos de memoria de la aplicación. Intente ejecutar de nuevo la generación de perfiles en un equipo con más memoria. Se activa esta regla cuando la cantidad de actividad de paginación supera el umbral de regla D0017.|  
|[DA0017: Alta frecuencia de paginación de memoria activa en el disco](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)|Se produjo una tasa relativamente alta de paginación de memoria activa hacia y desde el disco durante la generación de perfiles. Las tasas de paginación en este nivel normalmente afectan al rendimiento y la capacidad de respuesta de la aplicación. Considere la posibilidad de reducir las asignaciones de memoria mediante la revisión de los algoritmos. También es posible que deba tener en cuenta los requisitos de memoria de la aplicación. Intente ejecutar de nuevo la generación de perfiles en un equipo con más memoria.|



