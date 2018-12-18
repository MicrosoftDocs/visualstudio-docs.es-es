---
title: Reglas de rendimiento de la supervisión de recursos | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 258cb329adac23ea1bd463e22a0fd6ada7b526bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745619"
---
# <a name="resource-monitoring-performance-rules"></a>Reglas de rendimiento de la supervisión de recursos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la categoría de supervisión de recursos, los mensajes de rendimiento proporcionan datos adicionales sobre el rendimiento de la aplicación. Puede usar estos datos para analizar problemas de rendimiento. Estas reglas son informativas y se notifican para cada generación de perfiles.  
  
|||  
|-|-|  
|[DA0501: Promedio de consumo de CPU del proceso del que se está generando el perfil](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Este mensaje indica el porcentaje de tiempo que un procesador estuvo ocupado ejecutando instrucciones de la aplicación. El valor notificado es el promedio de todos los intervalos de medición en que estuvo activo el proceso del que se está generando el perfil.|  
|[DA0502: Consumo máximo de CPU del proceso del que se está generando el perfil](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Este mensaje indica el porcentaje de tiempo máximo que un procesador estuvo ocupado ejecutando instrucciones de la aplicación. El valor notificado es el valor máximo notificado entre todos los intervalos de medición en que estuvo activo el proceso del que se está generando el perfil.|  
|[DA0503: Promedio de espacio de trabajo en bytes para el proceso del que se está generando el perfil](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Este mensaje indica la cantidad media de memoria física, en bytes, que el proceso estaba usando mientras la generación de perfiles estaba activa. Esta medida de memoria física se conoce como el espacio de trabajo.|  
|[DA0504: Espacio de trabajo máximo en bytes para el proceso del que se está generando el perfil](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Este mensaje indica la cantidad máxima de memoria física, en bytes, que el proceso estaba usando mientras la generación de perfiles estaba activa.|  
|[DA0505: Promedio de bytes privados asignados para el proceso del que se está generando el perfil](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Este mensaje indica la cantidad media de memoria virtual que el proceso asignó en bytes mientras la generación de perfiles estaba activa. Esta medida de memoria virtual se conoce como *bytes privados*. Los bytes privados representan las ubicaciones de memoria virtual asignadas por el proceso a las que solo pueden acceder los subprocesos que se ejecutan dentro del proceso.|  
|[DA0506: Máximo de bytes privados asignados para el proceso del que se está generando el perfil](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Este mensaje indica la cantidad máxima de memoria virtual que el proceso asignó en bytes privados mientras la generación de perfiles estaba activa.|



