---
title: "Informe de perfil de bloqueo de tiempo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.blocking"
helpviewer_keywords: 
  - "Visualizador de simultaneidad, informe de perfil de tiempo de bloqueo"
ms.assetid: 3bc45af0-3ba6-4fa3-a336-be8e9ae95107
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Informe de perfil de bloqueo de tiempo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los informes de perfil proporcionan datos agregados del tiempo de bloqueo para las pilas de llamadas específicas de cada categoría de bloqueo \(por ejemplo, "E\/S" o "Sincronización"\).  El informe de preferencia lista los procesos que han adelantado el proceso actual junto con el número de las apariciones de preferencia.  Para compilar el informe de perfil bloqueante, la herramienta recopila las llamadas API de bloqueo y las acumula en un árbol de pilas de llamadas.  Los datos que se muestran en estos informes varían según el intervalo de tiempo actual, según los subprocesos ocultos y los dos filtros siguientes que se pueden aplicar:  
  
-   Si Solo mi código está seleccionado, solo se presentan los marcos de pila que tienen el código de usuario además de un nivel inferior al código de usuario.  
  
-   Si se establece el valor de Reducción de nodos irrelevantes, se omiten las pilas intercaladas que tienen una frecuencia menor que la especificada.  
  
 Expanda cualquier entrada del árbol de llamada para encontrar la línea de código en la que se gasta el tiempo de bloqueo.  Para localizar la línea del código fuente para una entrada, en su acceso directo, elija **Ver fuente**.  Para localizar la línea de código que llamó a ésta, en el acceso directo, elija **Ver sitios de llamada**.  Si sólo hay un sitio de llamada disponible, el comando se conecta con la línea resaltada de código para el sitio de llamada.  Si están disponibles muchos sitios de llamada, el comando abre un cuadro de diálogo en el que se puede seleccionar una entrada y se puede elegir luego el botón **Ir a fuente** para localizar el sitio de llamada resaltado.  Suele ser más útil ver el código de origen del sitio de llamada con el mayor número de apariciones, la mayor parte del tiempo o ambas.  
  
## Columnas del informe de tiempo de bloqueo  
 En la tabla siguiente se muestran las columnas de cada informe de tiempo de bloqueo.  
  
|Nombre de columna|Descripción|  
|-----------------------|-----------------|  
|Name|Nombre de la función para cada nivel de la pila de llamadas.|  
|Instancias|Número de instancias de la llamada de bloqueo en el período de tiempo visible.|  
|Tiempo de bloqueo inclusivo|El tiempo de bloqueo total que transcurre para todas las pilas comprendidas en este nivel del árbol de pila de llamadas.  El número inclusivo es la suma del tiempo de bloqueo exclusivo de esta función y el tiempo de bloqueo exclusivo de todos sus nodos secundarios.|  
|Tiempo de bloqueo exclusivo|El tiempo de bloqueo total que transcurre mientras esta función está en el nivel más bajo de la pila de llamadas.  Una entrada única de la pila de llamadas que tenga un tiempo de bloqueo exclusivo elevado puede ser una función de interés.|  
|Categoría de espera\/API|Solo se muestra para las funciones que se encuentran en el nivel más bajo de la pila de llamadas.  Siempre que se reconoce la firma de la llamada de bloqueo, se proporciona el nombre de la API de bloqueo.  Si no se reconoce la signatura, se proporciona la información proporcionada por el kernel.|  
|Detalles|Nombre completo de la función.  Esto incluye el recuento de líneas cuando está disponible.|  
  
### Sincronización  
 El informe de sincronización muestra las llamadas responsables del bloqueo de sincronización, junto con los tiempos de bloqueo agregados de cada pila de llamadas.  Para obtener más información, vea [Hora de sincronización](../profiling/synchronization-time.md)  
  
### Sleep  
 El informe en suspensión \(Sleep\) muestra las llamadas que son responsables del tiempo de bloqueo atribuido al tiempo dedicado a la suspensión, junto con los tiempos de bloqueo agregados de cada pila de llamadas.  Para obtener más información, vea [Tiempo de suspensión](../profiling/sleep-time.md).  
  
### E\/S  
 El informe de E\/S muestra las llamadas que son responsables del bloqueo de segmentos en la E\/S, junto con los tiempos de bloqueo agregados de cada pila de llamadas.  Para obtener más información, vea [Tiempo de E\/S \(Vista de subprocesos\)](../profiling/i-o-time-threads-view.md).  
  
### Administración de la memoria  
 El informe de administración de memoria muestra las llamadas que son responsables del bloqueo de segmentos en operaciones de administración de memoria, junto con los tiempos de bloqueo agregados de cada pila de llamadas.  Para obtener más información, vea [Tiempo de administración de la memoria](../profiling/memory-management-time.md).  
  
### Adelantamiento  
 El informe de preferencia lista los procesos que han adelantado el proceso actual junto con el número de apariciones.  Se puede expandir cada proceso para ver los subprocesos específicos que reemplazaron a los que están en el proceso actual y para ver una interrupción de las apariciones de preferencia por subproceso.  Este informe de bloqueo es menos procesable que los otros porque, normalmente, la expropiación es impuesta en el proceso por el sistema operativo, no por un problema en el código.  Para obtener más información, vea [Tiempo de adelantamiento](../profiling/preemption-time.md).  
  
### Procesamiento de interfaz de usuario  
 El informe de procesamiento de la interfaz de usuario muestra las llamadas responsables de bloquear los segmentos que están bloqueando los bloques de procesamiento de la IU, junto con los tiempos de bloqueo agregados de cada pila de llamadas.  Para obtener más información, vea [Tiempo de procesamiento de la interfaz de usuario](../profiling/ui-processing-time.md).  
  
## Vea también  
 [Vista de subprocesos](../profiling/threads-view-parallel-performance.md)