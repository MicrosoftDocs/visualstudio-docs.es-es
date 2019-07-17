---
title: Reglas de uso de herramientas de generación de perfiles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 693b43d4a421bd0d0d87fbf485af88573b26adff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68165729"
---
# <a name="profiling-tools-usage-rules"></a>Reglas de uso de herramientas de generación de perfiles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las reglas de rendimiento de la categoría Uso de herramientas de generación de perfiles proporcionan instrucciones para usar el generador de perfiles para recopilar datos de forma más eficaz.  
  
|||  
|-|-|  
|[DA0002: Falta VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md)|La generación de perfiles de línea de comandos podría contener datos incompletos para los binarios de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Esto podría deberse a que no se han establecido las variables de entorno correctas.|  
|[DA0003: Muchas muestras de kernel](../profiling/da0003-many-kernel-samples.md)|Se registraron muchas muestras de generación de perfiles que se produjeron fuera de la ejecución del binario de destino. Para recopilar datos más precisos, considere la posibilidad de utilizar el método de instrumentación.|  
|[DA0004: Uso intenso del procesador](../profiling/da0004-high-processor-usage.md)|Los datos de generación de perfiles sugieren que los procesadores estaban ocupados de manera continuada durante la generación de perfiles. Para recopilar datos más precisos, considere la posibilidad de utilizar el método de muestreo.|  
|[DA0008: Pocos ejemplos recopilados](../profiling/da0008-few-samples-collected.md)|El número de muestras recopiladas en la generación de perfiles no era lo suficientemente alto como para ser estadísticamente significativas. Considere la posibilidad de generar perfiles de nuevo y ejecutar la aplicación durante más tiempo. También puede considerar la posibilidad de utilizar el método de instrumentación para recopilar datos.|  
|[DA0026: Procesamiento excesivo de tiempo de CPU en modo kernel](../profiling/da0026-excessive-kernel-cpu-time-processing.md)|Se ha producido una cantidad considerable de tiempo en la generación de perfiles en el modo de kernel del procesador. Considere la posibilidad de obtener muestras mediante llamadas del sistema como la métrica en lugar de emplear la métrica de tiempo.|  
|[DA0029: Versión de CLR no admitida](../profiling/da0029-unsupported-clr-version.md)|El binario del que se generan perfiles está usando una versión de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] que no es compatible con el generador de perfiles. Los informes del generador de perfiles no pueden resolver nombres de símbolos.|  
|[DA0030: Recopilación de mediciones de interacción de capas para proyectos de base de datos](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md)|Se recopiló un número significativo de llamadas a métodos en el espacio de nombres <xref:System.Data?displayProperty=fullName>. Para incluir datos sobre las llamadas de base de datos, considere la posibilidad de recopilar datos de interacción de capas en los procesos de generación de perfiles.|
