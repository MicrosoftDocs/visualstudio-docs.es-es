---
title: Reglas de uso de herramientas de generación de perfiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: afa7db3b-8c1d-473a-81ac-24ede112a17f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dd7a74f546a7d9ae09767ee79747ce9d7fcaba36
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53961808"
---
# <a name="profiling-tools-usage-rules"></a>Reglas de uso de herramientas de generación de perfiles
Las reglas de rendimiento de la categoría Uso de herramientas de generación de perfiles proporcionan instrucciones para usar el generador de perfiles para recopilar datos de forma más eficaz.  


| | |
| - | - |
| [DA0002: Falta VSPerfCorProf.dll](../profiling/da0002-vsperfcorprof-dll-is-missing.md) | La generación de perfiles de línea de comandos podría contener datos incompletos para los binarios de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Esto podría deberse a que no se han establecido las variables de entorno correctas. |
| [DA0003: Muchas muestras de kernel](../profiling/da0003-many-kernel-samples.md) | Se registraron muchas muestras de generación de perfiles que se produjeron fuera de la ejecución del binario de destino. Para recopilar datos más precisos, considere la posibilidad de utilizar el método de instrumentación. |
| [DA0004: Uso intenso del procesador](../profiling/da0004-high-processor-usage.md) | Los datos de generación de perfiles sugieren que los procesadores estaban ocupados de manera continuada durante la generación de perfiles. Para recopilar datos más precisos, considere la posibilidad de utilizar el método de muestreo. |
| [DA0008: Pocos ejemplos recopilados](../profiling/da0008-few-samples-collected.md) | El número de muestras recopiladas en la generación de perfiles no era lo suficientemente alto como para ser estadísticamente significativas. Considere la posibilidad de generar perfiles de nuevo y ejecutar la aplicación durante más tiempo. También puede considerar la posibilidad de utilizar el método de instrumentación para recopilar datos. |
| [DA0026: Procesamiento excesivo de tiempo de CPU en modo kernel](../profiling/da0026-excessive-kernel-cpu-time-processing.md) | Se ha producido una cantidad considerable de tiempo en la generación de perfiles en el modo de kernel del procesador. Considere la posibilidad de obtener muestras mediante llamadas del sistema como la métrica en lugar de emplear la métrica de tiempo. |
| [DA0029: Versión de CLR no admitida](../profiling/da0029-unsupported-clr-version.md) | El binario del que se generan perfiles está usando una versión de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] que no es compatible con el generador de perfiles. Los informes del generador de perfiles no pueden resolver nombres de símbolos. |
| [DA0030: Recopilación de mediciones de interacción de capas para proyectos de base de datos](../profiling/da0030-gather-tier-interaction-measurements-for-database-projects.md) | Se recopiló un número significativo de llamadas a métodos en el espacio de nombres <xref:System.Data?displayProperty=fullName>. Para incluir datos sobre las llamadas de base de datos, considere la posibilidad de recopilar datos de interacción de capas en los procesos de generación de perfiles. |
