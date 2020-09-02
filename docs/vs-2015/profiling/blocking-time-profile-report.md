---
title: Informe de perfil de tiempo de bloqueo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.blocking
helpviewer_keywords:
- Concurrency Visualizer, Blocking Time Profile Report
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0efeb7fb0eb481d0b8d62ff4a9ebf9daad98c39f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147240"
---
# <a name="blocking-time-profile-report"></a>Informe de perfil de bloqueo de tiempo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los informes de perfil proporcionan datos agregados de tiempo de bloqueo para las pilas de llamadas que son específicas de cada categoría de bloqueo (por ejemplo, "E/S" o "Sincronización"). El informe de adelantamiento enumera los procesos que adelantaron el proceso actual junto con el número de instancias de adelantamiento. Para compilar el informe de perfil de bloqueo, la herramienta recopila las llamadas API de bloqueo y las acumula en un árbol de pilas de llamadas. Los datos que se muestran en estos informes varían según el intervalo de tiempo actual, los subprocesos ocultos y los dos filtros siguientes que se pueden aplicar:  
  
- Si se selecciona Solo mi código, solo se presentan marcos de pila que tienen código del usuario, más un nivel por debajo del código del usuario.  
  
- Si se establece el valor Reducción de nodos irrelevantes, se omiten las pilas recopiladas cuya frecuencia es menor que la especificada.  
  
  Expanda cualquier entrada del árbol de llamadas para buscar la línea de código en que se produce el tiempo de bloqueo. Para localizar la línea de código fuente de una entrada, elija **Ver código fuente** en el menú contextual. Para localizar la línea de código que llamó a este, elija **Ver sitios de llamada** en el menú contextual. Si solo hay un sitio de llamada, el comando se conecta a la línea de código resaltada para el sitio de llamada. Si hay varios sitios de llamada, el comando abre un cuadro de diálogo en que puede seleccionar una entrada y, a continuación, elegir el botón **Ir a código fuente** para localizar el sitio de llamada resaltado. A menudo resulta más útil ver el código fuente para el sitio de llamada que tiene el mayor número de instancias, más tiempo o ambos valores.  
  
## <a name="blocking-time-report-columns"></a>Columnas del informe de tiempo de bloqueo  
 En la siguiente tabla se muestran las columnas de cada informe de tiempo de bloqueo.  
  
|Nombre de columna|Description|  
|-----------------|-----------------|  
|Nombre|El nombre de la función para cada nivel de la pila de llamadas.|  
|Instancias|El número de instancias de la llamada de bloqueo para el período de tiempo visible.|  
|Tiempo de bloqueo inclusivo|El tiempo de bloqueo total que se emplea para todas las pilas comprendidas en este nivel del árbol de pila de llamadas. El número inclusivo es la suma del tiempo de bloqueo exclusivo de esta función y el tiempo de bloqueo exclusivo de todos sus nodos secundarios.|  
|Tiempo de bloqueo exclusivo|El tiempo de bloqueo total que se emplea durante el cual esta función es el nivel más bajo de la pila de llamadas. Una entrada de la pila de llamadas única que tenga un tiempo de bloqueo exclusivo elevado puede ser una función de interés.|  
|Categoría de espera/API|Se muestra solo para las funciones en el nivel más bajo de la pila de llamadas. Cuando se reconoce la firma de la llamada de bloqueo, se proporciona el nombre de la API de bloqueo. Si no se reconoce la firma, se proporciona la información notificada por el kernel.|  
|Detalles|Nombre completo de la función. Esto incluye el recuento de líneas cuando está disponible.|  
  
### <a name="synchronization"></a>Sincronización  
 En el informe de sincronización se muestran las llamadas responsables de los segmentos que bloquean la sincronización y los tiempos de bloqueo agregados de cada pila de llamadas. Para obtener más información, consulte [hora de sincronización](../profiling/synchronization-time.md) .  
  
### <a name="sleep"></a>Sleep  
 El informe Sleep muestra las llamadas responsables del tiempo de bloqueo atribuido al tiempo que se empleó en modo de suspensión y los tiempos de bloqueo agregados de cada pila de llamadas. Para obtener más información, consulte [tiempo de espera](../profiling/sleep-time.md).  
  
### <a name="io"></a>E/S  
 En el informe de E/S se muestran las llamadas responsables de los segmentos que bloquean la E/S y los tiempos de bloqueo agregados de cada pila de llamadas. Para obtener más información, consulte [tiempo de e/s (vista de subprocesos)](../profiling/i-o-time-threads-view.md).  
  
### <a name="memory-management"></a>Administración de memoria  
 En el informe de administración de memoria se muestran las llamadas responsables de los segmentos que bloquean las operaciones de administración de memoria y los tiempos de bloqueo agregados de cada pila de llamadas. Para obtener más información, consulte [Tiempo de administración de memoria](../profiling/memory-management-time.md).  
  
### <a name="preemption"></a>Adelantamiento  
 El informe de adelantamiento enumera los procesos que adelantaron el proceso actual junto con el número de instancias.  Puede expandir cada proceso para ver los subprocesos específicos que reemplazan los subprocesos del proceso actual y ver un desglose de las instancias de adelantamiento por subproceso. Este informe de bloqueo es menos factible que los otros porque el adelantamiento normalmente viene impuesto en el proceso por el sistema operativo, no por un problema en el código. Para obtener más información, consulte [tiempo de adelantamiento](../profiling/preemption-time.md).  
  
### <a name="ui-processing"></a>Procesamiento de IU  
 En el informe de procesamiento de IU se muestran las llamadas responsables de los segmentos de bloqueo que bloquean los bloques de procesamiento de IU y los tiempos de bloqueo agregados de cada pila de llamadas. Para obtener más información, vea tiempo de procesamiento de la [interfaz de usuario](../profiling/ui-processing-time.md).  
  
## <a name="see-also"></a>Consulte también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)
